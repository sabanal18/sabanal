using System;

public struct Time
{
    private readonly int minutes;

    public Time(int hh, int mm)
    {
        if (hh < 0 || hh > 23 || mm < 0 || mm > 59)
        {
            throw new ArgumentException("Invalid time");
        }
        this.minutes = 60 * hh + mm;
    }

    public int Hour => minutes / 60;
    public int Minute => minutes % 60;

    public override string ToString()
    {
        return $"{Hour:D2}:{Minute:D2}";
    }
}

class Program
{
    static void Main()
    {
        Time time1 = new Time(10, 5);
        Time time2 = new Time(0, 45);
        Time time3 = new Time(23, 45);

        Console.WriteLine("Time 1: " + time1);
        Console.WriteLine("Time 2: " + time2);
        Console.WriteLine("Time 3: " + time3);

        Console.WriteLine("Time 1 Hour: " + time1.Hour);
        Console.WriteLine("Time 1 Minute: " + time1.Minute);
        Console.WriteLine("Time 3 Hour: " + time3.Hour);
        Console.WriteLine("Time 3 Minute: " + time3.Minute);
    }
}
