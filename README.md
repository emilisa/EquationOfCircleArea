EquationOfCircleArea
====================

Check if the given point is IN the circle area

using System;

using System;

class EquationOfCircle
{
    static void Main() 
    
    // Formulas from - en.wikipedia.org/wiki/Circle (Cartesian coordinates: set of all points (x, y) that form the circle
    
    {
        while (true)
        {
            Console.Title = "EquationOfCircle";
            
            Console.WriteLine("Type two numbers to check if they are in given circle Area:");
            Console.ForegroundColor = ConsoleColor.Yellow;
            double x = double.Parse(Console.ReadLine());
            double y = double.Parse(Console.ReadLine());
            Console.ResetColor();

            // x and y are coordinates of random given point for witch we will determine if it is:
            // - IN the circle area (WITHIN according to Circumference of the circle) // Circumference: ПЕРИФЕРИЯ (окръжност, обиколка на кръг)
            // - OUT of the circle area (WITHOUT according to Circumference of the circle)
            // - ON Circumference of the circle (Cartesian coordinates)

            double a = 0d;  // centre coordinate a of the circle
            double b = 0d;  // centre coordinate b of the circle
            double r = 30d;  // radius r of the circle

            bool onCircumference = ((r * r) == (((x - a) * (x - a)) + ((y - b) * (y - b)))); // Equations - Cartesian coordinates

            bool inTheCircle = ((r * r) > (((x - a) * (x - a)) + ((y - b) * (y - b))));

            bool outTheCircle = ((r * r) < (((x - a) * (x - a)) + ((y - b) * (y - b))));

            // Note: that points a and b are part of the coordinate system x, y, just named differently for ease of calculations
            // In the output points a and b are renamed as x and y - 
            // to confirm that circle and the point are part of one and the same coordinate system

            if (onCircumference == true) // Check if the given point is on the Circumference
            {
                Console.ForegroundColor = ConsoleColor.Yellow;
                Console.WriteLine("Point with coordinates x={0}, y={1} is ON Circumference of the circle", x, y);
                Console.ResetColor();
                Console.WriteLine();
                Console.WriteLine("Circle details - Center coordinates: x={0}, y={1}, Radius={2}", a, b, r);
                Console.WriteLine();
                Console.WriteLine("Circumference: ПЕРИФЕРИЯ (окръжност, обиколка на кръг)");
            }

            if (inTheCircle == true) // Check if the given point is IN  the circle area
            {
                double xCircumference_1 = Math.Sqrt((r * r) - (y * y));
                double yCircumference_1 = Math.Sqrt((r * r) - (x * x));

                Console.ForegroundColor = ConsoleColor.Yellow;
                Console.WriteLine("Point with coordinates x={0}, y={1} is IN circle area", x, y);
                Console.ResetColor();
                Console.WriteLine();
                Console.WriteLine("Circle details - Center coordinates: x={0}, y={1}, Radius={2}", a, b, r);
                Console.WriteLine();
                Console.WriteLine("Point can be ON Circumference of the circle if:");
                Console.WriteLine("x={0}, but Y={1} also Y=-{1}", x, yCircumference_1, yCircumference_1);
                Console.WriteLine("OR");
                Console.WriteLine("y={0}, but X={1} also X=-{1}", y, xCircumference_1, xCircumference_1);
            }

            if (outTheCircle == true) // Check if the given point is OUT the circle area
            {
                double xCircumference_2 = 0;
                double yCircumference_2 = 0;

                Console.ForegroundColor = ConsoleColor.Yellow;
                Console.WriteLine("Point with coordinates x={0}, y={1} is OUT of circle area", x, y);
                Console.ResetColor();
                Console.WriteLine();
                Console.WriteLine("Circle details - Center coordinates: x={0}, y={1}, Radius={2}", a, b, r);
                Console.WriteLine();
                Console.WriteLine("Point can be ON Circumference of the circle if:");

                if (r <= x && r >= y && r >= y * (-1))
                {
                    xCircumference_2 = Math.Sqrt((r * r) - (y * y));

                    Console.WriteLine("y={0}, but X={1} also X=-{1}", y, xCircumference_2);

                    if (r == x)
                    {
                        Console.WriteLine("AND x={0}, but Y=0", x);
                    }

                    else
                    {
                        Console.WriteLine("if x={0}, point will NEVER be in circle area", x);
                    }
                }

                if (r >= x && r <= y && r >= x * (-1))
                {
                    yCircumference_2 = Math.Sqrt((r * r) - (x * x));

                    Console.WriteLine("x={0}, but Y={1} also Y=-{1} ", x, yCircumference_2);

                    if (r == y)
                    {
                        Console.WriteLine("AND y={0}, but X=0", y);
                    }

                    else
                    {
                        Console.WriteLine("if y={0}, point will NEVER be in circle area", y);
                    }
                }

                if (r <= x && r <= y || r <= x * (-1) && r <= y * (-1))
                {
                    Console.WriteLine("Exception_1");
                    Console.WriteLine("X={0} also X=-{0}, but Y=0", r);
                    Console.WriteLine("Y={0} also Y=-{0}, but X=0", r);
                }

                if (r <= x * (-1) && r <= y)
                {
                    Console.WriteLine("Exception_2");
                    Console.WriteLine("X={0} also X=-{0}, but Y=0", r);
                    Console.WriteLine("Y={0} also Y=-{0}, but X=0", r);
                }

                if (r <= y * (-1) && r <= x)
                {
                    Console.WriteLine("Exception_3");
                    Console.WriteLine("X={0} also X=-{0}, but Y=0", r);
                    Console.WriteLine("Y={0} also Y=-{0}, but X=0", r);
                }
            }
        }
    }
}
