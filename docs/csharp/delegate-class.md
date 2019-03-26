---
title: System.Delegate i `delegate` — słowo kluczowe
description: Więcej informacji na temat klas .NET Framework, które obsługują delegatów oraz sposób mapowania tych — słowo kluczowe "delegowanie".
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 4cf2b113fc9e2c6621f648af7ecb272a42b1f056
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465779"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="be775-103">System.Delegate i `delegate` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="be775-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="be775-104">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="be775-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="be775-105">W tym artykule omówiono klasy w .NET framework, które obsługuje delegatów oraz jak te mapowania `delegate` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="be775-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="be775-106">Definiowanie typów delegowanych</span><span class="sxs-lookup"><span data-stu-id="be775-106">Defining Delegate Types</span></span>

<span data-ttu-id="be775-107">Zacznijmy od słowa kluczowego "delegowanie", ponieważ jest to głównie będzie on potrzebny podczas pracy nad delegatów.</span><span class="sxs-lookup"><span data-stu-id="be775-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="be775-108">Kod, który kompilator generuje, gdy używasz `delegate` — słowo kluczowe będzie zmapowana do wywołania metody, które wywołują członkowie <xref:System.Delegate> i <xref:System.MulticastDelegate> klasy.</span><span class="sxs-lookup"><span data-stu-id="be775-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="be775-109">Należy zdefiniować typ obiektu delegowanego przy użyciu składni, która jest podobna do definiowania podpis metody.</span><span class="sxs-lookup"><span data-stu-id="be775-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="be775-110">Wystarczy dodać `delegate` — słowo kluczowe w definicji.</span><span class="sxs-lookup"><span data-stu-id="be775-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="be775-111">Możemy w dalszym użycie metody List.Sort() jako przykładu.</span><span class="sxs-lookup"><span data-stu-id="be775-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="be775-112">Pierwszym krokiem jest tworzenie typu dla delegata porównania:</span><span class="sxs-lookup"><span data-stu-id="be775-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="be775-113">Kompilator generuje klasę pochodną `System.Delegate` które odpowiadają podpisowi używane (w tym przypadku metoda zwraca liczbę całkowitą, która ma dwa argumenty).</span><span class="sxs-lookup"><span data-stu-id="be775-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="be775-114">Typ delegata jest `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="be775-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="be775-115">`Comparison` Typ delegata jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="be775-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="be775-116">Zobacz szczegółowe informacje na temat typów ogólnych [tutaj](generics.md).</span><span class="sxs-lookup"><span data-stu-id="be775-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="be775-117">Należy zauważyć, że składnia może pojawić się tak, jakby on jest zadeklarowanie zmiennej, ale jest faktycznie deklarowanie *typu*.</span><span class="sxs-lookup"><span data-stu-id="be775-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="be775-118">Można zdefiniować typy delegatów wewnątrz klasy, bezpośrednio w przestrzeni nazw albo nawet w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="be775-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="be775-119">Deklarowanie typów delegatów (lub inne typy) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="be775-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="be775-120">Kompilator generuje również dodawanie i usuwanie programów obsługi dla tego nowego typu, aby klienci tej klasy można dodawać i usuwać metody z wystąpieniem listy wywołań.</span><span class="sxs-lookup"><span data-stu-id="be775-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="be775-121">Kompilator będzie wymuszać, czy podpis metody dodawany lub usuwany pasuje do podpisu przy deklarowaniu metody.</span><span class="sxs-lookup"><span data-stu-id="be775-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="be775-122">Deklarowanie wystąpień obiektów delegowanych</span><span class="sxs-lookup"><span data-stu-id="be775-122">Declaring instances of delegates</span></span>

<span data-ttu-id="be775-123">Po zdefiniowaniu obiektu delegowanego, można utworzyć wystąpienia tego typu.</span><span class="sxs-lookup"><span data-stu-id="be775-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="be775-124">Wszystkie zmienne w, takich jak C#, nie można zadeklarować wystąpień delegata bezpośrednio w przestrzeni nazw lub w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="be775-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="be775-125">Typ zmiennej jest `Comparison<T>`, wcześniej zdefiniowaną typ delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="be775-126">Nazwa zmiennej jest `comparator`.</span><span class="sxs-lookup"><span data-stu-id="be775-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="be775-127">Ten fragment kodu powyżej zadeklarować zmienną członkowską wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="be775-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="be775-128">Można również zadeklarować zmienne delegata, które są zmiennymi lokalnymi lub argumenty do metody.</span><span class="sxs-lookup"><span data-stu-id="be775-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="be775-129">Wywoływanie delegatów</span><span class="sxs-lookup"><span data-stu-id="be775-129">Invoking Delegates</span></span>

