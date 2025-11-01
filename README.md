# MultiThreadRandOddEven
In this program we used three threads. first thread generates random integer for every 1 second and if the value is even, the second thread computes the square of the number and prints. If the value is odd, the third thread will print the value of cube of the number.
import java.util.Random;

class EvenNum implements Runnable
{
	public int a;
	public EvenNum(int a)
	
	{
		this.a=a;
		
	}
    public void run()
    {
    	System.out.println("the thread"+a+"is EVEN and square of"+a+"is:"+a*a);
    	
    }
}
//class for odd number
class OddNum implements Runnable
{
	public int a;
	public OddNum(int a)
	{
		this.a=a;
	}
   public void run()
   {
	   System.out.println("The Thread "+a+" is odd and cube of "+a+" is: "+a*a*a);

   }
   
}
class RandomNumGenerator extends Thread 
{
	public void run()
	{
		int n=0;
		Random rand = new Random();
		try
		{
			for(int i=0;i<10;i++)
			{
				n=rand.nextInt(20);
				System.out.println("Generation Number is "+n);
				if (n%2==0)
				{
					Thread thread1= new Thread(new EvenNum(n));
					thread1.start();
					
				}
				else
				{
					Thread thread2 =new Thread(new OddNum(n));
					thread2.start();
				}
				     Thread.sleep(1000);
				     System.out.println("      ");
				}
		}catch(Exception ex ) {
			System.out.println("ex getmessage()");
			
			}
		}
	}



public class MultiThreadRandOddEven {
	 

	public static void main(String[] args) {
	
		
		RandomNumGenerator rand_num =new RandomNumGenerator();
		rand_num.start();
	}

}
