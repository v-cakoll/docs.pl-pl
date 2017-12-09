---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a7f30293bb2d50981353badfb7e373b60dcfeec
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2017
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="22351-102">Programowanie zorientowane obiektowo (C#)</span><span class="sxs-lookup"><span data-stu-id="22351-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="22351-103">C# zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizm.</span><span class="sxs-lookup"><span data-stu-id="22351-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="22351-104">*Hermetyzacja* oznacza, że grupy powiązane właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="22351-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="22351-105">*Dziedziczenie* opisuje może tworzyć nowe klasy oparte na istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="22351-106">*Polimorfizm* oznacza, że może mieć wielu klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="22351-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="22351-107">W tej sekcji opisano następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="22351-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="22351-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="22351-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="22351-109">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="22351-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="22351-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="22351-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="22351-111">Metody</span><span class="sxs-lookup"><span data-stu-id="22351-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="22351-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="22351-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="22351-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="22351-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="22351-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="22351-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="22351-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="22351-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="22351-116">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="22351-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="22351-117">Utworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="22351-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="22351-118">Klasy statyczne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="22351-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="22351-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="22351-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="22351-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="22351-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="22351-121">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="22351-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="22351-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="22351-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="22351-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="22351-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="22351-124">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="22351-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a><span data-ttu-id="22351-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="22351-125">Classes and Objects</span></span>  
 <span data-ttu-id="22351-126">Warunki *klasy* i *obiektu* są czasami używane zamiennie, ale w rzeczywistości opisano klasy *typu* obiektów, gdy obiekty są użyteczne  *wystąpienia* klas.</span><span class="sxs-lookup"><span data-stu-id="22351-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="22351-127">Dlatego utworzenie obiektu jest nazywany *wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="22351-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="22351-128">Przy użyciu odpowiednio planu, klasa to umożliwi, a obiekt jest budynku z tego planu.</span><span class="sxs-lookup"><span data-stu-id="22351-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="22351-129">Aby zdefiniować klasy:</span><span class="sxs-lookup"><span data-stu-id="22351-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="22351-130">C# są także światła wersja klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i chcesz używać zbyt dużej ilości pamięci do tego.</span><span class="sxs-lookup"><span data-stu-id="22351-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="22351-131">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="22351-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="22351-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-133">klasy</span><span class="sxs-lookup"><span data-stu-id="22351-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="22351-134">— Struktura</span><span class="sxs-lookup"><span data-stu-id="22351-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a><span data-ttu-id="22351-135">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="22351-135">Class Members</span></span>  
 <span data-ttu-id="22351-136">Każda klasa może mieć różne *klasy elementów członkowskich* zawierające właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnych klas i obiektów.</span><span class="sxs-lookup"><span data-stu-id="22351-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a><span data-ttu-id="22351-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="22351-137">Properties and Fields</span></span>  
 <span data-ttu-id="22351-138">Pola i właściwości reprezentują informacje, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="22351-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="22351-139">Pola są podobne do zmiennych, ponieważ może być odczytany lub ustawić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="22351-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="22351-140">Aby zdefiniować pola:</span><span class="sxs-lookup"><span data-stu-id="22351-140">To define a field:</span></span>  
  
```csharp  
Class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="22351-141">Właściwości mają get i ustaw procedur, które zapewniają większą kontrolę w sposób ustawiona lub zwrócona wartości.</span><span class="sxs-lookup"><span data-stu-id="22351-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="22351-142">C# służy do utworzenia prywatnej pola do przechowywania wartości właściwości lub użyj tak zwane właściwości zaimplementowane automatycznie utworzyć w tym polu automatycznie w tle, które zapewniają podstawowa logika procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="22351-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="22351-143">Aby zdefiniować właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="22351-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="22351-144">Jeśli musisz wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawowa logika do przechowywania i pobierania jej:</span><span class="sxs-lookup"><span data-stu-id="22351-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 <span data-ttu-id="22351-145">Większość właściwości mają metody lub procedury zarówno Ustawianie i pobieranie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="22351-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="22351-146">Można jednak utworzyć właściwości tylko do odczytu lub w trybie tylko do zapisu, aby uniemożliwić ich modyfikacji lub odczytu.</span><span class="sxs-lookup"><span data-stu-id="22351-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="22351-147">W języku C#, można pominąć `get` lub `set` metody property.</span><span class="sxs-lookup"><span data-stu-id="22351-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="22351-148">Jednak automatycznie implementowane właściwości nie może być tylko do odczytu lub w trybie tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="22351-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="22351-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-150">Pobierz</span><span class="sxs-lookup"><span data-stu-id="22351-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="22351-151">zestaw</span><span class="sxs-lookup"><span data-stu-id="22351-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a><span data-ttu-id="22351-152">Metody</span><span class="sxs-lookup"><span data-stu-id="22351-152">Methods</span></span>  
 <span data-ttu-id="22351-153">A *metody* to operacja, którą można wykonać obiektu.</span><span class="sxs-lookup"><span data-stu-id="22351-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="22351-154">Aby zdefiniować metody klasy:</span><span class="sxs-lookup"><span data-stu-id="22351-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="22351-155">Klasa może mieć wielu implementacji lub *przeciążenia*, metody różne liczby parametrów ani typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="22351-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="22351-156">Aby można było przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="22351-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="22351-157">W większości przypadków należy zadeklarować metody w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="22351-158">Jednak C# obsługuje również *metody rozszerzenia* umożliwiające dodawanie metody do istniejącej klasy poza rzeczywiste definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="22351-159">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-160">Metody</span><span class="sxs-lookup"><span data-stu-id="22351-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="22351-161">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="22351-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a><span data-ttu-id="22351-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="22351-162">Constructors</span></span>  
 <span data-ttu-id="22351-163">Konstruktory są metody klasy, które są wykonywane automatycznie, gdy utworzono obiekt danego typu.</span><span class="sxs-lookup"><span data-stu-id="22351-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="22351-164">Konstruktory zainicjować zazwyczaj elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="22351-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="22351-165">Konstruktor można uruchomić tylko raz, podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="22351-166">Ponadto w Konstruktorze kod zawsze uruchamiany przed innymi kod w klasie.</span><span class="sxs-lookup"><span data-stu-id="22351-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="22351-167">Jednak w taki sam sposób jak w przypadku innych metod, można utworzyć wielu przeciążeń konstruktora.</span><span class="sxs-lookup"><span data-stu-id="22351-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="22351-168">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="22351-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="22351-169">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-169">For more information, see:</span></span>  
  
 <span data-ttu-id="22351-170">[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="22351-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a><span data-ttu-id="22351-171">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="22351-171">Finalizers</span></span>  
 <span data-ttu-id="22351-172">Finalizatory są używane do destruct wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="22351-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="22351-173">W programie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i wersji pamięci dla zarządzanych obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22351-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="22351-174">Jednakże nadal może być konieczne finalizatorów, aby oczyścić wszelkie niezarządzane zasoby, tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="22351-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="22351-175">Może istnieć tylko jedna finalizatory klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="22351-176">Aby uzyskać więcej informacji na temat finalizatory i wyrzucanie elementów bezużytecznych w programie .NET Framework, zobacz [wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="22351-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a><span data-ttu-id="22351-177">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="22351-177">Events</span></span>  
 <span data-ttu-id="22351-178">Zdarzenia włączyć klasę lub obiekt, aby powiadomić innych grup lub obiektów, kiedy coś odsetek występuje.</span><span class="sxs-lookup"><span data-stu-id="22351-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="22351-179">Klasa, która wysyła (lub zgłasza) zdarzenia jest nazywany *wydawcy* i klasy, które odbierać (lub dojścia) zdarzenia są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="22351-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="22351-180">Aby uzyskać więcej informacji o zdarzeniach, sposób ich pojawienia się i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="22351-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="22351-181">Aby zadeklarować zdarzenia w klasie, użyj [zdarzeń](../../../csharp/language-reference/keywords/event.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="22351-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="22351-182">Aby zgłosić zdarzenie, wywołania delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="22351-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="22351-183">Aby subskrybować zdarzenia, użyj `+=` operatora; Aby anulować subskrypcję zdarzenia, użyj `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="22351-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a><span data-ttu-id="22351-184">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="22351-184">Nested Classes</span></span>  
 <span data-ttu-id="22351-185">Nosi nazwę klasy zdefiniowanej w klasie innej *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="22351-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="22351-186">Domyślnie zagnieżdżona klasa jest prywatne.</span><span class="sxs-lookup"><span data-stu-id="22351-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="22351-187">Można utworzyć wystąpienia klasy zagnieżdżonej, należy użyć nazwy klasy kontenera znak kropki (.) i po niej nazwę klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="22351-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a><span data-ttu-id="22351-188">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="22351-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="22351-189">Wszystkie klasy i elementów członkowskich klasy można określić poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="22351-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="22351-190">Dostępne są następujące modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="22351-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="22351-191">Modyfikator C#</span><span class="sxs-lookup"><span data-stu-id="22351-191">C# Modifier</span></span>|<span data-ttu-id="22351-192">Definicja</span><span class="sxs-lookup"><span data-stu-id="22351-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="22351-193">publiczny</span><span class="sxs-lookup"><span data-stu-id="22351-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="22351-194">Typ lub element członkowski jest możliwy przez inny kod, w tym samym zestawie lub innego zestawu, który odwołuje się on.</span><span class="sxs-lookup"><span data-stu-id="22351-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="22351-195">prywatne</span><span class="sxs-lookup"><span data-stu-id="22351-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="22351-196">Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="22351-197">chronione</span><span class="sxs-lookup"><span data-stu-id="22351-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="22351-198">Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22351-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="22351-199">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="22351-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="22351-200">Typ lub element członkowski jest możliwy przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="22351-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="22351-201">chronionych wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="22351-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="22351-202">Typ lub element członkowski jest dostępna przez dowolny kod w tym samym zestawie lub dowolnej klasy pochodnej w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="22351-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="22351-203">prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="22351-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="22351-204">Typ lub element członkowski jest możliwy przez kod w tej samej klasy lub w klasie pochodnej w zestawie klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="22351-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="22351-205">Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="22351-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a><span data-ttu-id="22351-206">Utworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="22351-206">Instantiating Classes</span></span>  
 <span data-ttu-id="22351-207">Do utworzenia obiektu, należy utworzyć wystąpienia klasy lub utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="22351-208">Po utworzenie wystąpienia klasy, można przypisać wartości do właściwości i pola wystąpienia i wywołania metody klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="22351-209">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatory obiektów:</span><span class="sxs-lookup"><span data-stu-id="22351-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="22351-210">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-211">New — Operator</span><span class="sxs-lookup"><span data-stu-id="22351-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="22351-212">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="22351-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a><span data-ttu-id="22351-213">Klasy statyczne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="22351-213">Static Classes and Members</span></span>  
 <span data-ttu-id="22351-214">Statyczny element członkowski klasy jest właściwość, procedura lub pola, które jest współużytkowana przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="22351-215">Do definiowania statycznego elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="22351-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="22351-216">Aby uzyskać dostęp do statycznego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="22351-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="22351-217">Klasy statyczne w języku C# mieć tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="22351-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="22351-218">Statyczne elementy członkowskie także nie może uzyskać dostępu właściwości niestatycznego pola lub metody</span><span class="sxs-lookup"><span data-stu-id="22351-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="22351-219">Aby uzyskać więcej informacji, zobacz: [statycznych](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="22351-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a><span data-ttu-id="22351-220">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="22351-220">Anonymous Types</span></span>  
 <span data-ttu-id="22351-221">Typy anonimowe umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="22351-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="22351-222">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="22351-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="22351-223">Klasa nie ma używać nazwy i zawiera właściwości, które określisz w odwołaniu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="22351-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="22351-224">Można utworzyć wystąpienia typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="22351-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="22351-225">Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="22351-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a><span data-ttu-id="22351-226">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="22351-226">Inheritance</span></span>  
 <span data-ttu-id="22351-227">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa rozszerza i modyfikuje zachowanie, który jest zdefiniowany w innej klasy.</span><span class="sxs-lookup"><span data-stu-id="22351-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="22351-228">Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*, i nosi nazwę klasy, która dziedziczy tych członków *klasy*.</span><span class="sxs-lookup"><span data-stu-id="22351-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="22351-229">Jednak wszystkie klasy w języku C# niejawnie dziedziczyć <xref:System.Object> klasy, która obsługuje hierarchii klas .NET i udostępnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="22351-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22351-230">C# nie obsługuje wielu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="22351-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="22351-231">Oznacza to można określić tylko jedną klasę podstawową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22351-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="22351-232">Dziedziczenie z klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="22351-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 <span data-ttu-id="22351-233">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="22351-233">By default all classes can be inherited.</span></span> <span data-ttu-id="22351-234">Jednak można określić, czy nie mogą być używane jako klasę podstawową klasy lub utworzyć klasę, która może służyć jako klasę podstawową tylko.</span><span class="sxs-lookup"><span data-stu-id="22351-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="22351-235">Aby określić, że klasa nie można użyć jako klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="22351-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="22351-236">Aby określić, że klasa może służyć jako klasę podstawową tylko i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="22351-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="22351-237">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-238">zapieczętowane</span><span class="sxs-lookup"><span data-stu-id="22351-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="22351-239">abstrakcyjny</span><span class="sxs-lookup"><span data-stu-id="22351-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a><span data-ttu-id="22351-240">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="22351-240">Overriding Members</span></span>  
 <span data-ttu-id="22351-241">Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie ze swojej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="22351-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="22351-242">Aby zmienić zachowanie dziedziczony element członkowski, należy go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="22351-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="22351-243">Oznacza to można zdefiniować nowej implementacji metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22351-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="22351-244">Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:</span><span class="sxs-lookup"><span data-stu-id="22351-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="22351-245">Modyfikator C#</span><span class="sxs-lookup"><span data-stu-id="22351-245">C# Modifier</span></span>|<span data-ttu-id="22351-246">Definicja</span><span class="sxs-lookup"><span data-stu-id="22351-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="22351-247">wirtualny</span><span class="sxs-lookup"><span data-stu-id="22351-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="22351-248">Umożliwia elementu członkowskiego klasy do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22351-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="22351-249">zastąpienie</span><span class="sxs-lookup"><span data-stu-id="22351-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="22351-250">Zastępuje członka wirtualnego (możliwym do zastąpienia) zdefiniowana w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="22351-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="22351-251">abstrakcyjny</span><span class="sxs-lookup"><span data-stu-id="22351-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="22351-252">Wymaga, aby element członkowski klasy do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22351-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="22351-253">New — modyfikator</span><span class="sxs-lookup"><span data-stu-id="22351-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="22351-254">Ukrywa element członkowski dziedziczona z klasy podstawowej</span><span class="sxs-lookup"><span data-stu-id="22351-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a><span data-ttu-id="22351-255">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="22351-255">Interfaces</span></span>  
 <span data-ttu-id="22351-256">Interfejsy, takich jak klasy, zdefiniuj zbiór właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="22351-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="22351-257">Jednak w przeciwieństwie do klasy, interfejsy nie dostarcza implementacji.</span><span class="sxs-lookup"><span data-stu-id="22351-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="22351-258">Są implementowane przez klasy i zdefiniowane jako osobne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="22351-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="22351-259">Interfejs reprezentuje kontraktu, w tym klasy, która implementuje interfejs musi implementować każdego aspektu ten interfejs, dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="22351-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="22351-260">Aby zdefiniować interfejsu:</span><span class="sxs-lookup"><span data-stu-id="22351-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="22351-261">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="22351-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="22351-262">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="22351-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="22351-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="22351-264">Interfejs</span><span class="sxs-lookup"><span data-stu-id="22351-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a><span data-ttu-id="22351-265">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="22351-265">Generics</span></span>  
 <span data-ttu-id="22351-266">Klasy, struktury, interfejsy i metody w programie .NET Framework mogą zawierać *parametry typu* definiującą typów obiektów, które mogą przechowywać lub użyć.</span><span class="sxs-lookup"><span data-stu-id="22351-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="22351-267">Najbardziej typowym przykładem typów ogólnych jest kolekcją, w którym można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="22351-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="22351-268">Aby zdefiniować klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="22351-268">To define a generic class:</span></span>  
  
```csharp  
Public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="22351-269">Można utworzyć wystąpienia klasy generycznej:</span><span class="sxs-lookup"><span data-stu-id="22351-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="22351-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-271">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="22351-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="22351-272">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="22351-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a><span data-ttu-id="22351-273">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="22351-273">Delegates</span></span>  
 <span data-ttu-id="22351-274">A *delegować* jest typ, który określa podpis metody i można udostępnić odwołanie do dowolnej metody zgodnego podpisu.</span><span class="sxs-lookup"><span data-stu-id="22351-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="22351-275">Można wywołać (lub wywołać) metoda za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="22351-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="22351-276">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="22351-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22351-277">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="22351-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="22351-278">Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="22351-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="22351-279">Do utworzenia delegata:</span><span class="sxs-lookup"><span data-stu-id="22351-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="22351-280">Aby utworzyć odwołanie do metody, która odpowiada podpisu określony na podstawie delegata:</span><span class="sxs-lookup"><span data-stu-id="22351-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 <span data-ttu-id="22351-281">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22351-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="22351-282">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="22351-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="22351-283">Delegowanie</span><span class="sxs-lookup"><span data-stu-id="22351-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="22351-284">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22351-284">See Also</span></span>  
 [<span data-ttu-id="22351-285">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="22351-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
