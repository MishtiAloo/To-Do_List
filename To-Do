#include <bits/stdc++.h>

using namespace std;

#define current_time 1000
#define current_date 26092023

class USER;
class TASK;
class WORK_TASK;
class ACADEMIC_TASK;
class PERSONAL_TASK;
class Class_Routine;
class EXM;
class People;

class Class_Routine {
public:
    vector <vector <string>> theory;                               // Vector of vector
    vector <vector <string>> lab;
};

class EXM {
public:
    string exm_type;
    string subject;
    int exm_time;
    string room_No;
    int full_marks;
    int acquired_marks;
    bool done_status;
};

class People {
protected:
    string name;
    int age;
    string relation;
    int birthday;
public:
    void set_Name (string n) {name = n;}
    void set_relation (string n) {relation = n;}
    void set_Age (int n) {age = n;}
    void set_Bday (int n) {birthday = n;}
    string get_Name () {return name;}                                   //setter getter
    string get_relation () {return relation;}
    int get_Age () {return age;}
    int get_Bday () {return birthday;}
};

class TASK {                                                        // Abstract base class
protected:
    string task_name;
    int due_date;
    int due_time;
    bool done_status;
    int done_time;
    int done_date;
    string location;
    string reminder;                                          // Default & parameterized constructors
public:
    TASK () {due_date = 0; due_time = 0; done_status = 0; done_time = 0; done_date = 0;}
    TASK (string n, int dd, int dt) {task_name = n; due_date = dd; due_time = dt; done_status = 0;}
    ~TASK () {}

    string getTask_name () {return task_name;}
    string getLocation () {return location;}
    string getReminder () {return reminder;}
    int getDue_date () {return due_date;}
    int getDue_time () {return due_time;}
    int getDone_time () {return done_time;}
    int getDone_date () {return done_date;}
    bool getDone_status () {return done_status;}
    void setTask () {
        cout << "Task Title: "; cin >> task_name;
        cout << "Due Date: "; cin >> due_date;
        cout << "Due Time: "; cin >> due_time;
        cout << "Location: "; cin >> location;
        done_date = 0;
        done_time = 0;
        done_status = 0;
    }
    void mark_as_done (int cur_date, int cur_time) {
        done_time = cur_time;
        done_date = cur_date;
        done_status = 1;
    }
    virtual float task_score () = 0;                                // Pure virtual function

    void showTask () {
        cout << "Task Title: " << task_name << endl;
        cout << "Due Date: " << due_date << endl;
        cout << "Due Time: " << due_time << endl;
        cout << "Done Status: " << done_status << endl;
        cout << "Done Time: " << done_time << endl;
        cout << "Done date: " << done_date << endl;
        cout << "Location: " << location << endl;
    }

    friend istream& operator >> (istream& in, TASK& task) {
        cout << "Task Title: "; cin >> task.task_name;
        cout << "Due Date: "; cin >> task.due_date;
        cout << "Due Time: "; cin >> task.due_time;
        cout << "Done Status: "; cin >> task.done_status;                      // Operator overloading
        cout << "Done Time: "; cin >> task.done_time;
        cout << "Done date: "; cin >> task.done_date;
        cout << "Location: "; cin >> task.location;
        cout << "Reminder: "; cin >> task.reminder;
        return in;
    }
};


class WORK_TASK : public TASK {                                   // Inheritence
protected:
    string office_name;
    pair <int, int> office_hour;
    string post;
public:                                                         // Inheritence constructor call
    WORK_TASK () {
        task_name = "Nop";
    }                                             
    WORK_TASK (string a, int f, int g, string o, string p) : TASK (a, f, g) {office_name = o; post = p;}
    ~WORK_TASK () {}

    void setOffice_name (string o) {office_name = o;}
    void setPost (string o) {post = o;}
    void setOffice_hr (pair <int, int> p) {office_hour = p;}
    string getOffice_name () {return office_name;}
    string getPost () {return post;}
    pair <int, int> getOffice_hr () {return office_hour;}
    
