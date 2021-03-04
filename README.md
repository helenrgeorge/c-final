# c-final
Calculate date and save in CSV file

using System;
using System.Linq;

namespace Programming_Final_George
{
    class NoiseGen
    { 
        static double[] cleandata = new double [100];
        static double[] noisydata = new double [100];
        static double noiseFactor = .07;

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

            for (double a = 0; a < 100; a++)
            {
                double b = a / 100;
                cleandata[c] = Math.Sin(b);
                c = c + 1;
         
            }

            addNoise();
            printTable();

        }

        static void addNoise()
        {

            for (int a = 0; a < 100; a++)
            {
                noisydata[a] = (cleandata[a]) + (randomNumbers.NextDouble() * (noiseFactor - (-1 * noiseFactor)) + (-1 * noiseFactor));
            }
        }

        static void printTable ()
        {
            for (int a = 0; a < 100; a++)
            {
                Console.WriteLine(a + "\t" + cleandata[a] + "\t" + noisydata[a]);

            }
        }

        static void Main(string[] args)
        {

            NoiseGen myobj = new NoiseGen();
            getValues();
        }
    }
}

