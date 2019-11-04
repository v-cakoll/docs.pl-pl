---
title: System. Delegate i słowo kluczowe `delegate`
description: Dowiedz się więcej na temat klas w .NET Framework, które obsługują delegatów i jak te są mapowane na słowo kluczowe "Delegate".
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: f4635ff623feec9407021792cabd1677184b4d34
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420365"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="4f862-103">System. Delegate i słowo kluczowe `delegate`</span><span class="sxs-lookup"><span data-stu-id="4f862-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="4f862-104">Ubiegł</span><span class="sxs-lookup"><span data-stu-id="4f862-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="4f862-105">W tym artykule opisano klasy w programie .NET Framework, które obsługują delegatów i jak te są mapowane na `delegate` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4f862-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="4f862-106">Definiowanie typów delegatów</span><span class="sxs-lookup"><span data-stu-id="4f862-106">Defining Delegate Types</span></span>

<span data-ttu-id="4f862-107">Zacznijmy od słowa kluczowego "Delegate", ponieważ jest to przede wszystkim, czego będziesz używać podczas pracy z delegatami.</span><span class="sxs-lookup"><span data-stu-id="4f862-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="4f862-108">Kod generowany przez kompilator, gdy użycie słowa kluczowego `delegate` zostanie zmapowane na wywołania metody, które wywołują elementy członkowskie klas <xref:System.Delegate> i <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="4f862-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="4f862-109">Należy zdefiniować typ delegata przy użyciu składni podobnej do definiowania sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="4f862-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="4f862-110">Po prostu Dodaj słowo kluczowe `delegate` do definicji.</span><span class="sxs-lookup"><span data-stu-id="4f862-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="4f862-111">Kontynuujmy używanie metody list. Sort () jako przykładu.</span><span class="sxs-lookup"><span data-stu-id="4f862-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="4f862-112">Pierwszym krokiem jest utworzenie typu dla delegata porównania:</span><span class="sxs-lookup"><span data-stu-id="4f862-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="4f862-113">Kompilator generuje klasę pochodną `System.Delegate`, która pasuje do użytego podpisu (w tym przypadku metoda zwraca liczbę całkowitą i ma dwa argumenty).</span><span class="sxs-lookup"><span data-stu-id="4f862-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="4f862-114">Typ tego delegata jest `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="4f862-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="4f862-115">Typ delegata `Comparison` jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="4f862-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="4f862-116">Aby uzyskać szczegółowe informacje na temat typów ogólnych, zobacz [tutaj](programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f862-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="4f862-117">Zauważ, że składnia może wyglądać tak, jakby deklaruje zmienną, ale faktycznie deklaruje *Typ*.</span><span class="sxs-lookup"><span data-stu-id="4f862-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="4f862-118">Można definiować typy delegatów wewnątrz klas, bezpośrednio w przestrzeniach nazw, a nawet w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f862-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="4f862-119">Deklarowanie typów delegatów (lub innych typów) bezpośrednio w globalnej przestrzeni nazw nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="4f862-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="4f862-120">Kompilator generuje również procedury obsługi dodawania i usuwania dla tego nowego typu, tak aby klienci tej klasy mogli dodawać i usuwać metody z listy wywołań wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4f862-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="4f862-121">Kompilator wymusza, że podpis metody dodawanej lub usuwanej jest zgodny z podpisem używanym podczas deklarowania metody.</span><span class="sxs-lookup"><span data-stu-id="4f862-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="4f862-122">Deklarowanie wystąpień delegatów</span><span class="sxs-lookup"><span data-stu-id="4f862-122">Declaring instances of delegates</span></span>

<span data-ttu-id="4f862-123">Po zdefiniowaniu delegata można utworzyć wystąpienie tego typu.</span><span class="sxs-lookup"><span data-stu-id="4f862-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="4f862-124">Podobnie jak w przypadku C#wszystkich zmiennych w, nie można zadeklarować wystąpień delegatów bezpośrednio w przestrzeni nazw lub w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f862-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="4f862-125">Typ zmiennej to `Comparison<T>`, zdefiniowany wcześniej typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="4f862-126">Nazwa zmiennej jest `comparator`.</span><span class="sxs-lookup"><span data-stu-id="4f862-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="4f862-127">Ten fragment kodu jest zadeklarowany jako zmienna członkowska wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="4f862-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="4f862-128">Można również zadeklarować zmienne delegatów, które są zmiennymi lokalnymi lub argumenty metod.</span><span class="sxs-lookup"><span data-stu-id="4f862-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="4f862-129">Wywoływanie delegatów</span><span class="sxs-lookup"><span data-stu-id="4f862-129">Invoking Delegates</span></span>

