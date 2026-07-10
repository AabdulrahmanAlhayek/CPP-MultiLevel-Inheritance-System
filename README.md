#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

class clsPerson
{
private:
    string _FirstName;
    string _LastName;
    int _Id;
    string _Email;
    string _Phone;

public:
    /********Getters************/
    string GetFirstName() { return _FirstName; }
    string GetLastName() { return _LastName; }
    string GetFullName() { return _FirstName + " " + _LastName; }
    string GetEmail() { return _Email; }
    string GetPhone() { return _Phone; }
    int GetId() { return _Id; }

    /********setters************/
    void SetFirstName(string FirstName) { _FirstName = FirstName; }
    void SetLastName(string LastName) { _LastName = LastName; }
    void SetPhone(string Phone) { _Phone = Phone; }
    void SetEmail(string Email) { _Email = Email; }

    /********Properties*********/
    __declspec(property(get = GetFirstName, put = SetFirstName)) string FirstName;
    __declspec(property(get = GetLastName, put = SetLastName)) string LastName;
    __declspec(property(get = GetFullName)) string FullName;
    __declspec(property(get = GetPhone, put = SetPhone)) string Phone;
    __declspec(property(get = GetEmail, put = SetEmail)) string Email;
    __declspec(property(get = GetId)) int Id;

    /********constructors*******/
    clsPerson(string FirstName, string LastName, string Phone, string Email, int Id)
    {
        _FirstName = FirstName;
        _LastName = LastName;
        _Phone = Phone;
        _Email = Email;
        _Id = Id;
    }

    /********Methods************/
    void Print() {
        cout << "Info:\n"
            << "____________________________\n"
            << "ID\t: " << _Id << endl
            << "FirstName : " << _FirstName << endl
            << "LastName : " << _LastName << endl
            << "Full Name : " << FullName << endl
            << "Email : " << _Email << endl
            << "Phone Number : " << _Phone << endl
            << "____________________________\n\n\n";
    }
    void SendEmail(string Subject, string Body)
    {
        cout << "The Following Message Sent Successfully to Email (" << _Email << ")" << endl;
        cout << "Subject :" << Subject << endl;
        cout << "Body : " << Body << endl;
    }
    void SendSMS(string TextMessage)
    {
        cout << "The Following SMS Send Successfully to Phone \" " << _Phone << "\"" << endl;
        cout << "The Text Message is :" << TextMessage << endl;
    }
};

class clsEmployee : public clsPerson
{
private:
    float _Salary;
    string _Department;
    string _Title;

public:
    void setTitle(string Title) { _Title = Title; }
    string GetTitle() { return _Title; }
    
    void setDepartment(string Department) { _Department = Department; }
    string GetDepartment() { return _Department; }
    
    void setSalary(float Salary) { _Salary = Salary; }
    float GetSalary() { return _Salary; }

    // inheritance constructor
    clsEmployee(string FirstName, string LastName, string phone, string Email, int Id, string Department, string Title, float Salary) 
        : clsPerson(FirstName, LastName, phone, Email, Id)
    {
        _Salary = Salary;
        _Title = Title;
        _Department = Department;
    }

    /**********************************/
    __declspec(property(get = GetSalary, put = SetSalary)) float Salary;
    __declspec(property(get = GetDepartment, put = SetDepartment)) string Department;
    __declspec(property(get = GetTitle, put = SetTitle)) string Title;
    /**********************************/

    void Print()
    {
        cout << "Info:\n"
            << "____________________________\n"
            << "ID\t: " << Id << endl
            << "FirstName : " << FirstName << endl
            << "LastName : " << LastName << endl
            << "Full Name : " << FullName << endl
            << "Email : " << Email << endl
            << "Phone Number : " << Phone << endl
            << "Title :" << Title << endl
            << "Department : " << Department << endl
            << "Salary : " << Salary << endl
            << "____________________________\n\n\n";
    }
};

class clsProgrammer : public clsEmployee
{
private:
    string _MainProgrammingLanguage;

public:
    clsProgrammer(string FirstName, string LastName, string phone, string Email, int Id, string Department, string Title, float Salary, string MainProgrammingLanguage)
        : clsEmployee(FirstName, LastName, phone, Email, Id, Department, Title, Salary)
    {
        _MainProgrammingLanguage = MainProgrammingLanguage;
    }

    /***************setters*************/
    void SetMainProgrammingLanguage(string MainProgrammingLanguage) { _MainProgrammingLanguage = MainProgrammingLanguage; }
    /***************Getters*************/
    string GetMainProgrammingLanguage() { return _MainProgrammingLanguage; }

    __declspec(property(get = GetMainProgrammingLanguage, put = SetMainProgrammingLanguage)) string MainProgrammingLanguage;

    /***************Methods*************/
    void Print()
    {
        cout << "Info:\n"
            << "____________________________\n"
            << "ID\t: " << Id << endl
            << "FirstName : " << FirstName << endl
            << "LastName : " << LastName << endl
            << "Full Name : " << FullName << endl
            << "Email : " << Email << endl
            << "Phone Number : " << Phone << endl
            << "Title :" << Title << endl
            << "Department : " << Department << endl
            << "Salary : " << Salary << endl
            << "MainProgrammingLanguage : " << MainProgrammingLanguage << endl
            << "____________________________\n\n\n";
    }
};

int main()
{
    clsProgrammer Programmer1("Abdulrahman", "Alhayek", "0988544065", "Abdulrahman.Alhayek2005@gmail.com", 202411176, "Engineering", "Software Developer", 7500, "C++");
    Programmer1.Print();

    system("pause>0");
    return 0;
}
