
package jdbc;

import java.sql.*;

public class jdbcConnetionDemo {
	public static void main(String args[]){
		showData();
		create();
		insert();
		update();
		delete();
	}
	public static void showData(){
		try {
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/college_management_system","root","Gau@28949");
			
			Statement st= con.createStatement();
			ResultSet rs =st.executeQuery("select * from section");
			System.out.println("****** Section Table *******");
			System.out.println("\nSec_id    sec_name");
			while(rs.next()){
				int sec_id = rs.getInt("sec_id");
				String sec_name = rs.getString("sec_name");
				
				System.out.println("\n"+sec_id+"  "+sec_name);
			}
			st.close();
			con.close();
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
	}
	public static void create(){
		try{
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/college_management_system","root","Gau@28949");
			
			Statement st= con.createStatement();
			st.executeUpdate("create table if not exists Department(dept_id int(20) primary key , dept_name varchar(50))");
			st.executeUpdate("create table if not exists Exams(roll_no int(20) primary key , course varchar(50), stud_name varchar(100), marks int(50))");
			st.executeUpdate("create table if not exists Attendance(roll_no int(20) primary key , stud_name varchar(50), course varchar(50), percentage float(50))");
			st.executeUpdate("create table if not exists Course(course_id int(20) primary key , course varchar(50), qualification varchar(50), experience varchar(50))");
			st.executeUpdate("create table if not exists Student(roll_no int(20) primary key , stud_name varchar(50), address varchar(100), ph_no varchar(200))");
			st.executeUpdate("create table if not exists Administrator(admin_id int(20) primary key , admin_name varchar(50), password varchar(50))");

			System.out.println("\nTable created successfully");
			
			st.close();
			con.close();
		}catch(Exception e){
			e.printStackTrace();
		}
	}
	public static void insert(){
		try{
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/college_management_system","root","Gau@28949");
			
			Statement st= con.createStatement();
			st.executeUpdate("insert into department (dept_id,dept_name) values (6, 'Electrical')");
			st.executeUpdate("insert into exams(roll_no,course,stud_name,marks) values (6, 'C++', 'XYZ', 70)");
			st.executeUpdate("insert into attendance(roll_no,stud_name,course,percentage) values (6, 'XYZ', 'C++', 70)");
			st.executeUpdate("insert into course(course_id,course,qualification,experience) values (6, 'C++', 'M.E', 3)");
			st.executeUpdate("insert into student(roll_no,stud_name,address,ph_no) values (6, 'XYZ','Mumbai', 998877665)");
			st.executeUpdate("insert into administrator(admin_id,admin_name,password) values (106, 'Virat', 'abcxyz')");

			System.out.println("\nValues inserted successfully");
			
			st.close();
			con.close();
		}catch(Exception e){
			e.printStackTrace();
		}
	}
	public static void update(){
		try{
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/college_management_system","root","Gau@28949");
			
			Statement st= con.createStatement();
			st.executeUpdate("update department set dept_name = 'IT' where dept_id = 2");
			st.executeUpdate("update exams set course = 'Python' where roll_no = 2");
			st.executeUpdate("update attendance set course = 'Python' where roll_no = 2");
			st.executeUpdate("update course set course = 'Python' where course_id = 2");
			st.executeUpdate("update student set address = 'Pune' where roll_no = 2");
			st.executeUpdate("update administrator set admin_name = 'Admin' where admin_id = 2");

			System.out.println("\nValues updated successfully");
			
			st.close();
			con.close();
		}catch(Exception e){
			e.printStackTrace();
		}
	}
	public static void delete(){
		try{
			Class.forName("com.mysql.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/college_management_system","root","Gau@28949");
			
			Statement st= con.createStatement();
			st.executeUpdate("delete from department where dept_id = 2");
			st.executeUpdate("delete from exams where roll_no = 2");
			st.executeUpdate("delete from attendance where roll_no = 2");
			st.executeUpdate("delete from course where course_id = 2");
			st.executeUpdate("delete from student where roll_no = 2");
			st.executeUpdate("delete from administrator where admin_id = 2");

			System.out.println("\nValues deleted successfully");
			
			st.close();
			con.close();
		}catch(Exception e){
			e.printStackTrace();
		}
	}
}
