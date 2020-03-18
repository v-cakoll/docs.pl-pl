---
title: System.Delegate i `delegate` słowo kluczowe
description: Dowiedz się więcej o klasach w .NET, które obsługują delegatów i jak te mapy do "delegata" słowa kluczowego.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146284"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="74e02-103">System.Delegate i `delegate` słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="74e02-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="74e02-104">Wstecz</span><span class="sxs-lookup"><span data-stu-id="74e02-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="74e02-105">W tym artykule omówiono klasy w .NET, które `delegate` obsługują delegatów i jak te mapy do słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="74e02-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="74e02-106">Definiowanie typów pełnomocników</span><span class="sxs-lookup"><span data-stu-id="74e02-106">Define delegate types</span></span>

<span data-ttu-id="74e02-107">Zacznijmy od słowa kluczowego "delegować", ponieważ jest to przede wszystkim to, co będzie używane podczas pracy z delegatami.</span><span class="sxs-lookup"><span data-stu-id="74e02-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="74e02-108">Kod, który kompilator generuje `delegate` podczas korzystania ze słowa kluczowego zostanie <xref:System.Delegate> <xref:System.MulticastDelegate> mapowany do wywołania metody, które wywołają członków i klas.</span><span class="sxs-lookup"><span data-stu-id="74e02-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="74e02-109">Typ delegata można zdefiniować przy użyciu składni, która jest podobna do definiowania podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="74e02-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="74e02-110">Wystarczy dodać `delegate` słowo kluczowe do definicji.</span><span class="sxs-lookup"><span data-stu-id="74e02-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="74e02-111">Użyjmy metody List.Sort() jako naszego przykładu.</span><span class="sxs-lookup"><span data-stu-id="74e02-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="74e02-112">Pierwszym krokiem jest utworzenie typu dla delegata porównania:</span><span class="sxs-lookup"><span data-stu-id="74e02-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="74e02-113">Kompilator generuje klasę, wywodzącą się z `System.Delegate` tej zgodności z użytą sygnaturą (w tym przypadku metodę, która zwraca wartość całkowitą i ma dwa argumenty).</span><span class="sxs-lookup"><span data-stu-id="74e02-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="74e02-114">Typem tego pełnomocnika `Comparison`jest .</span><span class="sxs-lookup"><span data-stu-id="74e02-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="74e02-115">Typ `Comparison` delegata jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="74e02-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="74e02-116">Szczegółowe informacje na temat leków generycznych można znaleźć [tutaj](programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="74e02-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="74e02-117">Należy zauważyć, że składnia może wyglądać tak, jakby deklaruje zmienną, ale w rzeczywistości deklaruje *typ*.</span><span class="sxs-lookup"><span data-stu-id="74e02-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="74e02-118">Można zdefiniować typy delegatów wewnątrz klas, bezpośrednio wewnątrz obszarów nazw, a nawet w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74e02-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="74e02-119">Deklarowanie typów delegatów (lub innych typów) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="74e02-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="74e02-120">Kompilator generuje również dodawanie i usuwanie programów obsługi dla tego nowego typu, dzięki czemu klienci tej klasy można dodawać i usuwać metody z listy wywołania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="74e02-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="74e02-121">Kompilator wymusi, że podpis dodawanej lub usuwanej metody jest zgodny z podpisem używanym podczas deklarowania metody.</span><span class="sxs-lookup"><span data-stu-id="74e02-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="74e02-122">Deklarowanie wystąpień delegatów</span><span class="sxs-lookup"><span data-stu-id="74e02-122">Declare instances of delegates</span></span>

<span data-ttu-id="74e02-123">Po zdefiniowaniu pełnomocnika można utworzyć wystąpienie tego typu.</span><span class="sxs-lookup"><span data-stu-id="74e02-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="74e02-124">Podobnie jak wszystkie zmienne w języku C#, nie można zadeklarować wystąpień delegata bezpośrednio w obszarze nazw lub w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74e02-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="74e02-125">Typ zmiennej to `Comparison<T>`typ delegata zdefiniowany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="74e02-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="74e02-126">Nazwa zmiennej to `comparator`.</span><span class="sxs-lookup"><span data-stu-id="74e02-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="74e02-127">Ten fragment kodu powyżej zadeklarowane zmiennej składowej wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="74e02-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="74e02-128">Można również zadeklarować zmienne delegata, które są zmiennymi lokalnymi lub argumentami do metod.</span><span class="sxs-lookup"><span data-stu-id="74e02-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="74e02-129">Wywoływanie delegatów</span><span class="sxs-lookup"><span data-stu-id="74e02-129">Invoke delegates</span></span>

