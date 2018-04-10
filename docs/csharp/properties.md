---
title: Właściwości
description: Dowiedz się więcej o języku C# właściwości, które obejmują funkcje sprawdzania poprawności, obliczana wartości, obliczanie leniwe i zmienić właściwości powiadomienia.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 05e51d527dc3c05301fc85d7717c751dc46bf9fa
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="properties"></a><span data-ttu-id="992fe-104">Właściwości</span><span class="sxs-lookup"><span data-stu-id="992fe-104">Properties</span></span>

<span data-ttu-id="992fe-105">Właściwości są pierwszej klasie obywateli w języku C#.</span><span class="sxs-lookup"><span data-stu-id="992fe-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="992fe-106">Język definiuje składnię, która umożliwia deweloperom pisanie kodu, który dokładnie odzwierciedla cele ich projektu.</span><span class="sxs-lookup"><span data-stu-id="992fe-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="992fe-107">Właściwości przypominają pola, gdy są one używane.</span><span class="sxs-lookup"><span data-stu-id="992fe-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="992fe-108">Jednak w przeciwieństwie do pola, właściwości są implementowane przy użyciu metody dostępu definiujące instrukcje wykonywane, gdy właściwość jest dostępne lub przypisany.</span><span class="sxs-lookup"><span data-stu-id="992fe-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="992fe-109">Składnia właściwości</span><span class="sxs-lookup"><span data-stu-id="992fe-109">Property Syntax</span></span>

