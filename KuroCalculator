using System;
using System.Diagnostics;

namespace KuroCalculator
{
    class Program
    {
        //Physics Variables
        public const double INITIAL_VALUE = -12345.6789;
        public static double X_O = INITIAL_VALUE;
        public static double X_F = INITIAL_VALUE;
        public static double V_O = INITIAL_VALUE;
        public static double V_F = INITIAL_VALUE;
        public static double A = INITIAL_VALUE;
        public static double T = INITIAL_VALUE;

        //Turn System on;
        public static bool systemPower = true;
        public static int iteration = 0;

        static void Main(string[] args)
        {
            //Prompt User Input
            Console.WriteLine("Enter Password:");

            //CheckPassword
            string userInput = Console.ReadLine(); //Reads entire line HINT: Console.ReadKey = Reads single key
            if (userInput.Equals("jtk"))
            {
                //***If your reading this password in C#, then good job you deserve use this calculator***
                Console.WriteLine("Welcome to Secret Kuro Calculator");
            }
            else
            {
                Console.WriteLine("Failed Password");
                systemPower = false;
            }

            //Engage System, while power is on
            while (systemPower)
            {
                Physics();

                Outro();
            }
        }
        static void Physics()
        {
            Console.WriteLine("Here you can solve any basic physics kinematics equations!!!");
            Console.WriteLine();
            Console.WriteLine("Enter the following variables:      (while hitting enter between)");
            Console.WriteLine("Xo, Xf, Vo, Vf, A, T                (Enter -1 for unknown) ");
            Console.WriteLine();
            Console.WriteLine("Units Xo = m, Vo = m/s, A=m/s^2,    (m=meters, s=seconds)");
            Console.WriteLine("      Xf = m, Vf = m/s,  T=s");
            Console.WriteLine();
            Console.WriteLine("    Xo, Xf, Vo, Vf,  A, T");
            Console.WriteLine("Ex.  0, -1,  0, -1, 10, 5");
            Console.WriteLine();

            //User Input
            bool collectedValues = false;
            while (!collectedValues)
            {
                //Check and run!
                collectedValues = CollectUserVariables();

                if (collectedValues)
                {
                    Console.WriteLine("Got'em all!");
                    Console.WriteLine();
                }
                else
                {
                    Console.WriteLine("Hmmm, I wrote those down but lets do that one more time.");
                    Console.WriteLine();
                }
            }

            //Calculate
            CalculateSolution();

            systemPower = false;
        }
        static void Outro()
        {
            Console.WriteLine();
            Console.WriteLine("Want to play again?)");
            Console.WriteLine();

            string userInput = Console.ReadLine();
            userInput = userInput.ToLower();
            if (userInput.Equals("n"))
            {
                systemPower = false;
                Console.WriteLine("GoodBye!!!)");
            }

            resetVariables();
        }
        

        //Gather User Input
        static bool CollectUserVariables()
        {
            //Set Variables
            Console.WriteLine("Enter Xo = ");
            string XoInput = Console.ReadLine();
            if (X_O == INITIAL_VALUE)
            {
                X_O = Double.Parse(XoInput);
            }
            Console.WriteLine("Enter Xf = ");
            string XfInput = Console.ReadLine();
            if (X_F == INITIAL_VALUE)
            {
                X_F = Double.Parse(XfInput);
            }
            Console.WriteLine("Enter Vo = ");
            string VoInput = Console.ReadLine();
            if (V_O == INITIAL_VALUE)
            {
                V_O = Double.Parse(VoInput);
            }
            Console.WriteLine("Enter Vf = ");
            string VfInput = Console.ReadLine();
            if (V_F == INITIAL_VALUE)
            {
                V_F = Double.Parse(VfInput);
            }
            Console.WriteLine("Enter A = ");
            string AInput = Console.ReadLine();
            if (A == INITIAL_VALUE)
            {
                A = Double.Parse(AInput);
            }
            Console.WriteLine("Enter T = ");
            string TInput = Console.ReadLine();
            if (T == INITIAL_VALUE)
            {
                T = Double.Parse(TInput);
            }

            //Check Null Variables
            if (X_O != INITIAL_VALUE || X_F != INITIAL_VALUE || V_O != INITIAL_VALUE || V_F != INITIAL_VALUE || A != INITIAL_VALUE || T != INITIAL_VALUE)
            {
                return true;
            }
            return false;
        }

