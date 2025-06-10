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

    public Time(int totalMinutes)
    {
        int hours = totalMinutes / 60 % 24;
        int mins = totalMinutes % 60;
        this.minutes = hours * 60 + mins;
    }

    public int Hour => minutes / 60;
    public int Minute => minutes % 60;

    public override string ToString()
    {
        return $"{Hour:D2}:{Minute:D2}";
    }

    public static Time operator +(Time t1, Time t2)
    {
        return new Time(t1.minutes + t2.minutes);
    }

    public static Time operator -(Time t1, Time t2)
    {
        return new Time(t1.minutes - t2.minutes);
    }
}

class Program
{
    static void Main()
    {
        Time time1 = new Time(10, 30);
        Time time2 = new Time(2, 45);

        Time sum = time1 + time2;
        Time difference = time1 - time2;

        Console.WriteLine("Time 1: " + time1);
        Console.WriteLine("Time 2: " + time2);
        Console.WriteLine("Sum: " + sum);
        Console.WriteLine("Difference: " + difference);
    }
}
