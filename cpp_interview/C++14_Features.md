[C++14 Features](https://www.youtube.com/playlist?list=PLk6CEY9XxSIAloDTEauOy_ss9fEqSP4JR)



# Digit Separator in C++14

* Question:

  What is Digit Separator in C++14?

* Answer:

  1. There is a better code readability with Digit Separator in C++14.
  2. We use single quotation mark (') for as a Digit Separator.
  3. Why ' for Digit Separator, why not something else?

     There is no rule for using single quotation mark ( ' ) sign for Digit Separator.

  

  Example:

  ~~~~c++
  #include <iostream>
  
  //using namespace std;
  
  int main()
  {
  	auto val = 1'048'576;
  	std::cout << val << std::endl;
  
  	return 0;
  }
  ~~~~





# Binary Literals in C++14

* Question:

  What is Binary Literals in C++14?

* Answer:

  1. Now we can directly write Binary Literals in C++14.
  2. GCC compiler had this feature but not standardized, now C++14 have standardized it.

  

  Example:

  ~~~~c++
  #include <iostream>
  
  //using namespace std;
  
  int main()
  {
  	int b1 = 0xFF; // binary 11111111
  	std::cout << b1 << std::endl; // 255
  
  	int b2 = 0b11111111; // 0b OR 0B
  	std::cout << b2 << std::endl; // 255
  
  	int b3 = 0b1111'1111; // digit seperator
  	std::cout << b3 << std::endl; // 255
  
  	return 0;
  }
  ~~~~





# Deprecated Attribute in C++14

* Question:

  What is Deprecated Attribute in C++14?

* Answer:

  ~~~~
  [[Deprecated]]
  
  //marded as outdated
  ~~~~

  1. Deprecated means use of the name or entity declared with this attribute is allowed, but discouraged for some reason.
  2. Compiler gives warnings and if string literals are provided they are included in warnings.

  

  List which can be deprecated:

  * class, struct, union
  * typedef
  * variable
  * non-static data member
  * function 
  * namespace
  * enumeration 
  * enumerator
  * template specialization

  

  Example:

  ~~~~c++
  #include <iostream>
  
  //using namespace std;
  
  [[deprecated("This function will be replaced with template add function")]]
  int add(int a, int b) { return a + b; }
  
  int main()
  {
  	// warning: 'add' id deprecated: This function will be replaced with template add function
  	std::cout << add(1, 2) << std::endl;
  
  	return 0;
  }
  ~~~~





# Variable Template in C++14

* Question:

  What is Variable Template in C++14?

* Answer:

  Before C++14 we had Function Template and Class Template, now we have Variable Template.

  

  Example:

  ~~~~c++
  #include <iostream>
  //#include <complex>
  
  //using namespace std;
  
  template<typename T>
  T pi = T(3.1415926535897932384626433L);
  
  int main()
  {
  	pi<char> = 'a';
  	std::cout.precision(std::numeric_limits<long double>::max_digits10);
  	std::cout << pi<int> << std::endl;			// 3
  	std::cout << pi<float> << std::endl;		//  
  	std::cout << pi<double> << std::endl;		// 
  	std::cout << pi<long double> << std::endl;	// 
  	std::cout << pi<char> << std::endl; // a
  
  	return 0;
  }
  ~~~~





# Generic Lambda in C++14

* Question:

  What is Generic Lambda in C++14?

* Answer:

  1. Now in C++14 we have Generic / Polymorphic Lambda.
  2. It deduces type at run time.

  

  Example:

  ~~~~c++
  #include <iostream>
  
  //using namespace std;
  
  int main()
  {
      // auto is allowed in lambda parameter in C++14
  	auto add = [](auto x, auto y) { return x + y; };
  
  	int a = 1, b = 2;
  	std::string str1 = "Hello ", str2 = "World!";
  
  	std::cout << add(a, b) << std::endl; // 3
  	std::cout << add(str1, str2) << std::endl; // Hello World!
  
  	return 0;
  }
  ~~~~





# Return Type Deduction in C++14

* Question:

  What is Return Type Deduction in C++14?

* Answer:

  Using an auto return type in C++14, the compiler will attempt to deduce the type for you. 
  1. auto
  2. decltype(auto)

  

  Example:

  ~~~~c++
  #include <iostream>
  
  //using namespace std;
  
  // return type: int
  auto add(int a, int b) { return a + b; }
  
  // return type: int&
  //auto& increment(int& a) { a++; return a; }
  decltype(auto) increment(int& a) { a++; return a; }
  
  int main()
  {
  	int result1 = add(1, 2);
  	std::cout << result1 << std::endl;
  
  	int num = 10;
  	int& result2 = increment(num);
  	std::cout << result2 << std::endl;
  	std::cout << num << std::endl;
  
  
  	const int x = 0;
  	auto x1 = x; // int
  	decltype(auto) x2 = x; // const int
  
  	x1 = 10;
  	//x2 = 20; // error, x2 is const int
  
  	std::cout << x << std::endl; // 0
  	std::cout << x1 << std::endl; // 10
  	std::cout << x2 << std::endl; // 0
  
  
  	int y = 0;
  	int& y1 = y;
  	auto y2 = y1; // int
  	decltype(auto) y3 = y1; // int&
  
  	y2 = 10;
  	std::cout << y << std::endl; // 0
  	std::cout << y2 << std::endl; // 10
  	y3 = 10;
  	std::cout << y << std::endl; // 10
  	std::cout << y3 << std::endl; // 10
  
  
  	int&& z = 0;
  	auto z1 = std::move(z); // int
  	decltype(auto) z2 = std::move(z); // int&&
  
  	z1 = 10;
  	std::cout << z << std::endl; // 0
  	std::cout << z1 << std::endl; // 10
  	z2 = 10;
  	std::cout << z << std::endl; // 10
  	std::cout << z2 << std::endl; // 10
  
  	return 0;
  }
  ~~~~

  