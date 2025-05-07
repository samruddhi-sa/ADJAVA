# ADJAVA

EXP1A

import java.awt.*;
import java.applet.*;
import java.awt.event.*;

@SuppressWarnings("serial")
public class KeyEventDemo1 extends Applet implements KeyListener
{
    String msg = "";
 
    public void init()
    {
        addKeyListener(this);
    }
 
    public void keyReleased(KeyEvent k)
    {
        showStatus("Key Released");
        repaint();
    }
 
    public void keyTyped(KeyEvent k)
    {
        showStatus("Key Typed");
        repaint();
    }
 
    public void keyPressed(KeyEvent k)
    {
        showStatus("Key Pressed");
        repaint();
    }
 
    public void paint(Graphics g)
    {
        g.drawString(msg, 10, 10);
    }
}

/* 
   <applet code="KeyEventDemo1" height="400" width="400">
   </applet>
*/

EXP1B

import java.awt.*;
import java.applet.*;
import java.awt.event.*;

public class keyEventDemo extends Applet implements KeyListener
{
 String msg = "";
 
public void init()
{
	addKeyListener(this);
}
public void keyPressed(KeyEvent k)
{
    int key = k.getKeyCode();
  switch(key)
  {
  	case KeyEvent.VK_F1:
  	      msg = msg + "F1 ";
          break;
    case KeyEvent.VK_F2:
    	  msg = msg + "F2 ";
          break;
    case KeyEvent.VK_F3:
          msg = msg + "F3 ";
          break;
    case KeyEvent.VK_F4:
          msg = msg + "F4 ";
          break;
    case KeyEvent.VK_RIGHT:
          msg = msg + "RIGHT ";
          break;
    case KeyEvent.VK_LEFT:
          msg = msg + "LEFT ";
          break;
    case KeyEvent.VK_UP:
    	  msg = msg + "UP ";
    	  break;
    case KeyEvent.VK_DOWN:
    	  msg = msg + "DOWN ";
    	  break;
  }
  repaint();
}
public void keyReleased(KeyEvent k){}

public void keyTyped(KeyEvent k){}

public void paint(Graphics g)
{
  g.drawString(msg, 10, 10);
}
}
/* 
   <applet code="keyEventDemo" height=400 width=400>
   </applet>
*/


EXP2 AWT

package wb;

import java.awt.*;
import java.awt.event.*;
public class wb extends Frame implements MouseListener {
Label l;
wb() {
super("AWT Frame");
l = new Label();
l.setFont(new Font("Courier New", Font.ITALIC, 20));
l.setBackground(Color.GREEN);
l.setBounds(25, 60, 250, 30);
l.setAlignment(Label.CENTER);
this.add(l);
this.setSize(300, 300);
this.setLayout(null);
this.setVisible(true);
this.addMouseListener(this);
this.addWindowListener(new WindowAdapter() {
public void windowClosing(WindowEvent e) {
dispose();
}
});
}
public static void main(String[] args) {
new wb();
}
@Override
public void mouseClicked(MouseEvent e) {
l.setText("Mouse Clicked");
}
@Override
public void mousePressed(MouseEvent e) {
}
@Override
public void mouseReleased(MouseEvent e) {
}
@Override
public void mouseEntered(MouseEvent e) {
l.setText("Mouse Entered");

}
@Override
public void mouseExited(MouseEvent e) {
l.setText("Mouse Exited");
}
}

EXP3 STUDENT DATABASE

import java.awt.*;
import java.awt.event.*;

class Student extends Frame implements ActionListener
{
	Label lsname, lsrollno, lsclass, lgander, lsbg, lsmob, lsadrs;
	CheckboxGroup gander;
	Checkbox male, female, trainpass;
	Choice csclass;
	TextField tfsname, tfsrollno, tfsmob;
	TextArea tasadrs;
	Button submit;

	TextArea display_details;

