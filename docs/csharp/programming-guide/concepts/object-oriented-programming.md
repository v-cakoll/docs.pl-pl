---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: e277e24c1f345a8bbb6640e210a7ee30862169be
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590779"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="12ddf-102">Programowanie zorientowane obiektowo (C#)</span><span class="sxs-lookup"><span data-stu-id="12ddf-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="12ddf-103">C#zapewnia pełną obsługę programowania zorientowanego obiektowo, w tym hermetyzację, dziedziczenie i polimorfizm.</span><span class="sxs-lookup"><span data-stu-id="12ddf-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="12ddf-104">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich jest traktowana jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="12ddf-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="12ddf-105">*Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="12ddf-106">*Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, nawet jeśli każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="12ddf-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="12ddf-107">W tej sekcji opisano następujące pojęcia:</span><span class="sxs-lookup"><span data-stu-id="12ddf-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="12ddf-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="12ddf-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="12ddf-109">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="12ddf-109">Class Members</span></span>](#Members)

    - [<span data-ttu-id="12ddf-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="12ddf-110">Properties and Fields</span></span>](#Properties)

    - [<span data-ttu-id="12ddf-111">Metody</span><span class="sxs-lookup"><span data-stu-id="12ddf-111">Methods</span></span>](#Methods)

    - [<span data-ttu-id="12ddf-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="12ddf-112">Constructors</span></span>](#Constructors)

    - [<span data-ttu-id="12ddf-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="12ddf-113">Finalizers</span></span>](#Finalizers)

    - [<span data-ttu-id="12ddf-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="12ddf-114">Events</span></span>](#Events)

    - [<span data-ttu-id="12ddf-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="12ddf-115">Nested Classes</span></span>](#NestedClasses)

  - [<span data-ttu-id="12ddf-116">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="12ddf-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="12ddf-117">Tworzenie wystąpień klas</span><span class="sxs-lookup"><span data-stu-id="12ddf-117">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="12ddf-118">Klasy statyczne i składowe</span><span class="sxs-lookup"><span data-stu-id="12ddf-118">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="12ddf-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="12ddf-119">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="12ddf-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="12ddf-120">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="12ddf-121">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="12ddf-121">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="12ddf-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="12ddf-122">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="12ddf-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="12ddf-123">Generics</span></span>](#Generics)

- [<span data-ttu-id="12ddf-124">Delegaty</span><span class="sxs-lookup"><span data-stu-id="12ddf-124">Delegates</span></span>](#Delegates)

## <a name="Classes"></a><span data-ttu-id="12ddf-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="12ddf-125">Classes and Objects</span></span>

<span data-ttu-id="12ddf-126">Terminy *Klasa* i *obiekt* są czasami używane zamiennie, ale w rzeczywistości klasy opisują *Typ* obiektów, natomiast obiekty są użyteczne *wystąpienia* klas.</span><span class="sxs-lookup"><span data-stu-id="12ddf-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="12ddf-127">W związku z tym czynność tworzenia obiektu jest nazywana *tworzeniem wystąpień*.</span><span class="sxs-lookup"><span data-stu-id="12ddf-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="12ddf-128">Korzystając z strategii analogowej, Klasa jest planem, a obiekt jest kompilacją utworzoną z tego planu.</span><span class="sxs-lookup"><span data-stu-id="12ddf-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="12ddf-129">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="12ddf-129">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="12ddf-130">C#zapewnia również uproszczoną wersję klas o nazwie *Structures* , które są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i nie należy zużywać zbyt dużej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="12ddf-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="12ddf-131">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="12ddf-131">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="12ddf-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-132">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-133">class</span><span class="sxs-lookup"><span data-stu-id="12ddf-133">class</span></span>](../../language-reference/keywords/class.md)

- [<span data-ttu-id="12ddf-134">struct</span><span class="sxs-lookup"><span data-stu-id="12ddf-134">struct</span></span>](../../language-reference/keywords/struct.md)

### <a name="Members"></a><span data-ttu-id="12ddf-135">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="12ddf-135">Class Members</span></span>

<span data-ttu-id="12ddf-136">Każda klasa może mieć różne *składowe klasy* , które zawierają właściwości opisujące dane klasy, metody definiujące zachowanie klasy oraz zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="12ddf-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a><span data-ttu-id="12ddf-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="12ddf-137">Properties and Fields</span></span>

<span data-ttu-id="12ddf-138">Pola i właściwości reprezentują informacje, które zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="12ddf-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="12ddf-139">Pola są podobne do zmiennych, ponieważ mogą być odczytywane lub ustawiane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="12ddf-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="12ddf-140">Aby zdefiniować pole:</span><span class="sxs-lookup"><span data-stu-id="12ddf-140">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="12ddf-141">Właściwości mają procedury pobierania i ustawiania, które zapewniają większą kontrolę nad sposobem ustawiania lub zwracania wartości.</span><span class="sxs-lookup"><span data-stu-id="12ddf-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="12ddf-142">C#umożliwia utworzenie prywatnego pola do przechowywania wartości właściwości lub użycie, tak zwane automatycznie implementowane właściwości, które tworzą to pole automatycznie w tle i zapewniają podstawową logikę dla procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="12ddf-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="12ddf-143">Aby zdefiniować zaimplementowaną Właściwość:</span><span class="sxs-lookup"><span data-stu-id="12ddf-143">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="12ddf-144">Jeśli trzeba wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, Zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę do przechowywania i pobierania:</span><span class="sxs-lookup"><span data-stu-id="12ddf-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="12ddf-145">Większość właściwości ma metody lub procedury ustawiające i pobierające wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="12ddf-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="12ddf-146">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie.</span><span class="sxs-lookup"><span data-stu-id="12ddf-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="12ddf-147">W C#, możesz pominąć `get` metodę lub `set` właściwość.</span><span class="sxs-lookup"><span data-stu-id="12ddf-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="12ddf-148">Jednak właściwości zaimplementowane domyślnie nie mogą być tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="12ddf-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="12ddf-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-149">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-150">get</span><span class="sxs-lookup"><span data-stu-id="12ddf-150">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="12ddf-151">set</span><span class="sxs-lookup"><span data-stu-id="12ddf-151">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="Methods"></a><span data-ttu-id="12ddf-152">Form</span><span class="sxs-lookup"><span data-stu-id="12ddf-152">Methods</span></span>

<span data-ttu-id="12ddf-153">*Metoda* jest akcją, którą obiekt może wykonać.</span><span class="sxs-lookup"><span data-stu-id="12ddf-153">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="12ddf-154">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="12ddf-154">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="12ddf-155">Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="12ddf-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="12ddf-156">Aby przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="12ddf-156">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="12ddf-157">W większości przypadków deklaruje metodę w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="12ddf-158">Program C# obsługuje jednak również *metody rozszerzające* , które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="12ddf-159">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-159">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-160">Metody</span><span class="sxs-lookup"><span data-stu-id="12ddf-160">Methods</span></span>](../classes-and-structs/methods.md)

- [<span data-ttu-id="12ddf-161">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="12ddf-161">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> <span data-ttu-id="12ddf-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="12ddf-162">Constructors</span></span>

<span data-ttu-id="12ddf-163">Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="12ddf-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="12ddf-164">Konstruktory zazwyczaj inicjują elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="12ddf-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="12ddf-165">Konstruktor można uruchomić tylko raz podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="12ddf-166">Ponadto kod w konstruktorze zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie.</span><span class="sxs-lookup"><span data-stu-id="12ddf-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="12ddf-167">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku innych metod.</span><span class="sxs-lookup"><span data-stu-id="12ddf-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="12ddf-168">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="12ddf-168">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="12ddf-169">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-169">For more information, see:</span></span>

<span data-ttu-id="12ddf-170">[Konstruktory](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-170">[Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a> <span data-ttu-id="12ddf-171">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="12ddf-171">Finalizers</span></span>

<span data-ttu-id="12ddf-172">Finalizatory są używane do destruktora wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="12ddf-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="12ddf-173">W .NET Framework Moduł wyrzucania elementów bezużytecznych automatycznie zarządza alokacją i ilością pamięci dla obiektów zarządzanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12ddf-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="12ddf-174">Jednak nadal mogą być potrzebne finalizatory do czyszczenia wszystkich niezarządzanych zasobów tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="12ddf-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="12ddf-175">Dla klasy może istnieć tylko jeden finalizator.</span><span class="sxs-lookup"><span data-stu-id="12ddf-175">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="12ddf-176">Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a><span data-ttu-id="12ddf-177">Wydarzeniach</span><span class="sxs-lookup"><span data-stu-id="12ddf-177">Events</span></span>

<span data-ttu-id="12ddf-178">Zdarzenia umożliwiają klasie lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="12ddf-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="12ddf-179">Klasa, która wysyła (lub podnosi) zdarzenie, jest nazywana wydawcą i klasy, które odbierają (lub obsługują) zdarzenie są nazywane *subskrybentami*.</span><span class="sxs-lookup"><span data-stu-id="12ddf-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="12ddf-180">Aby uzyskać więcej informacji o zdarzeniach, sposobie ich podniesienia i obsłudze, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="12ddf-181">Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia](../../language-reference/keywords/event.md) .</span><span class="sxs-lookup"><span data-stu-id="12ddf-181">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="12ddf-182">Aby zgłosić zdarzenie, wywołaj delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="12ddf-182">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="12ddf-183">Aby subskrybować zdarzenie, użyj `+=` operatora; aby anulować subskrypcję zdarzenia, `-=` Użyj operatora.</span><span class="sxs-lookup"><span data-stu-id="12ddf-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a><span data-ttu-id="12ddf-184">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="12ddf-184">Nested Classes</span></span>

<span data-ttu-id="12ddf-185">Klasa zdefiniowana w innej klasie jest nazywana *zagnieżdżoną*.</span><span class="sxs-lookup"><span data-stu-id="12ddf-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="12ddf-186">Domyślnie Klasa zagnieżdżona jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="12ddf-186">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="12ddf-187">Aby utworzyć wystąpienie klasy zagnieżdżonej, użyj nazwy klasy kontenera, po której następuje kropka, a następnie po której następuje nazwa klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="12ddf-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a><span data-ttu-id="12ddf-188">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="12ddf-188">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="12ddf-189">Wszystkie klasy i elementy członkowskie klasy mogą określać poziom dostępu udostępniany innym klasom przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="12ddf-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="12ddf-190">Dostępne są następujące Modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="12ddf-190">The following access modifiers are available:</span></span>

|<span data-ttu-id="12ddf-191">C#Modyfikator</span><span class="sxs-lookup"><span data-stu-id="12ddf-191">C# Modifier</span></span>|<span data-ttu-id="12ddf-192">Definicja</span><span class="sxs-lookup"><span data-stu-id="12ddf-192">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="12ddf-193">public</span><span class="sxs-lookup"><span data-stu-id="12ddf-193">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="12ddf-194">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="12ddf-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="12ddf-195">private</span><span class="sxs-lookup"><span data-stu-id="12ddf-195">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="12ddf-196">Do typu lub elementu członkowskiego można uzyskać dostęp tylko w kodzie w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="12ddf-196">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="12ddf-197">protected</span><span class="sxs-lookup"><span data-stu-id="12ddf-197">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="12ddf-198">Do typu lub elementu członkowskiego można uzyskać dostęp tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="12ddf-199">internal</span><span class="sxs-lookup"><span data-stu-id="12ddf-199">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="12ddf-200">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="12ddf-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="12ddf-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="12ddf-201">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="12ddf-202">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="12ddf-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="12ddf-203">private protected</span><span class="sxs-lookup"><span data-stu-id="12ddf-203">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="12ddf-204">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą kodu w tej samej klasie lub w klasie pochodnej w ramach zestawu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="12ddf-205">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-205">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a><span data-ttu-id="12ddf-206">Tworzenie wystąpień klas</span><span class="sxs-lookup"><span data-stu-id="12ddf-206">Instantiating Classes</span></span>

<span data-ttu-id="12ddf-207">Aby utworzyć obiekt, należy utworzyć wystąpienie klasy, lub stworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="12ddf-208">Po utworzeniu wystąpienia klasy można przypisać wartości do właściwości i pól wystąpienia oraz wywołać metody klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="12ddf-209">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="12ddf-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="12ddf-210">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-210">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-211">new, operator</span><span class="sxs-lookup"><span data-stu-id="12ddf-211">new Operator</span></span>](../../language-reference/operators/new-operator.md)

- [<span data-ttu-id="12ddf-212">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="12ddf-212">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a><span data-ttu-id="12ddf-213">Klasy statyczne i składowe</span><span class="sxs-lookup"><span data-stu-id="12ddf-213">Static Classes and Members</span></span>

<span data-ttu-id="12ddf-214">Statyczny element członkowski klasy jest właściwością, procedurą lub polem, które są współużytkowane przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="12ddf-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="12ddf-215">Aby zdefiniować statyczną składową:</span><span class="sxs-lookup"><span data-stu-id="12ddf-215">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="12ddf-216">Aby uzyskać dostęp do statycznego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="12ddf-216">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="12ddf-217">Klasy statyczne w C# programie mają tylko statyczne elementy członkowskie i nie można tworzyć ich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="12ddf-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="12ddf-218">Statyczne elementy członkowskie również nie mogą uzyskać dostępu do właściwości niestatycznych, pól ani metod</span><span class="sxs-lookup"><span data-stu-id="12ddf-218">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="12ddf-219">Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-219">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a><span data-ttu-id="12ddf-220">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="12ddf-220">Anonymous Types</span></span>

<span data-ttu-id="12ddf-221">Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="12ddf-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="12ddf-222">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="12ddf-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="12ddf-223">Klasa nie ma użytecznej nazwy i zawiera właściwości określone w deklaracji obiektu.</span><span class="sxs-lookup"><span data-stu-id="12ddf-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="12ddf-224">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="12ddf-224">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="12ddf-225">Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-225">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a><span data-ttu-id="12ddf-226">Strukturze</span><span class="sxs-lookup"><span data-stu-id="12ddf-226">Inheritance</span></span>

<span data-ttu-id="12ddf-227">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie zdefiniowane w innej klasie.</span><span class="sxs-lookup"><span data-stu-id="12ddf-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="12ddf-228">Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="12ddf-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="12ddf-229">Jednak wszystkie klasy w C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="12ddf-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="12ddf-230">C#nie obsługuje dziedziczenia wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="12ddf-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="12ddf-231">Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-231">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="12ddf-232">Aby dziedziczyć z klasy bazowej:</span><span class="sxs-lookup"><span data-stu-id="12ddf-232">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="12ddf-233">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="12ddf-233">By default all classes can be inherited.</span></span> <span data-ttu-id="12ddf-234">Można jednak określić, czy Klasa nie może być używana jako klasa bazowa, ani utworzyć klasy, która może być używana tylko jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="12ddf-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="12ddf-235">Aby określić, że Klasa nie może być używana jako klasa bazowa:</span><span class="sxs-lookup"><span data-stu-id="12ddf-235">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="12ddf-236">Aby określić, że Klasa może być używana tylko jako klasa bazowa i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="12ddf-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="12ddf-237">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-237">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-238">sealed</span><span class="sxs-lookup"><span data-stu-id="12ddf-238">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="12ddf-239">abstract</span><span class="sxs-lookup"><span data-stu-id="12ddf-239">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a><span data-ttu-id="12ddf-240">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="12ddf-240">Overriding Members</span></span>

<span data-ttu-id="12ddf-241">Domyślnie Klasa pochodna dziedziczy wszystkich członków z jej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="12ddf-242">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="12ddf-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="12ddf-243">Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="12ddf-244">Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="12ddf-244">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="12ddf-245">C#Modyfikator</span><span class="sxs-lookup"><span data-stu-id="12ddf-245">C# Modifier</span></span>|<span data-ttu-id="12ddf-246">Definicja</span><span class="sxs-lookup"><span data-stu-id="12ddf-246">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="12ddf-247">virtual</span><span class="sxs-lookup"><span data-stu-id="12ddf-247">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="12ddf-248">Zezwala na przesłanianie składowej klasy w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-248">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="12ddf-249">override</span><span class="sxs-lookup"><span data-stu-id="12ddf-249">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="12ddf-250">Przesłania element członkowski wirtualny (zastępujący) zdefiniowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="12ddf-251">abstract</span><span class="sxs-lookup"><span data-stu-id="12ddf-251">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="12ddf-252">Wymaga, aby element członkowski klasy był zastępowany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12ddf-252">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="12ddf-253">new, modyfikator</span><span class="sxs-lookup"><span data-stu-id="12ddf-253">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="12ddf-254">Ukrywa składową dziedziczoną z klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="12ddf-254">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a><span data-ttu-id="12ddf-255">Interfejsów</span><span class="sxs-lookup"><span data-stu-id="12ddf-255">Interfaces</span></span>

<span data-ttu-id="12ddf-256">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="12ddf-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="12ddf-257">Ale w przeciwieństwie do klas, interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="12ddf-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="12ddf-258">Są one implementowane przez klasy i zdefiniowane jako osobne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="12ddf-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="12ddf-259">Interfejs reprezentuje kontrakt, w którym Klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="12ddf-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="12ddf-260">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="12ddf-260">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="12ddf-261">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="12ddf-261">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="12ddf-262">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-262">For more information, see:</span></span>

[<span data-ttu-id="12ddf-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="12ddf-263">Interfaces</span></span>](../interfaces/index.md)

[<span data-ttu-id="12ddf-264">interface</span><span class="sxs-lookup"><span data-stu-id="12ddf-264">interface</span></span>](../../language-reference/keywords/interface.md)

## <a name="Generics"></a><span data-ttu-id="12ddf-265">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="12ddf-265">Generics</span></span>

<span data-ttu-id="12ddf-266">Klasy, struktury, interfejsy i metody w .NET Framework mogą zawierać *parametry typu* , które definiują typy obiektów, które mogą być przechowywane lub używane.</span><span class="sxs-lookup"><span data-stu-id="12ddf-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="12ddf-267">Najbardziej typowym przykładem typów ogólnych jest kolekcja, w której można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="12ddf-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="12ddf-268">Aby zdefiniować klasę generyczną:</span><span class="sxs-lookup"><span data-stu-id="12ddf-268">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="12ddf-269">Aby utworzyć wystąpienie klasy generycznej:</span><span class="sxs-lookup"><span data-stu-id="12ddf-269">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="12ddf-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-270">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-271">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="12ddf-271">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="12ddf-272">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="12ddf-272">Generics</span></span>](../generics/index.md)

## <a name="Delegates"></a><span data-ttu-id="12ddf-273">Delegat</span><span class="sxs-lookup"><span data-stu-id="12ddf-273">Delegates</span></span>

<span data-ttu-id="12ddf-274">*Delegat* jest typem, który definiuje sygnaturę metody i może podać odwołanie do dowolnej metody ze zgodną sygnaturą.</span><span class="sxs-lookup"><span data-stu-id="12ddf-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="12ddf-275">Metodę można wywołać (lub wywołać) za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="12ddf-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="12ddf-276">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="12ddf-276">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="12ddf-277">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="12ddf-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="12ddf-278">Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="12ddf-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="12ddf-279">Aby utworzyć delegata:</span><span class="sxs-lookup"><span data-stu-id="12ddf-279">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="12ddf-280">Aby utworzyć odwołanie do metody, która jest zgodna z sygnaturą określoną przez delegata:</span><span class="sxs-lookup"><span data-stu-id="12ddf-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="12ddf-281">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="12ddf-281">For more information, see:</span></span>

- [<span data-ttu-id="12ddf-282">Delegaty</span><span class="sxs-lookup"><span data-stu-id="12ddf-282">Delegates</span></span>](../delegates/index.md)

- [<span data-ttu-id="12ddf-283">delegate</span><span class="sxs-lookup"><span data-stu-id="12ddf-283">delegate</span></span>](../../language-reference/keywords/delegate.md)

## <a name="see-also"></a><span data-ttu-id="12ddf-284">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12ddf-284">See also</span></span>

- [<span data-ttu-id="12ddf-285">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="12ddf-285">C# Programming Guide</span></span>](../index.md)
