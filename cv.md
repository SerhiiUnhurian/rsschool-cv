# Resume
## Serhii Unhurian 

### Personal information

Email: unguryan23@gmail.com\
Skype: kefirchik10\
Date of birth: 23th January 1993\
Current location: Ukraine, Kyiv\
Nationality: Ukrainian\
Marital status: single

### Summary

I have an engineering background and my previous experience is in aircraft construction. I worked as a strength engineer on Boeing projects. While I was working, I realized that I am attracted to IT technologies and programming in particular, just like my heart belongs to it. I find this a very exciting activity and devote a lot of time to self-education in this direction. My goal is to build a career as a software engineer.

### Education

* National Technical University of Ukraine "Kyiv Polytechnic Institute", Faculty of Mechanical Engineering, Master’s degree in Mechanical Engineering (09.2012-06.2017).
* Kiev College of electronic devices, Faculty of Mechanical Engineering/ Technology of processing materials and automatic processing line, Technical Diploma (09.2008-05.2012).

### Skills

* Bsics of HTML, CSS, Javascript
* Solid knowledge of C/C++
* Undestanding concepts of OOP.
* Undestanding common algorithms and data structures.
* Git/Github
* Experience with Jira
* Familiar with Java, PHP, OOAD, unit testing.

### Courses

* July 2019 - December 2019, successfully completed [Coding Boot Camp](https://devclub.com/what/bootcamp). I got basic knowledge along with a lot of practice in the following programming languages: C, C++. Also, I had the opportunity to write in Java and PHP. Learned basics of Git, unit testsing, algorithms and data structures.

*	May 4, 2016 - Successfully completed online training course "Software Testing"  in the QATestLab training center. Familiar with WEB and mobile applications testing, making test plans and checklists, making bug reports and entering them into bug tracking system.

* I regularly do online courses on https://www.linkedin.com/ and https://www.udemy.com/.
The latest are: Design Patterns, Object-Oriented Design, Data Structures.

### English

I speak English at upper-intermediate level. I have been learning English scince my early ages and have taken several advanced courses and got certificates. I also devoted a great deal of time to self-studying. For now, I regularly practice my language with my foreign friends.

### Code examples

Customer.h
```c++
#ifndef CUSTOMER_H
#define CUSTOMER_H

#include <iostream>
#include <set>

class Order;

class Customer {
private:
	std::string m_name;
	std::set<Order*> m_orders;

public:
	Customer(std::string name);

	~Customer();

	std::string getName() const;
	void getOrders() const;
	const std::set<Order*>& getAllOrders() const;

	void addOrder(Order* order);
	void deleteOrder(Order* order);
};

std::ostream& operator<<(std::ostream& out, const Customer* customer);

#endif // CUSTOMER_H
```

Customer.cpp
```C++
#include "Customer.h"
#include "Order.h"

Customer::Customer(std::string name) : m_name(name) 
{
}

Customer::~Customer() {
	if ( !m_orders.empty() ) {
		auto it = m_orders.begin();

		while ( it != m_orders.end() ) {
			delete *it;
			it++;
		}
	}
	std::cout << "Customer " << m_name << " is deleted!\n";
}

std::string Customer::getName() const {
	return m_name;
}

void Customer::getOrders() const {
	if ( !m_orders.empty() ) {
		auto it = m_orders.begin();

		while ( it != m_orders.end() ) {
			std::cout << *it << std::endl;
			it++;
		}
	}
}

const std::set<Order*>& Customer::getAllOrders() const {
	return m_orders;
}

void Customer::addOrder(Order* order) {
	m_orders.insert(order);	
}

void Customer::deleteOrder(Order* order) {
	m_orders.erase(order);
}

std::ostream& operator<<(std::ostream& out, const Customer* customer) {
	int size = customer->getAllOrders().size();
	std::string ending = size > 1 ? "s" : "";

	out << "Customer " << customer->getName() << " has "<< size << " order" << ending << std::endl;

	auto it = customer->getAllOrders().begin();

	while ( it != customer->getAllOrders().end() ) {
		out << "#" << (*it)->getID() << std::endl;
		it++;
	}
	return out;
}
```
