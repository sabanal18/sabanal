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

    public static implicit operator Time(int minutes)
    {
        return new Time(minutes);
    }

    public static explicit operator int(Time time)
    {
        return time.minutes;
    }
}

class Program
{
    static void Main()
    {
        Time time1 = new Time(10, 30);
        Time time2 = 605; // implicit conversion from int to Time

        Console.WriteLine("Time 1: " + time1);
        Console.WriteLine("Time 2: " + time2);

        int minutes = (int)time1; // explicit conversion from Time to int
        Console.WriteLine("Time 1 in minutes: " + minutes);
    }
}