<span data-ttu-id="be775-130">Można wywołać metody, które znajdują się na liście wywołanie delegata, przez wywołanie metody delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="be775-131">Wewnątrz `Sort()` metody kod wywoła metodę porównywania, aby określić kolejność, aby umieścić obiekty:</span><span class="sxs-lookup"><span data-stu-id="be775-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="be775-132">W wierszu powyżej kod *wywołuje* metody dołączony do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="be775-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="be775-133">Traktuj zmiennej jako nazwę metody i wywoływać ją za pomocą składni wywołania metody normalne.</span><span class="sxs-lookup"><span data-stu-id="be775-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="be775-134">Ten wiersz kodu sprawia, że niebezpieczne założeń: Nie ma żadnej gwarancji, że element docelowy został dodany do delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="be775-135">Jeśli dołączono żadnych elementów docelowych, spowodowałoby wiersz powyżej `NullReferenceException` zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="be775-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="be775-136">Idiomy używane, aby rozwiązać ten problem, są bardziej skomplikowane niż proste sprawdzanie wartości null i są objęte później w tym [serii](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="be775-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="be775-137">Przypisywanie, dodawanie i usuwanie celów wywołania</span><span class="sxs-lookup"><span data-stu-id="be775-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="be775-138">To, jak jest zdefiniowany typ obiektu delegowanego i jak zadeklarować i wywołana wystąpień delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="be775-139">Deweloperzy, które mają być używane `List.Sort()` metody należy zdefiniować metodę, którego podpis pasuje do definicji typu delegowanego i przypisz je do delegata używany przez metodę sortowania.</span><span class="sxs-lookup"><span data-stu-id="be775-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="be775-140">To przypisanie dodaje metodę do listy wywołań obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="be775-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="be775-141">Załóżmy, że chcesz sortować listę ciągów według ich długości.</span><span class="sxs-lookup"><span data-stu-id="be775-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="be775-142">Porównanie funkcji mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="be775-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="be775-143">Metoda jest zadeklarowany jako metoda prywatna.</span><span class="sxs-lookup"><span data-stu-id="be775-143">The method is declared as a private method.</span></span> <span data-ttu-id="be775-144">Jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="be775-144">That's fine.</span></span> <span data-ttu-id="be775-145">Może nie chcieć tę metodę, aby być częścią interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="be775-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="be775-146">Nadal można ją jako metodę porównywania, gdy dołączony do delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="be775-147">Kod wywołujący ma mieć ta metoda dołączone do listy docelowej obiektu delegowanego i można uzyskać do niego dostęp za pośrednictwem delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="be775-148">Tworzenie tej relacji, przekazując tej metody do `List.Sort()` metody:</span><span class="sxs-lookup"><span data-stu-id="be775-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="be775-149">Należy zauważyć, że nazwa metody jest używana, bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="be775-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="be775-150">Przy użyciu metody jako argument informuje kompilator, aby konwertować odwołanie do metody odwołania, który może służyć jako cel wywołania delegata, a następnie Dołącz tę metodę jako obiekt docelowy wywołania.</span><span class="sxs-lookup"><span data-stu-id="be775-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="be775-151">Możesz również mogło być jawne przez zadeklarowanie zmiennej typu `Comparison<string>` i wykonując przypisania:</span><span class="sxs-lookup"><span data-stu-id="be775-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="be775-152">W którym metoda używany jako cel delegata to metoda małe, jest często używa się używa [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) składni w celu przypisania:</span><span class="sxs-lookup"><span data-stu-id="be775-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="be775-153">Użycie wyrażeń lambda, obiektów docelowych delegata jest bardziej omówione w [później sekcji](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="be775-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="be775-154">W przykładzie Sort() zazwyczaj dołącza metoda pojedynczy element docelowy do delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="be775-155">Jednak obiekty delegata obsługują listy wywołania, które mają wiele metod docelowych dołączony do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="be775-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="be775-156">Klasy delegata i MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="be775-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="be775-157">Obsługa języków opisanych powyżej udostępnia funkcje i pomocy technicznej, które zwykle będą potrzebne do pracy z delegatów.</span><span class="sxs-lookup"><span data-stu-id="be775-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="be775-158">Te funkcje są oparte na dwóch klas w ramach platformy .NET Core: <xref:System.Delegate> i <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="be775-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="be775-159">`System.Delegate` Klasy, a jego pojedynczego bezpośrednich podrzędnych, `System.MulticastDelegate`, zapewniają obsługę framework do tworzenia delegatów, rejestrowanie metod jako elementy docelowe delegowanego i wywołanie wszystkie metody, które są zarejestrowane jako cel delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="be775-160">Co ciekawe `System.Delegate` i `System.MulticastDelegate` klasy nie są same typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="be775-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="be775-161">Zapewniają one podstawę dla wszystkich typów określonego delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="be775-162">Czy ten sam projekt języka procesu obowiązkowe na to, że nie można zadeklarować klasy, który pochodzi z `Delegate` lub `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="be775-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="be775-163">C# Reguł języka zabronić jego używania.</span><span class="sxs-lookup"><span data-stu-id="be775-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="be775-164">Zamiast tego C# kompilator tworzy wystąpienia klasy pochodzącej od `MulticastDelegate` zastosowania C# języka — słowo kluczowe do deklarowania typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="be775-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="be775-165">Ten projekt zawiera korzenie jego pierwszego wydania C# i .NET.</span><span class="sxs-lookup"><span data-stu-id="be775-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="be775-166">Jeden cel dla zespołu projektu było upewnij się, że język przy użyciu delegatów, wymuszane bezpieczeństwo typów.</span><span class="sxs-lookup"><span data-stu-id="be775-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="be775-167">Oznaczało to zapewnienie, że delegaty została wywołana przy użyciu właściwego typu i liczby argumentów.</span><span class="sxs-lookup"><span data-stu-id="be775-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="be775-168">Czas kompilacji i że zwracany typ any został poprawnie wskazane w.</span><span class="sxs-lookup"><span data-stu-id="be775-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="be775-169">Delegaty były częścią wersji .NET 1.0, który był wcześniej typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="be775-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="be775-170">Najlepszym sposobem, aby wymusić bezpieczeństwa tego typu był przez kompilator, aby utworzyć delegata konkretnych klas, które są reprezentowane podpis metody używane.</span><span class="sxs-lookup"><span data-stu-id="be775-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="be775-171">Mimo że nie można bezpośrednio utworzyć klasy pochodne, użyjesz metody zdefiniowane w ramach tych zajęć.</span><span class="sxs-lookup"><span data-stu-id="be775-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="be775-172">Przejdźmy przez najbardziej typowe metody, które będą używane podczas pracy z delegatów.</span><span class="sxs-lookup"><span data-stu-id="be775-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="be775-173">Fakt pierwszym, najważniejszym do zapamiętania jest, że każdy delegat pracujesz z jest tworzony na podstawie `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="be775-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="be775-174">Delegat multiemisji oznacza, że więcej niż jeden cel metoda może być wywoływany podczas wywoływania przez delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="be775-175">Oryginalny projekt jest traktowany jako, różnice między delegatów, gdzie można dołączonych i wywołana metoda tylko jednego obiektu docelowego i delegatów, gdzie można dołączyć i wywołana wielu metod docelowych.</span><span class="sxs-lookup"><span data-stu-id="be775-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="be775-176">Różnica w tym okazało się być mniej przydatne w praktyce niż pierwotnie traktować.</span><span class="sxs-lookup"><span data-stu-id="be775-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="be775-177">Dwoma różnymi klasami zostały już utworzone i zostały w ramach początkowego wydania publicznych.</span><span class="sxs-lookup"><span data-stu-id="be775-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="be775-178">Metody, które będą używane najczęściej z delegatów są `Invoke()` i `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="be775-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="be775-179">`Invoke()` wywoła wszystkie metody, które zostały dołączone do wystąpienia konkretnej pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="be775-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="be775-180">Jak przedstawiono powyżej, zazwyczaj należy wywołać delegatów za pomocą składni wywołania metody na zmiennej delegata.</span><span class="sxs-lookup"><span data-stu-id="be775-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="be775-181">Jak zobaczysz [dalej w tej serii](delegates-patterns.md), istnieją wzorców, które pracują bezpośrednio z tych metod.</span><span class="sxs-lookup"><span data-stu-id="be775-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="be775-182">Teraz, gdy wiesz, składni języka i klas, które obsługują delegatów, Przeanalizujmy jak silnie typizowanych obiektów delegowanych są używane, utworzona i wywoływane.</span><span class="sxs-lookup"><span data-stu-id="be775-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="be775-183">Next</span><span class="sxs-lookup"><span data-stu-id="be775-183">Next</span></span>](delegates-strongly-typed.md)