<span data-ttu-id="4f862-130">Metody, które znajdują się na liście wywołań delegata, są wywoływane przez wywołanie tego delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="4f862-131">Wewnątrz metody `Sort()` kod wywoła metodę porównania, aby określić, która kolejność umieszczania obiektów:</span><span class="sxs-lookup"><span data-stu-id="4f862-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="4f862-132">W wierszu powyżej kod *wywołuje* metodę dołączoną do delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="4f862-133">Zmienna jest traktowana jako nazwa metody i wywołuje ją przy użyciu standardowej składni wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="4f862-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="4f862-134">Ten wiersz kodu powoduje niebezpieczne założenie: nie ma gwarancji, że element docelowy został dodany do delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="4f862-135">Jeśli nie dołączono żadnych elementów docelowych, wiersz powyżej mógłby spowodować zgłoszenie `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="4f862-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="4f862-136">Idiomy używany do rozwiązywania tego problemu są bardziej skomplikowane niż proste sprawdzenie wartości null i zostały omówione w dalszej części tej [serii](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="4f862-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="4f862-137">Przypisywanie, Dodawanie i usuwanie elementów docelowych wywołań</span><span class="sxs-lookup"><span data-stu-id="4f862-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="4f862-138">Jest to sposób definiowania typu delegata oraz sposobu deklarowania i wywołania delegatów.</span><span class="sxs-lookup"><span data-stu-id="4f862-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="4f862-139">Deweloperzy, którzy chcą korzystać z metody `List.Sort()`, muszą zdefiniować metodę, której sygnatura jest zgodna z definicją typu delegata, i przypisać ją do delegata używanego przez metodę sortowania.</span><span class="sxs-lookup"><span data-stu-id="4f862-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="4f862-140">To przypisanie dodaje metodę do listy wywołań tego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="4f862-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="4f862-141">Załóżmy, że chcemy sortować listę ciągów według ich długości.</span><span class="sxs-lookup"><span data-stu-id="4f862-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="4f862-142">Funkcja porównania może być następująca:</span><span class="sxs-lookup"><span data-stu-id="4f862-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="4f862-143">Metoda jest zadeklarowana jako Metoda prywatna.</span><span class="sxs-lookup"><span data-stu-id="4f862-143">The method is declared as a private method.</span></span> <span data-ttu-id="4f862-144">To dobrze.</span><span class="sxs-lookup"><span data-stu-id="4f862-144">That's fine.</span></span> <span data-ttu-id="4f862-145">Nie można chcieć, aby ta metoda była częścią interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="4f862-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="4f862-146">Nadal może być używana jako metoda porównania w przypadku dołączenia do delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="4f862-147">Kod wywołujący będzie miał tę metodę dołączoną do listy docelowej obiektu delegowanego i może uzyskać do niej dostęp za pomocą tego delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="4f862-148">Należy utworzyć tę relację, przekazując tę metodę do metody `List.Sort()`:</span><span class="sxs-lookup"><span data-stu-id="4f862-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="4f862-149">Zauważ, że nazwa metody jest używana, bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="4f862-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="4f862-150">Użycie metody jako argumentu instruuje kompilator, aby przekonwertował odwołanie do metody na odwołanie, które może być użyte jako obiekt docelowy wywołania delegata i dołączyć tę metodę jako obiekt docelowy wywołania.</span><span class="sxs-lookup"><span data-stu-id="4f862-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="4f862-151">Można było również jawnie, deklarując zmienną typu `Comparison<string>` i wykonując przypisanie:</span><span class="sxs-lookup"><span data-stu-id="4f862-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="4f862-152">W używanym miejscu, gdzie Metoda używana jako obiekt docelowy delegata jest małą metodą, często jest używana składnia [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) do wykonania przypisania:</span><span class="sxs-lookup"><span data-stu-id="4f862-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="4f862-153">Użycie wyrażeń lambda dla obiektów docelowych delegatów zostało omówione w [dalszej części](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="4f862-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="4f862-154">Przykład Sort () zazwyczaj dołącza jedną metodę docelową do delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="4f862-155">Obiekty delegatów obsługują jednak listy wywołań, które mają wiele metod docelowych dołączonych do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="4f862-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="4f862-156">Klasy delegatów i MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="4f862-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="4f862-157">Opisana powyżej obsługa języka udostępnia funkcje i pomoc techniczną, które zwykle muszą współpracować z delegatami.</span><span class="sxs-lookup"><span data-stu-id="4f862-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="4f862-158">Te funkcje są oparte na dwóch klasach w programie .NET Core Framework: <xref:System.Delegate> i <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="4f862-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="4f862-159">Klasa `System.Delegate` i jej pojedynczej klasy podrzędnej bezpośredniej, `System.MulticastDelegate`, zapewniają obsługę struktury tworzenia delegatów, rejestrowania metod jako obiektów docelowych delegatów i wywoływania wszystkich metod, które są zarejestrowane jako obiekt docelowy delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="4f862-160">Interesujące klasy `System.Delegate` i `System.MulticastDelegate` nie są typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="4f862-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="4f862-161">Zapewniają one podstawę dla wszystkich określonych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="4f862-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="4f862-162">Ten sam proces projektowania języka nie może zadeklarować klasy, która pochodzi od `Delegate` lub `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="4f862-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="4f862-163">Reguły C# języka zabraniają tego.</span><span class="sxs-lookup"><span data-stu-id="4f862-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="4f862-164">Zamiast tego C# kompilator tworzy wystąpienia klasy pochodzącej od `MulticastDelegate`w przypadku użycia słowa kluczowego C# Language do deklarowania typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="4f862-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="4f862-165">Ten projekt zawiera elementy główne w pierwszej wersji programu C# i .NET.</span><span class="sxs-lookup"><span data-stu-id="4f862-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="4f862-166">Jednym z celów zespołu projektowego jest upewnienie się, że język wymusza bezpieczeństwo typów podczas korzystania z delegatów.</span><span class="sxs-lookup"><span data-stu-id="4f862-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="4f862-167">Ma to na celu zapewnienie, że Delegaty zostały wywołane z odpowiednim typem i liczbą argumentów.</span><span class="sxs-lookup"><span data-stu-id="4f862-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="4f862-168">I, że każdy typ zwracany został prawidłowo wskazany w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4f862-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="4f862-169">Delegaty były częścią wersji 1,0 .NET, która była wcześniejsza niż ogólna.</span><span class="sxs-lookup"><span data-stu-id="4f862-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="4f862-170">Najlepszym sposobem wymuszenia zapewnienia bezpieczeństwa tego typu był kompilator w celu utworzenia konkretnych klas delegatów, które reprezentują używany podpis metody.</span><span class="sxs-lookup"><span data-stu-id="4f862-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="4f862-171">Mimo że nie można bezpośrednio tworzyć klas pochodnych, należy użyć metod zdefiniowanych dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="4f862-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="4f862-172">Przejdźmy do najpopularniejszych metod, które będą używane podczas pracy z delegatami.</span><span class="sxs-lookup"><span data-stu-id="4f862-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="4f862-173">Pierwszym, najważniejszym faktem, że każdy delegat, z którym pracujesz, pochodzi od `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="4f862-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="4f862-174">Delegat multiemisji oznacza, że można wywołać więcej niż jeden obiekt docelowy metody podczas wywoływania za pośrednictwem delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="4f862-175">Oryginalny projekt uwzględniał rozróżnienie między delegatami, w których można dołączać i wywoływać tylko jedną metodę docelową, oraz delegatów, gdzie można dołączać i wywoływać wiele metod docelowych.</span><span class="sxs-lookup"><span data-stu-id="4f862-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="4f862-176">Takie rozróżnienie okazało się mniej użyteczne w rzeczywistości niż pierwotnie przemyślane.</span><span class="sxs-lookup"><span data-stu-id="4f862-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="4f862-177">Dwie różne klasy zostały już utworzone i zostały w strukturze od momentu jego początkowej wersji publicznej.</span><span class="sxs-lookup"><span data-stu-id="4f862-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="4f862-178">Metody, które będą używane najbardziej z delegatów, są `Invoke()` i `BeginInvoke()` / `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="4f862-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="4f862-179">`Invoke()` wywoła wszystkie metody, które zostały dołączone do określonego wystąpienia delegata.</span><span class="sxs-lookup"><span data-stu-id="4f862-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="4f862-180">Jak wspomniano powyżej, zazwyczaj wywołuje się delegatów przy użyciu składni wywołania metody w zmiennej delegat.</span><span class="sxs-lookup"><span data-stu-id="4f862-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="4f862-181">Jak widać [w dalszej części tej serii](delegates-patterns.md), istnieją wzorce, które współpracują bezpośrednio z tymi metodami.</span><span class="sxs-lookup"><span data-stu-id="4f862-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="4f862-182">Teraz, gdy znasz składnię języka i klasy obsługujące delegatów, sprawdźmy, jak są używane, tworzone i wywoływane delegatów o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="4f862-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="4f862-183">Next</span><span class="sxs-lookup"><span data-stu-id="4f862-183">Next</span></span>](delegates-strongly-typed.md)
