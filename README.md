using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace EventdelegatePRoj

    
{  
    public delegate void CheckID();



internal class Worker
    {
            static public event EventHandler  CheckIDEvent; 

        public string _workeType
        { get; private set; }   

        public string _workerId
        { get; private set; }   

        public int _workerPay
        { get; private set; }

        public static int _workerCount
        { get; private set; }

        public int  _inWorkerCount
        { get; private set; }   

        public static new List<Worker> _workers = new List<Worker>();

        public Worker( string WorkType, string WorkerId, int workerPay)
        {
            _workeType = WorkType;
            _workerId = WorkerId;
            _workerPay = workerPay;
            _workerCount++;
            _inWorkerCount++;
            _inWorkerCount -= 1;

            _workers.Add(new Worker(WorkType, WorkerId, workerPay, true));


        }

        public Worker(string WorkType, string WorkerId, int workerPay, bool trues)
        {    
            _workeType = WorkType;
            _workerId = WorkerId;
            _workerPay = workerPay;
            

        }

        public override string ToString()
        {
            return $"\nWorker ID - {_workerId}\nWorker Type - {_workeType}\nMonthly Payment - {_workerPay}";
        }

          static public void CheckID()
        {

            var args = new EventArgs();
            CheckIDEvent?.Invoke(Worker.CheckIDEvent,null);
        }



       


    }
}
