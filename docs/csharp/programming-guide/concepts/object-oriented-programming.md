---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 541d1a2581a3241f35fc8478040c007b6581e3b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396684"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="22fd6-102">Programowanie zorientowane obiektowo (C#)</span><span class="sxs-lookup"><span data-stu-id="22fd6-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="22fd6-103">Język C# zapewnia pełną obsługę programowania zorientowanego obiektowo, w tym hermetyzację, dziedziczenie i polimorfizm.</span><span class="sxs-lookup"><span data-stu-id="22fd6-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="22fd6-104">*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich jest traktowana jako pojedyncza jednostka lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="22fd6-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="22fd6-105">*Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="22fd6-106">*Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, nawet jeśli każda klasa implementuje te same właściwości lub metody na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="22fd6-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="22fd6-107">Klasy i obiekty</span><span class="sxs-lookup"><span data-stu-id="22fd6-107">Classes and objects</span></span>

<span data-ttu-id="22fd6-108">*Kategoria warunki i* *obiekt* opisują *Typ* obiektów i *wystąpienia* klas odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="22fd6-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="22fd6-109">W związku z tym czynność tworzenia obiektu jest nazywana *tworzeniem wystąpień*.</span><span class="sxs-lookup"><span data-stu-id="22fd6-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="22fd6-110">Korzystając z strategii analogowej, Klasa jest planem, a obiekt jest kompilacją utworzoną z tego planu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="22fd6-111">Aby zdefiniować klasę:</span><span class="sxs-lookup"><span data-stu-id="22fd6-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="22fd6-112">Język C# udostępnia również typy nazywane *strukturami* , które są przydatne, gdy nie potrzebujesz obsługi dziedziczenia lub polimorfizmu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="22fd6-113">Aby zdefiniować strukturę:</span><span class="sxs-lookup"><span data-stu-id="22fd6-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="22fd6-114">Aby uzyskać więcej informacji, zobacz artykuły w słowach kluczowych [klasy](../../language-reference/keywords/class.md) i [struktury](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="22fd6-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="22fd6-115">Elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="22fd6-115">Class members</span></span>

<span data-ttu-id="22fd6-116">Każda klasa może mieć różne *składowe klasy* , które zawierają właściwości opisujące dane klasy, metody definiujące zachowanie klasy oraz zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.</span><span class="sxs-lookup"><span data-stu-id="22fd6-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="22fd6-117">Właściwości i pola</span><span class="sxs-lookup"><span data-stu-id="22fd6-117">Properties and fields</span></span>

<span data-ttu-id="22fd6-118">Pola i właściwości reprezentują informacje, które zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="22fd6-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="22fd6-119">Pola są podobne do zmiennych, ponieważ mogą być odczytywane lub ustawiane bezpośrednio, zgodnie z odpowiednimi modyfikatorami dostępu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="22fd6-120">Aby zdefiniować pole, do którego można uzyskać dostęp z wystąpień klasy:</span><span class="sxs-lookup"><span data-stu-id="22fd6-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="22fd6-121">Właściwości mają `get` i `set` metody dostępu, które zapewniają większą kontrolę nad sposobem ustawiania lub zwracania wartości.</span><span class="sxs-lookup"><span data-stu-id="22fd6-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="22fd6-122">Język C# umożliwia utworzenie prywatnego pola do przechowywania wartości właściwości lub użycie automatycznie wdrożonych właściwości, które tworzą to pole automatycznie w tle i zapewniają podstawową logikę dla procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="22fd6-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="22fd6-123">Aby zdefiniować zaimplementowaną Właściwość:</span><span class="sxs-lookup"><span data-stu-id="22fd6-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="22fd6-124">Jeśli trzeba wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, Zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę do przechowywania i pobierania:</span><span class="sxs-lookup"><span data-stu-id="22fd6-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="22fd6-125">Większość właściwości ma metody lub procedury ustawiające i pobierające wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="22fd6-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="22fd6-126">Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie.</span><span class="sxs-lookup"><span data-stu-id="22fd6-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="22fd6-127">W języku C# można pominąć `get` `set` metodę lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="22fd6-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="22fd6-128">Jednak właściwości zaimplementowane domyślnie nie mogą być tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="22fd6-129">Właściwości, które są implementowane w trybie tylko do odczytu, można ustawić w konstruktorach klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="22fd6-130">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22fd6-130">For more information, see:</span></span>

- [<span data-ttu-id="22fd6-131">Pobierz</span><span class="sxs-lookup"><span data-stu-id="22fd6-131">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="22fd6-132">set</span><span class="sxs-lookup"><span data-stu-id="22fd6-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="22fd6-133">Metody</span><span class="sxs-lookup"><span data-stu-id="22fd6-133">Methods</span></span>

<span data-ttu-id="22fd6-134">*Metoda* jest akcją, którą obiekt może wykonać.</span><span class="sxs-lookup"><span data-stu-id="22fd6-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="22fd6-135">Aby zdefiniować metodę klasy:</span><span class="sxs-lookup"><span data-stu-id="22fd6-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="22fd6-136">Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="22fd6-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="22fd6-137">Aby przeciążyć metodę:</span><span class="sxs-lookup"><span data-stu-id="22fd6-137">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="22fd6-138">W większości przypadków deklaruje metodę w ramach definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="22fd6-139">Jednak w języku C# obsługiwane są również *metody rozszerzające* , które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="22fd6-140">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22fd6-140">For more information, see:</span></span>

- [<span data-ttu-id="22fd6-141">Metody</span><span class="sxs-lookup"><span data-stu-id="22fd6-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="22fd6-142">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="22fd6-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="22fd6-143">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="22fd6-143">Constructors</span></span>

<span data-ttu-id="22fd6-144">Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="22fd6-145">Konstruktory zazwyczaj inicjują elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="22fd6-146">Konstruktor można uruchomić tylko raz podczas tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="22fd6-147">Ponadto kod w konstruktorze zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie.</span><span class="sxs-lookup"><span data-stu-id="22fd6-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="22fd6-148">Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku innych metod.</span><span class="sxs-lookup"><span data-stu-id="22fd6-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="22fd6-149">Aby zdefiniować konstruktora dla klasy:</span><span class="sxs-lookup"><span data-stu-id="22fd6-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="22fd6-150">Aby uzyskać więcej informacji, zobacz [konstruktory](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="22fd6-151">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="22fd6-151">Finalizers</span></span>

<span data-ttu-id="22fd6-152">Finalizator jest używany do destruktora wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="22fd6-152">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="22fd6-153">W .NET Framework Moduł wyrzucania elementów bezużytecznych automatycznie zarządza alokacją i ilością pamięci dla obiektów zarządzanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22fd6-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="22fd6-154">Jednak nadal mogą być potrzebne finalizatory do czyszczenia wszystkich niezarządzanych zasobów tworzonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="22fd6-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="22fd6-155">Może istnieć tylko jeden finalizator dla klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-155">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="22fd6-156">Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="22fd6-157">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="22fd6-157">Events</span></span>

<span data-ttu-id="22fd6-158">Zdarzenia umożliwiają klasie lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="22fd6-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="22fd6-159">Klasa, która wysyła (lub podnosi) zdarzenie, jest nazywana *wydawcą* i klasy, które odbierają (lub obsługują) zdarzenie są nazywane *subskrybentami*.</span><span class="sxs-lookup"><span data-stu-id="22fd6-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="22fd6-160">Aby uzyskać więcej informacji o zdarzeniach, sposobie ich podniesienia i obsłudze, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="22fd6-161">Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia](../../language-reference/keywords/event.md) .</span><span class="sxs-lookup"><span data-stu-id="22fd6-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="22fd6-162">Aby zgłosić zdarzenie, wywołaj delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="22fd6-162">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="22fd6-163">Aby subskrybować zdarzenie, użyj `+=` operatora; aby anulować subskrypcję zdarzenia, użyj `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="22fd6-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="22fd6-164">Klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="22fd6-164">Nested classes</span></span>

<span data-ttu-id="22fd6-165">Klasa zdefiniowana w innej klasie jest nazywana *zagnieżdżoną*.</span><span class="sxs-lookup"><span data-stu-id="22fd6-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="22fd6-166">Domyślnie Klasa zagnieżdżona jest prywatna.</span><span class="sxs-lookup"><span data-stu-id="22fd6-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="22fd6-167">Aby utworzyć wystąpienie klasy zagnieżdżonej, użyj nazwy klasy kontenera, po której następuje kropka, a następnie po której następuje nazwa klasy zagnieżdżonej:</span><span class="sxs-lookup"><span data-stu-id="22fd6-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="22fd6-168">Modyfikatory dostępu i poziomy dostępu</span><span class="sxs-lookup"><span data-stu-id="22fd6-168">Access modifiers and access levels</span></span>

<span data-ttu-id="22fd6-169">Wszystkie klasy i elementy członkowskie klasy mogą określać poziom dostępu udostępniany innym klasom przy użyciu *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="22fd6-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="22fd6-170">Dostępne są następujące Modyfikatory dostępu:</span><span class="sxs-lookup"><span data-stu-id="22fd6-170">The following access modifiers are available:</span></span>

| <span data-ttu-id="22fd6-171">Modyfikator języka C#</span><span class="sxs-lookup"><span data-stu-id="22fd6-171">C# Modifier</span></span> | <span data-ttu-id="22fd6-172">Definicja</span><span class="sxs-lookup"><span data-stu-id="22fd6-172">Definition</span></span> |
|--|--|
| [<span data-ttu-id="22fd6-173">public</span><span class="sxs-lookup"><span data-stu-id="22fd6-173">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="22fd6-174">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="22fd6-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="22fd6-175">private</span><span class="sxs-lookup"><span data-stu-id="22fd6-175">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="22fd6-176">Do typu lub elementu członkowskiego można uzyskać dostęp tylko w kodzie w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="22fd6-176">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="22fd6-177">protected</span><span class="sxs-lookup"><span data-stu-id="22fd6-177">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="22fd6-178">Do typu lub elementu członkowskiego można uzyskać dostęp tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="22fd6-179">internal</span><span class="sxs-lookup"><span data-stu-id="22fd6-179">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="22fd6-180">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="22fd6-181">protected internal</span><span class="sxs-lookup"><span data-stu-id="22fd6-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="22fd6-182">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="22fd6-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="22fd6-183">private protected</span><span class="sxs-lookup"><span data-stu-id="22fd6-183">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="22fd6-184">Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą kodu w tej samej klasie lub w klasie pochodnej w ramach zestawu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="22fd6-185">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="22fd6-186">Tworzenie wystąpień klas</span><span class="sxs-lookup"><span data-stu-id="22fd6-186">Instantiating classes</span></span>

<span data-ttu-id="22fd6-187">Aby utworzyć obiekt, należy utworzyć wystąpienie klasy, lub stworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="22fd6-188">Po utworzeniu wystąpienia klasy można przypisać wartości do właściwości i pól wystąpienia oraz wywołać metody klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="22fd6-189">Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatorów obiektów:</span><span class="sxs-lookup"><span data-stu-id="22fd6-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="22fd6-190">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22fd6-190">For more information, see:</span></span>

- [<span data-ttu-id="22fd6-191">Operator new</span><span class="sxs-lookup"><span data-stu-id="22fd6-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="22fd6-192">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="22fd6-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="22fd6-193">Klasy statyczne i składowe</span><span class="sxs-lookup"><span data-stu-id="22fd6-193">Static Classes and Members</span></span>

<span data-ttu-id="22fd6-194">Statyczny element członkowski klasy jest właściwością, procedurą lub polem, które są współużytkowane przez wszystkie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="22fd6-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="22fd6-195">Aby zdefiniować statyczną składową:</span><span class="sxs-lookup"><span data-stu-id="22fd6-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="22fd6-196">Aby uzyskać dostęp do statycznego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:</span><span class="sxs-lookup"><span data-stu-id="22fd6-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="22fd6-197">Klasy statyczne w języku C# mają tylko statyczne elementy członkowskie i nie można tworzyć wystąpień.</span><span class="sxs-lookup"><span data-stu-id="22fd6-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="22fd6-198">Statyczne elementy członkowskie również nie mogą uzyskać dostępu do właściwości niestatycznych, pól ani metod</span><span class="sxs-lookup"><span data-stu-id="22fd6-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="22fd6-199">Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="22fd6-200">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="22fd6-200">Anonymous types</span></span>

<span data-ttu-id="22fd6-201">Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="22fd6-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="22fd6-202">Zamiast tego kompilator generuje klasę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="22fd6-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="22fd6-203">Klasa nie ma użytecznej nazwy i zawiera właściwości określone w deklaracji obiektu.</span><span class="sxs-lookup"><span data-stu-id="22fd6-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="22fd6-204">Aby utworzyć wystąpienie typu anonimowego:</span><span class="sxs-lookup"><span data-stu-id="22fd6-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="22fd6-205">Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="22fd6-206">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="22fd6-206">Inheritance</span></span>

<span data-ttu-id="22fd6-207">Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie zdefiniowane w innej klasie.</span><span class="sxs-lookup"><span data-stu-id="22fd6-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="22fd6-208">Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*.</span><span class="sxs-lookup"><span data-stu-id="22fd6-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="22fd6-209">Jednak wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="22fd6-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="22fd6-210">Język C# nie obsługuje dziedziczenia wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="22fd6-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="22fd6-211">Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="22fd6-212">Aby dziedziczyć z klasy bazowej:</span><span class="sxs-lookup"><span data-stu-id="22fd6-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="22fd6-213">Domyślnie wszystkie klasy mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="22fd6-213">By default all classes can be inherited.</span></span> <span data-ttu-id="22fd6-214">Można jednak określić, czy Klasa nie może być używana jako klasa bazowa, ani utworzyć klasy, która może być używana tylko jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="22fd6-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="22fd6-215">Aby określić, że Klasa nie może być używana jako klasa bazowa:</span><span class="sxs-lookup"><span data-stu-id="22fd6-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="22fd6-216">Aby określić, że Klasa może być używana tylko jako klasa bazowa i nie można utworzyć wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="22fd6-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="22fd6-217">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22fd6-217">For more information, see:</span></span>

- [<span data-ttu-id="22fd6-218">sealed</span><span class="sxs-lookup"><span data-stu-id="22fd6-218">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="22fd6-219">abstract</span><span class="sxs-lookup"><span data-stu-id="22fd6-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="22fd6-220">Zastępowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="22fd6-220">Overriding Members</span></span>

<span data-ttu-id="22fd6-221">Domyślnie Klasa pochodna dziedziczy wszystkich członków z jej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="22fd6-222">Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić.</span><span class="sxs-lookup"><span data-stu-id="22fd6-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="22fd6-223">Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="22fd6-224">Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="22fd6-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="22fd6-225">Modyfikator języka C#</span><span class="sxs-lookup"><span data-stu-id="22fd6-225">C# Modifier</span></span> | <span data-ttu-id="22fd6-226">Definicja</span><span class="sxs-lookup"><span data-stu-id="22fd6-226">Definition</span></span> |
|--|--|
| [<span data-ttu-id="22fd6-227">virtual</span><span class="sxs-lookup"><span data-stu-id="22fd6-227">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="22fd6-228">Zezwala na przesłanianie składowej klasy w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-228">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="22fd6-229">override</span><span class="sxs-lookup"><span data-stu-id="22fd6-229">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="22fd6-230">Przesłania element członkowski wirtualny (zastępujący) zdefiniowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-230">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="22fd6-231">abstract</span><span class="sxs-lookup"><span data-stu-id="22fd6-231">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="22fd6-232">Wymaga, aby element członkowski klasy był zastępowany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="22fd6-232">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="22fd6-233">new, modyfikator</span><span class="sxs-lookup"><span data-stu-id="22fd6-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="22fd6-234">Ukrywa składową dziedziczoną z klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="22fd6-234">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="22fd6-235">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="22fd6-235">Interfaces</span></span>

<span data-ttu-id="22fd6-236">Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="22fd6-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="22fd6-237">Ale w przeciwieństwie do klas, interfejsy nie zapewniają implementacji.</span><span class="sxs-lookup"><span data-stu-id="22fd6-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="22fd6-238">Są one implementowane przez klasy i zdefiniowane jako osobne jednostki z klas.</span><span class="sxs-lookup"><span data-stu-id="22fd6-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="22fd6-239">Interfejs reprezentuje kontrakt, w którym Klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="22fd6-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="22fd6-240">Aby zdefiniować interfejs:</span><span class="sxs-lookup"><span data-stu-id="22fd6-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="22fd6-241">Aby zaimplementować interfejs w klasie:</span><span class="sxs-lookup"><span data-stu-id="22fd6-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="22fd6-242">Aby uzyskać więcej informacji, zobacz artykuł Przewodnik programowania dotyczący [interfejsów](../interfaces/index.md) i artykułu referencyjnego języka dla słowa kluczowego [Interface](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="22fd6-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="22fd6-243">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="22fd6-243">Generics</span></span>

<span data-ttu-id="22fd6-244">Klasy, struktury, interfejsy i metody w .NET Framework mogą zawierać *parametry typu* , które definiują typy obiektów, które mogą być przechowywane lub używane.</span><span class="sxs-lookup"><span data-stu-id="22fd6-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="22fd6-245">Najbardziej typowym przykładem typów ogólnych jest kolekcja, w której można określić typ obiektów, które mają być przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="22fd6-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="22fd6-246">Aby zdefiniować klasę generyczną:</span><span class="sxs-lookup"><span data-stu-id="22fd6-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="22fd6-247">Aby utworzyć wystąpienie klasy generycznej:</span><span class="sxs-lookup"><span data-stu-id="22fd6-247">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="22fd6-248">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="22fd6-248">For more information, see:</span></span>

- [<span data-ttu-id="22fd6-249">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="22fd6-249">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="22fd6-250">Typy ogólne — Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="22fd6-250">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="22fd6-251">Delegaty</span><span class="sxs-lookup"><span data-stu-id="22fd6-251">Delegates</span></span>

<span data-ttu-id="22fd6-252">*Delegat* jest typem, który definiuje sygnaturę metody i może podać odwołanie do dowolnej metody ze zgodną sygnaturą.</span><span class="sxs-lookup"><span data-stu-id="22fd6-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="22fd6-253">Metodę można wywołać (lub wywołać) za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="22fd6-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="22fd6-254">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="22fd6-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="22fd6-255">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="22fd6-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="22fd6-256">Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="22fd6-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="22fd6-257">Aby utworzyć delegata:</span><span class="sxs-lookup"><span data-stu-id="22fd6-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="22fd6-258">Aby utworzyć odwołanie do metody, która jest zgodna z sygnaturą określoną przez delegata:</span><span class="sxs-lookup"><span data-stu-id="22fd6-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="22fd6-259">Aby uzyskać więcej informacji, zobacz artykuł Przewodnik programowania dotyczący [delegatów](../delegates/index.md) i artykuł referencyjny języka w słowie kluczowym [delegata](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="22fd6-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="22fd6-260">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22fd6-260">See also</span></span>

- [<span data-ttu-id="22fd6-261">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="22fd6-261">C# Programming Guide</span></span>](../index.md)
