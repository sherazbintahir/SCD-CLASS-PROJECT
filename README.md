# SCD-CLASS-PROJECT
we made an online learning system named " SMART ACADEMIC ASSISTANCE SYSTEM".

In this system, we additionally added an AI bot and allowed companies to collaborate with our system to offer jobs and internships to students after conducting interviews.

GROUP MEMBERS 
- TOUSEER AMIR (SP21312)
- SHERAZ BIN TAHIR (SP21299)
- MUHAMMAD ASIM (SP21277)
- SAIFULLAH KHAN (SP21306)
- IMRAN KHAN(SP-21317)

# DELIVERABLE 1
[Deliverable 1.pdf](https://github.com/sherazbintahir/SCD-CLASS-PROJECT/files/15366452/Deliverable.1.pdf)

# 1. Description of Each Functionality and Its Purpose:
- Register:
Purpose: Allows users (students, instructors, and admins) to create accounts on the 
platform.
- Login:
Purpose: Provides authenticated access to registered users.
- Enroll in Course:
Purpose: Enables students to select and join courses offered on the platform.
- Assignment:
Purpose: Facilitates the submission and evaluation of assignments by students and 
instructors.
- Quiz:
Purpose: Allows instructors to create quizzes for assessment purposes, and enables 
students to attempt and complete quizzes.
- AI Chatbot Interaction:
Purpose: Provides personalized learning support and assistance to students through AI-driven interactions.
- Interview:
Purpose: Enables students to participate in interviews for internships and job opportunities 
offered by collaborating companies.
- Collaboration:
Purpose: Facilitates partnerships and collaborations with external entities, such as 
companies, for internship and job opportunities for students.
- Content Management:
Purpose: Allows administrators to manage and organize educational content, including 
lectures, assignments, quizzes, and other course materials.
- Offer Internship & Job:
Purpose: Allows collaborating companies to offer internship and job opportunities to 
students through the platform.
# 2. Requirement’s Specification, Including Functional and Non-Functional Requirements.

**Functional Requirements:**
- User Authentication: Users must be able to register and log in securely using authentication 
mechanisms such as username/password or email verification.
- Course Enrollment: Students should be able to view available courses and enroll in them, 
while instructors should be able to manage course enrollments.
- Assignment Submission: Students should be able to submit assignments, and instructors 
should be able to view, grade, and provide feedback on submitted assignments.
- Quiz Management: Instructors should be able to create quizzes, and students should be 
able to attempt quizzes, with the system providing automated grading and feedback.
- AI Chatbot Integration: The platform should integrate an AI chatbot for personalized 
learning interactions with students.
- Interview Scheduling: Students should be able to schedule interviews for internships and 
jobs offered by collaborating companies.
- Collaboration Management: Administrators should have the ability to manage 
collaborations with external entities, including onboarding and communication.
- Content Publishing: Instructors should be able to publish course materials, and 
administrators should have oversight and management capabilities.

**Non-Functional Requirements:**
- Security: The platform should implement robust security measures to protect user data and 
ensure secure access to sensitive information.
- Scalability: The system should be able to handle a growing user base and increasing 
demand for courses and features without compromising performance.
- Usability: The user interface should be intuitive and user-friendly, catering to users of 
varying technical proficiency.
- Reliability: The platform should be reliable and available, with minimal downtime or 
disruptions to user access.
- Performance: The platform should be responsive and performant, providing a seamless 
user experience even under heavy load conditions


# DELIVERABLE 2
**Detailed Design Document**

[Deliverable 2.pdf](https://github.com/sherazbintahir/SCD-CLASS-PROJECT/files/15366465/Deliverable.2.pdf)


# DELIVERABLE 3
[DELIVERABLE 3,4.pdf](https://github.com/sherazbintahir/SCD-CLASS-PROJECT/files/15366552/DELIVERABLE.3.4.pdf)

** CODE **

import javax.swing.*;
import java.awt.*;
import java.util.ArrayList;
import java.util.List;

public class main {
    static List<Course> courses = new ArrayList<>();
    static List<User> users = new ArrayList<>();
    static List<Instructor> instructors = new ArrayList<>();
    static List<Admin> admins = new ArrayList<>();
    static List<Feedback> feedbacks = new ArrayList<>();
    static List<Company> companies = new ArrayList<>();
    static User currentUser;

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> new MainFrame());
    }
}

class MainFrame extends JFrame {
    CardLayout cardLayout;
    JPanel mainPanel;
    JPanel studentPanel;
    JPanel instructorPanel;
    JPanel adminPanel;

    public MainFrame() {
        setTitle("University Management System");
        setSize(600, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        
        // Adding sample data
        Admin admin = new Admin("admin", "password");
        main.admins.add(admin);

        Instructor instructor = new Instructor("instructor", "password");
        main.instructors.add(instructor);

        Student student = new Student("student", "password");
        main.users.add(student);

        main.courses.add(new Course("Java 101"));

        // Creating main panel with card layout
        cardLayout = new CardLayout();
        mainPanel = new JPanel(cardLayout);
        getContentPane().add(mainPanel);

        // Creating panels for each screen
        JPanel welcomePanel = new JPanel();
        JPanel registerPanel = new JPanel();
        JPanel loginPanel = new JPanel();
        studentPanel = new JPanel();
        instructorPanel = new JPanel();
        adminPanel = new JPanel();

        // Adding panels to main panel
        mainPanel.add(welcomePanel, "Welcome");
        mainPanel.add(registerPanel, "Register");
        mainPanel.add(loginPanel, "Login");
        mainPanel.add(studentPanel, "Student");
        mainPanel.add(instructorPanel, "Instructor");
        mainPanel.add(adminPanel, "Admin");

        // Welcome panel
        welcomePanel.setLayout(new GridLayout(3, 1));
        JButton registerButton = new JButton("Register");
        JButton loginButton = new JButton("Login");
        JButton exitButton = new JButton("Exit");

        welcomePanel.add(registerButton);
        welcomePanel.add(loginButton);
        welcomePanel.add(exitButton);

        // Register panel
        registerPanel.setLayout(new GridLayout(4, 2));
        JTextField registerUsernameField = new JTextField();
        JPasswordField registerPasswordField = new JPasswordField();
        String[] userTypes = {"Student", "Instructor", "Admin"};
        JComboBox<String> userTypeComboBox = new JComboBox<>(userTypes);
        JButton registerSubmitButton = new JButton("Register");

        registerPanel.add(new JLabel("Username:"));
        registerPanel.add(registerUsernameField);
        registerPanel.add(new JLabel("Password:"));
        registerPanel.add(registerPasswordField);
        registerPanel.add(new JLabel("User Type:"));
        registerPanel.add(userTypeComboBox);
        registerPanel.add(new JLabel());
        registerPanel.add(registerSubmitButton);

        // Login panel
        loginPanel.setLayout(new GridLayout(3, 2));
        JTextField loginUsernameField = new JTextField();
        JPasswordField loginPasswordField = new JPasswordField();
        JButton loginSubmitButton = new JButton("Login");

        loginPanel.add(new JLabel("Username:"));
        loginPanel.add(loginUsernameField);
        loginPanel.add(new JLabel("Password:"));
        loginPanel.add(loginPasswordField);
        loginPanel.add(new JLabel());
        loginPanel.add(loginSubmitButton);

        // Student panel
        studentPanel.setLayout(new GridLayout(5, 1));
        JButton enrollButton = new JButton("Enroll in Course");
        JButton accessLecturesButton = new JButton("Access Lectures");
        JButton submitAssignmentButton = new JButton("Submit Assignment");
        JButton attemptQuizButton = new JButton("Attempt Quiz");
        JButton studentLogoutButton = new JButton("Logout");

        studentPanel.add(enrollButton);
        studentPanel.add(accessLecturesButton);
        studentPanel.add(submitAssignmentButton);
        studentPanel.add(attemptQuizButton);
        studentPanel.add(studentLogoutButton);

        // Instructor panel
        instructorPanel.setLayout(new GridLayout(5, 1));
        JButton uploadLectureButton = new JButton("Upload Lecture");
        JButton uploadQuizButton = new JButton("Upload Quiz");
        JButton uploadAssignmentButton = new JButton("Upload Assignment");
        JButton viewAttendanceButton = new JButton("View Attendance");
        JButton instructorLogoutButton = new JButton("Logout");

        instructorPanel.add(uploadLectureButton);
        instructorPanel.add(uploadQuizButton);
        instructorPanel.add(uploadAssignmentButton);
        instructorPanel.add(viewAttendanceButton);
        instructorPanel.add(instructorLogoutButton);

        // Admin panel
        adminPanel.setLayout(new GridLayout(5, 1));
        JButton manageCoursesButton = new JButton("Manage Courses");
        JButton manageCompaniesButton = new JButton("Manage Companies");
        JButton viewFeedbackButton = new JButton("View Feedback");
        JButton adminProfileButton = new JButton("Profile Management");
        JButton adminLogoutButton = new JButton("Logout");

        adminPanel.add(manageCoursesButton);
        adminPanel.add(manageCompaniesButton);
        adminPanel.add(viewFeedbackButton);
        adminPanel.add(adminProfileButton);
        adminPanel.add(adminLogoutButton);

        // Button actions
        registerButton.addActionListener(e -> cardLayout.show(mainPanel, "Register"));
        loginButton.addActionListener(e -> cardLayout.show(mainPanel, "Login"));
        exitButton.addActionListener(e -> System.exit(0));

        registerSubmitButton.addActionListener(e -> {
            String username = registerUsernameField.getText();
            String password = new String(registerPasswordField.getPassword());
            String userType = (String) userTypeComboBox.getSelectedItem();

            switch (userType) {
                case "Student":
                    main.users.add(new Student(username, password));
                    JOptionPane.showMessageDialog(this, "Student registered successfully.");
                    break;
                case "Instructor":
                    main.instructors.add(new Instructor(username, password));
                    JOptionPane.showMessageDialog(this, "Instructor registered successfully.");
                    break;
                case "Admin":
                    main.admins.add(new Admin(username, password));
                    JOptionPane.showMessageDialog(this, "Admin registered successfully.");
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Invalid user type.");
            }

            cardLayout.show(mainPanel, "Welcome");
        });

        loginSubmitButton.addActionListener(e -> {
            String username = loginUsernameField.getText();
            String password = new String(loginPasswordField.getPassword());

            User user = getUserByUsername(username);

            if (user != null && user.getPassword().equals(password)) {
                JOptionPane.showMessageDialog(this, "Login successful.");
                main.currentUser = user;
                if (user instanceof Student) {
                    cardLayout.show(mainPanel, "Student");
                } else if (user instanceof Instructor) {
                    cardLayout.show(mainPanel, "Instructor");
                } else if (user instanceof Admin) {
                    cardLayout.show(mainPanel, "Admin");
                }
            } else {
                JOptionPane.showMessageDialog(this, "Invalid username or password.");
            }
        });

        // Student functionalities
        enrollButton.addActionListener(e -> {
            String[] courseTitles = main.courses.stream().map(Course::getTitle).toArray(String[]::new);
            String selectedCourse = (String) JOptionPane.showInputDialog(this, "Select Course", "Enroll", JOptionPane.QUESTION_MESSAGE, null, courseTitles, courseTitles[0]);
            if (selectedCourse != null) {
                Course course = main.courses.stream().filter(c -> c.getTitle().equals(selectedCourse)).findFirst().orElse(null);
                if (course != null) {
                    course.addStudent(main.currentUser);
                    JOptionPane.showMessageDialog(this, "Enrolled in " + selectedCourse);
                }
            }
        });

        accessLecturesButton.addActionListener(e -> extracted());

        submitAssignmentButton.addActionListener(e -> {
            String[] courseTitles = main.courses.stream().map(Course::getTitle).toArray(String[]::new);
            String selectedCourse = (String) JOptionPane.showInputDialog(this, "Select Course", "Submit Assignment", JOptionPane.QUESTION_MESSAGE, null, courseTitles, courseTitles[0]);
            if (selectedCourse != null) {
                String assignmentDetails = JOptionPane.showInputDialog(this, "Assignment Details:");
                if (assignmentDetails != null) {
                    Course course = main.courses.stream().filter(c -> c.getTitle().equals(selectedCourse)).findFirst().orElse(null);
                    if (course != null) {
                        Assignment assignment = new Assignment(course, assignmentDetails);
                        course.addAssignment(assignment);
                        JOptionPane.showMessageDialog(this, "Assignment submitted.");
                    }
                }
            }
        });

        attemptQuizButton.addActionListener(e -> {
            String[] courseTitles = main.courses.stream().map(Course::getTitle).toArray(String[]::new);
            String selectedCourse = (String) JOptionPane.showInputDialog(this, "Select Course", "Attempt Quiz", JOptionPane.QUESTION_MESSAGE, null, courseTitles, courseTitles[0]);
            if (selectedCourse != null) {
                String quizDetails = JOptionPane.showInputDialog(this, "Quiz Details:");
                if (quizDetails != null) {
                    Course course = main.courses.stream().filter(c -> c.getTitle().equals(selectedCourse)).findFirst().orElse(null);
                    if (course != null) {
                        Quiz quiz = new Quiz(course, quizDetails);
                        course.addQuiz(quiz);
                        JOptionPane.showMessageDialog(this, "Quiz attempted.");
                    }
                }
            }
        });

        studentLogoutButton.addActionListener(e -> {
            main.currentUser = null;
            cardLayout.show(mainPanel, "Welcome");
        });

        // Instructor functionalities
        uploadLectureButton.addActionListener(e -> {
            String[] courseTitles = main.courses.stream().map(Course::getTitle).toArray(String[]::new);
            String selectedCourse = (String) JOptionPane.showInputDialog(this, "Select Course", "Upload Lecture", JOptionPane.QUESTION_MESSAGE, null, courseTitles, courseTitles[0]);
            if (selectedCourse != null) {
                String lectureDetails = JOptionPane.showInputDialog(this, "Lecture Details:");
                if (lectureDetails != null) {
                    Course course = main.courses.stream().filter(c -> c.getTitle().equals(selectedCourse)).findFirst().orElse(null);
                    if (course != null) {
                        Lecture lecture = new Lecture(lectureDetails);
                        course.addLecture(lecture);
                        JOptionPane.showMessageDialog(this, "Lecture uploaded.");
                    }
                }
            }
        });

        uploadQuizButton.addActionListener(e -> {
            String[] courseTitles = main.courses.stream().map(Course::getTitle).toArray(String[]::new);
            String selectedCourse = (String) JOptionPane.showInputDialog(this, "Select Course", "Upload Quiz", JOptionPane.QUESTION_MESSAGE, null, courseTitles, courseTitles[0]);
            if (selectedCourse != null) {
                String quizDetails = JOptionPane.showInputDialog(this, "Quiz Details:");
                if (quizDetails != null) {
                    Course course = main.courses.stream().filter(c -> c.getTitle().equals(selectedCourse)).findFirst().orElse(null);
                    if (course != null) {
                        Quiz quiz = new Quiz(course, quizDetails);
                        course.addQuiz(quiz);
                        JOptionPane.showMessageDialog(this, "Quiz uploaded.");
                    }
                }
            }
        });

        uploadAssignmentButton.addActionListener(e -> {
            String[] courseTitles = main.courses.stream().map(Course::getTitle).toArray(String[]::new);
            String selectedCourse = (String) JOptionPane.showInputDialog(this, "Select Course", "Upload Assignment", JOptionPane.QUESTION_MESSAGE, null, courseTitles, courseTitles[0]);
            if (selectedCourse != null) {
                String assignmentDetails = JOptionPane.showInputDialog(this, "Assignment Details:");
                if (assignmentDetails != null) {
                    Course course = main.courses.stream().filter(c -> c.getTitle().equals(selectedCourse)).findFirst().orElse(null);
                    if (course != null) {
                        Assignment assignment = new Assignment(course, assignmentDetails);
                        course.addAssignment(assignment);
                        JOptionPane.showMessageDialog(this, "Assignment uploaded.");
                    }
                }
            }
        });

        viewAttendanceButton.addActionListener(e -> extracted2());

        instructorLogoutButton.addActionListener(e -> {
            main.currentUser = null;
            cardLayout.show(mainPanel, "Welcome");
        });

        // Admin functionalities
        manageCoursesButton.addActionListener(e -> {
            String[] options = {"Add Course", "View Courses"};
            String selectedOption = (String) JOptionPane.showInputDialog(this, "Manage Courses", "Course Management", JOptionPane.QUESTION_MESSAGE, null, options, options[0]);
            if (selectedOption != null) {
                switch (selectedOption) {
                    case "Add Course":
                        String courseTitle = JOptionPane.showInputDialog(this, "Course Title:");
                        if (courseTitle != null) {
                            main.courses.add(new Course(courseTitle));
                            JOptionPane.showMessageDialog(this, "Course added.");
                        }
                        break;
                    case "View Courses":
                        StringBuilder coursesList = new StringBuilder("Courses:\n");
                        for (Course course : main.courses) {
                            coursesList.append("- ").append(course.getTitle()).append("\n");
                        }
                        JOptionPane.showMessageDialog(this, coursesList.toString());
                        break;
                }
            }
        });

        manageCompaniesButton.addActionListener(e -> {
            String[] options = {"Add Company", "View Companies"};
            String selectedOption = (String) JOptionPane.showInputDialog(this, "Manage Companies", "Company Management", JOptionPane.QUESTION_MESSAGE, null, options, options[0]);
            if (selectedOption != null) {
                switch (selectedOption) {
                    case "Add Company":
                        String companyName = JOptionPane.showInputDialog(this, "Company Name:");
                        if (companyName != null) {
                            main.companies.add(new Company(companyName));
                            JOptionPane.showMessageDialog(this, "Company added.");
                        }
                        break;
                    case "View Companies":
                        StringBuilder companiesList = new StringBuilder("Companies:\n");
                        for (Company company : main.companies) {
                            companiesList.append("- ").append(company.getName()).append("\n");
                        }
                        JOptionPane.showMessageDialog(this, companiesList.toString());
                        break;
                }
            }
        });

        viewFeedbackButton.addActionListener(e -> {
            StringBuilder feedbackList = new StringBuilder("Feedbacks:\n");
            for (Feedback feedback : main.feedbacks) {
                feedbackList.append("- ").append(feedback.getUser().getUsername()).append(": ").append(feedback.getContent()).append("\n");
            }
            JOptionPane.showMessageDialog(this, feedbackList.toString());
        });

        adminProfileButton.addActionListener(e -> {
            // Profile management functionalities here
        });

        adminLogoutButton.addActionListener(e -> {
            main.currentUser = null;
            cardLayout.show(mainPanel, "Welcome");
        });

        setVisible(true);
    }

    private void extracted2() {
        Instructor instructor = (Instructor) main.currentUser;
        StringBuilder attendance = new StringBuilder("Attendance:\n");
        for (Course course : main.courses) {
            if (course.getEnrolledStudents().contains(instructor)) {
                attendance.append(course.getTitle()).append(":\n");
                for (User student : course.getEnrolledStudents()) {
                    attendance.append("- ").append(student.getUsername()).append("\n");
                }
            }
        }
        JOptionPane.showMessageDialog(this, attendance.toString());
    }

    private void extracted() {
        Student student = (Student) main.currentUser;
        StringBuilder lectures = new StringBuilder("Lectures:\n");
        for (Course course : main.courses) {
            if (course.getEnrolledStudents().contains(student)) {
                lectures.append(course.getTitle()).append(":\n");
                for (Lecture lecture : course.getLectures()) {
                    lectures.append("- ").append(lecture.getDetails()).append("\n");
                }
            }
        }
        JOptionPane.showMessageDialog(this, lectures.toString());
    }

    private User getUserByUsername(String username) {
        for (User user : main.users) {
            if (user.getUsername().equals(username)) {
                return user;
            }
        }
        for (Instructor instructor : main.instructors) {
            if (instructor.getUsername().equals(username)) {
                return instructor;
            }
        }
        for (Admin admin : main.admins) {
            if (admin.getUsername().equals(username)) {
                return admin;
            }
        }
        return null;
    }
}

abstract class User {
    private String username;
    private String password;

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public String getUsername() {
        return username;
    }

    public String getPassword() {
        return password;
    }
}

class Student extends User {
    public Student(String username, String password) {
        super(username, password);
    }
}

class Instructor extends User {
    public Instructor(String username, String password) {
        super(username, password);
    }
}

class Admin extends User {
    public Admin(String username, String password) {
        super(username, password);
    }
}

class Course {
    private String title;
    private List<User> enrolledStudents = new ArrayList<>();
    private List<Lecture> lectures = new ArrayList<>();
    private List<Assignment> assignments = new ArrayList<>();
    private List<Quiz> quizzes = new ArrayList<>();

    public Course(String title) {
        this.title = title;
    }

    public String getTitle() {
        return title;
    }

    public void addStudent(User student) {
        enrolledStudents.add(student);
    }

    public List<User> getEnrolledStudents() {
        return enrolledStudents;
    }

    public void addLecture(Lecture lecture) {
        lectures.add(lecture);
    }

    public List<Lecture> getLectures() {
        return lectures;
    }

    public void addAssignment(Assignment assignment) {
        assignments.add(assignment);
    }

    public void addQuiz(Quiz quiz) {
        quizzes.add(quiz);
    }
}

class Assignment {
    private Course course;
    private String details;

    public Assignment(Course course, String details) {
        this.course = course;
        this.details = details;
    }
}

class Quiz {
    private Course course;
    private String details;

    public Quiz(Course course, String details) {
        this.course = course;
        this.details = details;
    }
}

class Lecture {
    private String details;

    public Lecture(String details) {
        this.details = details;
    }

    public String getDetails() {
        return details;
    }
}

class Feedback {
    private User user;
    private String content;

    public Feedback(User user, String content) {
        this.user = user;
        this.content = content;
    }

    public User getUser() {
        return user;
    }

    public String getContent() {
        return content;
    }
}

class Company {
    private String name;

    public Company(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