<span data-ttu-id="74e02-130">Można wywołać metody, które znajdują się na liście wywołania delegata, wywołując tego delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="74e02-131">Wewnątrz `Sort()` metody kod wywoła metodę porównania, aby określić, która kolejność umieszczać obiekty:</span><span class="sxs-lookup"><span data-stu-id="74e02-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="74e02-132">W wierszu powyżej kod *wywołuje* metodę dołączony do delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="74e02-133">Zmienną należy traktować jako nazwę metody i wywołać ją przy użyciu składni wywołania metody normalnej.</span><span class="sxs-lookup"><span data-stu-id="74e02-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="74e02-134">Ten wiersz kodu sprawia, że niebezpieczne założenie: Nie ma żadnej gwarancji, że obiekt docelowy został dodany do delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="74e02-135">Jeśli nie zostały dołączone żadne cele, `NullReferenceException` powyższa linia spowoduje wyrzucenie.</span><span class="sxs-lookup"><span data-stu-id="74e02-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="74e02-136">Idiomy używane do rozwiązania tego problemu są bardziej skomplikowane niż proste sprawdzanie wartości null i są omówione w [dalszej](delegates-patterns.md)części tej serii .</span><span class="sxs-lookup"><span data-stu-id="74e02-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="74e02-137">Przypisywanie, dodawanie i usuwanie celów wywołania</span><span class="sxs-lookup"><span data-stu-id="74e02-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="74e02-138">W ten sposób typ delegata jest zdefiniowany i jak są deklarowane i wywoływane wystąpienia delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="74e02-139">Deweloperzy, którzy `List.Sort()` chcą użyć metody należy zdefiniować metodę, której podpis pasuje do definicji typu delegata i przypisać go do delegata używanego przez metodę sortowania.</span><span class="sxs-lookup"><span data-stu-id="74e02-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="74e02-140">To przypisanie dodaje metodę do listy wywołania tego obiektu delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="74e02-141">Załóżmy, że chcesz posortować listę ciągów według ich długości.</span><span class="sxs-lookup"><span data-stu-id="74e02-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="74e02-142">Funkcja porównywania może być następująca:</span><span class="sxs-lookup"><span data-stu-id="74e02-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="74e02-143">Metoda jest zadeklarowana jako metoda prywatna.</span><span class="sxs-lookup"><span data-stu-id="74e02-143">The method is declared as a private method.</span></span> <span data-ttu-id="74e02-144">To dobrze.</span><span class="sxs-lookup"><span data-stu-id="74e02-144">That's fine.</span></span> <span data-ttu-id="74e02-145">Ta metoda może nie być częścią interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="74e02-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="74e02-146">Nadal może służyć jako metoda porównania po dołączeniu do delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="74e02-147">Kod wywołujący będzie miał tę metodę dołączony do listy docelowej obiektu delegata i można uzyskać do niego dostęp za pośrednictwem tego pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="74e02-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="74e02-148">Tę relację tworzymy, przekazując tę metodę do `List.Sort()` metody:</span><span class="sxs-lookup"><span data-stu-id="74e02-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="74e02-149">Należy zauważyć, że nazwa metody jest używana, bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="74e02-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="74e02-150">Za pomocą metody jako argument informuje kompilator do konwersji odwołania do metody do odwołania, które mogą być używane jako obiekt docelowy wywołania delegata i dołączyć tę metodę jako miejsce docelowe wywołania.</span><span class="sxs-lookup"><span data-stu-id="74e02-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="74e02-151">Można również jawne, deklarując zmienną `Comparison<string>` typu i wykonując przypisanie:</span><span class="sxs-lookup"><span data-stu-id="74e02-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="74e02-152">W zastosowaniach, w których metoda używana jako obiekt docelowy delegata jest małą metodą, często używa się składni [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) do wykonywania przypisania:</span><span class="sxs-lookup"><span data-stu-id="74e02-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="74e02-153">Za pomocą wyrażeń lambda dla obiektów docelowych delegata jest omówiona bardziej w [dalszej sekcji](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="74e02-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="74e02-154">Przykład Sort() zazwyczaj dołącza jedną metodę docelową do delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="74e02-155">Jednak delegować obiekty obsługują listy wywołań, które mają wiele metod docelowych dołączonych do obiektu delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="74e02-156">Delegowanie i MulticastDelegate klasy</span><span class="sxs-lookup"><span data-stu-id="74e02-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="74e02-157">Obsługa języka opisana powyżej zapewnia funkcje i wsparcie, które zazwyczaj będą potrzebne do pracy z pełnomocnikami.</span><span class="sxs-lookup"><span data-stu-id="74e02-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="74e02-158">Te funkcje są zbudowane na dwóch klasach <xref:System.Delegate> <xref:System.MulticastDelegate>w ramach .NET Core: i .</span><span class="sxs-lookup"><span data-stu-id="74e02-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="74e02-159">Klasa `System.Delegate` i jej pojedynczej `System.MulticastDelegate`bezpośredniej podklasy, zapewniają wsparcie framework do tworzenia delegatów, rejestrowanie metod jako delegat obiektów docelowych i wywoływania wszystkich metod, które są zarejestrowane jako miejsce docelowe delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="74e02-160">Co ciekawe, `System.Delegate` `System.MulticastDelegate` i klasy nie są same typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="74e02-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="74e02-161">Stanowią one podstawę dla wszystkich określonych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="74e02-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="74e02-162">Ten sam proces projektowania języka upoważnił, że `Delegate` nie `MulticastDelegate`można zadeklarować klasy, która pochodzi od lub .</span><span class="sxs-lookup"><span data-stu-id="74e02-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="74e02-163">Reguły języka Języka C# go zabronić.</span><span class="sxs-lookup"><span data-stu-id="74e02-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="74e02-164">Zamiast tego kompilator C# tworzy wystąpienia `MulticastDelegate` klasy pochodzące z podczas używania języka C# — słowo kluczowe do deklarowania typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="74e02-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="74e02-165">Ten projekt ma swoje korzenie w pierwszej wersji C# i .NET.</span><span class="sxs-lookup"><span data-stu-id="74e02-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="74e02-166">Jednym z celów dla zespołu projektowego było zapewnienie, że język wymuszał bezpieczeństwo typów podczas korzystania z delegatów.</span><span class="sxs-lookup"><span data-stu-id="74e02-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="74e02-167">Oznaczało to zapewnienie, że delegaci zostali powołani z odpowiednim typem i liczbą argumentów.</span><span class="sxs-lookup"><span data-stu-id="74e02-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="74e02-168">I, że każdy typ zwracany został poprawnie wskazany w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="74e02-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="74e02-169">Delegaci byli częścią wersji .NET 1.0, która była przed generykami.</span><span class="sxs-lookup"><span data-stu-id="74e02-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="74e02-170">Najlepszym sposobem, aby wymusić bezpieczeństwo tego typu było dla kompilatora, aby utworzyć konkretne klasy delegata, który reprezentował podpis metody używane.</span><span class="sxs-lookup"><span data-stu-id="74e02-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="74e02-171">Nawet jeśli nie można utworzyć klas pochodnych bezpośrednio, będzie używać metod zdefiniowanych w tych klasach.</span><span class="sxs-lookup"><span data-stu-id="74e02-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="74e02-172">Przejdźmy przez najbardziej typowe metody, które będą używane podczas pracy z delegatów.</span><span class="sxs-lookup"><span data-stu-id="74e02-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="74e02-173">Pierwszym, najważniejszym faktem do zapamiętania jest to, że `MulticastDelegate`każdy delegat, z którym pracujesz, pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="74e02-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="74e02-174">Delegat multiemisji oznacza, że podczas wywoływania za pośrednictwem pełnomocnika można wywołać więcej niż jeden obiekt docelowy metody.</span><span class="sxs-lookup"><span data-stu-id="74e02-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="74e02-175">Oryginalny projekt rozważadokonywanie rozróżnienia między delegatów, gdzie można dołączyć i wywołać tylko jedną metodę docelową, a delegatów, gdzie wiele metod docelowych można dołączyć i wywołać.</span><span class="sxs-lookup"><span data-stu-id="74e02-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="74e02-176">Rozróżnienie to okazało się mniej użyteczne w praktyce niż początkowo sądzono.</span><span class="sxs-lookup"><span data-stu-id="74e02-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="74e02-177">Dwie różne klasy zostały już utworzone i zostały w ramach od jego pierwszego publicznego wydania.</span><span class="sxs-lookup"><span data-stu-id="74e02-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="74e02-178">Metody, które będą używane najbardziej z `Invoke()` `BeginInvoke()`  /  `EndInvoke()`delegatów są i .</span><span class="sxs-lookup"><span data-stu-id="74e02-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="74e02-179">`Invoke()`wywoła wszystkie metody, które zostały dołączone do wystąpienia określonego delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="74e02-180">Jak widać powyżej, zazwyczaj wywołać delegatów przy użyciu składni wywołania metody na zmiennej delegata.</span><span class="sxs-lookup"><span data-stu-id="74e02-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="74e02-181">Jak zobaczysz [w dalszej części tej serii,](delegates-patterns.md)istnieją wzorce, które działają bezpośrednio z tymi metodami.</span><span class="sxs-lookup"><span data-stu-id="74e02-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="74e02-182">Teraz, gdy widzieliście składnię języka i klas, które obsługują delegatów, zbadajmy, jak silnie typowane delegatów są używane, tworzone i wywoływane.</span><span class="sxs-lookup"><span data-stu-id="74e02-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="74e02-183">Dalej</span><span class="sxs-lookup"><span data-stu-id="74e02-183">Next</span></span>](delegates-strongly-typed.md)
