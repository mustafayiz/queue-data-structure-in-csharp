```csharp
using System;

namespace Queue
{
    //Queue class
    class Queue
    {
        private int[] queue; //Queue(Kuyruk) elemanlarını tutacak dizi
        private int front; //Queue başındaki verinin indeksi
        private int rear; //Queue sonundaki verinin indeksi
        private int capacity; //Queue maksimum eleman kapasitesi

        /*
            Queue tanımlamalarını bu metod da yapıyoruz.
            maxSize Queue oluşturulurken bizim tarafımızdan belirlenecek maksimum kapasitedir.
        */
        public Queue(int maxSize)
        {
            capacity = maxSize; //maxSize değişkenini capacity'e atıyoruz.
            queue = new int[capacity]; //Queue boyutu artık belirlediğimiz Array[capacity] kadar olacak burada onun tanımlamasını yaptık.
            front = 0; //Queue başı başlangıçta 0 değeri alır.
            rear = -1; //Kuyruğun sonu başlangıçta -1 değeri alır bu kuyruğun boş olduğunu belirtir.
        }

        /*
            Enqueue metodu Queue(Kuyruk) eleman ekler
            data değişkeni Queue oluşturduktan sonra gireceğimiz verileri temsil eder.
        */
        public void Enqueue(int data)
        {
            if (rear == capacity - 1) //Eğer Queue doluysa
            {
                Console.WriteLine("Queue dolu!"); //Bu hatayı ekrana yazdırır.
                return;       
            }

            rear++; //Queue dolu değilse rear bir artar ve veri eklemek için alan açılmış olur.
            queue[rear] = data; //data değişenindeki veri queue[rear]'a aktarılır ve Queue'ya veri eklenir. 
        }

        //Dequeue metodu Queue'dan veri çıkartır. FIFO kuralına göre kuyruğa ilk eklenen veri çıkartılır.
        public void Dequeue()
        {
            if (front > rear) //Eğer Queue boşsa yani Queue'daki verilerin hepsi FIFO kuralına göre hep ilk veriler çıktığı için front değeri rear değerinden büyükse kuyruk mantıken boş olur
            {
                Console.WriteLine("Queue boş!"); //Bu hatayı ekrana yazdırır.
                return;
            }
            
            front++; //Queue'yi bir arttırıyoruz. Yani gerçek hayattaki gibi sıra'dan bir kişi çıktığında sıradaki kişiler biraz daha ilerliyor gibi.
        }

        //Peek metodu Queue'nun en başındaki(ilk) verisini gösterir.
        public int Peek()
        {
            if (front > rear) //Queue boş ise
            {
                Console.WriteLine("Queue boş!"); //Bu hatayı ekrana yazdırır.
                return -1;
            }
            
            return queue[front]; //Queue'nun ilk verisini dönderir.
        }

        //Print metodu tüm Queue verilerini ekrana yazdırır.
        public void Print()
        {
            if (front > rear) //Queue boş ise
            {
                Console.WriteLine("Queue Boş"); //Bu hatayı ekrana yazdır
            }
            else // Queue boş değil ise
            {
                for (int i = rear; i >= front; i--)
                {
                    Console.WriteLine(queue[i]); // Tüm verileri ekrana yazdır.
                }
            }
        }
    }

    class Program
    {
        static void Main()
        {
            Queue queue = new Queue(5); //5 elemanlı bir Queue başlattık.
            queue.Enqueue(1); //1 Queue'ya eklendi
            queue.Enqueue(2);
            queue.Enqueue(3);
            queue.Enqueue(4);
            queue.Enqueue(5);
            queue.Print();  //Tüm veriler ekrana yazdırıldı.
            Console.WriteLine("----------");
            queue.Dequeue(); //Queue'ya ilk eklenen veri (1) çıkartıldı.
            queue.Dequeue(); //Ondan sonra eklenen veri (2) çıkartıldı.
            queue.Print();
            Console.ReadKey();

        }
    } 
}
```
