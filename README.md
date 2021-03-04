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

        // create randome object and seed with 243

        static Random randomNumbers = new Random(243);

        NoiseGen()
        {

        }

        NoiseGen(double input)
        {

        }

        
        static void getValues()
        {
            int c = 0;

            // calculate clean data

            for (double a = 0; a < 100; a++)
            {
                double b = a / 100;
                cleandata[c] = Math.Sin(b);
                c = c + 1;
         
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
            for (int a = 0; a < 100; a++)
            {
                Console.WriteLine(a + "\t" + cleandata[a] + "\t" + noisydata[a]);

            }
        }

        static void Main(string[] args)
        {
            // Create noisegen object
            NoiseGen myobj = new NoiseGen();

            // call method
            getValues();
        }
    }
}
