# Java-Streams-Programs-Interview-Questions

1. Java program to count the occurrence of each character in a string?

       Example : Java
       
       J = 1 a = 2 v =1
   
2. Java program to find all duplicate & Unique element from a given string?

3. Java program to find first non-repeat element from a given string?

4. Java program to find longest string from given array?

5. Java program to find all elements from array who starts with 1?

---------------------------------------------------------------------------------

These are the methods are discussed,

  	forEach(Consumer)  -> iteration purupsoe.....
  	filter(Predicate)
  	collect(Collector) ....list , map
  	map(Function)
  	distinct()   ... avoid duplicates
  	flatMap(Function)
  	sorted(Comparator both ASC and DESC)
  	min() and max()
  	GroupBy
  	findFirst()
  	findAny()
  	anyMatch(Predicate)
  	allMatch(Predicate)
  	noneMatch(Predicate)
  	limit(long maxSize)
  	skip(long n)

Java Stream Highest Paid Salary Statement.

	List<Employee> highestSalaryAscOrderList = employees.stream().sorted(Comparator.comparing(Employee::getSalary).collect(Collectors.toList());

	List<Employee> highestSalaryDscOrderList = employees.stream.sorted(Collections.reverseOrder(Comparator.comparing(Employee::getSalary)).collect(Collectors.toList());

	Optional<employee>  highestPaidEmployee  = employeesList.stream().max(Comparator.comparingDouble(Employee::getSalary())).forEach(System.out::println);

	Optional<employee>  lowestPaidEmployee  = employeesList.stream().min(Comparator.comparingDouble(Employee::getSalary())).forEach(System.out::println);


Get Gender :

	Map<String, List<Employee>> employeeGroup = employees.stream().collect(Collectors.groupingBy(Employee::getGender);

// Gender -> names 

	Map<String,List<String>> employeeGroupName = employees.stream().collect(Collectors.groupingBy(Employee::getGender,Collectors.mapping(Employee::getName),Collectors.toList());

// Gender -> count

	Map<String,Long> genderCount = employees.stream().collect(Collectors.groupingBy(Employee::getGender,Collectors.counting());


//find first

	Optional<Employee> findFirstElement = employees.stream().filter(e->e.getDept().equals("Dev")).findFirst();

		System.out.println(findFirstElement.get()); //NPE

		if(findFirstElement.isPresent()){
		  System.out.println(findFirstElement.get());
		}
		
	findFirstElement.isPresent(e->System.out.println(e.getName());

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

	Employee findFirstElement = employees.stream().filter(e->e.getDept().equals("Dev")).findFirst().orElseThrow(()->new IllegalArgumentException("Employee Not Found"));

	System.out.println(findFirstElement); 

	In case wrong dept, it will throw Exception.

	Employee findFirstElement = employees.stream().filter(e->e.getDept().equals("xyz")).findFirst().orElseThrow(()->new IllegalArgumentException("Employee Not Found"));

// findAny

	Employee findAnyElement = employees.stream().filter(e->e.getDept().equals("xyz")).findAny().orElseThrow(()->new IllegalArgumentException("Employee Not Found"));

	System.out.println(findAnyElement);

//anyMatch(Predicate), allMatch(Predicate) , noneMatch(Predicate)

	boolean developmentEmpAnyMatch = employees.stream().anyMatch(e->e.getDept().equals("Development"));

	System.out.println("Is there any employee match from development dept "+ developmentEmpAnyMatch);


	if you give some random name it will fail.

	boolean developmentEmpAnyMatch = employees.stream().anyMatch(e->e.getDept().equals("fdfdd"));


	boolean developmentEmpAllMatch = employees.stream().allMatch(e->e.getSalary>50000); // 55000

	System.out.println("Is there all employee match from development dept "+ developmentEmpAllMatch);  //false

	boolean isNoneMatch = employees.stream().noneMatch(e->e.getDept().equals("HR"));

	System.out.println(isNoneMatch); //false

	boolean isNoneMatch = employees.stream().noneMatch(e->e.getDept().equals("affafd"));

	System.out.println(isNoneMatch); //true

// limit(long)

Top 3 paid employee find.

	List<Employee> top3PaidEmployee = employees.stream().sorted(Comparator.comparing(Employee::getSalary).reversed()).limit(3).collect(Collectors.toList());

	//System.out.println(top3PaidEmployee);

	//top3PaidEmployee.forEach(System.out::println);

	top3PaidEmployee.forEach(e-> System.out.println(e.getName()));

// skip(long) , first 5 elements. it is mostly using for pagination purpose.

	List<Employee> skipEmployee = employees.stream().skip(5).collect(Collectors.toList());