    friend ostream& operator << (ostream& out, WORK_TASK& wt) {
        cout << "Office name: " << wt.getOffice_name() << endl;                   // Operator overloading
        cout << "Post: " << wt.getPost() << endl;
        wt.showTask();        
        return out;
    }
    float task_score () {
        int date_now = done_date / 10000;
        int day_now = date_now / 100;
        int month_now = date_now % 100;
        int days_now = day_now + month_now*30;

        date_now = due_date / 10000;
        day_now = date_now / 100;
        month_now = date_now % 100;
        int ddays_now = day_now + month_now*30;        

        float score = (due_time - done_time)*0.5 + (ddays_now - days_now)*5;
        return score;
    }                                                                       // Definition of pure virtual fn
};

class ACADEMIC_TASK : public TASK {
protected:
    string current_class;
    string institute;
public:
    ACADEMIC_TASK () {task_name = "No";}
    ACADEMIC_TASK (string a, int f, int g, string o, string p) : TASK (a, f, g) {current_class = o; institute = p;}
    ~ACADEMIC_TASK () {}

    void setCurrent_class (string c) {current_class = c;}
    void setInstitute (string i) {institute = i;}
    string getCurrent_class () {return current_class;}
    string getInstitute () {return institute;}

    friend ostream& operator << (ostream& out, ACADEMIC_TASK& wt) {
        cout << "Current class: " << wt.getCurrent_class() << endl;
        cout << "Institute: " << wt.getInstitute() << endl;
        wt.showTask();
        return out;
    }

    float task_score () {        
        int date_now = done_date / 10000;
        int day_now = date_now / 100;
        int month_now = date_now % 100;
        int days_now = day_now + month_now*30;

        date_now = due_date / 10000;
        day_now = date_now / 100;
        month_now = date_now % 100;
        int ddays_now = day_now + month_now*30;        

        float score = (due_time - done_time)*0.5 + (ddays_now - days_now)*5;
        return score;
    } 
};

class PERSONAL_TASK : public TASK {
public:
    PERSONAL_TASK () {task_name = "No";}
    PERSONAL_TASK (string a, int f, int g, string o, string p) : TASK (a, f, g) {}
    
    friend ostream& operator << (ostream& out, PERSONAL_TASK& wt) {
        wt.showTask();
        return out;                                                                 // Friend function
    }

    float task_score () {
        int date_now = done_date / 10000;
        int day_now = date_now / 100;
        int month_now = date_now % 100;
        int days_now = day_now + month_now*30;

        date_now = due_date / 10000;
        day_now = date_now / 100;
        month_now = date_now % 100;
        int ddays_now = day_now + month_now*30;        

        float score = (due_time - done_time)*0.5 + (ddays_now - days_now)*5;
        return score;
    }    
};

class USER {
    Class_Routine class_routine;                           // Nested class
    vector <EXM> exam;
    vector <People> people;
    vector <WORK_TASK> work_task;
    vector <ACADEMIC_TASK> academic_task;                // Vector 
    vector <PERSONAL_TASK> personal_task;
    string user_name;
    string password;
    TASK* ptr;                                          // Base class pointer
public:
    vector <WORK_TASK>     get_work_task_vector () {return work_task;}
    vector <ACADEMIC_TASK> get_academic_task_vector () {return academic_task;}
    vector <PERSONAL_TASK> get_personal_task_vector () {return personal_task;}

    USER () {
        user_name = "ggg"; password = "gg";
        file_update();
    }
    ~USER () {}

    bool login_authentication (string name, string pass) {
        if (name != user_name || pass != password) {
            cout << "Error. Try again.\n\n";
            return 0;
        }
        else {
            cout << "Login successful.\n\n";
            return 1;
        }
    }