	Student()
	{
		lsname   = new Label("Name : ");
		lsrollno = new Label("Roll No : ");
		lsclass  = new Label("Class : ");
		lgander  = new Label("Gander : ");
		lsbg     = new Label("Blood Group : ");
		lsmob    = new Label("Mobile : ");
		lsadrs   = new Label("Address : ");

		gander = new CheckboxGroup();  
        male   = new Checkbox("Male", gander, false);   
        female = new Checkbox("Female", gander, false);  

        trainpass = new Checkbox("Apply For Train Concession");

        csclass = new Choice();  
        csclass.add("BSc IT");  
        csclass.add("BSc CS");  
        csclass.add("BCA");  
        csclass.add("MSc IT");  
        csclass.add("MSc CS");
        csclass.add("MCA");

		tfsname   = new TextField();
		tfsrollno = new TextField();
		tfsmob    = new TextField();

		tasadrs = new TextArea("", 2 , 100 , TextArea.SCROLLBARS_NONE);

		submit  = new Button("Submit");

		display_details = new TextArea("", 2 , 100 , TextArea.SCROLLBARS_NONE);
		display_details.setEditable(false);

		lsname.setBounds(10, 30, 50, 20);
		tfsname.setBounds(70, 30, 150, 20);
		
		lsrollno.setBounds(240, 30, 50, 20);
		tfsrollno.setBounds(300, 30, 150, 20);
		
		lsclass.setBounds(10, 60, 50, 20);
		csclass.setBounds(70, 60, 150, 20);
		
		lgander.setBounds(240, 60, 50, 20);
		male.setBounds(300, 60, 50, 20);
		female.setBounds(360, 60, 50, 20);
		
		lsmob.setBounds(10, 90, 50, 20);
		tfsmob.setBounds(70, 90, 150, 20);

		trainpass.setBounds(240, 90, 150, 20);

		lsadrs.setBounds(10, 120, 50, 20);
		tasadrs.setBounds(70, 120, 380, 70);

		submit.setBounds(10, 200, 440, 30);

		display_details.setBounds(10, 240, 440, 130);

		add(lsname);
		add(lsrollno);
		add(lsclass);
		add(lgander);
		add(lsbg);
		add(lsadrs);
		add(lsmob);
		add(male);
		add(female);
		add(csclass);
		add(tfsname);
		add(tfsrollno);
		add(tasadrs);
		add(tfsmob);
		add(trainpass);
		add(submit);
		add(display_details);
		submit.addActionListener(this);

		setTitle("Students Details");
		setSize(460,390);
		setLayout(null);
		setVisible(true);

		addWindowListener(new WindowAdapter()
		{  
           			 public void windowClosing(WindowEvent e)
           			 {  
            			    dispose();  
          			  }  
     		   });
	}

	public void actionPerformed(ActionEvent e)
	{
		if(e.getSource()==submit)
		{
			String tp = trainpass.getState() ? "Applied for Train Concession" : "Not Applied for Train Concession";

			String sdetails = " ***** Students Details *****n Name : " + tfsname.getText() + "n Roll No. :" + tfsrollno.getText() + "n Class : " + csclass.getSelectedItem() + "n Gander : " + gander.getSelectedCheckbox().getLabel() + "n Mobile : " + tfsmob.getText() + "n Train Pass : " + tp + "n Address : " + tasadrs.getText();

			display_details.setText(sdetails);
		}
	}

	public static void main(String[] args)
	{
		new Student();
	}
}


EXP4 A JDBC

// Program to Insert Data into Database
 
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.SQLException;
 
public class InsertStaticOracle
{ 
 public static void main(String args[])
 {
  Statement  st = null;
  Connection connection = null; 
  try{
   oracle.jdbc.OracleDriver driverObj = new oracle.jdbc.OracleDriver();
    
   String url = "jdbc:oracle:thin:@localhost:1521:XE", username = "System" ,password = "pass";
   
   connection =DriverManager.getConnection(url,username,password);
  
   if(connection!=null)
    System.out.println("Connection established successfully");
 
    st = connection.createStatement();
 
   String qry = "Insert into Student values(104 ,'Atharva Agrawal','Dhule')";
   
   int count =  st.executeUpdate(qry);
 
   System.out.println(count+" Statement Created Successfully ");
  }
  catch(Exception e)
  {
   e.printStackTrace();
  }
  finally{  
   try
   {
    if(st != null) 
     st.close();
    if(connection != null)
     connection.close();
   }
   catch(SQLException e){
    e.printStackTrace();
   }
  } }}


EXP4 B JDBC

