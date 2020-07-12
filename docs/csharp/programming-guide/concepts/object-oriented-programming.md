---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 83140a9dbd16f60f04f50ba18c71099cdd862f15
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226637"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="45546-102">Programowanie zorientowane obiektowo (C#)</span><span class="sxs-lookup"><span data-stu-id="45546-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="45546-103">Język C# zapewnia pełną obsługę programowania zorientowanego obiektowo, w tym abstrakcję, hermetyzację, dziedziczenie i polimorfizm.</span><span class="sxs-lookup"><span data-stu-id="45546-103">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="45546-104">*Abstrakcja* oznacza ukrycie niepotrzebnych informacji od odbiorców typu.</span><span class="sxs-lookup"><span data-stu-id="45546-104">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="45546-105">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich jest traktowana jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="45546-105">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="45546-106">*Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-106">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="45546-107">*Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, nawet jeśli każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="45546-107">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="45546-108">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="45546-108">Classes and objects</span></span>

<span data-ttu-id="45546-109">*Kategoria warunki i* *obiekt* opisują *Typ* obiektów i *wystąpienia* klas odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="45546-109">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="45546-110">W związku z tym czynność tworzenia obiektu jest nazywana *tworzeniem wystąpień*.</span><span class="sxs-lookup"><span data-stu-id="45546-110">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="45546-111">Korzystając z strategii analogowej, Klasa jest planem, a obiekt jest kompilacją utworzoną z tego planu.</span><span class="sxs-lookup"><span data-stu-id="45546-111">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="45546-112">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="45546-112">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="45546-113">Język C# udostępnia również typy nazywane *strukturami* , które są przydatne, gdy nie potrzebujesz obsługi dziedziczenia lub polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="45546-113">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="45546-114">Aby uzyskać więcej informacji, zobacz [Wybieranie między klasą i strukturą](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span><span class="sxs-lookup"><span data-stu-id="45546-114">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="45546-115">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="45546-115">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="45546-116">Aby uzyskać więcej informacji, zobacz artykuły w słowach kluczowych [klasy](../../language-reference/keywords/class.md) i [struktury](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="45546-116">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="45546-117">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="45546-117">Class members</span></span>

<span data-ttu-id="45546-118">Każda klasa może mieć różne *składowe klasy* , które zawierają właściwości opisujące dane klasy, metody definiujące zachowanie klasy oraz zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="45546-118">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="45546-119">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="45546-119">Properties and fields</span></span>

<span data-ttu-id="45546-120">Pola i właściwości reprezentują informacje, które zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="45546-120">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="45546-121">Pola są podobne do zmiennych, ponieważ mogą być odczytywane lub ustawiane bezpośrednio, zgodnie z odpowiednimi modyfikatorami dostępu.</span><span class="sxs-lookup"><span data-stu-id="45546-121">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="45546-122">Aby zdefiniować pole, do którego można uzyskać dostęp z wystąpień klasy:</span><span class="sxs-lookup"><span data-stu-id="45546-122">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="45546-123">Właściwości mają `get` i `set` metody dostępu, które zapewniają większą kontrolę nad sposobem ustawiania lub zwracania wartości.</span><span class="sxs-lookup"><span data-stu-id="45546-123">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="45546-124">Język C# umożliwia utworzenie prywatnego pola do przechowywania wartości właściwości lub użycie automatycznie wdrożonych właściwości, które tworzą to pole automatycznie w tle i zapewniają podstawową logikę dla procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="45546-124">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="45546-125">Aby zdefiniować zaimplementowaną Właściwość:</span><span class="sxs-lookup"><span data-stu-id="45546-125">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="45546-126">Jeśli trzeba wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, Zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę do przechowywania i pobierania:</span><span class="sxs-lookup"><span data-stu-id="45546-126">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="45546-127">Większość właściwości ma metody lub procedury ustawiające i pobierające wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="45546-127">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="45546-128">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie.</span><span class="sxs-lookup"><span data-stu-id="45546-128">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="45546-129">W języku C# można pominąć `get` `set` metodę lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="45546-129">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="45546-130">Jednak właściwości zaimplementowane domyślnie nie mogą być tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="45546-130">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="45546-131">Właściwości, które są implementowane w trybie tylko do odczytu, można ustawić w konstruktorach klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="45546-131">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="45546-132">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="45546-132">For more information, see:</span></span>