    void file_update () {
        ifstream inf;
        ofstream outf;

        outf.open ("Work_task.bin", ios::binary);
        outf.close();

        inf.open ("Work_task.bin", ios::binary);

        if (!inf) 
            cout << "Error opening wt" << endl;  
        else cout << "Success\n\n";

        WORK_TASK tmp;
        while (inf.read ((char*)&tmp, sizeof(tmp))) {work_task.push_back(tmp);}
        inf.close();

        outf.open ("Academic_task.bin", ios::binary);
        outf.close();        

        inf.open ("Academic_task.bin", ios::binary);

        if (!inf) 
            cout << "Error opening at" << endl;        
        else cout << "Success\n\n";

        ACADEMIC_TASK temp;
        while (inf.read ((char*)&temp, sizeof(temp))) {academic_task.push_back(temp);}
        inf.close();

        outf.open ("Personal_task.bin", ios::binary);
        outf.close();        

        inf.open ("Personal_task.bin", ios::binary);

        if (!inf) 
            cout << "Error opening pt" << endl;        
        else cout << "Success\n\n";
        
        PERSONAL_TASK teemp;
        while (inf.read ((char*)&teemp, sizeof(teemp))) {personal_task.push_back(teemp);}
        inf.close();        
    }

    void class_routine_fn () {

        cout << "\n1. Update\n2. Show\n";
        cout << "Enter choice: ";
        int choice; cin >> choice;
        getchar ();
        cout << endl;
        if (choice == 1) {
            Class_Routine tmp;

            for (int i = 0; i < 5; i++) {
                cout << "For weekday " << i+1 << endl;
                vector <string> cls;
                for (int j = 0; j < 6; j++) {
                    string class_name;
                    cout << "Enter period " << j+1 << ": ";
                    getline (cin, class_name);
                    cls.push_back (class_name);
                }                                                       // File handing input
                tmp.theory.push_back (cls);
            }

            for (int i = 0; i < 5; i++) {
                cout << "For weekday " << i+1 << endl;
                vector <string> lab;
                for (int j = 0; j < 3; j++) {
                    string lab_name;
                    cout << "Enter period " << j+1 << ": ";
                    getline (cin, lab_name);
                    lab.push_back (lab_name);
                }
                tmp.lab.push_back (lab);
            }
            class_routine = tmp;

            ofstream outf;
            outf.open ("Class_routine.txt");

            outf << "\n****************Theory Class******************\n\n";
            for (int i = 0; i < tmp.theory.size(); i++) {
                for (int j = 0; j < tmp.theory[i].size(); j++)
                    outf << tmp.theory[i][j] << " ";
                outf << endl;
            }            
            
            outf << "\n****************Lab Class******************\n\n";
            for (int i = 0; i < tmp.lab.size(); i++) {
                for (int j = 0; j < tmp.lab[i].size(); j++)
                    outf << tmp.lab[i][j] << " ";
                outf << endl;
            }   
            outf.close();          
        }

        else {
            ifstream inf ;
            inf.open ("Class_routine.txt");

            string s;                                                // File handling output
            while (getline(inf, s))
                cout << s << endl;
             
            inf.close();
            cout << endl;
        }
    }
    void people_fn () {
        cout << "\n1. Add people\n2. View all\n\n";
        cout << "Enter choice: ";
        int choice; cin >> choice;
        cout << endl;

        if (choice == 1) {

            ofstream outf;
            outf.open ("People.txt", ios::binary|ios::app);

            cout << "How many? ";
            int num; cin >> num;
            getchar ();
            for (int i = 0; i < num; i++) {
                People tmp;
                cout << "\nEnter name: "; string n; getline (cin, n); tmp.set_Name(n);
                cout << "Enter age: "; int a; cin >> a; getchar (); tmp.set_Age(a);
                cout << "Enter relation: "; string r; getline (cin, r); tmp.set_relation(r);
                cout << "Enter bday: "; int b; cin >> b; tmp.set_Bday (b);
                getchar ();
                people.push_back(tmp);

                outf.write ((char*)&tmp, sizeof(tmp));
            }
            outf.close();
        }
        else {                                                              // Read writing whole obj into file

            ifstream inf;
            inf.open ("People.txt", ios::binary);
            
            cout << "***************People****************\n\n";

            People tmp;

            while(inf.read ((char*)&tmp, sizeof(tmp))) {
                cout << tmp.get_Name() << endl;
                cout << tmp.get_Age() << endl;
                cout << tmp.get_relation() << endl;
                cout << tmp.get_Bday() << endl;
                cout << endl;
                people.push_back(tmp);
            }
            inf.close();
        }
    }
    void exm_fn () {
        cout << "\n1. Add exm\n2. Update exm\n3. Show all\n\n";
        cout << "Enter choice: ";
        int choice; cin >> choice;

        if (choice == 1) {
            EXM tmp;
            cout << "How many? "; int num; cin >> num; getchar();

            for (int i = 0; i < num; i++) {
                cout << "\nType: "; getline (cin, tmp.exm_type); 
                cout << "Subj: "; getline (cin, tmp.subject);
                cout << "exm_time: "; cin >> tmp.exm_time; getchar();
                cout << "Room_No.: "; getline (cin, tmp.room_No);
                cout << "Full_marks: "; cin >> tmp.full_marks; getchar();
                tmp.done_status = 0;
                tmp.acquired_marks = 0;
                exam.push_back(tmp);
            }
        }
        else if (choice == 2) {
            if (exam.size() == 0) {cout << "No exam for now!!! Chill out.\n\n"; return;}

            for (int i = 0; i < exam.size(); i++) {
                cout << "\nType:" << exam[i].exm_type << "\nSubj: " << exam[i].subject << "\nTime: " << exam[i].exm_time << "\nRoom no: " << exam[i].room_No << "\nFull marks: " << exam[i].full_marks << "\nAcquired marks: " << exam[i].acquired_marks << "\nDone status: " << exam[i].done_status << "\n\n";
            }
            cout << "Exm No? "; int num; cin >> num;
            exam[num-1].done_status = 1;
            int marks;
            cout << "Acquired marks: "; cin >> marks; exam[num - 1].acquired_marks = marks;
        }
        else if (choice == 3) {
            if (exam.size() == 0) {cout << "No exam for now!!! Chill out.\n\n"; return;}
            for (int i = 0; i < exam.size(); i++) {
                cout << "\nType:" << exam[i].exm_type << "\nSubj: " << exam[i].subject << "\nTime: " << exam[i].exm_time << "\nRoom no: " << exam[i].room_No << "\nFull marks: " << exam[i].full_marks << "\nAcquired marks: " << exam[i].acquired_marks << "\nDone status: " << exam[i].done_status << "\n\n";
            }
        }
    }
    void work_task_fn () {
        cout << "\n1. Add task\n2. Update task\n3. Show all\n4. Delete task\n\n";
        cout << "Enter choice: "; int choice; cin >> choice;

        switch (choice) {
            case 1 : {
                ofstream outf;
                outf.open ("Work_task.bin", ios::binary|ios::app);

                cout << "How many? "; int num; cin >> num; getchar();
                for (int i = 0; i < num; i++) {
                    WORK_TASK tmp;
                    cout << "Office name: "; string n; getline (cin, n); tmp.setOffice_name(n);
                    cout << "office hour: "; pair <int, int> p; cin >> p.first >> p.second; tmp.setOffice_hr (p); getchar();
                    cout << "Enter post: "; string pp; getline (cin, pp); tmp.setPost (pp);
                    tmp.setTask();
                    getchar();
                    work_task.push_back (tmp);
                    cout << endl;

                    outf.write ((char*)&tmp, sizeof(tmp));
                }
                outf.close();
                cout << "\n\n";
                break;
            }
            case 2 : {
                if (work_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < work_task.size(); i++) {
                    cout << work_task[i];
                    cout << endl;
                }
                cout << "\n\n";

                cout << "Serial No. of task? "; int n; cin >> n;
                work_task[n-1].mark_as_done(current_date, current_time);
                cout << "\n\n";
                break;
            }
            case 3 : {
                if (work_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < work_task.size(); i++) {
                    cout << work_task[i];
                    cout << endl;
                }
                cout << "\n\n";
                break;
            }
            case 4 : {
                if (work_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < work_task.size(); i++) {
                    cout << work_task[i];
                    cout << endl;
                }
                cout << "\n\n";

                cout << "Serial No. of task? "; int n; cin >> n;
                work_task.erase(work_task.begin()+ n-1);
                cout << "Delete Successful\n\n";
                break;                
            }
            default : {cout << "Error command\n\n"; break;}
        }
    }
    void display_all_task_score () {
        cout << "\n************Displaying Work Task scores**************\n";
        for (int i = 0; i < work_task.size(); i++) {
            if (work_task[i].getDone_status()) {
                ptr = &work_task[i];                                            // Polymorphism
                cout << ptr->task_score() << endl;
            }
        }
        cout << "\n************Displaying academic Task scores**************\n";
        for (int i = 0; i < academic_task.size(); i++) {
            if (academic_task[i].getDone_status()) {
                ptr = &academic_task[i];
                cout << ptr->task_score() << endl;                                        // Polymorphism
            }
        }
        cout << "\n************Displaying personal Task scores**************\n";
        for (int i = 0; i < personal_task.size(); i++) {
            if (personal_task[i].getDone_status()) {
                ptr = &personal_task[i];                                               // Polymorphism
                cout << ptr->task_score() << endl;
            }
        }
        cout << "\n\n";
    }
    void academic_task_fn () {
        cout << "\n1. Add task\n2. Update task\n3. Show all\n4. Delete task\n\n";
        cout << "Enter choice: "; int choice; cin >> choice;

        switch (choice) {            
            case 1 : {
                ofstream outf;
                outf.open ("Academic_task.bin", ios::binary|ios::app);

                cout << "How many? "; int num; cin >> num; getchar();
                for (int i = 0; i < num; i++) {
                    ACADEMIC_TASK tmp;
                    cout << "Current class: "; string n; getline (cin, n); tmp.setCurrent_class(n);
                    cout << "Institute: "; string pp; getline (cin, pp); tmp.setInstitute (pp);
                    tmp.setTask();
                    getchar();
                    academic_task.push_back (tmp);
                    cout << endl;

                    outf.write ((char*)&tmp, sizeof(tmp));
                }
                outf.close();
                cout << "\n\n";
                break;
            }
            case 2 : {
                if (academic_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < academic_task.size(); i++) {
                    cout << academic_task[i];
                    cout << endl;
                }
                cout << "\n\n";

                cout << "Serial No. of task? "; int n; cin >> n;
                academic_task[n-1].mark_as_done(current_date, current_time);
                cout << "\n\n";
                break;
            }
            case 3 : {
                if (academic_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < academic_task.size(); i++) {
                    cout << academic_task[i];
                    cout << endl;
                }
                cout << "\n\n";
                break;
            }
            case 4 : {
                if (academic_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < academic_task.size(); i++) {
                    cout << academic_task[i];
                    cout << endl;
                }
                cout << "\n\n";

                cout << "Serial No. of task? "; int n; cin >> n;
                work_task.erase(work_task.begin()+ n-1);
                cout << "Delete Successful\n\n";
                break; 
            }            
            default : {cout << "Error command\n\n"; break;}
        }
    }
    void personal_task_fn () {
        cout << "\n1. Add task\n2. Update task\n3. Show all\n4. Delete task\n\n";
        cout << "Enter choice: "; int choice; cin >> choice;

        switch (choice) {
            case 1 : {
                ofstream outf;
                outf.open ("Personal_task.bin", ios::binary|ios::app);

                cout << "How many? "; int num; cin >> num; getchar();
                for (int i = 0; i < num; i++) {
                    PERSONAL_TASK tmp;
                    tmp.setTask();
                    getchar();
                    personal_task.push_back (tmp);
                    cout << endl;

                    outf.write ((char*)&tmp, sizeof (tmp));
                }
                outf.close();
                cout << "\n\n";
                break;
            }
            case 2 : {
                if (personal_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < personal_task.size(); i++) {
                    personal_task[i].showTask();
                    cout << endl;
                }
                cout << "\n\n";

                cout << "Serial No. of task? "; int n; cin >> n;
                personal_task[n-1].mark_as_done(current_date, current_time);
                cout << "\n\n";
                break;
            }
            case 3 : {
                if (personal_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < personal_task.size(); i++) {
                    personal_task[i].showTask();
                    cout << endl;
                }
                cout << "\n\n";
                break;
            }
            case 4 : {
                if (personal_task.size() == 0) {cout << "No task available\n\n"; break;}
                for (int i = 0; i < personal_task.size(); i++) {
                    personal_task[i].showTask();
                    cout << endl;
                }
                cout << "\n\n";

                cout << "Serial No. of task? "; int n; cin >> n;
                work_task.erase(work_task.begin()+ n-1);
                cout << "Delete Successful\n\n";
                break; 
            }
            default : {cout << "Error command\n\n"; break;}
        }        
    }
    void birthday_finder () {
        int date_now = current_date / 10000;
        int day_now = date_now / 100;
        int month_now = date_now % 100;
        int days_now = day_now + month_now*30;

        for (int i = 0; i < people.size(); i++) {
            int ppl_date = people[i].get_Bday()/10000;
            int ppl_day = ppl_date / 100;
            int ppl_month = ppl_date % 100;
            int ppl_days = ppl_day + ppl_month*30;

            if (ppl_days - days_now <= 7 && ppl_days - days_now >= 0) {
                cout << people[i].get_Name() << " is turning " << people[i].get_Age() + 1 << " this week!!" << endl;
            }
        }
        cout << "\n\n";
    }
    template <class T>
    T search (vector <T> t, string n) {

        for (int i = 0; i < t.size(); i++)                          // Template function
            if (t[i].getTask_name() == n)
                return t[i];
        cout << "Not found\n";
        return T();
    }
};