//Program to retrieve data:

import java.sql.Connection;
import java.sql.SQLException;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.ResultSet;
 
public class SelectOracle
{
 public static void main(String args[]) throws SQLException
 {
  System.out.println("Step 1: ");
  oracle.jdbc.driver.OracleDriver obj = new oracle.jdbc.driver.OracleDriver();
  // Class.forName(oracle.jdbc.driver.OracleDriver);
  System.out.println("Driver loaded successfully");
 
  System.out.println("Step 2: ");
  String url="jdbc:oracle:thin:@localhost:1521:XE",uname="SYSTEM" , password="Atharva007";
  Connection connection = DriverManager.getConnection(url,uname,password);
  if(connection!=null)
   System.out.println("Connection Established Successfully");
  else
   System.out.println("Connection Not Established Successfully");
 
   
  System.out.println("Step 3: ");
  Statement st = connection.createStatement();
  System.out.println("Statement Referenced   ");
 
  System.out.println("Step 4: ");
  System.out.println("Step 5: ");
  String qry = "select * from Student";
  ResultSet rs = st.executeQuery(qry);
  System.out.println("rs: "+rs);
   
  System.out.println("Step 6: ");
  System.out.println("Id\tName\taddress");
  while(rs.next())
  {
   int x = rs.getInt(1);
   String y = rs.getString("Name");
   String s = rs.getString(3);
   System.out.println(x+"\t"+y+"\t"+s);
  }    
     
  System.out.println("Step 7: ");
  rs.close();
  st.close();
  connection.close();
 } 
}

EXP 5 RMI

//one.java
import java.rmi.*;
interface one extends Remote
{

    public int palin(String a) throws RemoteException;
}

//two.java
import java.rmi.*;
import java.lang.*;
import java.rmi.server.*;
public class two extends UnicastRemoteObject implements one
{
    public two() throws RemoteException { }
    public int palin(String a) throws RemoteException
    {
        System.out.println("Hello");
        StringBuffer str = new StringBuffer(a);
        String str1 = str.toString();
        System.out.println("Print : " + str1.toString());
        StringBuffer str2 = str.reverse();
        System.out.println("Print : " + str2.toString());
        int b = str1.compareTo(str2.toString());
        System.out.println("Print : " + b);
        if (b == 0)
            return 1;
        else
            return 0;
    }
}

//rmiserver.java
import java.io.*;
import java.rmi.*;
import java.net.*;
public class rmiserver
{
    public static void main(String args[]) throws Exception
    {
        try
        {
            two twox = new two();
            Naming.bind("palin", twox);
            System.out.println("Object registered");
        }
        catch(Exception e)
        {
            System.out.println("Exception" + e);
        }
    }
}

//rmiclient.java
import java.io.*;
import java.rmi.*;
import java.net.*;
public class rmiclient
{
    public static void main(String args[]) throws Exception
    {
        try
        {
            String s1 = "rmi://localhost/palin";
            one onex = (one)Naming.lookup(s1);
            int m = onex.palin("madam");
            System.out.println("Print : " + m);
            if (m == 1)
            {
                System.out.println("The given string is a Palindrome");
            }
            else
            {
                System.out.println("The given string is not a Palindrome");
            }
        }
        catch (Exception e)
        {
            System.out.println("Exception" + e);
        }
    }
}


EXP 6 INET ADDRESS

import java.io.*;
import java.net.*;
import java.util.*;

class scalar {
	public static void main(String[] args)
		throws UnknownHostException
	{
		// To get and print the InetAddress of the Local Host
		InetAddress address1 = InetAddress.getLocalHost();
		System.out.println("InetAddress of Local Host : "
						+ address1);

		// To get and print the InetAddress of the Named Host
		InetAddress address2
			= InetAddress.getByName("45.22.30.39");
		System.out.println("InetAddress of Named Host : "
						+ address2);

		// To get and print ALL InetAddresses of Named Host
		InetAddress address3[]
			= InetAddress.getAllByName("172.19.25.29");
		for (int i = 0; i < address3.length; i++) {
			System.out.println(
				"ALL InetAddresses of Named Host : "
				+ address3[i]);
		}

		// To get and print InetAddresses of Host with specified IP Address
		byte IPAddress[] = { 125, 0, 0, 1 };
		InetAddress address4
			= InetAddress.getByAddress(IPAddress);
		System.out.println(
			"InetAddresses of Host with specified IP Address : "
			+ address4);

		// To get and print InetAddresses of Host with specified IP Address and hostname
		byte[] IPAddress2
			= { 105, 22, (byte)223, (byte)186 };
		InetAddress address5 = InetAddress.getByAddress(
			"www.scaler.com/topics/", IPAddress2);
		System.out.println(
			"InetAddresses of Host with specified IP Address and hostname : "
			+ address5);
	}
}

