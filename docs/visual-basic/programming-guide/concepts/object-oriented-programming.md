---
title: Programowanie zorientowane obiektowo (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297091"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="7bc20-102">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bc20-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="7bc20-103">Visual Basic zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="7bc20-104">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="7bc20-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="7bc20-105">*Dziedziczenie* opisuje zdolność do tworzenia nowych klas w oparciu o istniejącą klasą.</span><span class="sxs-lookup"><span data-stu-id="7bc20-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="7bc20-106">*Polimorfizm* oznacza, że może mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody w różny sposób.</span><span class="sxs-lookup"><span data-stu-id="7bc20-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="7bc20-107">W tej sekcji opisano następujące pojęcia:</span><span class="sxs-lookup"><span data-stu-id="7bc20-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="7bc20-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="7bc20-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="7bc20-109">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="7bc20-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="7bc20-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="7bc20-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="7bc20-111">Metody</span><span class="sxs-lookup"><span data-stu-id="7bc20-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="7bc20-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7bc20-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="7bc20-113">Destruktory</span><span class="sxs-lookup"><span data-stu-id="7bc20-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="7bc20-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7bc20-114">Events</span></span>](#events)
    - [<span data-ttu-id="7bc20-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="7bc20-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="7bc20-116">Modyfikatory dostępu oraz poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="7bc20-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="7bc20-117">Tworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="7bc20-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="7bc20-118">Udostępnione klas i składowych</span><span class="sxs-lookup"><span data-stu-id="7bc20-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="7bc20-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7bc20-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="7bc20-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="7bc20-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="7bc20-121">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7bc20-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="7bc20-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7bc20-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="7bc20-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7bc20-123">Generics</span></span>](#generics)
- [<span data-ttu-id="7bc20-124">Delegaty</span><span class="sxs-lookup"><span data-stu-id="7bc20-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="7bc20-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="7bc20-125">Classes and objects</span></span>

<span data-ttu-id="7bc20-126">Warunki *klasy* i *obiektu* są czasami stosowane zamiennie, jednak w rzeczywistości klasy opisują *typu* obiektów, podczas gdy obiekty to użytkowe  *wystąpienia* klas.</span><span class="sxs-lookup"><span data-stu-id="7bc20-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="7bc20-127">Więc, akt tworzenia obiektu jest nazywany *wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="7bc20-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="7bc20-128">Korzystając z analogii planu, klasa to plan, a obiekt to budynek utworzony z tego planu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="7bc20-129">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="7bc20-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="7bc20-130">Visual Basic oferuje również uproszczonej wersji klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć duże tablice obiektów i czy chcesz zużyć do tego zbyt dużej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="7bc20-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="7bc20-131">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="7bc20-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="7bc20-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-132">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-133">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="7bc20-134">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="7bc20-135">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="7bc20-135">Class members</span></span>

<span data-ttu-id="7bc20-136">Każda klasa może mieć różne *elementy członkowskie klasy* którzy zawierają właściwości, które opisują dane klasy, metody, które definiują zachowanie klasy i wydarzenia, które zapewniają komunikację między różnych klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="7bc20-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="7bc20-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="7bc20-137">Properties and fields</span></span>

<span data-ttu-id="7bc20-138">Pola i właściwości reprezentują informacje zawarte w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="7bc20-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="7bc20-139">Pola przypominają zmienne, ponieważ można je odczytać lub ustawić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="7bc20-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="7bc20-140">Aby zdefiniować pole:</span><span class="sxs-lookup"><span data-stu-id="7bc20-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="7bc20-141">Właściwości mają get i ustawić procedur, które zapewniają większą kontrolę nad jak ustawiania lub zwracania wartości.</span><span class="sxs-lookup"><span data-stu-id="7bc20-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="7bc20-142">Visual Basic zezwala na tworzenie prywatnego pola do przechowywania wartości właściwości lub użyć tzw automatycznie implementowanych właściwości, które tworzą to pole automatycznie w tle i ustanowiają podstawowe logiki dla procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="7bc20-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="7bc20-143">Aby zdefiniować automatycznie implementowanej właściwości:</span><span class="sxs-lookup"><span data-stu-id="7bc20-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="7bc20-144">Jeśli musisz wykonać kilka dodatkowych operacji odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i Zaoferuj podstawową logikę do przechowywania i pobierania:</span><span class="sxs-lookup"><span data-stu-id="7bc20-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="7bc20-145">Większość właściwości posiada metody lub procedury do ustawiania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="7bc20-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="7bc20-146">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie.</span><span class="sxs-lookup"><span data-stu-id="7bc20-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="7bc20-147">W języku Visual Basic można użyć `ReadOnly` i `WriteOnly` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="7bc20-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="7bc20-148">Jednak automatycznie implementowanych właściwości nie może być tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="7bc20-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-149">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-150">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="7bc20-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="7bc20-151">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="7bc20-152">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="7bc20-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="7bc20-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="7bc20-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="7bc20-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="7bc20-155">Metody</span><span class="sxs-lookup"><span data-stu-id="7bc20-155">Methods</span></span>

 <span data-ttu-id="7bc20-156">A *metoda* to działanie, którą obiekt może wykonywać.</span><span class="sxs-lookup"><span data-stu-id="7bc20-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc20-157">W języku Visual Basic, istnieją dwa sposoby tworzenia metody: `Sub` instrukcja jest używane, jeśli metoda nie zwraca wartości; `Function` instrukcja jest używane, jeśli metoda zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="7bc20-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="7bc20-158">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="7bc20-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="7bc20-159">Klasa może mieć kilka implementacji lub *przeciążenia*, z tej samej metody, które różnią się liczbą typów parametru lub parametrów.</span><span class="sxs-lookup"><span data-stu-id="7bc20-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="7bc20-160">Aby przeciążyć metodę</span><span class="sxs-lookup"><span data-stu-id="7bc20-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="7bc20-161">W większości przypadków użytkownik deklaruje metodę w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="7bc20-162">Jednak języka Visual Basic obsługuje również *metody rozszerzenia* umożliwiającą dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="7bc20-163">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-163">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-164">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="7bc20-165">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7bc20-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="7bc20-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="7bc20-167">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="7bc20-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="7bc20-168">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="7bc20-168">Constructors</span></span>

<span data-ttu-id="7bc20-169">Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="7bc20-170">Konstruktory zwykle inicjują członków danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="7bc20-171">Konstruktor można uruchomić tylko raz, po utworzeniu klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="7bc20-172">Ponadto kod w Konstruktorze zawsze jest uruchamiany przed innymi kodami w klasie.</span><span class="sxs-lookup"><span data-stu-id="7bc20-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="7bc20-173">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku każdej innej metody.</span><span class="sxs-lookup"><span data-stu-id="7bc20-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="7bc20-174">Aby zdefiniować Konstruktor dla klasy:</span><span class="sxs-lookup"><span data-stu-id="7bc20-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="7bc20-175">Aby uzyskać więcej informacji, zobacz: [okres istnienia obiektów: jak obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="7bc20-176">Destruktory</span><span class="sxs-lookup"><span data-stu-id="7bc20-176">Destructors</span></span>

<span data-ttu-id="7bc20-177">Destruktory są używane do niszczenia wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="7bc20-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="7bc20-178">W .NET Framework moduł odśmiecania pamięci automatycznie zarządza alokacją i zwolnieniem pamięci dla obiektów zarządzanych w Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bc20-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="7bc20-179">Jednakże nadal może być konieczne usunięcie przez destruktory niezarządzanych zasobów tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7bc20-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="7bc20-180">Może istnieć jedynie jeden destruktor klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="7bc20-181">Aby uzyskać więcej informacji dotyczących destruktorów i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="7bc20-182">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7bc20-182">Events</span></span>

<span data-ttu-id="7bc20-183">Zdarzenie pozwala klasie lub obiektowi powiadomić inne klasy lub obiektów, kiedy stanie się coś istotnego.</span><span class="sxs-lookup"><span data-stu-id="7bc20-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="7bc20-184">Nosi nazwę klasy, która wysyła (lub generuje) zdarzenie *wydawcy* i klasy, otrzymywać (lub uchwyt) zdarzenia, które są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="7bc20-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="7bc20-185">Aby uzyskać więcej informacji na temat zdarzeń, jak ich wywoływania i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="7bc20-186">Aby zadeklarować zdarzenia, użyj [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="7bc20-187">Aby wywołać zdarzenia, należy użyć [RaiseEvent — instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="7bc20-188">Aby określić obsługę zdarzenia przy użyciu deklaratywną metodę, należy użyć [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrukcji i [obsługuje](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7bc20-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="7bc20-189">Aby mieć możliwość dynamicznego dodawania, usuwania i zmiany obsługi zdarzenia powiązanego ze zdarzeniem, użyj [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md) i [RemoveHandler — instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md) wraz z [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="7bc20-190">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="7bc20-190">Nested classes</span></span>

<span data-ttu-id="7bc20-191">Nosi nazwę klasy zdefiniowanej w ramach innej klasy *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="7bc20-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="7bc20-192">Domyślnie zagnieżdżona klasa jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="7bc20-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="7bc20-193">Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, następuje kropki (.), a następnie według nazwy zagnieżdżonej klasy:</span><span class="sxs-lookup"><span data-stu-id="7bc20-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="7bc20-194">Modyfikatory dostępu oraz poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="7bc20-194">Access modifiers and access levels</span></span>

<span data-ttu-id="7bc20-195">Wszystkie klasy i składowych klasy, można określić poziom dostępu, jaki stanowią dla innych klas przy użyciu *modyfikatorach dostępu*.</span><span class="sxs-lookup"><span data-stu-id="7bc20-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="7bc20-196">Dostępne są następujące modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="7bc20-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="7bc20-197">Modyfikator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bc20-197">Visual Basic Modifier</span></span>|<span data-ttu-id="7bc20-198">Definicja</span><span class="sxs-lookup"><span data-stu-id="7bc20-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="7bc20-199">Public</span><span class="sxs-lookup"><span data-stu-id="7bc20-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="7bc20-200">Typ lub element członkowski może zostać oceniony przez inny kod, w tym samym zestawie lub w innym zestawie, który odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="7bc20-201">Private</span><span class="sxs-lookup"><span data-stu-id="7bc20-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="7bc20-202">Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="7bc20-203">Protected</span><span class="sxs-lookup"><span data-stu-id="7bc20-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="7bc20-204">Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="7bc20-205">Friend</span><span class="sxs-lookup"><span data-stu-id="7bc20-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="7bc20-206">Typ lub element członkowski może zostać oceniony przez każdy kod z tego samego zestawu, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="7bc20-207">Typ lub element członkowski jest możliwy przez każdy kod z tego samego zestawu lub każdą pochodną klasę w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7bc20-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="7bc20-208">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="7bc20-209">Tworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="7bc20-209">Instantiating classes</span></span>

<span data-ttu-id="7bc20-210">Aby utworzyć obiekt, należy utworzyć wystąpienia klasy lub utworzyć wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="7bc20-211">Po utworzeniu wystąpienia klasy, można przypisać wartości do pól i właściwości instancji i wywołania metod klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="7bc20-212">Aby przypisać wartości do właściwości w procesie tworzenia wystąpienia klasy, użyj inicjalizatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="7bc20-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="7bc20-213">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-213">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-214">New, operator</span><span class="sxs-lookup"><span data-stu-id="7bc20-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="7bc20-215">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="7bc20-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="7bc20-216">Udostępnione klas i składowych</span><span class="sxs-lookup"><span data-stu-id="7bc20-216">Shared classes and members</span></span>

 <span data-ttu-id="7bc20-217">Udostępnione składową klasy jest właściwość, procedura lub pole, który jest współużytkowany przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="7bc20-218">Aby zdefiniować udostępnionego elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="7bc20-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="7bc20-219">Aby uzyskać dostęp do udostępnionej składowej, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="7bc20-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="7bc20-220">Udostępnione moduły w języku Visual Basic zostały udostępnione tylko elementy członkowskie i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7bc20-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="7bc20-221">Udostępniane elementy członkowskie także nie może uzyskać dostępu nieudostępnione właściwości, pól ani metod</span><span class="sxs-lookup"><span data-stu-id="7bc20-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="7bc20-222">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-222">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-223">Shared</span><span class="sxs-lookup"><span data-stu-id="7bc20-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="7bc20-224">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="7bc20-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="7bc20-225">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7bc20-225">Anonymous types</span></span>

<span data-ttu-id="7bc20-226">Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="7bc20-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="7bc20-227">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="7bc20-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="7bc20-228">Klasa nie ma użytecznych nazw i zawiera właściwości, które określisz w odwołaniu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="7bc20-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="7bc20-229">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="7bc20-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="7bc20-230">Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="7bc20-231">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="7bc20-231">Inheritance</span></span>

<span data-ttu-id="7bc20-232">Dziedziczenie umożliwia utworzenie nowej klasy, która używa, rozszerza i modyfikuje zachowanie, która jest zdefiniowana w innej klasy.</span><span class="sxs-lookup"><span data-stu-id="7bc20-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="7bc20-233">Nosi nazwę klasy, której członkowie są dziedziczeni *klasy bazowej*, a klasa, która dziedziczy tych członków, jest nazywana *klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="7bc20-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="7bc20-234">Jednakże wszystkie klasy w języku Visual Basic niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia niskopoziomowe usługi dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="7bc20-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc20-235">Język Visual Basic nie obsługuje wielokrotne dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="7bc20-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="7bc20-236">Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="7bc20-237">Dziedziczenie z klasy bazowej:</span><span class="sxs-lookup"><span data-stu-id="7bc20-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="7bc20-238">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="7bc20-238">By default all classes can be inherited.</span></span> <span data-ttu-id="7bc20-239">Można jednak określić klasy nie może być używany jako klasa bazowa, czy utworzyć klasę, która może służyć jako klasę bazową tylko.</span><span class="sxs-lookup"><span data-stu-id="7bc20-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="7bc20-240">Aby określić, że klasa nie można użyć jako klasa bazowa:</span><span class="sxs-lookup"><span data-stu-id="7bc20-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="7bc20-241">Aby określić, że klasa może służyć jako klasę bazową tylko i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="7bc20-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="7bc20-242">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-242">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-243">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="7bc20-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="7bc20-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="7bc20-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="7bc20-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="7bc20-246">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7bc20-246">Overriding members</span></span>

<span data-ttu-id="7bc20-247">Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie w swojej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="7bc20-248">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, należy go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="7bc20-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="7bc20-249">Oznacza to można zdefiniować nową metodę implementacji metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="7bc20-250">Następujące Modyfikatory są używane do kontrolowania, jak zastąpić właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="7bc20-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="7bc20-251">Modyfikator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bc20-251">Visual Basic Modifier</span></span>|<span data-ttu-id="7bc20-252">Definicja</span><span class="sxs-lookup"><span data-stu-id="7bc20-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="7bc20-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="7bc20-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="7bc20-254">Zezwala na element członkowski klasy został nadpisany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="7bc20-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="7bc20-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="7bc20-256">Zastępuje wirtualny element członkowski (przesłanialny) zdefiniowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="7bc20-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="7bc20-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="7bc20-258">Element członkowski zapobiega zastępowaniu w klasie dziedziczącej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="7bc20-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="7bc20-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="7bc20-260">Wymaga, aby element członkowski klasy został nadpisany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7bc20-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="7bc20-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="7bc20-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="7bc20-262">Ukrywa członka dziedziczonego z klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="7bc20-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="7bc20-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7bc20-263">Interfaces</span></span>

<span data-ttu-id="7bc20-264">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7bc20-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="7bc20-265">Jednak w przeciwieństwie do klasy, interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="7bc20-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="7bc20-266">One są implementowane przez klasy i definiowane jako osobne jednostki od klas.</span><span class="sxs-lookup"><span data-stu-id="7bc20-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="7bc20-267">Interfejs reprezentuje kontrakt, w tym, że klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu, dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7bc20-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="7bc20-268">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="7bc20-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="7bc20-269">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="7bc20-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="7bc20-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-270">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-271">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7bc20-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="7bc20-272">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="7bc20-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="7bc20-273">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="7bc20-274">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7bc20-274">Generics</span></span>

<span data-ttu-id="7bc20-275">Klasy, struktury, interfejsy i metody na platformie .NET mogą obejmować *parametry typu* który definiują typy obiektów, które można przechowywać lub używać.</span><span class="sxs-lookup"><span data-stu-id="7bc20-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="7bc20-276">Najbardziej typowym przykładem typów ogólnych jest kolekcja, której można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7bc20-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="7bc20-277">Aby zdefiniować klasę ogólną:</span><span class="sxs-lookup"><span data-stu-id="7bc20-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="7bc20-278">Aby utworzyć wystąpienie klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="7bc20-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="7bc20-279">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-279">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-280">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7bc20-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="7bc20-281">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bc20-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="7bc20-282">Delegaty</span><span class="sxs-lookup"><span data-stu-id="7bc20-282">Delegates</span></span>

 <span data-ttu-id="7bc20-283">A *delegować* to typ, który definiuje podpis metody i można podać odwołanie do dowolnej metody mającą zgodny podpis.</span><span class="sxs-lookup"><span data-stu-id="7bc20-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="7bc20-284">Można wywołać (lub wywołać) metodę przez delegat.</span><span class="sxs-lookup"><span data-stu-id="7bc20-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="7bc20-285">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="7bc20-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc20-286">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="7bc20-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="7bc20-287">Aby uzyskać więcej informacji dotyczących używania delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bc20-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="7bc20-288">Aby utworzyć delegat:</span><span class="sxs-lookup"><span data-stu-id="7bc20-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="7bc20-289">Aby utworzyć odwołanie do metody, która pasuje do oznaczenia określonego przez delegat:</span><span class="sxs-lookup"><span data-stu-id="7bc20-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="7bc20-290">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="7bc20-290">For more information, see:</span></span>

- [<span data-ttu-id="7bc20-291">Delegaty</span><span class="sxs-lookup"><span data-stu-id="7bc20-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="7bc20-292">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7bc20-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="7bc20-293">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="7bc20-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="7bc20-294">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bc20-294">See also</span></span>

- [<span data-ttu-id="7bc20-295">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bc20-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