int main ()
{
    cout << "\n\n*******************Welcome to To-Do*********************\n\n\n";
    USER user;

    while (1) {
        string name, pass;
        cout << "Enter Username: ";
        getline (cin, name);
        cout << "Enter Password: ";
        getline (cin, pass);

        if (user.login_authentication (name, pass)) break;
    }

    while (1) {
        int choice;

        cout << "1. Class routine\n2. People\n3. Exam routine\n4. Birthdays this week\n5. Work task\n6. Academic task\n7. Personal task\n8. Display scores\n9. Search\n10. Exit\n";
        cout << "Enter choice: "; cin >> choice;

        switch (choice) {
            case 1 : {
                getchar();
                user.class_routine_fn ();
                break;
            }
            case 2 : {
                user.people_fn();
                break;
            }
            case 3 : {
                user.exm_fn();
                break;
            }
            case 4 : {
                user.birthday_finder();
                break;
            }
            case 5 : {
                user.work_task_fn();
                break;
            }
            case 6 : {
                user.academic_task_fn();
                break;
            }
            case 7 : {
                user.personal_task_fn();
                break;
            }
            case 8 : {
                user.display_all_task_score();
                break;
            }
            case 9 : {
                cout << "1. Work task\n2. Academic task\n3. Personal task\n";
                cout << "Enter choice: ";
                int task_choice; cin >> task_choice; getchar ();

                cout << "Name of the task: "; string n; getline (cin, n);

                switch (task_choice) {
                    case 1 : {
                        WORK_TASK tmp;
                        tmp = user.search (user.get_work_task_vector(), n);
                        cout << "\n\n";
                        if (tmp.getTask_name() == "Nop") break;
                        cout << tmp;
                        cout << "\n\n";
                        break;
                    }
                    case 2 : {
                        ACADEMIC_TASK tmp;
                        tmp = user.search (user.get_academic_task_vector(), n);
                        if (tmp.getTask_name() == "Nop") break;
                        cout << "\n\n";
                        cout << tmp;
                        cout << "\n\n";
                        break;
                    }
                    case 3 : {
                        PERSONAL_TASK tmp;
                        tmp = user.search (user.get_personal_task_vector(), n);
                        if (tmp.getTask_name() == "Nop") break;
                        cout << "\n\n";
                        cout << tmp;
                        cout << "\n\n";
                        break;
                    }
                }
                break;
            }
            case 10 : {
                return 0;
                break;
            }
            default : {
                cout << "Error command\n\n";
                break;
            }
        }
    }
}
