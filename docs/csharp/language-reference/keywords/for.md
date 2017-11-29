---
title: "for (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a><span data-ttu-id="4bdff-102">for (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4bdff-102">for (C# Reference)</span></span>
<span data-ttu-id="4bdff-103">Za pomocą `for` pętli, można wykonać instrukcji lub blok instrukcji wielokrotnie aż wynikiem obliczenia określonego wyrażenia jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4bdff-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="4bdff-104">Tego rodzaju pętli jest przydatne do Iterowanie przez tablice za i inne aplikacje, w których znasz z wyprzedzeniem jak często mają iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bdff-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bdff-105">Example</span></span>  
 <span data-ttu-id="4bdff-106">W poniższym przykładzie wartość `i` jest wyświetlony w konsoli i zwiększana o 1 podczas każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 <span data-ttu-id="4bdff-107">`for` Instrukcji w poprzednim przykładzie wykonuje następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="4bdff-107">The `for` statement in the previous example performs the following actions.</span></span>  
  
1.  <span data-ttu-id="4bdff-108">Po pierwsze, początkowej wartości zmiennej `i` zostanie nawiązane.</span><span class="sxs-lookup"><span data-stu-id="4bdff-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="4bdff-109">Ten krok odbywa się tylko raz, niezależnie od tego, jak często powtórzeń pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="4bdff-110">Inicjowanie ten można traktować jako w toku poza procesem pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-110">You can think of this initialization as happening outside the looping process.</span></span>  
  
2.  <span data-ttu-id="4bdff-111">Próba sprawdzenia warunku (`i <= 5`), wartość `i` jest porównywany z 5.</span><span class="sxs-lookup"><span data-stu-id="4bdff-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>  
  
    -   <span data-ttu-id="4bdff-112">Jeśli `i` nie może być większa niż 5, warunek jest `true`, i są wykonywane następujące akcje.</span><span class="sxs-lookup"><span data-stu-id="4bdff-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="4bdff-113">`Console.WriteLine` Instrukcji w treści pętli Wyświetla wartość `i`.</span><span class="sxs-lookup"><span data-stu-id="4bdff-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="4bdff-114">Wartość `i` jest zwiększana o 1.</span><span class="sxs-lookup"><span data-stu-id="4bdff-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="4bdff-115">Zwraca pętli do początku krok 2, aby ponownie sprawdzić warunku.</span><span class="sxs-lookup"><span data-stu-id="4bdff-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="4bdff-116">Jeśli `i` jest większa niż 5, wyrażenie `false`, i zamknąć pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
 <span data-ttu-id="4bdff-117">Należy zauważyć, że jeśli początkowa wartość `i` jest większa niż 5, treści pętli nie Uruchom jeszcze raz.</span><span class="sxs-lookup"><span data-stu-id="4bdff-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>  
  
 <span data-ttu-id="4bdff-118">Każdy `for` instrukcji definiuje sekcje inicjatora, warunek i iteratora.</span><span class="sxs-lookup"><span data-stu-id="4bdff-118">Every `for` statement defines initializer, condition, and iterator sections.</span></span> <span data-ttu-id="4bdff-119">Następujące sekcje są zazwyczaj określić liczbę iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-119">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 <span data-ttu-id="4bdff-120">Sekcje służą do następujących celów.</span><span class="sxs-lookup"><span data-stu-id="4bdff-120">The sections serve the following purposes.</span></span>  
  
-   <span data-ttu-id="4bdff-121">W sekcji inicjatora ustawia warunków początkowych.</span><span class="sxs-lookup"><span data-stu-id="4bdff-121">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="4bdff-122">Instrukcje w tej sekcji uruchomić tylko raz, przed wprowadzeniem pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-122">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="4bdff-123">Sekcja może zawierać tylko jeden z poniższych dwóch opcji.</span><span class="sxs-lookup"><span data-stu-id="4bdff-123">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="4bdff-124">Deklaracji i inicjowania zmiennej lokalnej, jak w pierwszym przykładzie (`int i = 1`).</span><span class="sxs-lookup"><span data-stu-id="4bdff-124">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="4bdff-125">Zmienna jest lokalny dla pętli i nie mogą być dostępne spoza pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-125">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="4bdff-126">Zero lub więcej expressons instrukcji z poniższej listy rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="4bdff-126">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="4bdff-127">[Przypisanie](../../../csharp/language-reference/operators/assignment-operator.md) — instrukcja</span><span class="sxs-lookup"><span data-stu-id="4bdff-127">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="4bdff-128">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="4bdff-128">invocation of a method</span></span>  
  
        -   <span data-ttu-id="4bdff-129">Prefiks lub przyrostka [przyrostu](../../../csharp/language-reference/operators/increment-operator.md) wyrażenia, takich jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="4bdff-129">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="4bdff-130">Prefiks lub przyrostka [dekrementacji](../../../csharp/language-reference/operators/decrement-operator.md) wyrażenia, takich jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="4bdff-130">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="4bdff-131">Tworzenie obiektu przy użyciu [nowych](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="4bdff-131">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="4bdff-132">[await](../../../csharp/language-reference/keywords/await.md) wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4bdff-132">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="4bdff-133">Sekcja warunku zawiera wyrażenie logiczne, które jest obliczane czy pętli powinny być kończone, czy powinno być ono uruchomione ponownie.</span><span class="sxs-lookup"><span data-stu-id="4bdff-133">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="4bdff-134">Sekcja iteratora definiuje, co się stanie po każdej iteracji pętli treści.</span><span class="sxs-lookup"><span data-stu-id="4bdff-134">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="4bdff-135">Sekcja iteratora zawiera zero lub więcej z następujących wyrażenia instrukcji, oddzielonych przecinkami:</span><span class="sxs-lookup"><span data-stu-id="4bdff-135">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="4bdff-136">[Przypisanie](../../../csharp/language-reference/operators/assignment-operator.md) — instrukcja</span><span class="sxs-lookup"><span data-stu-id="4bdff-136">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="4bdff-137">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="4bdff-137">invocation of a method</span></span>  
  
    -   <span data-ttu-id="4bdff-138">Prefiks lub przyrostka [przyrostu](../../../csharp/language-reference/operators/increment-operator.md) wyrażenia, takich jak `++i` lub`i++`</span><span class="sxs-lookup"><span data-stu-id="4bdff-138">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="4bdff-139">Prefiks lub przyrostka [dekrementacji](../../../csharp/language-reference/operators/decrement-operator.md) wyrażenia, takich jak `--i` lub`i--`</span><span class="sxs-lookup"><span data-stu-id="4bdff-139">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="4bdff-140">Tworzenie obiektu przy użyciu [nowych](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="4bdff-140">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="4bdff-141">[await](../../../csharp/language-reference/keywords/await.md) wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4bdff-141">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="4bdff-142">Treści pętli zawiera instrukcję, pustą instrukcję lub blok instrukcji, tworzonych przez otaczającej instrukcji zero lub więcej w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="4bdff-142">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="4bdff-143">Mogą być dzielone z `for` pętli przy użyciu [podziału](../../../csharp/language-reference/keywords/break.md) — słowo kluczowe, lub można krok do następnej iteracji przy użyciu [kontynuować](../../../csharp/language-reference/keywords/continue.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4bdff-143">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="4bdff-144">Za pomocą może zostać wyjść żadnych pętli [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4bdff-144">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
 <span data-ttu-id="4bdff-145">Pierwszym przykładzie w tym temacie przedstawiono najbardziej typowe rodzaj `for` pętli, co sprawia, że następujące opcje dla sekcji.</span><span class="sxs-lookup"><span data-stu-id="4bdff-145">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections.</span></span>  
  
-   <span data-ttu-id="4bdff-146">Inicjator deklaruje i inicjuje zmiennej lokalnej `i`, który przechowuje liczba powtórzeń pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-146">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="4bdff-147">Warunek sprawdza wartości zmiennej pętli względem żadnej znanej wartości końcowej 5.</span><span class="sxs-lookup"><span data-stu-id="4bdff-147">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="4bdff-148">Sekcja iteratora używa instrukcję operatory przyrostka inkrementacji `i++`, aby sprawdzać każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="4bdff-148">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>  
  
 <span data-ttu-id="4bdff-149">Poniższy przykład przedstawia kilka mniej typowe opcje: przypisywanie wartości do zmiennej pętli zewnętrznych w sekcji inicjatora, wywoływania `Console.WriteLine` metody zarówno inicjator i sekcje iteratora oraz zmienianie wartości dwu zmienne w sekcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="4bdff-149">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section,  invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 <span data-ttu-id="4bdff-150">Wszystkie wyrażenia, które definiują `for` instrukcji są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4bdff-150">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="4bdff-151">Na przykład następująca instrukcja tworzy Pętla nieskończona.</span><span class="sxs-lookup"><span data-stu-id="4bdff-151">For example, the following statement creates an infinite loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4bdff-152">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4bdff-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4bdff-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bdff-153">See Also</span></span>  
 [<span data-ttu-id="4bdff-154">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4bdff-154">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4bdff-155">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4bdff-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4bdff-156">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4bdff-156">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4bdff-157">Instrukcja foreach w</span><span class="sxs-lookup"><span data-stu-id="4bdff-157">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="4bdff-158">for — instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="4bdff-158">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
 [<span data-ttu-id="4bdff-159">Iteracja — instrukcje</span><span class="sxs-lookup"><span data-stu-id="4bdff-159">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