<span data-ttu-id="992fe-110">Składnia właściwości jest stanowi naturalne rozszerzenie do pól.</span><span class="sxs-lookup"><span data-stu-id="992fe-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="992fe-111">Pole określa lokalizację magazynu:</span><span class="sxs-lookup"><span data-stu-id="992fe-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-112">Definicja właściwości zawiera deklaracje dla `get` i `set` dostępu, która pobiera i przypisuje wartość tej właściwości:</span><span class="sxs-lookup"><span data-stu-id="992fe-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-113">Składnia pokazanym powyżej jest *automatycznie właściwości* składni.</span><span class="sxs-lookup"><span data-stu-id="992fe-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="992fe-114">Kompilator generuje lokalizację przechowywania dla pola, które wykonuje kopię zapasową właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="992fe-115">Kompilator implementuje również treści `get` i `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="992fe-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="992fe-116">Czasami należy zainicjować właściwość na wartość inną niż domyślna dla jego typu.</span><span class="sxs-lookup"><span data-stu-id="992fe-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="992fe-117">C# umożliwia który przez ustawienie wartości nawiasem zamykającym dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="992fe-118">Możesz wybrać wartość początkową `FirstName` właściwość jako ciąg pusty zamiast `null`.</span><span class="sxs-lookup"><span data-stu-id="992fe-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="992fe-119">Należy wprowadzić ten w sposób przedstawiony poniżej:</span><span class="sxs-lookup"><span data-stu-id="992fe-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-120">Jest to najbardziej przydatny w przypadku właściwości tylko do odczytu, jak można zauważyć w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="992fe-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="992fe-121">Istnieje także możliwość zdefiniowania magazynu użytkownika, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="992fe-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-122">Jeśli implementacja właściwości jest jedno wyrażenie, możesz użyć *zabudowanych wyrażenia elementów członkowskich* metody pobierającej lub ustawiającej:</span><span class="sxs-lookup"><span data-stu-id="992fe-122">When a property implementation is a single expression, you can use *expression-bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-123">Tej składni uproszczoną będą używane, jeśli to możliwe, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="992fe-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="992fe-124">Definicja właściwości pokazanym powyżej jest właściwością odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="992fe-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="992fe-125">Zwróć uwagę, słowo kluczowe `value` w metody dostępu set.</span><span class="sxs-lookup"><span data-stu-id="992fe-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="992fe-126">`set` Akcesor zawsze ma jeden parametr o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="992fe-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="992fe-127">`get` Akcesora musi zwracać wartość do przekonwertowania na typ właściwości (`string` w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="992fe-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="992fe-128">To podstawy składni.</span><span class="sxs-lookup"><span data-stu-id="992fe-128">That's the basics of the syntax.</span></span> <span data-ttu-id="992fe-129">Istnieje wiele różnych odmiany, które obsługują szereg idioms inny projekt.</span><span class="sxs-lookup"><span data-stu-id="992fe-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="992fe-130">Umożliwia Eksplorowanie te i Dowiedz się opcje Składnia dla każdego.</span><span class="sxs-lookup"><span data-stu-id="992fe-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="992fe-131">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="992fe-131">Scenarios</span></span>

<span data-ttu-id="992fe-132">Powyższych przykładach pokazano, co najprostszym przypadków definicji właściwości: właściwości odczytu / zapisu o nie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="992fe-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="992fe-133">Pisanie kodu mają w `get` i `set` metody dostępu, możesz utworzyć wiele różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="992fe-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="992fe-134">Walidacja</span><span class="sxs-lookup"><span data-stu-id="992fe-134">Validation</span></span>

<span data-ttu-id="992fe-135">Możesz pisać kod `set` dostępu, aby upewnić się, czy wartości reprezentowane przez właściwość zawsze są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="992fe-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="992fe-136">Na przykład, załóżmy, że jedną regułę `Person` klasy jest, że nazwa nie może być puste lub biały znak.</span><span class="sxs-lookup"><span data-stu-id="992fe-136">For example, suppose one rule for the `Person` class is that the name cannot be blank or white space.</span></span> <span data-ttu-id="992fe-137">Czy zapisz ją w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="992fe-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-138">W powyższym przykładzie wymusza zasadę czy imię nie może być puste lub biały znak.</span><span class="sxs-lookup"><span data-stu-id="992fe-138">The example above enforces the rule that the first name must not be blank or white space.</span></span> <span data-ttu-id="992fe-139">Jeśli zapisuje dewelopera</span><span class="sxs-lookup"><span data-stu-id="992fe-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="992fe-140">Przypisanie zgłasza `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="992fe-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="992fe-141">Ponieważ metodą dostępu set właściwości musi mieć zwracanego typu void, należy włączyć raportowanie błędów metody dostępu set przez Zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="992fe-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="992fe-142">To jest prostym przypadku weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="992fe-142">That is a simple case of validation.</span></span> <span data-ttu-id="992fe-143">Można rozszerzyć tej samej składni na niczego wymagane w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="992fe-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="992fe-144">Sprawdź relacje między inne właściwości lub sprawdzania poprawności żadnych warunków zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="992fe-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="992fe-145">Wszystkie prawidłowe C# instrukcje są prawidłowe w akcesor właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="992fe-146">tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="992fe-146">Read-only</span></span>

<span data-ttu-id="992fe-147">Do tego momentu wszystkich przejrzanych definicji właściwości są właściwości odczytu/zapisu z metod dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="992fe-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="992fe-148">To nie jest jedyną poprawną ułatwień dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="992fe-149">Można utworzyć właściwości tylko do odczytu, lub zapewniają różne ułatwień dostępu w zestawie i metody dostępu get.</span><span class="sxs-lookup"><span data-stu-id="992fe-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="992fe-150">Załóżmy, że Twoje `Person` klasy należy włączyć tylko zmiana wartości `FirstName` właściwości z innych metod tej klasy.</span><span class="sxs-lookup"><span data-stu-id="992fe-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="992fe-151">Możesz podać metody dostępu set `private` dostępności zamiast `public`:</span><span class="sxs-lookup"><span data-stu-id="992fe-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-152">Teraz `FirstName` właściwości są dostępne z kodu, ale można go przypisać tylko z innego kodu w `Person` klasy.</span><span class="sxs-lookup"><span data-stu-id="992fe-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="992fe-153">Można dodać żadnych modyfikator dostępu ograniczające albo zestaw lub metody dostępu get.</span><span class="sxs-lookup"><span data-stu-id="992fe-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="992fe-154">Wszelkie modyfikator dostępu umieszczony na poszczególnych akcesora musi być bardziej ograniczone niż modyfikatora dostępu w definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="992fe-155">Powyższe jest dozwolony ponieważ `FirstName` właściwość jest `public`, ale set jest `private`.</span><span class="sxs-lookup"><span data-stu-id="992fe-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="992fe-156">Nie można deklarować `private` właściwości o `public` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="992fe-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="992fe-157">Deklaracje właściwości również mogą być deklarowane `protected`, `internal`, `protected internal`, `private protected` lub nawet `private`.</span><span class="sxs-lookup"><span data-stu-id="992fe-157">Property declarations can also be declared `protected`, `internal`, `protected internal`, `private protected` or even `private`.</span></span>   