- [<span data-ttu-id="45546-133">Pobierz</span><span class="sxs-lookup"><span data-stu-id="45546-133">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="45546-134">zbiór</span><span class="sxs-lookup"><span data-stu-id="45546-134">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="45546-135">Metody</span><span class="sxs-lookup"><span data-stu-id="45546-135">Methods</span></span>

<span data-ttu-id="45546-136">*Metoda* jest akcją, którą obiekt może wykonać.</span><span class="sxs-lookup"><span data-stu-id="45546-136">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="45546-137">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="45546-137">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="45546-138">Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="45546-138">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="45546-139">Aby przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="45546-139">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="45546-140">W większości przypadków deklaruje metodę w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-140">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="45546-141">Jednak w języku C# obsługiwane są również *metody rozszerzające* , które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-141">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="45546-142">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="45546-142">For more information, see:</span></span>

- [<span data-ttu-id="45546-143">Metody</span><span class="sxs-lookup"><span data-stu-id="45546-143">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="45546-144">Metody rozszerzania</span><span class="sxs-lookup"><span data-stu-id="45546-144">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="45546-145">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="45546-145">Constructors</span></span>

<span data-ttu-id="45546-146">Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="45546-146">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="45546-147">Konstruktory zazwyczaj inicjują elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="45546-147">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="45546-148">Konstruktor można uruchomić tylko raz podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-148">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="45546-149">Ponadto kod w konstruktorze zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie.</span><span class="sxs-lookup"><span data-stu-id="45546-149">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="45546-150">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku innych metod.</span><span class="sxs-lookup"><span data-stu-id="45546-150">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="45546-151">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="45546-151">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="45546-152">Aby uzyskać więcej informacji, zobacz [konstruktory](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="45546-152">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="45546-153">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="45546-153">Finalizers</span></span>

<span data-ttu-id="45546-154">Finalizator jest używany do destruktora wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="45546-154">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="45546-155">W programie .NET moduł zbierający elementy bezużyteczne automatycznie zarządza alokacją i ilością pamięci dla zarządzanych obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45546-155">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="45546-156">Jednak nadal mogą być potrzebne finalizatory do czyszczenia wszystkich niezarządzanych zasobów tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="45546-156">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="45546-157">Może istnieć tylko jeden finalizator dla klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-157">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="45546-158">Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w programie .NET, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="45546-158">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="45546-159">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="45546-159">Events</span></span>

<span data-ttu-id="45546-160">Zdarzenia umożliwiają klasie lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="45546-160">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="45546-161">Klasa, która wysyła (lub podnosi) zdarzenie, jest nazywana *wydawcą* i klasy, które odbierają (lub obsługują) zdarzenie są nazywane *subskrybentami*.</span><span class="sxs-lookup"><span data-stu-id="45546-161">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="45546-162">Aby uzyskać więcej informacji o zdarzeniach, sposobie ich podniesienia i obsłudze, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="45546-162">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="45546-163">Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia](../../language-reference/keywords/event.md) .</span><span class="sxs-lookup"><span data-stu-id="45546-163">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="45546-164">Aby zgłosić zdarzenie, wywołaj delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="45546-164">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="45546-165">Aby subskrybować zdarzenie, użyj `+=` operatora; aby anulować subskrypcję zdarzenia, użyj `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="45546-165">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="45546-166">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="45546-166">Nested classes</span></span>

<span data-ttu-id="45546-167">Klasa zdefiniowana w innej klasie jest nazywana *zagnieżdżoną*.</span><span class="sxs-lookup"><span data-stu-id="45546-167">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="45546-168">Domyślnie Klasa zagnieżdżona jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="45546-168">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="45546-169">Aby utworzyć wystąpienie klasy zagnieżdżonej, użyj nazwy klasy kontenera, po której następuje kropka, a następnie po której następuje nazwa klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="45546-169">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="45546-170">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="45546-170">Access modifiers and access levels</span></span>

<span data-ttu-id="45546-171">Wszystkie klasy i elementy członkowskie klasy mogą określać poziom dostępu udostępniany innym klasom przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="45546-171">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="45546-172">Dostępne są następujące Modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="45546-172">The following access modifiers are available:</span></span>

| <span data-ttu-id="45546-173">Modyfikator języka C#</span><span class="sxs-lookup"><span data-stu-id="45546-173">C# Modifier</span></span> | <span data-ttu-id="45546-174">Definicja</span><span class="sxs-lookup"><span data-stu-id="45546-174">Definition</span></span> |
|--|--|
| [<span data-ttu-id="45546-175">public</span><span class="sxs-lookup"><span data-stu-id="45546-175">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="45546-176">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="45546-176">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="45546-177">użytek</span><span class="sxs-lookup"><span data-stu-id="45546-177">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="45546-178">Do typu lub elementu członkowskiego można uzyskać dostęp tylko w kodzie w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="45546-178">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="45546-179">protected</span><span class="sxs-lookup"><span data-stu-id="45546-179">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="45546-180">Do typu lub elementu członkowskiego można uzyskać dostęp tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="45546-180">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="45546-181">internal</span><span class="sxs-lookup"><span data-stu-id="45546-181">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="45546-182">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="45546-182">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="45546-183">protected internal</span><span class="sxs-lookup"><span data-stu-id="45546-183">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="45546-184">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="45546-184">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="45546-185">private protected</span><span class="sxs-lookup"><span data-stu-id="45546-185">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="45546-186">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą kodu w tej samej klasie lub w klasie pochodnej w ramach zestawu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="45546-186">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="45546-187">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="45546-187">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="45546-188">Tworzenie wystąpień klas</span><span class="sxs-lookup"><span data-stu-id="45546-188">Instantiating classes</span></span>

<span data-ttu-id="45546-189">Aby utworzyć obiekt, należy utworzyć wystąpienie klasy, lub stworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-189">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="45546-190">Po utworzeniu wystąpienia klasy można przypisać wartości do właściwości i pól wystąpienia oraz wywołać metody klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-190">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="45546-191">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="45546-191">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="45546-192">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="45546-192">For more information, see:</span></span>

- [<span data-ttu-id="45546-193">Operator new</span><span class="sxs-lookup"><span data-stu-id="45546-193">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="45546-194">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="45546-194">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="45546-195">Klasy statyczne i składowe</span><span class="sxs-lookup"><span data-stu-id="45546-195">Static Classes and Members</span></span>

<span data-ttu-id="45546-196">Statyczny element członkowski klasy jest właściwością, procedurą lub polem, które są współużytkowane przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="45546-196">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="45546-197">Aby zdefiniować statyczną składową:</span><span class="sxs-lookup"><span data-stu-id="45546-197">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="45546-198">Aby uzyskać dostęp do statycznego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="45546-198">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="45546-199">Klasy statyczne w języku C# mają tylko statyczne elementy członkowskie i nie można tworzyć wystąpień.</span><span class="sxs-lookup"><span data-stu-id="45546-199">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="45546-200">Statyczne elementy członkowskie również nie mogą uzyskać dostępu do właściwości niestatycznych, pól ani metod</span><span class="sxs-lookup"><span data-stu-id="45546-200">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="45546-201">Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="45546-201">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="45546-202">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="45546-202">Anonymous types</span></span>

<span data-ttu-id="45546-203">Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="45546-203">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="45546-204">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="45546-204">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="45546-205">Klasa nie ma użytecznej nazwy i zawiera właściwości określone w deklaracji obiektu.</span><span class="sxs-lookup"><span data-stu-id="45546-205">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="45546-206">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="45546-206">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="45546-207">Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="45546-207">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="45546-208">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="45546-208">Inheritance</span></span>

<span data-ttu-id="45546-209">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie zdefiniowane w innej klasie.</span><span class="sxs-lookup"><span data-stu-id="45546-209">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="45546-210">Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="45546-210">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="45546-211">Jednak wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="45546-211">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="45546-212">Język C# nie obsługuje dziedziczenia wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="45546-212">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="45546-213">Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="45546-213">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="45546-214">Aby dziedziczyć z klasy bazowej:</span><span class="sxs-lookup"><span data-stu-id="45546-214">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="45546-215">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="45546-215">By default all classes can be inherited.</span></span> <span data-ttu-id="45546-216">Można jednak określić, czy Klasa nie może być używana jako klasa bazowa, ani utworzyć klasy, która może być używana tylko jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="45546-216">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="45546-217">Aby określić, że Klasa nie może być używana jako klasa bazowa:</span><span class="sxs-lookup"><span data-stu-id="45546-217">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="45546-218">Aby określić, że Klasa może być używana tylko jako klasa bazowa i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="45546-218">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="45546-219">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="45546-219">For more information, see:</span></span>

- [<span data-ttu-id="45546-220">sealed</span><span class="sxs-lookup"><span data-stu-id="45546-220">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="45546-221">streszczeń</span><span class="sxs-lookup"><span data-stu-id="45546-221">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="45546-222">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="45546-222">Overriding Members</span></span>

<span data-ttu-id="45546-223">Domyślnie Klasa pochodna dziedziczy wszystkich członków z jej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="45546-223">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="45546-224">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="45546-224">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="45546-225">Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="45546-225">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="45546-226">Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="45546-226">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="45546-227">Modyfikator języka C#</span><span class="sxs-lookup"><span data-stu-id="45546-227">C# Modifier</span></span> | <span data-ttu-id="45546-228">Definicja</span><span class="sxs-lookup"><span data-stu-id="45546-228">Definition</span></span> |
|--|--|
| [<span data-ttu-id="45546-229">wirtualnej</span><span class="sxs-lookup"><span data-stu-id="45546-229">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="45546-230">Zezwala na przesłanianie składowej klasy w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="45546-230">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="45546-231">override</span><span class="sxs-lookup"><span data-stu-id="45546-231">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="45546-232">Przesłania element członkowski wirtualny (zastępujący) zdefiniowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="45546-232">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="45546-233">streszczeń</span><span class="sxs-lookup"><span data-stu-id="45546-233">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="45546-234">Wymaga, aby element członkowski klasy był zastępowany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="45546-234">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="45546-235">new, modyfikator</span><span class="sxs-lookup"><span data-stu-id="45546-235">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="45546-236">Ukrywa składową dziedziczoną z klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="45546-236">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="45546-237">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="45546-237">Interfaces</span></span>

<span data-ttu-id="45546-238">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="45546-238">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="45546-239">Ale w przeciwieństwie do klas, interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="45546-239">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="45546-240">Są one implementowane przez klasy i zdefiniowane jako osobne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="45546-240">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="45546-241">Interfejs reprezentuje kontrakt, w którym Klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="45546-241">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="45546-242">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="45546-242">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="45546-243">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="45546-243">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="45546-244">Aby uzyskać więcej informacji, zobacz artykuł Przewodnik programowania dotyczący [interfejsów](../interfaces/index.md) i artykułu referencyjnego języka dla słowa kluczowego [Interface](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="45546-244">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="45546-245">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="45546-245">Generics</span></span>

<span data-ttu-id="45546-246">Klasy, struktury, interfejsy i metody w programie .NET mogą zawierać *parametry typu* , które definiują typy obiektów, które mogą być przechowywane lub używane.</span><span class="sxs-lookup"><span data-stu-id="45546-246">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="45546-247">Najbardziej typowym przykładem typów ogólnych jest kolekcja, w której można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="45546-247">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="45546-248">Aby zdefiniować klasę generyczną:</span><span class="sxs-lookup"><span data-stu-id="45546-248">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="45546-249">Aby utworzyć wystąpienie klasy generycznej:</span><span class="sxs-lookup"><span data-stu-id="45546-249">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="45546-250">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="45546-250">For more information, see:</span></span>

- [<span data-ttu-id="45546-251">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="45546-251">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="45546-252">Typy ogólne — Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="45546-252">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="45546-253">Delegaci</span><span class="sxs-lookup"><span data-stu-id="45546-253">Delegates</span></span>

<span data-ttu-id="45546-254">*Delegat* jest typem, który definiuje sygnaturę metody i może podać odwołanie do dowolnej metody ze zgodną sygnaturą.</span><span class="sxs-lookup"><span data-stu-id="45546-254">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="45546-255">Metodę można wywołać (lub wywołać) za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="45546-255">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="45546-256">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="45546-256">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="45546-257">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="45546-257">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="45546-258">Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="45546-258">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="45546-259">Aby utworzyć delegata:</span><span class="sxs-lookup"><span data-stu-id="45546-259">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="45546-260">Aby utworzyć odwołanie do metody, która jest zgodna z sygnaturą określoną przez delegata:</span><span class="sxs-lookup"><span data-stu-id="45546-260">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
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

<span data-ttu-id="45546-261">Aby uzyskać więcej informacji, zobacz artykuł Przewodnik programowania dotyczący [delegatów](../delegates/index.md) i artykuł referencyjny języka w słowie kluczowym [delegata](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="45546-261">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="45546-262">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45546-262">See also</span></span>

- [<span data-ttu-id="45546-263">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="45546-263">C# Programming Guide</span></span>](../index.md)
