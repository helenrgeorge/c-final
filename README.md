# c-final
using System;
using System.Linq;

namespace Programming_Final_George
{
    class NoiseGen
    {
        static double[] cleandata = new double [100];
        static double[] noisydata = new double [100];
        static double noiseFactor = .07;

        // create random object and seed with 243

        static Random randomNumbers = new Random(243);

        
        NoiseGen()
        {
           
        }

        NoiseGen(double input)
        {
            noiseFactor = input;
        }


        static void getValues()
        {

   

            // calculate clean data

            for (int a = 0; a < 100; a++)
            {
                double b = (double)a / 100;
                cleandata[a] = Math.Sin(b);

            }

            addNoise();
            printTable();

        }

        // calculate noisy data

      
        static void addNoise()
        {

            for (int a = 0; a < 100; a++)
            {
                noisydata[a] = (cleandata[a]) + (randomNumbers.NextDouble() * (noiseFactor - (-1 * noiseFactor)) + (-1 * noiseFactor));
            }
        }

        // print both arrays and their positions

        static void printTable ()
        {
            Console.WriteLine("Element" + "," + "Clean" + "," + "Noisy");
            for (int a = 0; a < 100; a++)
            {
                Console.WriteLine(a + "," + cleandata[a] + "," + noisydata[a]);

            }
        }

        static void Main(string[] args)
        {

            try
            {
                Console.Write("Enter the new noise factor: ");

                double input = Convert.ToDouble(Console.ReadLine());
                NoiseGen myobj = new NoiseGen(input);
            }

            catch
            {
                NoiseGen myobj = new NoiseGen();
            }
         

            // call method
            getValues();
        }
    }
}
