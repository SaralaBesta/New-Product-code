# New-Product-code

package com.friends.anilkumar;

import javax.persistence.Column;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;


@javax.persistence.Entity
@Table(name = "students")
public class students {

	public String getname() {
		return getname();
	}

	public void setname(String name ) {
		this.name = name;
	}

	public int gets_id() {
		return s_id;
	}

	public void sets_id(int s_id) {
		this.s_id = s_id;
	}

	public String gets_course() {
		return s_course;
	}

	public void sets_course(String s_course) {
		this.s_course = s_course;
	}
	public int getc_id() {
		return c_id;
	}

	public void setc_id(int c_id) {
		this.c_id = c_id;
	}


	@Id
	@Column(name="c_id")
	int c_id;
	@Column(name = "s_course")
	String s_course;
	@Column(name = "s_id")
	int s_id;
	@Column(name="name")
//	@GeneratedValue(strategy = GenerationType.IDENTITY)
	String name;
	
	
	
	

	public students() {
		// TODO Auto-generated constructor stub
	}

	@Override
	public String toString() {
		return "Learner [learnerId=" + name + ", learnerName=" + s_id + ", learnerDomain=" + s_course+",courseid="+c_id
				+ "]";
	}

	public students(String name,int s_id, String s_course,int c_id) {
	
		this.name = name;
		this.s_id=s_id;
		this.s_course=s_course;
		this.c_id=c_id;
//		this.learnerDomain = learnerDomain;
	}
	
	
	
}

package com.friends.anilkumar;

import java.util.List;

import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class App 
{
    public static void main( String[] args )
    {
//        Get the SessionFactory
    	SessionFactory factory = new Configuration()
    								.configure("hibernate.cfg.xml")
    								.addAnnotatedClass(students.class)
    								.buildSessionFactory();
    	
//    	Get the Session
    	Session theSession = factory.getCurrentSession();
    	
    	try {
//    		Add a new learner
    		students theLearner = new students("m.anil",109,"devops",1105);
    		
    		
//    		Start the transaction
    		theSession.beginTransaction();
    		
//    		Save the learner
    		theSession.save(theLearner);
    		
//    		Commit the transaction
    		theSession.getTransaction().commit();
    		System.out.println("new students sucessfully inserted ");
    		System.out.println("Learner id : " + theLearner.name);
    		
//    		Learner learner = theSession.get(Learner.class, 2);
//    		
//    		System.out.println("Learner details by id : " + learner);
    		
 
    		
    		
    		
    	}finally {
    		factory.close();
    	}
    }}
