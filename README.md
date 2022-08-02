
using EventdelegatePRoj;


Worker GegaWork = new Worker("Smith","0401",2750);



Worker MishaWork = new Worker("Smith", "0401", 2750);



Worker ZukaWork = new Worker("Hardware support", "0901", 3200);

Worker.CheckIDEvent += Worker_CheckIDEvent;

Worker.CheckID();


void Worker_CheckIDEvent(object? sender, EventArgs e)
{


    for (int a = 0; a < Worker._workerCount; a++)
    {
        int IDrepeatedamount = 0;
        foreach (var worker in Worker._workers)
        {
            if (Worker._workers[a]._workerId == worker._workerId)
            {
                IDrepeatedamount++;
            }
        }


        if (IDrepeatedamount > 1)
        {
            Console.WriteLine("Alert, there are more than one user with the same ID !");
        }


    }
}
