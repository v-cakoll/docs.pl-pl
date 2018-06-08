---
title: System.Delegate i `delegate` — słowo kluczowe
description: Więcej informacji na temat klas w programie .NET Framework, które obsługują delegatów oraz sposobu mapowania tych — słowo kluczowe "delegowanie".
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 39dca1053f87a5059bdc60f8b722091ba991cbd5
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827303"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="af36c-103">System.Delegate i `delegate` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="af36c-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="af36c-104">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="af36c-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="af36c-105">W tym artykule opisano klas w programie .NET framework, które obsługują delegatów, oraz sposobu te mapowania `delegate` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="af36c-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="af36c-106">Definiowanie typów delegata</span><span class="sxs-lookup"><span data-stu-id="af36c-106">Defining Delegate Types</span></span>

<span data-ttu-id="af36c-107">Zacznijmy pomocą słowa kluczowego "delegowanie", ponieważ jest to przede wszystkim co będzie używać podczas pracy z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="af36c-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="af36c-108">Kod generowany przez kompilator, korzystając z `delegate` — słowo kluczowe przypisze do wywołania metody, które wywołują członkami <xref:System.Delegate> i <xref:System.MulticastDelegate> klasy.</span><span class="sxs-lookup"><span data-stu-id="af36c-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="af36c-109">Należy zdefiniować typem obiektu delegowanego przy użyciu składni, która jest podobna do definiowania podpis metody.</span><span class="sxs-lookup"><span data-stu-id="af36c-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="af36c-110">Możesz dodać `delegate` — słowo kluczowe w definicji.</span><span class="sxs-lookup"><span data-stu-id="af36c-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="af36c-111">Przejdź w naszym przykładzie przy użyciu metody List.Sort().</span><span class="sxs-lookup"><span data-stu-id="af36c-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="af36c-112">Pierwszym krokiem jest tworzenie typu dla delegata porównania:</span><span class="sxs-lookup"><span data-stu-id="af36c-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="af36c-113">Kompilator generuje klasę pochodzącą od `System.Delegate` odpowiadającego podpis używany (w tym przypadku metoda zwraca liczbę całkowitą, która ma dwa argumenty).</span><span class="sxs-lookup"><span data-stu-id="af36c-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="af36c-114">Ten delegat jest `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="af36c-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="af36c-115">`Comparison` Typ delegata jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="af36c-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="af36c-116">Szczegółowe informacje na ogólne można znaleźć [tutaj](generics.md).</span><span class="sxs-lookup"><span data-stu-id="af36c-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="af36c-117">Należy zauważyć, że składnia może pojawić się tak, jakby jest deklarowanie zmiennej, ale faktycznie jest deklarowanie *typu*.</span><span class="sxs-lookup"><span data-stu-id="af36c-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="af36c-118">Można określić typy delegatów wewnątrz klasy, bezpośrednio w przestrzeni nazw, a nawet w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="af36c-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="af36c-119">Deklarowanie typów delegata (lub innego typu) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="af36c-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="af36c-120">Kompilator generuje również dodawanie i usuwanie programów obsługi dla tego nowego typu, aby klienci tej klasy można dodać i usunąć z wystąpienia listy wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="af36c-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="af36c-121">Kompilator będzie wymuszać zgodność podpisu przy deklarowaniu metody podpis metody jest dodany lub usunięty.</span><span class="sxs-lookup"><span data-stu-id="af36c-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="af36c-122">Deklarowanie wystąpień obiektów delegowanych</span><span class="sxs-lookup"><span data-stu-id="af36c-122">Declaring instances of delegates</span></span>

<span data-ttu-id="af36c-123">Po zdefiniowaniu delegata, można utworzyć wystąpienia tego typu.</span><span class="sxs-lookup"><span data-stu-id="af36c-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="af36c-124">Podobnie jak wszystkie zmienne w języku C# nie można zadeklarować obiektu delegowanego wystąpień bezpośrednio w przestrzeni nazw lub w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="af36c-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="af36c-125">Typ zmiennej jest `Comparison<T>`, typ delegata zdefiniowanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="af36c-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="af36c-126">Nazwa zmiennej jest `comparator`.</span><span class="sxs-lookup"><span data-stu-id="af36c-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="af36c-127">Ten fragment kodu powyżej zadeklarować zmiennej członkowskiej wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="af36c-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="af36c-128">Można również zadeklarować zmienne delegata, które są zmienne lokalne lub argumenty do metod.</span><span class="sxs-lookup"><span data-stu-id="af36c-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="af36c-129">Wywoływanie delegatów</span><span class="sxs-lookup"><span data-stu-id="af36c-129">Invoking Delegates</span></span>