<span data-ttu-id="992fe-158">Jest również prawne do umieszczenia na bardziej restrykcyjne modyfikator `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="992fe-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="992fe-159">Na przykład można mieć `public` właściwości, ograniczając jednocześnie `get` metody dostępu `private`.</span><span class="sxs-lookup"><span data-stu-id="992fe-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="992fe-160">W tym scenariuszu rzadko odbywa się w praktyce.</span><span class="sxs-lookup"><span data-stu-id="992fe-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="992fe-161">Można również ograniczyć modyfikacji właściwości, dzięki czemu można ustawić tylko w konstruktorze lub inicjatorze właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="992fe-162">Można zmodyfikować `Person` klasy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="992fe-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-163">Ta funkcja jest najczęściej używana do inicjowania kolekcji, które są dostępne jako właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="992fe-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="992fe-164">Właściwości obliczanej</span><span class="sxs-lookup"><span data-stu-id="992fe-164">Computed Properties</span></span>

<span data-ttu-id="992fe-165">Właściwość nie trzeba po prostu zwrócić wartość pola elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="992fe-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="992fe-166">Można utworzyć właściwości, które zwracają obliczoną wartość.</span><span class="sxs-lookup"><span data-stu-id="992fe-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="992fe-167">Umożliwia rozwijanie `Person` obiektu do zwrócenia pełną nazwę, obliczone przez łączenie imiona i nazwiska:</span><span class="sxs-lookup"><span data-stu-id="992fe-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="992fe-168">Przykład powyżej używa [ciągu interpolacji](../csharp/language-reference/tokens/interpolated.md) funkcję, aby utworzyć ciąg sformatowany dla pełnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="992fe-168">The example above uses the [string interpolation](../csharp/language-reference/tokens/interpolated.md) feature to create the formatted string for the full name.</span></span>

<span data-ttu-id="992fe-169">Można również użyć *zabudowanych wyrażenia elementów członkowskich*, który zapewnia bardziej zwięzły sposób utworzyć obliczone `FullName` właściwości:</span><span class="sxs-lookup"><span data-stu-id="992fe-169">You can also use *expression-bodied members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="992fe-170">*Członkowie zabudowanych wyrażenie* użyj *wyrażenia lambda* składni w celu zdefiniowania metody, która zawiera jedno wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="992fe-170">*Expression-bodied members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="992fe-171">W tym miejscu tego wyrażenia zwraca pełną nazwę dla obiekt osoby.</span><span class="sxs-lookup"><span data-stu-id="992fe-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="992fe-172">Właściwości obliczane opóźnione</span><span class="sxs-lookup"><span data-stu-id="992fe-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="992fe-173">Można mieszać pojęcie właściwości obliczanej z magazynem i utworzyć *opóźnieniem obliczone właściwości*.</span><span class="sxs-lookup"><span data-stu-id="992fe-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="992fe-174">Na przykład można zaktualizować `FullName` właściwości tak, aby tylko ciągu formatowania wystąpił uzyskiwał został po raz pierwszy:</span><span class="sxs-lookup"><span data-stu-id="992fe-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="992fe-175">Powyższy kod zawiera usterkę, mimo że.</span><span class="sxs-lookup"><span data-stu-id="992fe-175">The above code contains a bug though.</span></span> <span data-ttu-id="992fe-176">Jeśli kod aktualizuje wartość albo `FirstName` lub `LastName` właściwości, wcześniej ocenionych `fullName` pole jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="992fe-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="992fe-177">Musisz zaktualizować `set` metod dostępu `FirstName` i `LastName` właściwości, aby `fullName` pola jest obliczane ponownie:</span><span class="sxs-lookup"><span data-stu-id="992fe-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="992fe-178">Wynikiem tej wersji ostatecznej `FullName` właściwość tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="992fe-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="992fe-179">Jeśli poprzednio obliczonej wersji jest prawidłowy, jest używany.</span><span class="sxs-lookup"><span data-stu-id="992fe-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="992fe-180">Jeśli inna zmiana stanu unieważnia poprzednio obliczonej wersji, zostaną obliczone go ponownie.</span><span class="sxs-lookup"><span data-stu-id="992fe-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="992fe-181">Deweloperzy korzystający z tej klasy nie trzeba znać szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="992fe-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="992fe-182">Żadna z tych zmian wewnętrzny wpływa na użycie obiektu osoby.</span><span class="sxs-lookup"><span data-stu-id="992fe-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="992fe-183">To klucza Przyczyna przy użyciu właściwości do udostępnienia danych elementów członkowskich obiektu.</span><span class="sxs-lookup"><span data-stu-id="992fe-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="992fe-184">INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="992fe-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="992fe-185">Końcowe scenariusz, w których należy napisać kod w metodzie dostępu właściwości służy do obsługi `INotifyPropertyChanged` interfejs używany do powiadamiania klientów powiązania danych, które wartość została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="992fe-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="992fe-186">Po zmianie wartości właściwości obiektu zgłasza `PropertyChanged` zdarzeń, aby wskazać zmianę.</span><span class="sxs-lookup"><span data-stu-id="992fe-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="992fe-187">Powiązanie bibliotek, danych z kolei aktualizacji wyświetlanych elementów oparte na tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="992fe-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="992fe-188">Poniższy kod przedstawia sposób czy implementuje `INotifyPropertyChanged` dla `FirstName` właściwości tej klasy osoby.</span><span class="sxs-lookup"><span data-stu-id="992fe-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="992fe-189">`?.` Operator jest nazywany *null operator warunkowy*.</span><span class="sxs-lookup"><span data-stu-id="992fe-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="992fe-190">Sprawdza odwołanie o wartości null przed obliczeniem po prawej stronie operatora.</span><span class="sxs-lookup"><span data-stu-id="992fe-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="992fe-191">W rezultacie jest to, że jeśli nie ma żadnych subskrybentów `PropertyChanged` zdarzeń, kod, aby zgłosić zdarzenie nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="992fe-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="992fe-192">Go spowoduje zgłoszenie `NullReferenceException` bez to w takim przypadku Sprawdź.</span><span class="sxs-lookup"><span data-stu-id="992fe-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="992fe-193">Przejrzyj stronę [ `events` ](delegates-events.md) więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="992fe-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="992fe-194">W tym przykładzie również używa nowego `nameof` operatora konwersji z symbol nazwa właściwości jego reprezentacja tekstowa.</span><span class="sxs-lookup"><span data-stu-id="992fe-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="992fe-195">Przy użyciu `nameof` może zmniejszyć liczbę błędów, gdzie ma została błędnie wpisana nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="992fe-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="992fe-196">Ponownie, to przykładem jest przypadek, w którym można napisać kod w metod dostępu do sieci na potrzeby obsługi scenariuszy, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="992fe-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="992fe-197">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="992fe-197">Summing up</span></span>

<span data-ttu-id="992fe-198">Właściwości są formę inteligentne pola w klasie lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="992fe-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="992fe-199">Z poza obiekt, pojawią się one takich jak pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="992fe-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="992fe-200">Jednak właściwości można zaimplementować korzystanie z palety pełnej funkcjonalności C#.</span><span class="sxs-lookup"><span data-stu-id="992fe-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="992fe-201">Możesz podać sprawdzania poprawności, różnych ułatwień dostępu, obliczanie leniwe lub żadnych wymagań dotyczących scenariuszy, należy.</span><span class="sxs-lookup"><span data-stu-id="992fe-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