        //Physics Procedure
        static void CalculateSolution()
        {

            //loop
            bool calculating = true;
            while (calculating) {
                //Record initial values
                double _X_O = X_O;
                double _X_F = X_F;
                double _V_O = V_O;
                double _V_F = V_F;
                double _A = A;
                double _T = T;
                double unknown = -1;

                    //Run equations!
                //Establish Initial Position
                if (X_O == unknown && X_F == unknown)
                {
                    X_O = 0;                                      //Establish Initial Position
                }

                //Solve for Initial Velocity
                if (V_O == unknown && V_F != unknown && A != unknown && T != unknown)
                {
                    V_O = returnInitialVelocity(V_F, A, T);            //Solve for Initial Velocity
                }
                if (V_O == unknown && X_O != unknown && X_F != unknown && A != unknown && T != unknown)
                {
                    V_O = returnInitialVelocity(X_O, X_F, A, T);       //Solve for Initial Velocity
                }
                if (V_O == unknown && X_O != unknown && X_F != unknown && V_F != unknown && A != unknown)
                {
                    V_O = returnInitialVelocityTwo(X_O, X_F, V_F, A);  //Solve for Initial Velocity
                }
                if (V_O == unknown && X_O != unknown && X_F != unknown && V_F != unknown && T != unknown)
                {
                    V_O = returnInitialVelocityThree(X_O, X_F, V_F, T);//Solve for Initial Velocity
                }


                //Solve for Final Velocity
                if (V_F == unknown && X_O != unknown && X_F != unknown && V_O != unknown && A != unknown)
                {
                    V_F = returnFinalVelocity(X_O, X_F, V_O, A);       //Solve for Final Velocity
                }
                if (V_F == unknown && V_O != unknown && A != unknown && T != unknown)
                {
                    V_F = returnFinalVelocity(V_O, A, T);              //Solve for Final Velocity
                }


                //Solve for Final Position
                if (X_F == unknown && V_O != unknown && V_F != unknown && A != unknown)
                {
                    X_F = returnFinalPosition(V_O, V_F, A);            //Solve for Final Position
                }
                if (X_F == unknown && X_O != unknown && V_O != unknown && A != unknown && T != unknown)
                {
                    X_F = returnFinalPosition(X_O, V_O, A, T);         //Solve for Final Position
                }
                if (X_F == unknown && V_O != unknown && V_F != unknown && T != unknown)
                {
                    X_F = returnFinalPositionTwo(V_O, V_F, T);         //Solve for Final Position
                }

                //Solve for Acceleration
                if (A == unknown && X_O != unknown && X_F != unknown && V_O != unknown && V_F != unknown)
                {
                    A = returnAcceleration(V_O, V_F, X_O, X_F);        //Solve for Acceleration
                }
                if (A == unknown && V_O != unknown && V_F != unknown && T != unknown)
                {
                    A = returnAcceleration(V_O, V_F, T);               //Solve for Acceleration
                }
                if (A == unknown && X_O != unknown && X_F != unknown && V_O != unknown && T != unknown)
                {
                    A = returnAccelerationTwo(X_O, X_F, V_O, T);       //Solve for Acceleration
                }

                //Solve for time
                if (T == unknown && X_O != unknown && X_F != unknown && V_O != unknown && A != unknown) {
                    T = returnTime(X_O, X_F, V_O, A);
                }


                //Check if equations have changed
                if (_X_O == X_O && _X_F == X_F && _V_O == V_O && _V_F == V_F && _A == A && _T == T)
                {
                    //If no change since recorded, exit loop
                    calculating = false;
                }

                //Print
                iteration++;
                printVariableReport();
            }
        }
        static void printVariableReport()
        {
            Console.WriteLine();
            Console.WriteLine("-----------------"+iteration+"-------------------");
            Console.WriteLine("Initial Position = " + X_O);
            Console.WriteLine("Final Position   = " + X_F);
            Console.WriteLine("Initial Velocity = " + V_O);
            Console.WriteLine("Final Velocity   = " + V_F);
            Console.WriteLine("Acceleration     = " + A);
            Console.WriteLine("Time             = " + T);
            Console.WriteLine("--------------------------------------");
        }
        static void resetVariables()
        {
            X_O = INITIAL_VALUE;
            X_F = INITIAL_VALUE;
            V_O = INITIAL_VALUE;
            V_F = INITIAL_VALUE;
            A = INITIAL_VALUE;
            T = INITIAL_VALUE;
        }

        //Formulas
        static double returnFinalPosition(double Xo, double Vo, double A, double T)
        {
            double finalPosition = Xo + Vo * T + 0.5 * A * T * T;

            return finalPosition;
        }
        static double returnFinalPosition(double Vo, double Vf, double A)
        {
            double finalPosition = ((Vf*Vf)-(Vo*Vo)) / (2*A);

            return finalPosition;
        }
        static double returnFinalPositionTwo(double Vo, double Vf, double T)
        {
            double finalPosition = T*((Vo+Vf)/2);

            return finalPosition;
        }
        static double returnInitialVelocity(double Vf, double A, double T)
        {
            double initialVelocity = A * T - Vf;

            return initialVelocity;
        }
        static double returnInitialVelocity(double Xo, double Xf, double A, double T)
        {
            double initialVelocity = ((Xf-Xo) - (0.5*A*T*T)) / T;

            return initialVelocity;
        }
        static double returnInitialVelocityTwo(double Xo, double Xf, double Vf, double A)
        {
            double initialVelocity = (Vf*Vf) - (2*A*(Xf-Xo));
            initialVelocity = Math.Sqrt(initialVelocity);
            return initialVelocity;
        }
        static double returnInitialVelocityThree(double Xo, double Xf, double Vf, double T)
        {
            double initialVelocity = (((Xf-Xo)*2)/T) - Vf;

            return initialVelocity;
        }
        static double returnFinalVelocity(double Xo, double Xf, double Vo, double A)
        {
            double finalVelocity = Vo * Vo + 2 * A * (Xf - Xo);
            finalVelocity = Math.Sqrt(finalVelocity);

            return finalVelocity;
        }
        static double returnFinalVelocity(double Vo, double A, double T)
        {
            double finalVelocity = Vo + A * T;
            
            return finalVelocity;
        }
        static double returnAcceleration(double Vo, double Vf, double Xo, double Xf)
        {
            double acceleration = ((Vf*Vf) - (Vo*Vo)) / (2*(Xf-Xo));

            return acceleration;
        }
        static double returnAcceleration(double Vo, double Vf, double T)
        {
            double acceleration = (Vf - Vo) / (T);

            return acceleration;
        }
        static double returnAccelerationTwo(double Xo, double Xf, double Vo, double T)
        {
            double acceleration = ((Xf-Xo) - (Vo*T)) / (0.5*T*T);

            return acceleration;
        }
        static double returnTime(double Xo, double Xf, double Vo, double A)
        {
            double time = ((-Vo)+Math.Sqrt((Vo*Vo)+(2*A*(Xf-Xo))))/ A;

            return time;
        }
    }
}
