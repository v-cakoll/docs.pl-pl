---
title: Programowanie obiektowe (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627893"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="f18e0-102">Programowanie obiektowe (C#)</span><span class="sxs-lookup"><span data-stu-id="f18e0-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="f18e0-103">C# zapewnia pełną obsługę programowania obiektowego, w tym hermetyzacji, dziedziczenia i polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="f18e0-104">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="f18e0-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="f18e0-105">*Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="f18e0-106">*Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="f18e0-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="f18e0-107">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="f18e0-107">Classes and objects</span></span>

<span data-ttu-id="f18e0-108">Terminy *klasy* i *obiektu* opisują *typ* obiektów i *wystąpienia* klas, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f18e0-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="f18e0-109">Tak więc akt tworzenia obiektu nazywa się *tworzeniem wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="f18e0-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="f18e0-110">Przy użyciu analogii planu, klasa jest plan, a obiekt jest budynek wykonany z tego planu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="f18e0-111">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="f18e0-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="f18e0-112">C# zawiera również typy o nazwie *struktur,* które są przydatne, gdy nie potrzebujesz wsparcia dla dziedziczenia lub polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="f18e0-113">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="f18e0-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="f18e0-114">Aby uzyskać więcej informacji, zobacz artykuły na [temat klas](../../language-reference/keywords/class.md) i słów kluczowych [struktury.](../../language-reference/builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="f18e0-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="f18e0-115">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="f18e0-115">Class members</span></span>

<span data-ttu-id="f18e0-116">Każda klasa może mieć różne *elementy członkowskie klasy,* które zawierają właściwości, które opisują dane klasy, metody, które definiują zachowanie klasy i zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="f18e0-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="f18e0-117">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="f18e0-117">Properties and fields</span></span>

<span data-ttu-id="f18e0-118">Pola i właściwości reprezentują informacje zawarte w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="f18e0-119">Pola są jak zmienne, ponieważ mogą być odczytywane lub ustawiane bezpośrednio, z zastrzeżeniem odpowiednich modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="f18e0-120">Aby zdefiniować pole, do których można uzyskać dostęp z poziomu wystąpień klasy:</span><span class="sxs-lookup"><span data-stu-id="f18e0-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="f18e0-121">Właściwości mają `get` `set` i akcesorów, które zapewniają większą kontrolę nad jak wartości są ustawiane lub zwracane.</span><span class="sxs-lookup"><span data-stu-id="f18e0-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="f18e0-122">C# umożliwia utworzenie pola prywatnego do przechowywania wartości właściwości lub użyć właściwości autoimplementowane, które tworzą to pole automatycznie za kulisami i zapewniają podstawową logikę dla procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="f18e0-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="f18e0-123">Aby zdefiniować właściwość implementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="f18e0-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="f18e0-124">Jeśli konieczne jest wykonanie dodatkowych operacji odczytu i zapisu wartości właściwości, należy zdefiniować pole do przechowywania wartości właściwości i podać podstawową logikę przechowywania i pobierania jej:</span><span class="sxs-lookup"><span data-stu-id="f18e0-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="f18e0-125">Większość właściwości mają metody lub procedury zarówno ustawić i uzyskać wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="f18e0-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="f18e0-126">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby ograniczyć ich modyfikowanie lub odczytywanie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="f18e0-127">W języku `get` C#, można `set` pominąć lub metody właściwości.</span><span class="sxs-lookup"><span data-stu-id="f18e0-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="f18e0-128">Jednak właściwości implementowane automatycznie nie mogą być tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="f18e0-129">Właściwości autoimplementowane tylko do odczytu można ustawić w konstruktorów klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="f18e0-130">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f18e0-130">For more information, see:</span></span>

- [<span data-ttu-id="f18e0-131">get</span><span class="sxs-lookup"><span data-stu-id="f18e0-131">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="f18e0-132">Ustawić</span><span class="sxs-lookup"><span data-stu-id="f18e0-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="f18e0-133">Metody</span><span class="sxs-lookup"><span data-stu-id="f18e0-133">Methods</span></span>

<span data-ttu-id="f18e0-134">*Metoda* jest akcją, którą obiekt może wykonać.</span><span class="sxs-lookup"><span data-stu-id="f18e0-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="f18e0-135">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="f18e0-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="f18e0-136">Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="f18e0-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="f18e0-137">Aby przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="f18e0-137">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="f18e0-138">W większości przypadków deklarujesz metodę w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="f18e0-139">Jednak C# obsługuje również *metody rozszerzenia,* które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="f18e0-140">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f18e0-140">For more information, see:</span></span>

- [<span data-ttu-id="f18e0-141">Metody</span><span class="sxs-lookup"><span data-stu-id="f18e0-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="f18e0-142">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="f18e0-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="f18e0-143">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="f18e0-143">Constructors</span></span>

<span data-ttu-id="f18e0-144">Konstruktory są metody klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="f18e0-145">Konstruktorzy zwykle inicjowania elementów członkowskich danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="f18e0-146">Konstruktora można uruchomić tylko raz, gdy klasa jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="f18e0-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="f18e0-147">Ponadto kod w konstruktorze zawsze działa przed innym kodem w klasie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="f18e0-148">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób, jak dla każdej innej metody.</span><span class="sxs-lookup"><span data-stu-id="f18e0-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="f18e0-149">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="f18e0-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="f18e0-150">Aby uzyskać więcej informacji, zobacz [Konstruktora](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="f18e0-151">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="f18e0-151">Finalizers</span></span>

<span data-ttu-id="f18e0-152">Finalizatory są używane do nimniejszania wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="f18e0-152">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="f18e0-153">W platformie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacją i zwalnianiem pamięci dla obiektów zarządzanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f18e0-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="f18e0-154">Jednak nadal może być konieczne finalizatorów do czyszczenia wszystkich zasobów niezarządzanych, które tworzy aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f18e0-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="f18e0-155">Może istnieć tylko jeden finalizatorów dla klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-155">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="f18e0-156">Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w platformie .NET Framework, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="f18e0-157">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f18e0-157">Events</span></span>

<span data-ttu-id="f18e0-158">Zdarzenia umożliwiają klasy lub obiektu, aby powiadomić inne klasy lub obiekty, gdy coś interesującego występuje.</span><span class="sxs-lookup"><span data-stu-id="f18e0-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="f18e0-159">Klasa, która wysyła (lub wywołuje) zdarzenie jest wywoływana *wydawcy* i klas, które odbierają (lub doobsługi) zdarzenie są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="f18e0-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="f18e0-160">Aby uzyskać więcej informacji o zdarzeniach, jak są one wywoływane i obsługiwane, zobacz [Zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="f18e0-161">Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia.](../../language-reference/keywords/event.md)</span><span class="sxs-lookup"><span data-stu-id="f18e0-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="f18e0-162">Aby wywołać zdarzenie, wywołać delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f18e0-162">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="f18e0-163">Aby subskrybować `+=` zdarzenie, użyj operatora; aby zrezygnować z subskrypcji `-=` wydarzenia, skorzystaj z operatora.</span><span class="sxs-lookup"><span data-stu-id="f18e0-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="f18e0-164">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="f18e0-164">Nested classes</span></span>

<span data-ttu-id="f18e0-165">Klasa zdefiniowana w innej klasie jest *nazywana zagnieżdżonym*.</span><span class="sxs-lookup"><span data-stu-id="f18e0-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="f18e0-166">Domyślnie klasa zagnieżdżona jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="f18e0-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="f18e0-167">Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, po której następuje kropka, a następnie nazwa klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="f18e0-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="f18e0-168">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="f18e0-168">Access modifiers and access levels</span></span>

<span data-ttu-id="f18e0-169">Wszystkie klasy i elementy członkowskie klasy można określić, jaki poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="f18e0-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="f18e0-170">Dostępne są następujące modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="f18e0-170">The following access modifiers are available:</span></span>

|<span data-ttu-id="f18e0-171">Modyfikator Języka C#</span><span class="sxs-lookup"><span data-stu-id="f18e0-171">C# Modifier</span></span>|<span data-ttu-id="f18e0-172">Definicja</span><span class="sxs-lookup"><span data-stu-id="f18e0-172">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="f18e0-173">Publicznego</span><span class="sxs-lookup"><span data-stu-id="f18e0-173">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="f18e0-174">Typ lub element członkowski są dostępne przez inny kod w tym samym zestawie lub innego zestawu, który odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="f18e0-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="f18e0-175">Prywatny</span><span class="sxs-lookup"><span data-stu-id="f18e0-175">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="f18e0-176">Typ lub element członkowski są dostępne tylko przez kod w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-176">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="f18e0-177">protected</span><span class="sxs-lookup"><span data-stu-id="f18e0-177">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="f18e0-178">Typ lub element członkowski jest dostępny tylko przez kod w tej samej klasie lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="f18e0-179">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="f18e0-179">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="f18e0-180">Typ lub element członkowski są dostępne przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="f18e0-181">protected internal</span><span class="sxs-lookup"><span data-stu-id="f18e0-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="f18e0-182">Typ lub element członkowski są dostępne przez dowolny kod w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="f18e0-183">private protected</span><span class="sxs-lookup"><span data-stu-id="f18e0-183">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="f18e0-184">Typ lub element członkowski są dostępne przez kod w tej samej klasie lub w klasie pochodnej w zestawie klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="f18e0-185">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="f18e0-186">Tworzenie wystąpienia klas</span><span class="sxs-lookup"><span data-stu-id="f18e0-186">Instantiating classes</span></span>

<span data-ttu-id="f18e0-187">Aby utworzyć obiekt, należy utworzyć utworzenie klasy lub utworzyć wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="f18e0-188">Po ujmowaniu klasy można przypisać wartości do właściwości i pól wystąpienia i wywołać metody klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="f18e0-189">Aby przypisać wartości do właściwości podczas procesu wystąpienia klasy, należy użyć inicjatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="f18e0-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="f18e0-190">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f18e0-190">For more information, see:</span></span>

- [<span data-ttu-id="f18e0-191">new, operator</span><span class="sxs-lookup"><span data-stu-id="f18e0-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="f18e0-192">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="f18e0-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="f18e0-193">Klasy statyczne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f18e0-193">Static Classes and Members</span></span>

<span data-ttu-id="f18e0-194">Statyczny element członkowski klasy jest właściwością, procedurą lub polem współużytkowane przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="f18e0-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="f18e0-195">Aby zdefiniować statyczny element członkowski:</span><span class="sxs-lookup"><span data-stu-id="f18e0-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="f18e0-196">Aby uzyskać dostęp do statycznego elementu członkowskiego, użyj nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="f18e0-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="f18e0-197">Klasy statyczne w języku C# mają tylko elementy członkowskie statyczne i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f18e0-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="f18e0-198">Elementy statyczny nie mogą również uzyskiwać dostępu do właściwości, pól lub metod niestatycznych</span><span class="sxs-lookup"><span data-stu-id="f18e0-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="f18e0-199">Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="f18e0-200">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="f18e0-200">Anonymous types</span></span>

<span data-ttu-id="f18e0-201">Typy anonimowe umożliwiają tworzenie obiektów bez zapisywania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="f18e0-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="f18e0-202">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="f18e0-203">Klasa nie ma nazwy użytkowej i zawiera właściwości określone w deklarowaniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f18e0-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="f18e0-204">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="f18e0-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="f18e0-205">Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="f18e0-206">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="f18e0-206">Inheritance</span></span>

<span data-ttu-id="f18e0-207">Dziedziczenie umożliwia utworzenie nowej klasy, która używa ponownie, rozszerza i modyfikuje zachowanie, które jest zdefiniowane w innej klasie.</span><span class="sxs-lookup"><span data-stu-id="f18e0-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="f18e0-208">Klasa, której elementy członkowskie są dziedziczone jest nazywany *klasy podstawowej*, a klasa, która dziedziczy te elementy członkowskie jest *wywoływana klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="f18e0-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="f18e0-209">Jednak wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="f18e0-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="f18e0-210">C# nie obsługuje wiele dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="f18e0-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="f18e0-211">Oznacza to, że można określić tylko jedną klasę podstawową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="f18e0-212">Dziedziczyć z klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="f18e0-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="f18e0-213">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="f18e0-213">By default all classes can be inherited.</span></span> <span data-ttu-id="f18e0-214">Można jednak określić, czy klasa nie może być używana jako klasa podstawowa, lub utworzyć klasę, która może być używana tylko jako klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="f18e0-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="f18e0-215">Aby określić, że klasa nie może być używana jako klasa podstawowa:</span><span class="sxs-lookup"><span data-stu-id="f18e0-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="f18e0-216">Aby określić, że klasa może służyć tylko jako klasa podstawowa i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="f18e0-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="f18e0-217">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f18e0-217">For more information, see:</span></span>

- [<span data-ttu-id="f18e0-218">sealed</span><span class="sxs-lookup"><span data-stu-id="f18e0-218">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="f18e0-219">Abstrakcja</span><span class="sxs-lookup"><span data-stu-id="f18e0-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="f18e0-220">Nadrzędne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f18e0-220">Overriding Members</span></span>

<span data-ttu-id="f18e0-221">Domyślnie klasa pochodna dziedziczy wszystkie elementy członkowskie z jego klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="f18e0-222">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="f18e0-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="f18e0-223">Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="f18e0-224">Następujące modyfikatory są używane do kontrolowania sposobu zastępowania właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="f18e0-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="f18e0-225">Modyfikator Języka C#</span><span class="sxs-lookup"><span data-stu-id="f18e0-225">C# Modifier</span></span>|<span data-ttu-id="f18e0-226">Definicja</span><span class="sxs-lookup"><span data-stu-id="f18e0-226">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="f18e0-227">virtual</span><span class="sxs-lookup"><span data-stu-id="f18e0-227">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="f18e0-228">Umożliwia zastępowanie elementu członkowskiego klasy w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-228">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="f18e0-229">override</span><span class="sxs-lookup"><span data-stu-id="f18e0-229">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="f18e0-230">Zastępuje wirtualny (overridable) element członkowski zdefiniowany w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-230">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="f18e0-231">Abstrakcja</span><span class="sxs-lookup"><span data-stu-id="f18e0-231">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="f18e0-232">Wymaga, aby element członkowski klasy został zastąpiony w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f18e0-232">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="f18e0-233">new, modyfikator</span><span class="sxs-lookup"><span data-stu-id="f18e0-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="f18e0-234">Ukrywa element członkowski odziedziczony z klasy podstawowej</span><span class="sxs-lookup"><span data-stu-id="f18e0-234">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="f18e0-235">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f18e0-235">Interfaces</span></span>

<span data-ttu-id="f18e0-236">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f18e0-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="f18e0-237">Ale w przeciwieństwie do klas interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="f18e0-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="f18e0-238">Są one implementowane przez klasy i zdefiniowane jako oddzielne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="f18e0-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="f18e0-239">Interfejs reprezentuje kontrakt, w tym klasy, która implementuje interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f18e0-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="f18e0-240">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="f18e0-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="f18e0-241">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="f18e0-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="f18e0-242">Aby uzyskać więcej informacji, zobacz artykuł przewodnik programowania na [interfejsy](../interfaces/index.md) i artykuł odwołania do języka na [interfejs](../../language-reference/keywords/interface.md) słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f18e0-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="f18e0-243">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="f18e0-243">Generics</span></span>

<span data-ttu-id="f18e0-244">Klasy, struktury, interfejsy i metody w platformie .NET Framework mogą zawierać *parametry typu* definiujące typy obiektów, które mogą przechowywać lub używać.</span><span class="sxs-lookup"><span data-stu-id="f18e0-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="f18e0-245">Najczęstszym przykładem typów ogólnych jest kolekcja, gdzie można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f18e0-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="f18e0-246">Aby zdefiniować klasę rodzajową:</span><span class="sxs-lookup"><span data-stu-id="f18e0-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="f18e0-247">Aby utworzyć wystąpienie klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="f18e0-247">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="f18e0-248">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f18e0-248">For more information, see:</span></span>

- [<span data-ttu-id="f18e0-249">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="f18e0-249">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="f18e0-250">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="f18e0-250">Generics</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="f18e0-251">Delegaty</span><span class="sxs-lookup"><span data-stu-id="f18e0-251">Delegates</span></span>

<span data-ttu-id="f18e0-252">*Pełnomocnik* jest typem, który definiuje podpis metody i może zapewnić odwołanie do dowolnej metody z zgodnym podpisem.</span><span class="sxs-lookup"><span data-stu-id="f18e0-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="f18e0-253">Można wywołać (lub wywołać) metodę za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="f18e0-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="f18e0-254">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="f18e0-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="f18e0-255">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="f18e0-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="f18e0-256">Aby uzyskać więcej informacji na temat używania pełnomocników w obsłudze zdarzeń, zobacz [Zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f18e0-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="f18e0-257">Aby utworzyć pełnomocnika:</span><span class="sxs-lookup"><span data-stu-id="f18e0-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="f18e0-258">Aby utworzyć odwołanie do metody, która pasuje do podpisu określonego przez pełnomocnika:</span><span class="sxs-lookup"><span data-stu-id="f18e0-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="f18e0-259">Aby uzyskać więcej informacji, zobacz artykuł przewodnik programowania na [delegatów](../delegates/index.md) i artykuł odwołania do języka na słowo kluczowe [pełnomocnika.](../../language-reference/builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="f18e0-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="f18e0-260">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f18e0-260">See also</span></span>

- [<span data-ttu-id="f18e0-261">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f18e0-261">C# Programming Guide</span></span>](../index.md)
