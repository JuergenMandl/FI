# FI
Homework


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.Entity;


namespace NewDatabase

{
    class Program
    {
        static void Main(string[] args)
        {


            using (var db = new CatContext())
            {


               
                Console.Write("Enter a name for a new housewife: ");
               
                var name = Console.ReadLine();




                var housewife = new housewife { Name = name };
               
                db.housewife.Add(housewife);
               
                db.SaveChanges();





                var query = from b in db.housewifes
                            orderby b.Name
                            select b;




                Console.WriteLine("All housewifes in the database:");
                
                foreach (var item in query)
               
                
                {
                    Console.WriteLine(item.Name);
                }

                
                
                
                Console.WriteLine("Press any key to exit...");
                Console.ReadKey();
            } 
        }
   
    
    }

   
    
    public class housewife
    
    {
       
        public int housewifeId { get; set; }
        
        public string Name { get; set; }

        public virtual List<hoover> hoovers { get; set; }
    
    }

   
    public class hoover
    
    {
      
        public int hooverId { get; set; }
     
        public string Name { get; set; }

        public int hooverId { get; set; }
      
        public virtual hoover hoover { get; set; }
   
    }

   
    public class hooverContext : DbContext
    
    {
      
        public DbSet<housewife> housewifes { get; set; }
      
        public DbSet<hoover> hoovers { get; set; }
    
    }
}