<span data-ttu-id="af36c-130">Wywołuje metody, które się na liście wywołania delegata przez wywołanie tego delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="af36c-131">Wewnątrz `Sort()` metody kod wywoła metodę porównywania, aby określić kolejność, aby umieścić obiekty:</span><span class="sxs-lookup"><span data-stu-id="af36c-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="af36c-132">W wierszu powyżej kod *wywołuje* metody dołączony do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="af36c-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="af36c-133">Traktuj zmiennej jako nazwę metody, a następnie wywołaj za pomocą składni wywołań metody normalnego.</span><span class="sxs-lookup"><span data-stu-id="af36c-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="af36c-134">Ten wiersz kodu założeń niebezpieczny: nie ma żadnej gwarancji, że element docelowy został dodany do delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="af36c-135">Jeśli nie zostały dołączone nie elementy docelowe, spowodowałoby wiersz powyżej `NullReferenceException` zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="af36c-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="af36c-136">Idioms używane w celu rozwiązania tego problemu są bardziej skomplikowane niż proste sprawdzanie wartości null i są uwzględnione w dalszej części tego [serii](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="af36c-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="af36c-137">Przypisywanie, dodawanie i usuwanie celów wywołania</span><span class="sxs-lookup"><span data-stu-id="af36c-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="af36c-138">To, jak jest zdefiniowany typ delegata i jak zadeklarowany i wywołać delegata wystąpień.</span><span class="sxs-lookup"><span data-stu-id="af36c-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="af36c-139">Deweloperzy, które mają być wykorzystywane `List.Sort()` metody trzeba zdefiniować metody, których Podpis pasuje do definicji typu delegowanego i przypisz je do delegata, używany przez metodę sortowania.</span><span class="sxs-lookup"><span data-stu-id="af36c-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="af36c-140">To przypisanie dodaje metodę do listy wywołania tego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="af36c-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="af36c-141">Załóżmy, że chcesz sortować listę ciągów ich długość.</span><span class="sxs-lookup"><span data-stu-id="af36c-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="af36c-142">Porównanie funkcji mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="af36c-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="af36c-143">Metoda jest zadeklarowany jako metoda prywatna.</span><span class="sxs-lookup"><span data-stu-id="af36c-143">The method is declared as a private method.</span></span> <span data-ttu-id="af36c-144">Się.</span><span class="sxs-lookup"><span data-stu-id="af36c-144">That's fine.</span></span> <span data-ttu-id="af36c-145">Nie można tej metody jako część publicznego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af36c-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="af36c-146">Może nadal służyć jako metodę porównywania po podłączeniu do delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="af36c-147">Kod wywołujący będą mieli tej metody dołączony do listy docelowej obiektu delegowanego i można do niego dostęp za pośrednictwem tego delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="af36c-148">Przez przekazanie tej metody do tworzenia relacji `List.Sort()` metody:</span><span class="sxs-lookup"><span data-stu-id="af36c-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="af36c-149">Zwróć uwagę, że używana jest nazwa metody bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="af36c-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="af36c-150">Przy użyciu metody jako argument informuje kompilator, aby przekonwertować odwołania do metody odwołanie, które mogą być używane jako element docelowy wywołania delegata i Dołącz tej metody jako obiekt docelowy wywołania.</span><span class="sxs-lookup"><span data-stu-id="af36c-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="af36c-151">Możesz również mogło być jawne przez deklarowanie zmiennej typu "porównanie<string>" i wykonując przypisania:</span><span class="sxs-lookup"><span data-stu-id="af36c-151">You could also have been explicit by declaring a variable of type 'Comparison<string>\` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="af36c-152">W zastosowaniach, gdzie metodę używany jako cel delegata to mały metoda jest często stosowanym rozwiązaniem użyj [wyrażenia Lambda](lambda-expressions.md) składni w celu przypisania:</span><span class="sxs-lookup"><span data-stu-id="af36c-152">In uses where the method being used as a delegate target is a small method, it's common to use [Lambda Expression](lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="af36c-153">Dla celów delegata za pomocą wyrażenia Lambda jest objęte bardziej [później sekcji](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="af36c-153">Using Lambda Expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="af36c-154">W przykładzie Sort() zazwyczaj dołącza metody pojedynczym elementem docelowym delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="af36c-155">Jednak obiektów delegata obsługuje listy wywołania, które mają wiele metod docelowych dołączony do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="af36c-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="af36c-156">Delegat i MulticastDelegate klas</span><span class="sxs-lookup"><span data-stu-id="af36c-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="af36c-157">Obsługa języków opisane powyżej udostępnia funkcje i pomocy technicznej, które zwykle będą potrzebne do pracy z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="af36c-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="af36c-158">Te funkcje są wbudowane w dwóch klas w ramach platformy .NET Core: <xref:System.Delegate> i <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="af36c-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="af36c-159">`System.Delegate` Klasy i jego bezpośrednich jednej klasy podrzędne, `System.MulticastDelegate`, zapewniają obsługę framework do tworzenia delegatów, rejestrowanie metod jako miejsca docelowe delegata i wywoływanie wszystkie metody, które są zarejestrowane jako cel delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="af36c-160">Interesujące jest, że `System.Delegate` i `System.MulticastDelegate` klasy nie są samych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="af36c-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="af36c-161">Udostępniają one podstawę dla wszystkich typów określonego delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="af36c-162">Czy samej konstrukcji języka procesu obowiązkowe, że nie można zadeklarować klasy, która pochodzi z `Delegate` lub `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="af36c-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="af36c-163">Reguły języka C# zabronić jego używania.</span><span class="sxs-lookup"><span data-stu-id="af36c-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="af36c-164">Zamiast tego kompilatora C# tworzy wystąpienia klasy pochodzącej od `MulticastDelegate` przy deklarować typów delegowanych za pomocą słowa kluczowego języka C#.</span><span class="sxs-lookup"><span data-stu-id="af36c-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="af36c-165">Ten projekt nie ma jej katalogów głównych w pierwszej wersji programu C# i .NET.</span><span class="sxs-lookup"><span data-stu-id="af36c-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="af36c-166">Celem jednego zespołu projektu był aby upewnić się, że język używanie delegatów, wymuszone zabezpieczenie typów.</span><span class="sxs-lookup"><span data-stu-id="af36c-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="af36c-167">Która przeznaczone zapewnienie, że delegatów zostały wywołana z prawidłowym typem i liczby argumentów.</span><span class="sxs-lookup"><span data-stu-id="af36c-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="af36c-168">Czas kompilacji i że dowolnego typu zwracanego poprawnie wskazano w.</span><span class="sxs-lookup"><span data-stu-id="af36c-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="af36c-169">Obiekty delegowane były częścią wersji .NET 1.0, która została przed ogólne.</span><span class="sxs-lookup"><span data-stu-id="af36c-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="af36c-170">Najlepszym sposobem na wymuszenie bezpieczeństwa tego typu był przeznaczony dla kompilatora, aby utworzyć konkretnego obiektu delegowanego klasy, które reprezentowane podpis metody jest używany.</span><span class="sxs-lookup"><span data-stu-id="af36c-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="af36c-171">Mimo że nie można utworzyć klasy pochodne bezpośrednio, używasz metody zdefiniowane na tych klas.</span><span class="sxs-lookup"><span data-stu-id="af36c-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="af36c-172">Przejdź przez najbardziej typowe metody, które będą używane podczas pracy z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="af36c-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="af36c-173">Po pierwsze, najważniejsze do zapamiętania to czy jest pochodną co delegata pracować z `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="af36c-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="af36c-174">Delegat multiemisji oznacza, że więcej niż jeden cel metoda może być wywoływana podczas wywoływania za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="af36c-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="af36c-175">Oryginalny projekt uznawane za różnice między delegatów, gdzie można podłączony i wywołać metody tylko jeden obiekt docelowy i delegatów, gdzie można dołączyć i wywołać wielu metod docelowych.</span><span class="sxs-lookup"><span data-stu-id="af36c-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="af36c-176">Różnica w tym okazały się mniej użyteczny w praktyce niż pierwotnie traktować.</span><span class="sxs-lookup"><span data-stu-id="af36c-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="af36c-177">Dwoma różnymi klasami zostały już utworzone, a zostały w ramach początkowego wydania publicznych.</span><span class="sxs-lookup"><span data-stu-id="af36c-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="af36c-178">Metody, które będą używane najczęściej z delegatów są `Invoke()` i `BeginInvoke()`  /  `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="af36c-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="af36c-179">`Invoke()` wywoła wszystkie metody, które zostały dołączone do wystąpienia określonego delegata.</span><span class="sxs-lookup"><span data-stu-id="af36c-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="af36c-180">Jak przedstawiono powyżej, zazwyczaj należy wywołać delegatów za pomocą składni wywołań metody zmiennej obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="af36c-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="af36c-181">Jak można zauważyć [dalej w tej serii](delegates-patterns.md), istnieją wzorców, które współpracują bezpośrednio z tych metod.</span><span class="sxs-lookup"><span data-stu-id="af36c-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="af36c-182">Skoro już znasz składni języka i klas, które obsługują delegatów Przeanalizujmy jak jednoznacznie delegatów są używane, tworzone i wywoływane.</span><span class="sxs-lookup"><span data-stu-id="af36c-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="af36c-183">Next</span><span class="sxs-lookup"><span data-stu-id="af36c-183">Next</span></span>](delegates-strongly-typed.md)
