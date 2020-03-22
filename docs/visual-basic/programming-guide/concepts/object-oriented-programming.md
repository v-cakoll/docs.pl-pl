---
title: Programowanie obiektowe
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400688"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="47138-102">Programowanie obiektowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47138-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="47138-103">Visual Basic zapewnia pełną obsługę programowania obiektowego, w tym hermetyzacji, dziedziczenia i polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="47138-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="47138-104">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="47138-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="47138-105">*Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="47138-106">*Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="47138-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="47138-107">W tej sekcji opisano następujące pojęcia:</span><span class="sxs-lookup"><span data-stu-id="47138-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="47138-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="47138-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="47138-109">Elementy klasy</span><span class="sxs-lookup"><span data-stu-id="47138-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="47138-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="47138-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="47138-111">Metody</span><span class="sxs-lookup"><span data-stu-id="47138-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="47138-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="47138-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="47138-113">Destruktory</span><span class="sxs-lookup"><span data-stu-id="47138-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="47138-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="47138-114">Events</span></span>](#events)
    - [<span data-ttu-id="47138-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="47138-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="47138-116">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="47138-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="47138-117">Tworzenie lekcji tworzenia wystąpienia</span><span class="sxs-lookup"><span data-stu-id="47138-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="47138-118">Wspólne zajęcia i członkowie</span><span class="sxs-lookup"><span data-stu-id="47138-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="47138-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="47138-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="47138-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="47138-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="47138-121">Zastępowanie członków</span><span class="sxs-lookup"><span data-stu-id="47138-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="47138-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="47138-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="47138-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="47138-123">Generics</span></span>](#generics)
- [<span data-ttu-id="47138-124">Delegaty</span><span class="sxs-lookup"><span data-stu-id="47138-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="47138-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="47138-125">Classes and objects</span></span>

<span data-ttu-id="47138-126">*Klasy* i *obiektu* terminów są czasami używane zamiennie, ale w rzeczywistości klasy opisują *typ* obiektów, podczas gdy obiekty są *użytecznymi wystąpieniami* klas.</span><span class="sxs-lookup"><span data-stu-id="47138-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="47138-127">Tak więc, akt tworzenia obiektu jest nazywany *wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="47138-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="47138-128">Przy użyciu analogii planu, klasa jest planem, a obiekt jest budynkiem wykonanym z tego planu.</span><span class="sxs-lookup"><span data-stu-id="47138-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="47138-129">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="47138-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="47138-130">Visual Basic zapewnia również lekką wersję klas o nazwie *struktur,* które są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i nie chcesz zużywać zbyt dużo pamięci do tego.</span><span class="sxs-lookup"><span data-stu-id="47138-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="47138-131">Aby zdefiniować strukturę, należy:</span><span class="sxs-lookup"><span data-stu-id="47138-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="47138-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-132">For more information, see:</span></span>

- [<span data-ttu-id="47138-133">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="47138-134">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="47138-135">Elementy klasy</span><span class="sxs-lookup"><span data-stu-id="47138-135">Class members</span></span>

<span data-ttu-id="47138-136">Każda klasa może mieć różne *elementy członkowskie klasy,* które zawierają właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="47138-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="47138-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="47138-137">Properties and fields</span></span>

<span data-ttu-id="47138-138">Pola i właściwości reprezentują informacje zawarte w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="47138-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="47138-139">Pola są jak zmienne, ponieważ można je odczytać lub ustawić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="47138-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="47138-140">Aby zdefiniować pole, należy:</span><span class="sxs-lookup"><span data-stu-id="47138-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="47138-141">Właściwości mają get i ustawić procedury, które zapewniają większą kontrolę nad jak wartości są ustawiane lub zwracane.</span><span class="sxs-lookup"><span data-stu-id="47138-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="47138-142">Visual Basic umożliwia utworzenie pola prywatnego do przechowywania wartości właściwości lub użycie tak zwanych właściwości automatycznie implementowanych, które automatycznie tworzą to pole za kulisami i zapewniają podstawową logikę dla procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="47138-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="47138-143">Aby zdefiniować właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="47138-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="47138-144">Jeśli trzeba wykonać kilka dodatkowych operacji do odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę przechowywania i pobierania:</span><span class="sxs-lookup"><span data-stu-id="47138-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="47138-145">Większość właściwości mają metody lub procedury, aby ustawić i uzyskać wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="47138-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="47138-146">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby ograniczyć ich możliwość modyfikowanie lub odczytywanie.</span><span class="sxs-lookup"><span data-stu-id="47138-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="47138-147">W języku Visual `ReadOnly` Basic `WriteOnly` można używać i słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="47138-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="47138-148">Jednak właściwości automatycznie implementowane nie mogą być tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="47138-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="47138-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-149">For more information, see:</span></span>

- [<span data-ttu-id="47138-150">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="47138-151">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="47138-152">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="47138-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="47138-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="47138-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="47138-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="47138-155">Metody</span><span class="sxs-lookup"><span data-stu-id="47138-155">Methods</span></span>

 <span data-ttu-id="47138-156">*Metoda* jest akcją, którą obiekt może wykonać.</span><span class="sxs-lookup"><span data-stu-id="47138-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="47138-157">W języku Visual Basic istnieją dwa sposoby `Sub` tworzenia metody: instrukcja jest używana, jeśli metoda nie zwraca wartości; instrukcja `Function` jest używana, jeśli metoda zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="47138-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="47138-158">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="47138-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="47138-159">Klasa może mieć kilka implementacji lub *przeciążenia*, tej samej metody, które różnią się liczbą parametrów lub typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="47138-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="47138-160">Aby przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="47138-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="47138-161">W większości przypadków deklarujesz metodę w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="47138-162">Jednak Visual Basic obsługuje również *metody rozszerzenia,* które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="47138-163">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-163">For more information, see:</span></span>

- [<span data-ttu-id="47138-164">Instrukcja funkcji</span><span class="sxs-lookup"><span data-stu-id="47138-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="47138-165">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="47138-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="47138-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="47138-167">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="47138-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="47138-168">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="47138-168">Constructors</span></span>

<span data-ttu-id="47138-169">Konstruktory są metody klasy, które są wykonywane automatycznie podczas tworzenia obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="47138-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="47138-170">Konstruktory zwykle inicjują elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="47138-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="47138-171">Konstruktor można uruchomić tylko raz podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="47138-172">Ponadto kod w konstruktorze zawsze działa przed innym kodem w klasie.</span><span class="sxs-lookup"><span data-stu-id="47138-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="47138-173">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób, jak w przypadku każdej innej metody.</span><span class="sxs-lookup"><span data-stu-id="47138-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="47138-174">Aby zdefiniować konstruktor dla klasy:</span><span class="sxs-lookup"><span data-stu-id="47138-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="47138-175">Aby uzyskać więcej informacji, zobacz: [Okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="47138-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="47138-176">Destruktory</span><span class="sxs-lookup"><span data-stu-id="47138-176">Destructors</span></span>

<span data-ttu-id="47138-177">Destruktory są używane do destrukcji wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="47138-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="47138-178">W .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i zwalniania pamięci dla obiektów zarządzanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47138-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="47138-179">Jednak nadal może być konieczne destruktory, aby oczyścić wszelkie niezarządzane zasoby, które tworzy aplikacja.</span><span class="sxs-lookup"><span data-stu-id="47138-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="47138-180">Może istnieć tylko jeden destruktor dla klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="47138-181">Aby uzyskać więcej informacji na temat destruktorów i wyrzucania elementów bezużytecznych w ramach .NET Framework, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="47138-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="47138-182">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="47138-182">Events</span></span>

<span data-ttu-id="47138-183">Zdarzenia umożliwiają klasy lub obiektu powiadamiać inne klasy lub obiekty, gdy wystąpi coś interesującego.</span><span class="sxs-lookup"><span data-stu-id="47138-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="47138-184">Klasa, która wysyła (lub wywołuje) zdarzenie jest nazywany *wydawcą* i klasy, które odbierają (lub dojdą) zdarzenie są nazywane *subskrybentów.*</span><span class="sxs-lookup"><span data-stu-id="47138-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="47138-185">Aby uzyskać więcej informacji o zdarzeniach, sposób ich wywoływania i obsługi, zobacz [Zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="47138-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="47138-186">Aby zadeklarować zdarzenia, należy użyć [instrukcji zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47138-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="47138-187">Aby podnieść zdarzenia, użyj [RaiseEvent Instrukcji](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47138-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="47138-188">Aby określić programy obsługi zdarzeń przy użyciu deklaratywny sposób, należy użyć [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrukcji i [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="47138-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="47138-189">Aby móc dynamicznie dodawać, usuwać i zmieniać program obsługi zdarzeń skojarzony ze zdarzeniem, należy użyć [instrukcji AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) i [Instrukcji RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) wraz z [operatorem AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="47138-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="47138-190">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="47138-190">Nested classes</span></span>

<span data-ttu-id="47138-191">Klasa zdefiniowana w innej klasie jest *nazywana zagnieżdżoną*.</span><span class="sxs-lookup"><span data-stu-id="47138-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="47138-192">Domyślnie klasa zagnieżdżona jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="47138-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="47138-193">Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, po której następuje kropka, a następnie następuje nazwa klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="47138-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="47138-194">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="47138-194">Access modifiers and access levels</span></span>

<span data-ttu-id="47138-195">Wszystkie klasy i członkowie klasy mogą określić, jaki poziom dostępu zapewniają innym klasom za pomocą *modyfikatorów dostępu.*</span><span class="sxs-lookup"><span data-stu-id="47138-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="47138-196">Dostępne są następujące modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="47138-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="47138-197">Modyfikator języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47138-197">Visual Basic Modifier</span></span>|<span data-ttu-id="47138-198">Definicja</span><span class="sxs-lookup"><span data-stu-id="47138-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="47138-199">Public</span><span class="sxs-lookup"><span data-stu-id="47138-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="47138-200">Typ lub element członkowski mogą być dostępne przez inny kod w tym samym zestawie lub innego zestawu, który odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="47138-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="47138-201">Private</span><span class="sxs-lookup"><span data-stu-id="47138-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="47138-202">Dostęp do typu lub elementu członkowskiego można uzyskać tylko za pomocą kodu w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="47138-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="47138-203">Chronione</span><span class="sxs-lookup"><span data-stu-id="47138-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="47138-204">Dostęp do typu lub elementu członkowskiego można uzyskać tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="47138-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="47138-205">Friend</span><span class="sxs-lookup"><span data-stu-id="47138-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="47138-206">Typ lub element członkowski mogą być dostępne przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="47138-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="47138-207">Typ lub element członkowski są dostępne za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="47138-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="47138-208">Aby uzyskać więcej informacji, zobacz [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="47138-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="47138-209">Tworzenie lekcji tworzenia wystąpienia</span><span class="sxs-lookup"><span data-stu-id="47138-209">Instantiating classes</span></span>

<span data-ttu-id="47138-210">Aby utworzyć obiekt, należy utworzyć wystąpienie klasy lub utworzyć wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="47138-211">Po wystąpieniu klasy można przypisać wartości do właściwości i pól wystąpienia i wywołać metody klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="47138-212">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, użyj inicjatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="47138-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="47138-213">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-213">For more information, see:</span></span>

- [<span data-ttu-id="47138-214">Nowy operator</span><span class="sxs-lookup"><span data-stu-id="47138-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="47138-215">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="47138-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="47138-216">Wspólne zajęcia i członkowie</span><span class="sxs-lookup"><span data-stu-id="47138-216">Shared classes and members</span></span>

 <span data-ttu-id="47138-217">Udostępniony element członkowski klasy jest właściwością, procedurą lub polem współużytkowane przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="47138-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="47138-218">Aby zdefiniować współużytkowane elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="47138-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="47138-219">Aby uzyskać dostęp do udostępnionego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="47138-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="47138-220">Udostępnione moduły w języku Visual Basic mają tylko współużytkowanych elementów członkowskich i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="47138-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="47138-221">Współdzielonych członków również nie można uzyskać dostępu do nieudzielonych właściwości, pól lub metod</span><span class="sxs-lookup"><span data-stu-id="47138-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="47138-222">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-222">For more information, see:</span></span>

- [<span data-ttu-id="47138-223">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="47138-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="47138-224">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="47138-225">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="47138-225">Anonymous types</span></span>

<span data-ttu-id="47138-226">Typy anonimowe umożliwiają tworzenie obiektów bez zapisywania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="47138-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="47138-227">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="47138-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="47138-228">Klasa nie ma nazwy użytkowej i zawiera właściwości określone podczas deklarowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="47138-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="47138-229">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="47138-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="47138-230">Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="47138-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="47138-231">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="47138-231">Inheritance</span></span>

<span data-ttu-id="47138-232">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie, które jest zdefiniowane w innej klasie.</span><span class="sxs-lookup"><span data-stu-id="47138-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="47138-233">Klasa, której członkowie są dziedziczone jest nazywany *klasy podstawowej*, a klasa, która dziedziczy tych członków jest nazywany *klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="47138-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="47138-234">Jednak wszystkie klasy w języku Visual <xref:System.Object> Basic niejawnie dziedziczą z klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="47138-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="47138-235">Visual Basic nie obsługuje wielu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="47138-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="47138-236">Oznacza to, że można określić tylko jedną klasę podstawową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="47138-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="47138-237">Aby dziedziczyć z klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="47138-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="47138-238">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="47138-238">By default all classes can be inherited.</span></span> <span data-ttu-id="47138-239">Można jednak określić, czy klasa nie może być używana jako klasa podstawowa, czy też utworzyć klasę, która może być używana tylko jako klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="47138-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="47138-240">Aby określić, że klasa nie może być używana jako klasa podstawowa:</span><span class="sxs-lookup"><span data-stu-id="47138-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="47138-241">Aby określić, że klasa może być używana tylko jako klasa podstawowa i nie można jej utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="47138-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="47138-242">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-242">For more information, see:</span></span>

- [<span data-ttu-id="47138-243">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="47138-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="47138-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="47138-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="47138-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="47138-246">Zastępowanie członków</span><span class="sxs-lookup"><span data-stu-id="47138-246">Overriding members</span></span>

<span data-ttu-id="47138-247">Domyślnie klasa pochodna dziedziczy wszystkie elementy członkowskie z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="47138-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="47138-248">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="47138-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="47138-249">Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="47138-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="47138-250">Następujące modyfikatory są używane do kontrolowania, jak właściwości i metody są zastępowane:</span><span class="sxs-lookup"><span data-stu-id="47138-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="47138-251">Modyfikator języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47138-251">Visual Basic Modifier</span></span>|<span data-ttu-id="47138-252">Definicja</span><span class="sxs-lookup"><span data-stu-id="47138-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="47138-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="47138-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="47138-254">Umożliwia element członkowski klasy, które mają zostać zastąpione w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="47138-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="47138-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="47138-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="47138-256">Zastępuje wirtualny (nadpisalny) element członkowski zdefiniowany w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="47138-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="47138-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="47138-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="47138-258">Zapobiega element członkowski z nadrzędnego w klasie dziedziczącej.</span><span class="sxs-lookup"><span data-stu-id="47138-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="47138-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="47138-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="47138-260">Wymaga, aby element członkowski klasy został zastąpiony w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="47138-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="47138-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="47138-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="47138-262">Ukrywa element członkowski odziedziczony po klasie podstawowej</span><span class="sxs-lookup"><span data-stu-id="47138-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="47138-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="47138-263">Interfaces</span></span>

<span data-ttu-id="47138-264">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="47138-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="47138-265">Ale w przeciwieństwie do klas interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="47138-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="47138-266">Są one implementowane przez klasy i definiowane jako oddzielne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="47138-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="47138-267">Interfejs reprezentuje kontrakt, w tym klasy, która implementuje interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="47138-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="47138-268">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="47138-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="47138-269">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="47138-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="47138-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-270">For more information, see:</span></span>

- [<span data-ttu-id="47138-271">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="47138-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="47138-272">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="47138-273">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="47138-274">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="47138-274">Generics</span></span>

<span data-ttu-id="47138-275">Klasy, struktury, interfejsy i metody w .NET mogą zawierać *parametry typu,* które definiują typy obiektów, które mogą przechowywać lub używać.</span><span class="sxs-lookup"><span data-stu-id="47138-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="47138-276">Najczęstszym przykładem generics jest kolekcja, gdzie można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="47138-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="47138-277">Aby zdefiniować klasę rodzajową:</span><span class="sxs-lookup"><span data-stu-id="47138-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="47138-278">Aby utworzyć wystąpienie klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="47138-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="47138-279">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-279">For more information, see:</span></span>

- [<span data-ttu-id="47138-280">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="47138-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="47138-281">Typy ogólne w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47138-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="47138-282">Delegaty</span><span class="sxs-lookup"><span data-stu-id="47138-282">Delegates</span></span>

 <span data-ttu-id="47138-283">*Pełnomocnik* jest typem, który definiuje podpis metody i może zapewnić odwołanie do dowolnej metody z zgodnym podpisem.</span><span class="sxs-lookup"><span data-stu-id="47138-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="47138-284">Można wywołać (lub wywołać) metodę za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="47138-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="47138-285">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="47138-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="47138-286">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="47138-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="47138-287">Aby uzyskać więcej informacji na temat używania pełnomocników w obsłudze zdarzeń, zobacz [Zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="47138-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="47138-288">Aby utworzyć pełnomocnika:</span><span class="sxs-lookup"><span data-stu-id="47138-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="47138-289">Aby utworzyć odwołanie do metody zgodnej z podpisem określonym przez pełnomocnika:</span><span class="sxs-lookup"><span data-stu-id="47138-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="47138-290">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="47138-290">For more information, see:</span></span>

- [<span data-ttu-id="47138-291">Delegaty</span><span class="sxs-lookup"><span data-stu-id="47138-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="47138-292">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47138-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="47138-293">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="47138-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="47138-294">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47138-294">See also</span></span>

- [<span data-ttu-id="47138-295">Przewodnik programowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47138-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
