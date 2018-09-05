---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 8e211fec25ceb2e8e42620ff3f421e6943d8b5e5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522158"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="66bd5-102">Programowanie zorientowane obiektowo (C#)</span><span class="sxs-lookup"><span data-stu-id="66bd5-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="66bd5-103">C# zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="66bd5-104">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="66bd5-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="66bd5-105">*Dziedziczenie* opisuje zdolność do tworzenia nowych klas w oparciu o istniejącą klasą.</span><span class="sxs-lookup"><span data-stu-id="66bd5-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="66bd5-106">*Polimorfizm* oznacza, że może mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody w różny sposób.</span><span class="sxs-lookup"><span data-stu-id="66bd5-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="66bd5-107">W tej sekcji opisano następujące pojęcia:</span><span class="sxs-lookup"><span data-stu-id="66bd5-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="66bd5-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="66bd5-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="66bd5-109">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="66bd5-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="66bd5-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="66bd5-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="66bd5-111">Metody</span><span class="sxs-lookup"><span data-stu-id="66bd5-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="66bd5-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="66bd5-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="66bd5-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="66bd5-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="66bd5-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="66bd5-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="66bd5-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="66bd5-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="66bd5-116">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="66bd5-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="66bd5-117">Tworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="66bd5-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="66bd5-118">Klasy statyczne i członkowie</span><span class="sxs-lookup"><span data-stu-id="66bd5-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="66bd5-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="66bd5-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="66bd5-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="66bd5-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="66bd5-121">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="66bd5-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="66bd5-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="66bd5-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="66bd5-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="66bd5-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="66bd5-124">Delegaci</span><span class="sxs-lookup"><span data-stu-id="66bd5-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a> <span data-ttu-id="66bd5-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="66bd5-125">Classes and Objects</span></span>  
 <span data-ttu-id="66bd5-126">Warunki *klasy* i *obiektu* są czasami stosowane zamiennie, jednak w rzeczywistości klasy opisują *typu* obiektów, podczas gdy obiekty to użytkowe  *wystąpienia* klas.</span><span class="sxs-lookup"><span data-stu-id="66bd5-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="66bd5-127">Więc, akt tworzenia obiektu jest nazywany *wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="66bd5-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="66bd5-128">Korzystając z analogii planu, klasa to plan, a obiekt to budynek utworzony z tego planu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="66bd5-129">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="66bd5-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="66bd5-130">C# oferuje także uproszczonej wersji klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć duże tablice obiektów i czy chcesz zużyć do tego zbyt dużej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="66bd5-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="66bd5-131">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="66bd5-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="66bd5-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-133">class</span><span class="sxs-lookup"><span data-stu-id="66bd5-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="66bd5-134">struct</span><span class="sxs-lookup"><span data-stu-id="66bd5-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> <span data-ttu-id="66bd5-135">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="66bd5-135">Class Members</span></span>  
 <span data-ttu-id="66bd5-136">Każda klasa może mieć różne *elementy członkowskie klasy* którzy zawierają właściwości, które opisują dane klasy, metody, które definiują zachowanie klasy i wydarzenia, które zapewniają komunikację między różnych klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="66bd5-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a> <span data-ttu-id="66bd5-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="66bd5-137">Properties and Fields</span></span>  
 <span data-ttu-id="66bd5-138">Pola i właściwości reprezentują informacje zawarte w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="66bd5-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="66bd5-139">Pola przypominają zmienne, ponieważ można je odczytać lub ustawić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="66bd5-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="66bd5-140">Aby zdefiniować pole:</span><span class="sxs-lookup"><span data-stu-id="66bd5-140">To define a field:</span></span>  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="66bd5-141">Właściwości mają get i ustawić procedur, które zapewniają większą kontrolę nad jak ustawiania lub zwracania wartości.</span><span class="sxs-lookup"><span data-stu-id="66bd5-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="66bd5-142">C# pozwala na tworzenie prywatnego pola do przechowywania wartości właściwości lub użyć tzw automatycznie implementowanych właściwości, które tworzą to pole automatycznie w tle i ustanowiają podstawowe logiki dla procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="66bd5-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="66bd5-143">Aby zdefiniować automatycznie implementowanej właściwości:</span><span class="sxs-lookup"><span data-stu-id="66bd5-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="66bd5-144">Jeśli musisz wykonać kilka dodatkowych operacji odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i Zaoferuj podstawową logikę do przechowywania i pobierania:</span><span class="sxs-lookup"><span data-stu-id="66bd5-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="66bd5-145">Większość właściwości posiada metody lub procedury do ustawiania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="66bd5-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="66bd5-146">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie.</span><span class="sxs-lookup"><span data-stu-id="66bd5-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="66bd5-147">W języku C# można pominąć `get` lub `set` metody właściwości.</span><span class="sxs-lookup"><span data-stu-id="66bd5-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="66bd5-148">Jednak automatycznie implementowanych właściwości nie może być tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="66bd5-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-150">get</span><span class="sxs-lookup"><span data-stu-id="66bd5-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="66bd5-151">set</span><span class="sxs-lookup"><span data-stu-id="66bd5-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> <span data-ttu-id="66bd5-152">Metody</span><span class="sxs-lookup"><span data-stu-id="66bd5-152">Methods</span></span>  
 <span data-ttu-id="66bd5-153">A *metoda* to działanie, którą obiekt może wykonywać.</span><span class="sxs-lookup"><span data-stu-id="66bd5-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="66bd5-154">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="66bd5-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="66bd5-155">Klasa może mieć kilka implementacji lub *przeciążenia*, z tej samej metody, które różnią się liczbą typów parametru lub parametrów.</span><span class="sxs-lookup"><span data-stu-id="66bd5-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="66bd5-156">Aby przeciążyć metodę</span><span class="sxs-lookup"><span data-stu-id="66bd5-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="66bd5-157">W większości przypadków użytkownik deklaruje metodę w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="66bd5-158">Jednakże, C# obsługuje również *metody rozszerzenia* umożliwiającą dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="66bd5-159">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-160">Metody</span><span class="sxs-lookup"><span data-stu-id="66bd5-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="66bd5-161">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="66bd5-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> <span data-ttu-id="66bd5-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="66bd5-162">Constructors</span></span>  
 <span data-ttu-id="66bd5-163">Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="66bd5-164">Konstruktory zwykle inicjują członków danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="66bd5-165">Konstruktor można uruchomić tylko raz, po utworzeniu klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="66bd5-166">Ponadto kod w Konstruktorze zawsze jest uruchamiany przed innymi kodami w klasie.</span><span class="sxs-lookup"><span data-stu-id="66bd5-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="66bd5-167">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku każdej innej metody.</span><span class="sxs-lookup"><span data-stu-id="66bd5-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="66bd5-168">Aby zdefiniować Konstruktor dla klasy:</span><span class="sxs-lookup"><span data-stu-id="66bd5-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="66bd5-169">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-169">For more information, see:</span></span>  
  
 <span data-ttu-id="66bd5-170">[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="66bd5-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a> <span data-ttu-id="66bd5-171">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="66bd5-171">Finalizers</span></span>  
 <span data-ttu-id="66bd5-172">Finalizatory są używane do niszczenia wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="66bd5-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="66bd5-173">W .NET Framework moduł odśmiecania pamięci automatycznie zarządza alokacją i zwolnieniem pamięci dla obiektów zarządzanych w Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66bd5-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="66bd5-174">Jednakże nadal może być konieczne finalizatorów, aby wyczyścić zasoby niezarządzane, tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="66bd5-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="66bd5-175">Może istnieć tylko jeden finalizatory klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="66bd5-176">Aby uzyskać więcej informacji na temat finalizatory i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="66bd5-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a> <span data-ttu-id="66bd5-177">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="66bd5-177">Events</span></span>  
 <span data-ttu-id="66bd5-178">Zdarzenie pozwala klasie lub obiektowi powiadomić inne klasy lub obiektów, kiedy stanie się coś istotnego.</span><span class="sxs-lookup"><span data-stu-id="66bd5-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="66bd5-179">Nosi nazwę klasy, która wysyła (lub generuje) zdarzenie *wydawcy* i klasy, otrzymywać (lub uchwyt) zdarzenia, które są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="66bd5-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="66bd5-180">Aby uzyskać więcej informacji na temat zdarzeń, jak ich wywoływania i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="66bd5-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="66bd5-181">Aby zadeklarować zdarzenia w klasie, użyj [zdarzeń](../../../csharp/language-reference/keywords/event.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="66bd5-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="66bd5-182">Aby wywołać zdarzenie, wywołaj delegat wydarzenia.</span><span class="sxs-lookup"><span data-stu-id="66bd5-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="66bd5-183">Aby subskrybować zdarzenie, użyj `+=` operatora; Aby anulować subskrypcję zdarzenia, użyj `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="66bd5-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a> <span data-ttu-id="66bd5-184">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="66bd5-184">Nested Classes</span></span>  
 <span data-ttu-id="66bd5-185">Nosi nazwę klasy zdefiniowanej w ramach innej klasy *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="66bd5-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="66bd5-186">Domyślnie zagnieżdżona klasa jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="66bd5-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="66bd5-187">Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, następuje kropki (.), a następnie według nazwy zagnieżdżonej klasy:</span><span class="sxs-lookup"><span data-stu-id="66bd5-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> <span data-ttu-id="66bd5-188">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="66bd5-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="66bd5-189">Wszystkie klasy i składowych klasy, można określić poziom dostępu, jaki stanowią dla innych klas przy użyciu *modyfikatorach dostępu*.</span><span class="sxs-lookup"><span data-stu-id="66bd5-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="66bd5-190">Dostępne są następujące modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="66bd5-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="66bd5-191">Modyfikator C#</span><span class="sxs-lookup"><span data-stu-id="66bd5-191">C# Modifier</span></span>|<span data-ttu-id="66bd5-192">Definicja</span><span class="sxs-lookup"><span data-stu-id="66bd5-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="66bd5-193">public</span><span class="sxs-lookup"><span data-stu-id="66bd5-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="66bd5-194">Typ lub element członkowski może zostać oceniony przez inny kod, w tym samym zestawie lub w innym zestawie, który odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="66bd5-195">private</span><span class="sxs-lookup"><span data-stu-id="66bd5-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="66bd5-196">Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="66bd5-197">protected</span><span class="sxs-lookup"><span data-stu-id="66bd5-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="66bd5-198">Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="66bd5-199">internal</span><span class="sxs-lookup"><span data-stu-id="66bd5-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="66bd5-200">Typ lub element członkowski może zostać oceniony przez każdy kod z tego samego zestawu, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="66bd5-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="66bd5-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="66bd5-202">Typ lub element członkowski jest możliwy przez każdy kod z tego samego zestawu lub każdą pochodną klasę w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="66bd5-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="66bd5-203">private protected</span><span class="sxs-lookup"><span data-stu-id="66bd5-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="66bd5-204">Typ lub element członkowski możliwy przez kod z tej samej klasy lub w klasie pochodnej w zestawie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="66bd5-205">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md). </span><span class="sxs-lookup"><span data-stu-id="66bd5-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a> <span data-ttu-id="66bd5-206">Tworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="66bd5-206">Instantiating Classes</span></span>  
 <span data-ttu-id="66bd5-207">Aby utworzyć obiekt, należy utworzyć wystąpienia klasy lub utworzyć wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="66bd5-208">Po utworzeniu wystąpienia klasy, można przypisać wartości do pól i właściwości instancji i wywołania metod klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="66bd5-209">Aby przypisać wartości do właściwości w procesie tworzenia wystąpienia klasy, użyj inicjalizatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="66bd5-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="66bd5-210">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-211">new, operator</span><span class="sxs-lookup"><span data-stu-id="66bd5-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="66bd5-212">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="66bd5-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> <span data-ttu-id="66bd5-213">Klasy statyczne i członkowie</span><span class="sxs-lookup"><span data-stu-id="66bd5-213">Static Classes and Members</span></span>  
 <span data-ttu-id="66bd5-214">Statycznej składowej klasy jest właściwość, procedura lub pole, który jest współużytkowany przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="66bd5-215">Aby zdefiniować statyczny element członkowski:</span><span class="sxs-lookup"><span data-stu-id="66bd5-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="66bd5-216">Aby uzyskać dostęp do statycznej składowej, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="66bd5-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="66bd5-217">Klasy statyczne w języku C# mają tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="66bd5-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="66bd5-218">Statyczne elementy członkowskie także nie może uzyskać dostępu niestatycznej właściwości, pól ani metod</span><span class="sxs-lookup"><span data-stu-id="66bd5-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="66bd5-219">Aby uzyskać więcej informacji, zobacz: [statyczne](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="66bd5-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a> <span data-ttu-id="66bd5-220">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="66bd5-220">Anonymous Types</span></span>  
 <span data-ttu-id="66bd5-221">Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="66bd5-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="66bd5-222">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="66bd5-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="66bd5-223">Klasa nie ma użytecznych nazw i zawiera właściwości, które określisz w odwołaniu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="66bd5-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="66bd5-224">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="66bd5-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="66bd5-225">Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="66bd5-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a> <span data-ttu-id="66bd5-226">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="66bd5-226">Inheritance</span></span>  
 <span data-ttu-id="66bd5-227">Dziedziczenie umożliwia utworzenie nowej klasy, która używa, rozszerza i modyfikuje zachowanie, która jest zdefiniowana w innej klasy.</span><span class="sxs-lookup"><span data-stu-id="66bd5-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="66bd5-228">Nosi nazwę klasy, której członkowie są dziedziczeni *klasy bazowej*, a klasa, która dziedziczy tych członków, jest nazywana *klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="66bd5-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="66bd5-229">Jednakże wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia niskopoziomowe usługi dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="66bd5-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66bd5-230">C# nie obsługują wielokrotnego dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="66bd5-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="66bd5-231">Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="66bd5-232">Dziedziczenie z klasy bazowej:</span><span class="sxs-lookup"><span data-stu-id="66bd5-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass {}  
```  
  
 <span data-ttu-id="66bd5-233">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="66bd5-233">By default all classes can be inherited.</span></span> <span data-ttu-id="66bd5-234">Można jednak określić klasy nie może być używany jako klasa bazowa, czy utworzyć klasę, która może służyć jako klasę bazową tylko.</span><span class="sxs-lookup"><span data-stu-id="66bd5-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="66bd5-235">Aby określić, że klasa nie można użyć jako klasa bazowa:</span><span class="sxs-lookup"><span data-stu-id="66bd5-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="66bd5-236">Aby określić, że klasa może służyć jako klasę bazową tylko i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="66bd5-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="66bd5-237">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-238">sealed</span><span class="sxs-lookup"><span data-stu-id="66bd5-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="66bd5-239">abstract</span><span class="sxs-lookup"><span data-stu-id="66bd5-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> <span data-ttu-id="66bd5-240">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="66bd5-240">Overriding Members</span></span>  
 <span data-ttu-id="66bd5-241">Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie w swojej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="66bd5-242">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, należy go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="66bd5-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="66bd5-243">Oznacza to można zdefiniować nową metodę implementacji metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="66bd5-244">Następujące Modyfikatory są używane do kontrolowania, jak zastąpić właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="66bd5-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="66bd5-245">Modyfikator C#</span><span class="sxs-lookup"><span data-stu-id="66bd5-245">C# Modifier</span></span>|<span data-ttu-id="66bd5-246">Definicja</span><span class="sxs-lookup"><span data-stu-id="66bd5-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="66bd5-247">virtual</span><span class="sxs-lookup"><span data-stu-id="66bd5-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="66bd5-248">Zezwala na element członkowski klasy został nadpisany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="66bd5-249">override</span><span class="sxs-lookup"><span data-stu-id="66bd5-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="66bd5-250">Zastępuje wirtualny element członkowski (przesłanialny) zdefiniowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="66bd5-251">abstract</span><span class="sxs-lookup"><span data-stu-id="66bd5-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="66bd5-252">Wymaga, aby element członkowski klasy został nadpisany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="66bd5-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="66bd5-253">new, modyfikator</span><span class="sxs-lookup"><span data-stu-id="66bd5-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="66bd5-254">Ukrywa członka dziedziczonego z klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="66bd5-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a> <span data-ttu-id="66bd5-255">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="66bd5-255">Interfaces</span></span>  
 <span data-ttu-id="66bd5-256">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="66bd5-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="66bd5-257">Jednak w przeciwieństwie do klasy, interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="66bd5-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="66bd5-258">One są implementowane przez klasy i definiowane jako osobne jednostki od klas.</span><span class="sxs-lookup"><span data-stu-id="66bd5-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="66bd5-259">Interfejs reprezentuje kontrakt, w tym, że klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu, dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="66bd5-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="66bd5-260">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="66bd5-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="66bd5-261">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="66bd5-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="66bd5-262">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="66bd5-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="66bd5-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="66bd5-264">interface</span><span class="sxs-lookup"><span data-stu-id="66bd5-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> <span data-ttu-id="66bd5-265">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="66bd5-265">Generics</span></span>  
 <span data-ttu-id="66bd5-266">Klasy, struktury, interfejsy i metody W.NET Framework mogą zawierać *parametry typu* który definiują typy obiektów, które można przechowywać lub używać.</span><span class="sxs-lookup"><span data-stu-id="66bd5-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="66bd5-267">Najbardziej typowym przykładem typów ogólnych jest kolekcja, której można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="66bd5-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="66bd5-268">Aby zdefiniować klasę ogólną:</span><span class="sxs-lookup"><span data-stu-id="66bd5-268">To define a generic class:</span></span>  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="66bd5-269">Aby utworzyć wystąpienie klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="66bd5-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="66bd5-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-271">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="66bd5-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="66bd5-272">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="66bd5-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> <span data-ttu-id="66bd5-273">Delegaty</span><span class="sxs-lookup"><span data-stu-id="66bd5-273">Delegates</span></span>  
 <span data-ttu-id="66bd5-274">A *delegować* to typ, który definiuje podpis metody i można podać odwołanie do dowolnej metody mającą zgodny podpis.</span><span class="sxs-lookup"><span data-stu-id="66bd5-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="66bd5-275">Można wywołać (lub wywołać) metodę przez delegat.</span><span class="sxs-lookup"><span data-stu-id="66bd5-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="66bd5-276">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="66bd5-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66bd5-277">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="66bd5-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="66bd5-278">Aby uzyskać więcej informacji dotyczących używania delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="66bd5-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="66bd5-279">Aby utworzyć delegat:</span><span class="sxs-lookup"><span data-stu-id="66bd5-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="66bd5-280">Aby utworzyć odwołanie do metody, która pasuje do oznaczenia określonego przez delegat:</span><span class="sxs-lookup"><span data-stu-id="66bd5-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="66bd5-281">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="66bd5-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="66bd5-282">Delegaci</span><span class="sxs-lookup"><span data-stu-id="66bd5-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="66bd5-283">delegate</span><span class="sxs-lookup"><span data-stu-id="66bd5-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="66bd5-284">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66bd5-284">See Also</span></span>

- [<span data-ttu-id="66bd5-285">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="66bd5-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
