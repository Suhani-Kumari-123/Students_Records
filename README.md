# Students_Records

import java.util.*;
class Student_record {
    private int SId;
    private String Sname;
    private String Department;
    private int Sphone;
    private int Year;

    Student_record(int SId, String sname, String Department, int Sphone, int year){
        //this keyword refers to the current object in method or constructor.
        this.SId =SId;
        this.Sname =sname;
        this.Department=Department;
        this.Sphone=Sphone;
        this.Year=year;
    }
    //Returns the value of the current element of the sequence.
    public int getSId(){
        return SId;
    }
    public String getSname(){
        return Sname;
    }
    public String getDepartment(){
        return Department;
    }
    public int getSphone(){
        return Sphone;
    }
    public int getYear(){
        return Year;
    }
    //serialization 
    public String toString(){
        return ""+SId+" "+Sname+" "+Department+" "+Sphone+" "+Year+"";
    }}
    /**
     *
     */
    class list{
        public static void main(String[] args){
            List<Student_record>c=new ArrayList<Student_record>();
            Scanner input= new Scanner(System.in);
            Scanner input1=new Scanner(System.in);
            int i;
            do{
                System.out.println("\t\t\t_____________________________________________________");
                System.out.println("\t\t\t_____________________________________________________");
                System.out.println("\t\t\t\t\tSTUDENT's RECORDS");
                System.out.println("\t\t\t_____________________________________________________");
                System.out.println("\t\t\t_____________________________________________________\n");
                System.out.println("[Q] What you want to do with this Record?\n");
                System.out.println("....................................................");
                System.out.println("[1] Insert the new record of Student");
                System.out.println("....................................................");
                System.out.println("[2] Display the record of whole Students");
                System.out.println("....................................................");
                System.out.println("[3] Search the record of any particalar Student");
                System.out.println("....................................................");
                System.out.println("[4] Delete the particular records any Student");
                System.out.println("....................................................");
                System.out.println("[5] Update the record of a particular Student");
                System.out.println("----------------------------------------------------------------------------------------------\n");
                System.out.print("\t\t\t\t\tEnter Your Choice\n");
                System.out.println("\t\t\t\t________________________________\n");
                i=input.nextInt();
                switch(i){
                    case 1:
                    System.out.println("----------------------");
                    System.out.print("\nEnter the Student URoll Number: ");
                    int SId= input.nextInt();
                    System.out.print("Enter Student name: ");
                    String Sname =input1.nextLine();
                    System.out.print("Enter the Department of the Student: ");
                    String Sdep= input1.nextLine();
                    System.out.print("Enter the Phone number of the student: ");
                    int Sphone= input.nextInt();
                    System.out.print("Mention the Year of the student:");
                    int Year= input.nextInt();

                    c.add( new Student_record(SId,Sname,Sdep,Sphone,Year));
                    break;
                    case 2:
                    System.out.println("________________________________________________");
                   Iterator<Student_record> n=c.iterator();
                   while(n.hasNext()){
                    Student_record s=n.next();
                    System.out.println(s);
                   }
                   System.out.println("___________________________________________________");
                    break;
                    case 3:
                    Boolean found=false;
                    System.out.println("Enter the sno to search:\n");
                    int roll=input.nextInt();
                    System.out.println("__________________________________________________");
                    n=c.iterator();
                    while(n.hasNext()){
                     Student_record s=n.next();
                     if(s.getSId()==roll)
                     System.out.println(s);
                     found= true;
                    }
                   
                    if(!found){
                        System.out.println("Record not found");
                    }
                    System.out.println("___________________________________________________");
                     break;
                     case 4:
                     found=false;
                    System.out.println("Enter the sno to Delete the record:\n");
                    roll=input.nextInt();
                    System.out.println("__________________________________________________");
                    n=c.iterator();
                    while(n.hasNext()){
                     Student_record s=n.next();
                     if(s.getSId()==roll)
                     n.remove();
                     found= true;
                    }
                   
                    if(!found){
                        System.out.println("Record not found");
                    } else {
                        System.out.println("Record is Deleted Successfully");
                    }
                    
                    System.out.println("___________________________________________________");
                     break;

                     case 5:
                      //list iterator is available in list collection make us able to access the functionality of list iterator
                      found=false;
                      System.out.println("Enter the sno to Update the record:\n");
                      roll=input.nextInt();
                      ListIterator<Student_record>li=c.listIterator();
                      while(li.hasNext()){
                       Student_record s=li.next();
                       if(s.getSId()==roll)
                       System.out.print("Enter new URoll:");
                        SId= input.nextInt();
                        System.out.print("Enter new name:");
                        Sname =input1.nextLine();
                        System.out.print("Enter the new Department : ");
                        Sdep= input1.nextLine();
                        System.out.print("Enter the new Phone number : ");
                        Sphone= input.nextInt();
                        System.out.print("Mention the new Year:");
                        Year= input.nextInt();
                        li.set(new Student_record(SId, Sname, Sdep, Sphone, Year));
                        
                       found= true;
                      }
                     
                      if(!found){
                          System.out.println("Record not found");
                      } else {
                          System.out.println("Record is Updated Successfully");
                      }
                      
                       break;
  
                }
            }while(i!=0);
            input.close();
            input1.close();
        }
    }
