---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6da28e97a33e962d4926a3b65d0fdf388c252d9a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="7fcb2-102">Programowanie zorientowane obiektowo (C#)</span><span class="sxs-lookup"><span data-stu-id="7fcb2-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="7fcb2-103">C# zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizm.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="7fcb2-104">*Hermetyzacja* oznacza, że grupy powiązane właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="7fcb2-105">*Dziedziczenie* opisuje może tworzyć nowe klasy oparte na istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="7fcb2-106">*Polimorfizm* oznacza, że może mieć wielu klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="7fcb2-107">W tej sekcji opisano następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="7fcb2-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="7fcb2-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="7fcb2-109">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="7fcb2-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="7fcb2-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="7fcb2-111">Metody</span><span class="sxs-lookup"><span data-stu-id="7fcb2-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="7fcb2-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7fcb2-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="7fcb2-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="7fcb2-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="7fcb2-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7fcb2-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="7fcb2-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="7fcb2-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="7fcb2-116">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="7fcb2-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="7fcb2-117">Utworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="7fcb2-118">Klasy statyczne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7fcb2-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="7fcb2-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7fcb2-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="7fcb2-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="7fcb2-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="7fcb2-121">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7fcb2-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="7fcb2-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="7fcb2-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7fcb2-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="7fcb2-124">Delegaci</span><span class="sxs-lookup"><span data-stu-id="7fcb2-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a> <span data-ttu-id="7fcb2-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="7fcb2-125">Classes and Objects</span></span>  
 <span data-ttu-id="7fcb2-126">Warunki *klasy* i *obiektu* są czasami używane zamiennie, ale w rzeczywistości opisano klasy *typu* obiektów, gdy obiekty są użyteczne  *wystąpienia* klas.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="7fcb2-127">Dlatego utworzenie obiektu jest nazywany *wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="7fcb2-128">Przy użyciu odpowiednio planu, klasa to umożliwi, a obiekt jest budynku z tego planu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="7fcb2-129">Aby zdefiniować klasy:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="7fcb2-130">C# są także światła wersja klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i chcesz używać zbyt dużej ilości pamięci do tego.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="7fcb2-131">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="7fcb2-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-133">class</span><span class="sxs-lookup"><span data-stu-id="7fcb2-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="7fcb2-134">struct</span><span class="sxs-lookup"><span data-stu-id="7fcb2-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> <span data-ttu-id="7fcb2-135">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-135">Class Members</span></span>  
 <span data-ttu-id="7fcb2-136">Każda klasa może mieć różne *klasy elementów członkowskich* zawierające właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnych klas i obiektów.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a> <span data-ttu-id="7fcb2-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="7fcb2-137">Properties and Fields</span></span>  
 <span data-ttu-id="7fcb2-138">Pola i właściwości reprezentują informacje, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="7fcb2-139">Pola są podobne do zmiennych, ponieważ może być odczytany lub ustawić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="7fcb2-140">Aby zdefiniować pola:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-140">To define a field:</span></span>  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="7fcb2-141">Właściwości mają get i ustaw procedur, które zapewniają większą kontrolę w sposób ustawiona lub zwrócona wartości.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="7fcb2-142">C# służy do utworzenia prywatnej pola do przechowywania wartości właściwości lub użyj tak zwane właściwości zaimplementowane automatycznie utworzyć w tym polu automatycznie w tle, które zapewniają podstawowa logika procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="7fcb2-143">Aby zdefiniować właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="7fcb2-144">Jeśli musisz wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawowa logika do przechowywania i pobierania jej:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="7fcb2-145">Większość właściwości mają metody lub procedury zarówno Ustawianie i pobieranie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="7fcb2-146">Można jednak utworzyć właściwości tylko do odczytu lub w trybie tylko do zapisu, aby uniemożliwić ich modyfikacji lub odczytu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="7fcb2-147">W języku C#, można pominąć `get` lub `set` metody property.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="7fcb2-148">Jednak automatycznie implementowane właściwości nie może być tylko do odczytu lub w trybie tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="7fcb2-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-150">get</span><span class="sxs-lookup"><span data-stu-id="7fcb2-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="7fcb2-151">set</span><span class="sxs-lookup"><span data-stu-id="7fcb2-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> <span data-ttu-id="7fcb2-152">Metody</span><span class="sxs-lookup"><span data-stu-id="7fcb2-152">Methods</span></span>  
 <span data-ttu-id="7fcb2-153">A *metody* to operacja, którą można wykonać obiektu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="7fcb2-154">Aby zdefiniować metody klasy:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="7fcb2-155">Klasa może mieć wielu implementacji lub *przeciążenia*, metody różne liczby parametrów ani typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="7fcb2-156">Aby można było przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="7fcb2-157">W większości przypadków należy zadeklarować metody w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="7fcb2-158">Jednak C# obsługuje również *metody rozszerzenia* umożliwiające dodawanie metody do istniejącej klasy poza rzeczywiste definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="7fcb2-159">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-160">Metody</span><span class="sxs-lookup"><span data-stu-id="7fcb2-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="7fcb2-161">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="7fcb2-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> <span data-ttu-id="7fcb2-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7fcb2-162">Constructors</span></span>  
 <span data-ttu-id="7fcb2-163">Konstruktory są metody klasy, które są wykonywane automatycznie, gdy utworzono obiekt danego typu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="7fcb2-164">Konstruktory zainicjować zazwyczaj elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="7fcb2-165">Konstruktor można uruchomić tylko raz, podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="7fcb2-166">Ponadto w Konstruktorze kod zawsze uruchamiany przed innymi kod w klasie.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="7fcb2-167">Jednak w taki sam sposób jak w przypadku innych metod, można utworzyć wielu przeciążeń konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="7fcb2-168">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="7fcb2-169">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-169">For more information, see:</span></span>  
  
 <span data-ttu-id="7fcb2-170">[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a> <span data-ttu-id="7fcb2-171">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="7fcb2-171">Finalizers</span></span>  
 <span data-ttu-id="7fcb2-172">Finalizatory są używane do destruct wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="7fcb2-173">W programie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i wersji pamięci dla zarządzanych obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="7fcb2-174">Jednakże nadal może być konieczne finalizatorów, aby oczyścić wszelkie niezarządzane zasoby, tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="7fcb2-175">Może istnieć tylko jedna finalizatory klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="7fcb2-176">Aby uzyskać więcej informacji na temat finalizatory i wyrzucanie elementów bezużytecznych w programie .NET Framework, zobacz [wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a> <span data-ttu-id="7fcb2-177">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7fcb2-177">Events</span></span>  
 <span data-ttu-id="7fcb2-178">Zdarzenia włączyć klasę lub obiekt, aby powiadomić innych grup lub obiektów, kiedy coś odsetek występuje.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="7fcb2-179">Klasa, która wysyła (lub zgłasza) zdarzenia jest nazywany *wydawcy* i klasy, które odbierać (lub dojścia) zdarzenia są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="7fcb2-180">Aby uzyskać więcej informacji o zdarzeniach, sposób ich pojawienia się i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="7fcb2-181">Aby zadeklarować zdarzenia w klasie, użyj [zdarzeń](../../../csharp/language-reference/keywords/event.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="7fcb2-182">Aby zgłosić zdarzenie, wywołania delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="7fcb2-183">Aby subskrybować zdarzenia, użyj `+=` operatora; Aby anulować subskrypcję zdarzenia, użyj `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a> <span data-ttu-id="7fcb2-184">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="7fcb2-184">Nested Classes</span></span>  
 <span data-ttu-id="7fcb2-185">Nosi nazwę klasy zdefiniowanej w klasie innej *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="7fcb2-186">Domyślnie zagnieżdżona klasa jest prywatne.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="7fcb2-187">Można utworzyć wystąpienia klasy zagnieżdżonej, należy użyć nazwy klasy kontenera znak kropki (.) i po niej nazwę klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> <span data-ttu-id="7fcb2-188">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="7fcb2-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="7fcb2-189">Wszystkie klasy i elementów członkowskich klasy można określić poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="7fcb2-190">Dostępne są następujące modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="7fcb2-191">C# Modifier</span><span class="sxs-lookup"><span data-stu-id="7fcb2-191">C# Modifier</span></span>|<span data-ttu-id="7fcb2-192">Definicja</span><span class="sxs-lookup"><span data-stu-id="7fcb2-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="7fcb2-193">public</span><span class="sxs-lookup"><span data-stu-id="7fcb2-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="7fcb2-194">Typ lub element członkowski jest możliwy przez inny kod, w tym samym zestawie lub innego zestawu, który odwołuje się on.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="7fcb2-195">private</span><span class="sxs-lookup"><span data-stu-id="7fcb2-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="7fcb2-196">Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="7fcb2-197">protected</span><span class="sxs-lookup"><span data-stu-id="7fcb2-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="7fcb2-198">Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="7fcb2-199">internal</span><span class="sxs-lookup"><span data-stu-id="7fcb2-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="7fcb2-200">Typ lub element członkowski jest możliwy przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="7fcb2-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="7fcb2-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="7fcb2-202">Typ lub element członkowski jest dostępna przez dowolny kod w tym samym zestawie lub dowolnej klasy pochodnej w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="7fcb2-203">private protected</span><span class="sxs-lookup"><span data-stu-id="7fcb2-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="7fcb2-204">Typ lub element członkowski jest możliwy przez kod w tej samej klasy lub w klasie pochodnej w zestawie klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="7fcb2-205">Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a> <span data-ttu-id="7fcb2-206">Utworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-206">Instantiating Classes</span></span>  
 <span data-ttu-id="7fcb2-207">Do utworzenia obiektu, należy utworzyć wystąpienia klasy lub utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="7fcb2-208">Po utworzenie wystąpienia klasy, można przypisać wartości do właściwości i pola wystąpienia i wywołania metody klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="7fcb2-209">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatory obiektów:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="7fcb2-210">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-211">new, operator</span><span class="sxs-lookup"><span data-stu-id="7fcb2-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="7fcb2-212">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="7fcb2-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> <span data-ttu-id="7fcb2-213">Klasy statyczne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7fcb2-213">Static Classes and Members</span></span>  
 <span data-ttu-id="7fcb2-214">Statyczny element członkowski klasy jest właściwość, procedura lub pola, które jest współużytkowana przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="7fcb2-215">Do definiowania statycznego elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="7fcb2-216">Aby uzyskać dostęp do statycznego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="7fcb2-217">Klasy statyczne w języku C# mieć tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="7fcb2-218">Statyczne elementy członkowskie także nie może uzyskać dostępu właściwości niestatycznego pola lub metody</span><span class="sxs-lookup"><span data-stu-id="7fcb2-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="7fcb2-219">Aby uzyskać więcej informacji, zobacz: [statycznych](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a> <span data-ttu-id="7fcb2-220">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7fcb2-220">Anonymous Types</span></span>  
 <span data-ttu-id="7fcb2-221">Typy anonimowe umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="7fcb2-222">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="7fcb2-223">Klasa nie ma używać nazwy i zawiera właściwości, które określisz w odwołaniu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="7fcb2-224">Można utworzyć wystąpienia typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="7fcb2-225">Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a> <span data-ttu-id="7fcb2-226">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="7fcb2-226">Inheritance</span></span>  
 <span data-ttu-id="7fcb2-227">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa rozszerza i modyfikuje zachowanie, który jest zdefiniowany w innej klasy.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="7fcb2-228">Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*, i nosi nazwę klasy, która dziedziczy tych członków *klasy*.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="7fcb2-229">Jednak wszystkie klasy w języku C# niejawnie dziedziczyć <xref:System.Object> klasy, która obsługuje hierarchii klas .NET i udostępnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fcb2-230">C# nie obsługuje wielu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="7fcb2-231">Oznacza to można określić tylko jedną klasę podstawową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="7fcb2-232">Dziedziczenie z klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 <span data-ttu-id="7fcb2-233">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-233">By default all classes can be inherited.</span></span> <span data-ttu-id="7fcb2-234">Jednak można określić, czy nie mogą być używane jako klasę podstawową klasy lub utworzyć klasę, która może służyć jako klasę podstawową tylko.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="7fcb2-235">Aby określić, że klasa nie można użyć jako klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="7fcb2-236">Aby określić, że klasa może służyć jako klasę podstawową tylko i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="7fcb2-237">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-238">sealed</span><span class="sxs-lookup"><span data-stu-id="7fcb2-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="7fcb2-239">abstract</span><span class="sxs-lookup"><span data-stu-id="7fcb2-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> <span data-ttu-id="7fcb2-240">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7fcb2-240">Overriding Members</span></span>  
 <span data-ttu-id="7fcb2-241">Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie ze swojej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="7fcb2-242">Aby zmienić zachowanie dziedziczony element członkowski, należy go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="7fcb2-243">Oznacza to można zdefiniować nowej implementacji metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="7fcb2-244">Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="7fcb2-245">C# Modifier</span><span class="sxs-lookup"><span data-stu-id="7fcb2-245">C# Modifier</span></span>|<span data-ttu-id="7fcb2-246">Definicja</span><span class="sxs-lookup"><span data-stu-id="7fcb2-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="7fcb2-247">virtual</span><span class="sxs-lookup"><span data-stu-id="7fcb2-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="7fcb2-248">Umożliwia elementu członkowskiego klasy do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="7fcb2-249">override</span><span class="sxs-lookup"><span data-stu-id="7fcb2-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="7fcb2-250">Zastępuje członka wirtualnego (możliwym do zastąpienia) zdefiniowana w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="7fcb2-251">abstract</span><span class="sxs-lookup"><span data-stu-id="7fcb2-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="7fcb2-252">Wymaga, aby element członkowski klasy do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="7fcb2-253">new, modyfikator</span><span class="sxs-lookup"><span data-stu-id="7fcb2-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="7fcb2-254">Ukrywa element członkowski dziedziczona z klasy podstawowej</span><span class="sxs-lookup"><span data-stu-id="7fcb2-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a> <span data-ttu-id="7fcb2-255">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-255">Interfaces</span></span>  
 <span data-ttu-id="7fcb2-256">Interfejsy, takich jak klasy, zdefiniuj zbiór właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="7fcb2-257">Jednak w przeciwieństwie do klasy, interfejsy nie dostarcza implementacji.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="7fcb2-258">Są implementowane przez klasy i zdefiniowane jako osobne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="7fcb2-259">Interfejs reprezentuje kontraktu, w tym klasy, która implementuje interfejs musi implementować każdego aspektu ten interfejs, dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="7fcb2-260">Aby zdefiniować interfejsu:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="7fcb2-261">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="7fcb2-262">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="7fcb2-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7fcb2-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="7fcb2-264">interface</span><span class="sxs-lookup"><span data-stu-id="7fcb2-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> <span data-ttu-id="7fcb2-265">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7fcb2-265">Generics</span></span>  
 <span data-ttu-id="7fcb2-266">Klasy, struktury, interfejsy i metody w programie .NET Framework mogą zawierać *parametry typu* definiującą typów obiektów, które mogą przechowywać lub użyć.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="7fcb2-267">Najbardziej typowym przykładem typów ogólnych jest kolekcją, w którym można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="7fcb2-268">Aby zdefiniować klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-268">To define a generic class:</span></span>  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="7fcb2-269">Można utworzyć wystąpienia klasy generycznej:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="7fcb2-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-271">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7fcb2-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="7fcb2-272">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7fcb2-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> <span data-ttu-id="7fcb2-273">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="7fcb2-273">Delegates</span></span>  
 <span data-ttu-id="7fcb2-274">A *delegować* jest typ, który określa podpis metody i można udostępnić odwołanie do dowolnej metody zgodnego podpisu.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="7fcb2-275">Można wywołać (lub wywołać) metoda za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="7fcb2-276">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fcb2-277">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="7fcb2-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="7fcb2-278">Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7fcb2-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="7fcb2-279">Do utworzenia delegata:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="7fcb2-280">Aby utworzyć odwołanie do metody, która odpowiada podpisu określony na podstawie delegata:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="7fcb2-281">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7fcb2-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7fcb2-282">Delegaci</span><span class="sxs-lookup"><span data-stu-id="7fcb2-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="7fcb2-283">delegate</span><span class="sxs-lookup"><span data-stu-id="7fcb2-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="7fcb2-284">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fcb2-284">See Also</span></span>  
 [<span data-ttu-id="7fcb2-285">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7fcb2-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