/*
Output

InetAddress of Local Host : localhost/127.0.0.1
InetAddress of Named Host: /45.22.30.39
ALL InetAddresses of Named Host: /172.19.25.29
InetAddresses of Host with specified IP Address : /125.0.0.1
InetAddresses of Host with specified IP Address and hostname: https://www.scaler.com/topics//105.22.223.186

*/


EXP7 SERVLET


index.html
<html>
    <head>
        <title>login form</title>
    </head>
    <body>
        <form method="post" action="login">
        Email ID:<input type="text" name="email" /><br/>
        Password:<input type="text" name="pass" /><br/>
        <input type="submit" value="login" />
        </form>
    </body>
</html>



Login.java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;
import java.sql.*;

public class Login extends HttpServlet {
 
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        
        String email = request.getParameter("email");
        String pass = request.getParameter("pass");
        
        if(Validate.checkUser(email, pass))
        {
            RequestDispatcher rs = request.getRequestDispatcher("Welcome");
            rs.forward(request, response);
        }
        else
        {
           out.println("Username or Password incorrect");
           RequestDispatcher rs = request.getRequestDispatcher("index.html");
           rs.include(request, response);
        }
    }  
}



Validate.java
import java.sql.*;
public class Validate {
    public static boolean checkUser(String email,String pass) 
    {
        boolean st =false;
        try {

            //loading drivers for mysql
            Class.forName("com.mysql.jdbc.Driver");

            //creating connection with the database
            Connection con = DriverManager.getConnection("jdbc:mysql:/ /localhost:3306/test","root","studytonight");
            PreparedStatement ps = con.prepareStatement("select * from register where email=? and pass=?");
            ps.setString(1, email);
            ps.setString(2, pass);
            ResultSet rs =ps.executeQuery();
            st = rs.next();

        }
        catch(Exception e) {
            e.printStackTrace();
        }
        return st;                 
    }   
}




Welcome.java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;
import java.sql.*;
public class Welcome extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        out.println("Welcome user");
      }  
}




web.xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app version="3.0" xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" >

    <servlet>
        <servlet-name>login</servlet-name>
        <servlet-class>Login</servlet-class>
    </servlet>
    <servlet>
        <servlet-name>Welcome</servlet-name>
        <servlet-class>Welcome</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>login</servlet-name>
        <url-pattern>/login</url-pattern>
    </servlet-mapping>
    <servlet-mapping>
        <servlet-name>Welcome</servlet-name>
        <url-pattern>/Welcome</url-pattern>
    </servlet-mapping>
    
</web-app>




EXP8 JDBC

import java.sql.*;
 
public class GFG {
 
    // Step1: Main driver method
    public static void main(String[] args)
    {
        // Step 2: Making connection using
        // Connection type and inbuilt function on
        Connection con = null;
        PreparedStatement p = null;
        ResultSet rs = null;
 
        con = connection.connectDB();
 
        // Try block to catch exception/s
        try {
 
            // SQL command data stored in String datatype
            String sql = "select * from cuslogin";
            p = con.prepareStatement(sql);
            rs = p.executeQuery();
 
            // Printing ID, name, email of customers
            // of the SQL command above
            System.out.println("id\t\tname\t\temail");
 
            // Condition check
            while (rs.next()) {
 
                int id = rs.getInt("id");
                String name = rs.getString("name");
                String email = rs.getString("email");
                System.out.println(id + "\t\t" + name
                                   + "\t\t" + email);
            }
        }
 
        // Catch block to handle exception
        catch (SQLException e) {
 
            // Print exception pop-up on screen
            System.out.println(e);
        }
    }
}


