---
title: Programowanie zorientowane obiektowo (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 950f080949dce0fc1a2834825d2f7c945007fb7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="cc1bb-102">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc1bb-102">Object-Oriented Programming (Visual Basic)</span></span>
<span data-ttu-id="cc1bb-103">Programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizm Visual Basic zapewnia pełną obsługę.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="cc1bb-104">*Hermetyzacja* oznacza, że grupy powiązane właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="cc1bb-105">*Dziedziczenie* opisuje może tworzyć nowe klasy oparte na istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="cc1bb-106">*Polimorfizm* oznacza, że może mieć wielu klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="cc1bb-107">W tej sekcji opisano następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="cc1bb-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="cc1bb-108">Classes and objects</span></span>](#classes-and-objects)  
  
    -   [<span data-ttu-id="cc1bb-109">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-109">Class members</span></span>](#members)  
  
         [<span data-ttu-id="cc1bb-110">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="cc1bb-110">Properties and fields</span></span>](#properties-and-fields)  
  
         [<span data-ttu-id="cc1bb-111">Metody</span><span class="sxs-lookup"><span data-stu-id="cc1bb-111">Methods</span></span>](#methods)  
  
         [<span data-ttu-id="cc1bb-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="cc1bb-112">Constructors</span></span>](#constructors)  
  
         [<span data-ttu-id="cc1bb-113">Destruktory</span><span class="sxs-lookup"><span data-stu-id="cc1bb-113">Destructors</span></span>](#destructors)  
  
         [<span data-ttu-id="cc1bb-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cc1bb-114">Events</span></span>](#events)  
  
         [<span data-ttu-id="cc1bb-115">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="cc1bb-115">Nested classes</span></span>](#nested-classes)  
  
    -   [<span data-ttu-id="cc1bb-116">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="cc1bb-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)  
  
    -   [<span data-ttu-id="cc1bb-117">Utworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-117">Instantiating classes</span></span>](#instantiating-classes)  
  
    -   [<span data-ttu-id="cc1bb-118">Udostępniony klas i członków</span><span class="sxs-lookup"><span data-stu-id="cc1bb-118">Shared classes and members</span></span>](#shared-classes-and-members)  
  
    -   [<span data-ttu-id="cc1bb-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="cc1bb-119">Anonymous types</span></span>](#anonymous-types)  
  
-   [<span data-ttu-id="cc1bb-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="cc1bb-120">Inheritance</span></span>](#inheritance)  
  
    -   [<span data-ttu-id="cc1bb-121">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="cc1bb-121">Overriding members</span></span>](#overriding-members)  
  
-   [<span data-ttu-id="cc1bb-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-122">Interfaces</span></span>](#interfaces)  
  
-   [<span data-ttu-id="cc1bb-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="cc1bb-123">Generics</span></span>](#generics)  
  
-   [<span data-ttu-id="cc1bb-124">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="cc1bb-124">Delegates</span></span>](#delegates)  
  
## <a name="classes-and-objects"></a><span data-ttu-id="cc1bb-125">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="cc1bb-125">Classes and objects</span></span>  
<span data-ttu-id="cc1bb-126">Warunki *klasy* i *obiektu* są czasami używane zamiennie, ale w rzeczywistości opisano klasy *typu* obiektów, gdy obiekty są użyteczne  *wystąpienia* klas.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="cc1bb-127">Dlatego utworzenie obiektu jest nazywany *wystąpienia*.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="cc1bb-128">Przy użyciu odpowiednio planu, klasa to umożliwi, a obiekt jest budynku z tego planu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="cc1bb-129">Aby zdefiniować klasy:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-129">To define a class:</span></span>

```vb  
Class SampleClass
End Class
```

<span data-ttu-id="cc1bb-130">Visual Basic dostarcza również światła wersję klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i chcesz używać zbyt dużej ilości pamięci do tego.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="cc1bb-131">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-131">To define a structure:</span></span>  

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="cc1bb-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-132">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-133">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="cc1bb-134">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="cc1bb-135">Członkowie klasy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-135">Class members</span></span>
<span data-ttu-id="cc1bb-136">Każda klasa może mieć różne *klasy elementów członkowskich* zawierające właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnych klas i obiektów.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="cc1bb-137">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="cc1bb-137">Properties and fields</span></span>
<span data-ttu-id="cc1bb-138">Pola i właściwości reprezentują informacje, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="cc1bb-139">Pola są podobne do zmiennych, ponieważ może być odczytany lub ustawić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="cc1bb-140">Aby zdefiniować pola:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="cc1bb-141">Właściwości mają get i ustaw procedur, które zapewniają większą kontrolę w sposób ustawiona lub zwrócona wartości.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="cc1bb-142">Visual Basic służy do utworzenia prywatnej pola do przechowywania wartości właściwości lub użyj tak zwane właściwości zaimplementowane automatycznie utworzyć w tym polu automatycznie w tle, które zapewniają podstawowa logika procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="cc1bb-143">Aby zdefiniować właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="cc1bb-144">Jeśli musisz wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawowa logika do przechowywania i pobierania jej:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="cc1bb-145">Większość właściwości mają metody lub procedury zarówno Ustawianie i pobieranie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="cc1bb-146">Można jednak utworzyć właściwości tylko do odczytu lub w trybie tylko do zapisu, aby uniemożliwić ich modyfikacji lub odczytu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="cc1bb-147">W języku Visual Basic można użyć `ReadOnly` i `WriteOnly` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="cc1bb-148">Jednak automatycznie implementowane właściwości nie może być tylko do odczytu lub w trybie tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="cc1bb-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-149">For more information, see:</span></span>
  
-   [<span data-ttu-id="cc1bb-150">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="cc1bb-151">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [<span data-ttu-id="cc1bb-152">Set — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [<span data-ttu-id="cc1bb-153">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cc1bb-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [<span data-ttu-id="cc1bb-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="cc1bb-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a><span data-ttu-id="cc1bb-155">Metody</span><span class="sxs-lookup"><span data-stu-id="cc1bb-155">Methods</span></span>  
 <span data-ttu-id="cc1bb-156">A *metody* to operacja, którą można wykonać obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-156">A *method* is an action that an object can perform.</span></span>  

> [!NOTE]
>  <span data-ttu-id="cc1bb-157">W języku Visual Basic, istnieją dwa sposoby tworzenia metody: `Sub` używana jest instrukcja, jeśli metoda nie zwraca wartości; `Function` używana jest instrukcja, jeśli metoda zwróci wartość.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="cc1bb-158">Aby zdefiniować metody klasy:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="cc1bb-159">Klasa może mieć wielu implementacji lub *przeciążenia*, metody różne liczby parametrów ani typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="cc1bb-160">Aby można było przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="cc1bb-161">W większości przypadków należy zadeklarować metody w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="cc1bb-162">Jednak obsługuje również Visual Basic *metody rozszerzenia* umożliwiające dodawanie metody do istniejącej klasy poza rzeczywiste definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="cc1bb-163">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-163">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-164">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  

- [<span data-ttu-id="cc1bb-165">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [<span data-ttu-id="cc1bb-166">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="cc1bb-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [<span data-ttu-id="cc1bb-167">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="cc1bb-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a><span data-ttu-id="cc1bb-168">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="cc1bb-168">Constructors</span></span>  
<span data-ttu-id="cc1bb-169">Konstruktory są metody klasy, które są wykonywane automatycznie, gdy utworzono obiekt danego typu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="cc1bb-170">Konstruktory zainicjować zazwyczaj elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="cc1bb-171">Konstruktor można uruchomić tylko raz, podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="cc1bb-172">Ponadto w Konstruktorze kod zawsze uruchamiany przed innymi kod w klasie.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="cc1bb-173">Jednak w taki sam sposób jak w przypadku innych metod, można utworzyć wielu przeciążeń konstruktora.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="cc1bb-174">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

<span data-ttu-id="cc1bb-175">Aby uzyskać więcej informacji, zobacz: [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="cc1bb-176">Destruktory</span><span class="sxs-lookup"><span data-stu-id="cc1bb-176">Destructors</span></span>
<span data-ttu-id="cc1bb-177">Destruktory służą do destruct wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="cc1bb-178">W programie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i wersji pamięci dla zarządzanych obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="cc1bb-179">Jednakże nadal może być konieczne destruktory Aby oczyścić wszelkie niezarządzane zasoby, tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="cc1bb-180">Może istnieć tylko jeden destruktora dla klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="cc1bb-181">Aby uzyskać więcej informacji na temat destruktory i wyrzucanie elementów bezużytecznych w programie .NET Framework, zobacz [wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="cc1bb-182">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cc1bb-182">Events</span></span>
<span data-ttu-id="cc1bb-183">Zdarzenia włączyć klasę lub obiekt, aby powiadomić innych grup lub obiektów, kiedy coś odsetek występuje.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="cc1bb-184">Klasa, która wysyła (lub zgłasza) zdarzenia jest nazywany *wydawcy* i klasy, które odbierać (lub dojścia) zdarzenia są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="cc1bb-185">Aby uzyskać więcej informacji o zdarzeniach, sposób ich pojawienia się i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="cc1bb-186">Aby zadeklarować zdarzenia, użyj [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="cc1bb-187">Aby wywołać zdarzenia, użyj [RaiseEvent — instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="cc1bb-188">Aby określić przy użyciu na deklaratywne procedury obsługi zdarzeń, użyj [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrukcji i [obsługuje](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="cc1bb-189">Aby mieć możliwość dynamicznego dodawania, usuwania i zmień skojarzone ze zdarzeniem programu obsługi zdarzeń, należy użyć [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md) i [RemoveHandler — instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md) razem z [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="cc1bb-190">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="cc1bb-190">Nested classes</span></span>  
<span data-ttu-id="cc1bb-191">Nosi nazwę klasy zdefiniowanej w klasie innej *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="cc1bb-192">Domyślnie zagnieżdżona klasa jest prywatne.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="cc1bb-193">Można utworzyć wystąpienia klasy zagnieżdżonej, należy użyć nazwy klasy kontenera znak kropki (.) i po niej nazwę klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="cc1bb-194">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="cc1bb-194">Access modifiers and access levels</span></span>  
<span data-ttu-id="cc1bb-195">Wszystkie klasy i elementów członkowskich klasy można określić poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="cc1bb-196">Dostępne są następujące modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="cc1bb-197">Modyfikator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc1bb-197">Visual Basic Modifier</span></span>|<span data-ttu-id="cc1bb-198">Definicja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="cc1bb-199">Publiczna</span><span class="sxs-lookup"><span data-stu-id="cc1bb-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="cc1bb-200">Typ lub element członkowski jest możliwy przez inny kod, w tym samym zestawie lub innego zestawu, który odwołuje się on.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="cc1bb-201">Prywatne</span><span class="sxs-lookup"><span data-stu-id="cc1bb-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="cc1bb-202">Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="cc1bb-203">Chronione</span><span class="sxs-lookup"><span data-stu-id="cc1bb-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="cc1bb-204">Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="cc1bb-205">Friend</span><span class="sxs-lookup"><span data-stu-id="cc1bb-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="cc1bb-206">Typ lub element członkowski jest możliwy przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="cc1bb-207">Typ lub element członkowski jest dostępna przez dowolny kod w tym samym zestawie lub dowolnej klasy pochodnej w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="cc1bb-208">Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="cc1bb-209">Utworzenie wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-209">Instantiating classes</span></span>  
<span data-ttu-id="cc1bb-210">Do utworzenia obiektu, należy utworzyć wystąpienia klasy lub utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="cc1bb-211">Po utworzenie wystąpienia klasy, można przypisać wartości do właściwości i pola wystąpienia i wywołania metody klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="cc1bb-212">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatory obiektów:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="cc1bb-213">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-213">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-214">New — Operator</span><span class="sxs-lookup"><span data-stu-id="cc1bb-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)

- [<span data-ttu-id="cc1bb-215">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="cc1bb-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <span data-ttu-id="cc1bb-216"><a name="Static"></a>Udostępniony klas i członków</span><span class="sxs-lookup"><span data-stu-id="cc1bb-216"><a name="Static"></a> Shared Classes and Members</span></span>  
 <span data-ttu-id="cc1bb-217">Udostępnionego elementu członkowskiego klasy jest właściwość, procedura lub pola, które jest współużytkowana przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="cc1bb-218">Aby zdefiniować udostępnionego elementu członkowskiego:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-218">To define a shared member:</span></span>  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 <span data-ttu-id="cc1bb-219">Aby uzyskać dostęp do udostępnionego elementu członkowskiego, użyj nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 <span data-ttu-id="cc1bb-220">Udostępniony moduły w języku Visual Basic udostępnionego tylko elementy członkowskie i nie można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="cc1bb-221">Udostępniane elementy członkowskie także nie może uzyskać dostępu właściwości nieudostępnione, pola lub metody</span><span class="sxs-lookup"><span data-stu-id="cc1bb-221">Shared members also cannot access non-shared properties, fields or methods</span></span>  
  
 <span data-ttu-id="cc1bb-222">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-222">For more information, see:</span></span>  
  
-   [<span data-ttu-id="cc1bb-223">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="cc1bb-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [<span data-ttu-id="cc1bb-224">Module — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a><span data-ttu-id="cc1bb-225">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="cc1bb-225">Anonymous types</span></span>  
<span data-ttu-id="cc1bb-226">Typy anonimowe umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="cc1bb-227">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="cc1bb-228">Klasa nie ma używać nazwy i zawiera właściwości, które określisz w odwołaniu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="cc1bb-229">Można utworzyć wystąpienia typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="cc1bb-230">Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="cc1bb-231">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="cc1bb-231">Inheritance</span></span>
<span data-ttu-id="cc1bb-232">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa rozszerza i modyfikuje zachowanie, który jest zdefiniowany w innej klasy.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="cc1bb-233">Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*, i nosi nazwę klasy, która dziedziczy tych członków *klasy*.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="cc1bb-234">Jednak wszystkie klasy w Visual Basic niejawnie dziedziczyć <xref:System.Object> klasy, która obsługuje hierarchii klas .NET i udostępnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
>  <span data-ttu-id="cc1bb-235">Visual Basic nie obsługuje wielu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="cc1bb-236">Oznacza to można określić tylko jedną klasę podstawową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="cc1bb-237">Dziedziczenie z klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="cc1bb-238">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-238">By default all classes can be inherited.</span></span> <span data-ttu-id="cc1bb-239">Jednak można określić, czy nie mogą być używane jako klasę podstawową klasy lub utworzyć klasę, która może służyć jako klasę podstawową tylko.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="cc1bb-240">Aby określić, że klasa nie można użyć jako klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="cc1bb-241">Aby określić, że klasa może służyć jako klasę podstawową tylko i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="cc1bb-242">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-242">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-243">Inherits — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [<span data-ttu-id="cc1bb-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="cc1bb-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [<span data-ttu-id="cc1bb-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="cc1bb-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="cc1bb-246">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="cc1bb-246">Overriding members</span></span>
<span data-ttu-id="cc1bb-247">Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie ze swojej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="cc1bb-248">Aby zmienić zachowanie dziedziczony element członkowski, należy go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="cc1bb-249">Oznacza to można zdefiniować nowej implementacji metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="cc1bb-250">Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="cc1bb-251">Modyfikator Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc1bb-251">Visual Basic Modifier</span></span>|<span data-ttu-id="cc1bb-252">Definicja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="cc1bb-253">Możliwym do zastąpienia</span><span class="sxs-lookup"><span data-stu-id="cc1bb-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="cc1bb-254">Umożliwia elementu członkowskiego klasy do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="cc1bb-255">Zastąpienia</span><span class="sxs-lookup"><span data-stu-id="cc1bb-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="cc1bb-256">Zastępuje członka wirtualnego (możliwym do zastąpienia) zdefiniowana w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="cc1bb-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="cc1bb-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="cc1bb-258">Element członkowski zapobiega zastępowaniu klasy dziedziczące.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="cc1bb-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="cc1bb-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="cc1bb-260">Wymaga, aby element członkowski klasy do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="cc1bb-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="cc1bb-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="cc1bb-262">Ukrywa element członkowski dziedziczona z klasy podstawowej</span><span class="sxs-lookup"><span data-stu-id="cc1bb-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="cc1bb-263">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-263">Interfaces</span></span>
<span data-ttu-id="cc1bb-264">Interfejsy, takich jak klasy, zdefiniuj zbiór właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="cc1bb-265">Jednak w przeciwieństwie do klasy, interfejsy nie dostarcza implementacji.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="cc1bb-266">Są implementowane przez klasy i zdefiniowane jako osobne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="cc1bb-267">Interfejs reprezentuje kontraktu, w tym klasy, która implementuje interfejs musi implementować każdego aspektu ten interfejs, dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="cc1bb-268">Aby zdefiniować interfejsu:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="cc1bb-269">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="cc1bb-270">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-270">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-271">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc1bb-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  

- [<span data-ttu-id="cc1bb-272">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [<span data-ttu-id="cc1bb-273">Implements — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a><span data-ttu-id="cc1bb-274">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="cc1bb-274">Generics</span></span>
<span data-ttu-id="cc1bb-275">Klasy, struktury, interfejsy i metody w środowisku .NET mogą obejmować *parametry typu* definiującą typów obiektów, które mogą przechowywać lub użyć.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="cc1bb-276">Najbardziej typowym przykładem typów ogólnych jest kolekcją, w którym można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  

<span data-ttu-id="cc1bb-277">Aby zdefiniować klasy ogólnej:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="cc1bb-278">Można utworzyć wystąpienia klasy generycznej:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="cc1bb-279">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-279">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-280">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="cc1bb-280">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="cc1bb-281">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc1bb-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="cc1bb-282">Delegaty</span><span class="sxs-lookup"><span data-stu-id="cc1bb-282">Delegates</span></span>
 <span data-ttu-id="cc1bb-283">A *delegować* jest typ, który określa podpis metody i można udostępnić odwołanie do dowolnej metody zgodnego podpisu.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="cc1bb-284">Można wywołać (lub wywołać) metoda za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="cc1bb-285">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
>  <span data-ttu-id="cc1bb-286">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="cc1bb-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="cc1bb-287">Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc1bb-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="cc1bb-288">Do utworzenia delegata:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="cc1bb-289">Aby utworzyć odwołanie do metody, która odpowiada podpisu określony na podstawie delegata:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="cc1bb-290">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cc1bb-290">For more information, see:</span></span>

- [<span data-ttu-id="cc1bb-291">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="cc1bb-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)

- [<span data-ttu-id="cc1bb-292">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc1bb-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="cc1bb-293">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="cc1bb-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="cc1bb-294">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc1bb-294">See also</span></span>
 [<span data-ttu-id="cc1bb-295">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc1bb-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
