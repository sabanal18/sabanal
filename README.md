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

    public override string ToString()
    {
        int hours = minutes / 60;
        int mins = minutes % 60;
        return $"{hours:D2}:{mins:D2} ({minutes} minutes since midnight)";
    }
}

class Program
{
    static void Main()
    {
        Time time1 = new Time(10, 5);
        Time time2 = new Time(0, 45);

        Console.WriteLine("Time 1: " + time1);
        Console.WriteLine("Time 2: " + time2);
    }
}
