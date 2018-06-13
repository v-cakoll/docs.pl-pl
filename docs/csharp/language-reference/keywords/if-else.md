---
title: if-else (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: eb8fe4c3a02cab8f8c887ec37244bede04b8a663
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218758"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="d4259-102">if-else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d4259-102">if-else (C# Reference)</span></span>
<span data-ttu-id="d4259-103">`if` Identyfikuje instrukcji, które instrukcji do uruchomienia na podstawie wartości z `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d4259-103">An `if` statement identifies which statement to run based on the value of a `Boolean` expression.</span></span> <span data-ttu-id="d4259-104">W poniższym przykładzie `Boolean` zmiennej `result` ustawiono `true` , a następnie zaewidencjonowany `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d4259-104">In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="d4259-105">Dane wyjściowe `The condition is true`.</span><span class="sxs-lookup"><span data-stu-id="d4259-105">The output is `The condition is true`.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 <span data-ttu-id="d4259-106">Przykłady można uruchomić w tym temacie, umieszczając je w `Main` metoda aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="d4259-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>  
  
 <span data-ttu-id="d4259-107">`if` Instrukcji w języku C# może zająć dwie formy, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d4259-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>  
  
```csharp  
// if-else statement  
if (condition)  
{  
    then-statement;  
}  
else  
{  
    else-statement;  
}  
// Next statement in the program.  
  
// if statement without an else  
if (condition)  
{  
    then-statement;  
}  
// Next statement in the program.  
```  
  
 <span data-ttu-id="d4259-108">W `if-else` instrukcji, jeśli `condition` zwraca wartość true, `then-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="d4259-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="d4259-109">Jeśli `condition` ma wartość false, `else-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="d4259-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="d4259-110">Ponieważ `condition` nie może być jednocześnie true i false, `then-statement` i `else-statement` z `if-else` instrukcji nigdy oba uruchomić.</span><span class="sxs-lookup"><span data-stu-id="d4259-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="d4259-111">Po `then-statement` lub `else-statement` działa, kontroli są przesyłane do następnej instrukcji po `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d4259-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="d4259-112">W `if` instrukcji, która nie zawiera `else` instrukcji, jeśli `condition` ma wartość true, `then-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="d4259-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="d4259-113">Jeśli `condition` ma wartość false, sterowania są przesyłane do następnej instrukcji po `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d4259-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="d4259-114">Zarówno `then-statement` i `else-statement` składa się z jednej instrukcji lub wiele instrukcji, które są ujęte w nawiasy klamrowe (`{}`).</span><span class="sxs-lookup"><span data-stu-id="d4259-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="d4259-115">Dla jednej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.</span><span class="sxs-lookup"><span data-stu-id="d4259-115">For a single statement, the braces are optional but recommended.</span></span>  
  
 <span data-ttu-id="d4259-116">Instrukcji lub instrukcjach w `then-statement` i `else-statement` mogą być dowolnego rodzaju, włącznie z innego `if` zagnieżdżonych instrukcji w oryginalnej `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d4259-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="d4259-117">Zagnieżdżone w `if` instrukcji każdego `else` klauzuli należy do ostatniego `if` który nie ma odpowiedniego elementu `else`.</span><span class="sxs-lookup"><span data-stu-id="d4259-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="d4259-118">W poniższym przykładzie `Result1` jest wyświetlany, jeśli obie `m > 10` i `n > 20` zwrócić wartość true.</span><span class="sxs-lookup"><span data-stu-id="d4259-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="d4259-119">Jeśli `m > 10` ma wartość true, ale `n > 20` ma wartość false, `Result2` pojawi się.</span><span class="sxs-lookup"><span data-stu-id="d4259-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 <span data-ttu-id="d4259-120">Jeśli natomiast ma `Result2` się pojawiać, gdy `(m > 10)` ma wartość false, to skojarzenie można określić za pomocą nawiasów klamrowych ustanowienie początek i koniec zagnieżdżone `if` instrukcji, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d4259-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 <span data-ttu-id="d4259-121">`Result2` jest wyświetlana, gdy warunek `(m > 10)` daje w wyniku wartość false.</span><span class="sxs-lookup"><span data-stu-id="d4259-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4259-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4259-122">Example</span></span>  
 <span data-ttu-id="d4259-123">W poniższym przykładzie, wpisz znak z klawiatury, a program używa zagnieżdżoną `if` instrukcji, aby określić, czy znak wejściowy jest znakiem alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="d4259-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="d4259-124">Jeśli znak wejściowy jest litera, program sprawdza, czy znak wejściowy jest małe lub wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="d4259-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="d4259-125">Pojawi się komunikat dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="d4259-125">A message appears for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="d4259-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4259-126">Example</span></span>  
 <span data-ttu-id="d4259-127">Ponadto można zagnieżdżać `if` instrukcji wewnątrz innego bloku, jak przedstawiono na poniższym kodu częściowej.</span><span class="sxs-lookup"><span data-stu-id="d4259-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="d4259-128">Przykład zagnieżdża `if` instrukcje wewnątrz dwa bloki else i jeden blok następnie.</span><span class="sxs-lookup"><span data-stu-id="d4259-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="d4259-129">Komentarze Określ warunki, które są true lub false w każdym bloku.</span><span class="sxs-lookup"><span data-stu-id="d4259-129">The comments specify which conditions are true or false in each block.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="d4259-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4259-130">Example</span></span>  
 <span data-ttu-id="d4259-131">Poniższy przykład określa, czy znak wejściowy jest mała litera, wielką literą lub cyfrą.</span><span class="sxs-lookup"><span data-stu-id="d4259-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="d4259-132">Jeśli wszystkie trzy warunki false, znak nie jest znakiem alfanumerycznym.</span><span class="sxs-lookup"><span data-stu-id="d4259-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="d4259-133">Przykład wyświetla komunikat dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="d4259-133">The example displays a message for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 <span data-ttu-id="d4259-134">Tak samo, jak instrukcji else bloku lub następnie bloku może być dowolnym prawidłową instrukcję, używając dowolne prawidłowe wyrażenie logiczne dla warunku.</span><span class="sxs-lookup"><span data-stu-id="d4259-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="d4259-135">Można użyć operatorów logicznych, takich jak [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md), [ & ](../../../csharp/language-reference/operators/and-operator.md), [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md), [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) i [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="d4259-135">You can use logical operators such as [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="d4259-136">Aby można było złożonych warunków.</span><span class="sxs-lookup"><span data-stu-id="d4259-136">to make compound conditions.</span></span> <span data-ttu-id="d4259-137">Poniższy kod przedstawia przykłady.</span><span class="sxs-lookup"><span data-stu-id="d4259-137">The following code shows examples.</span></span>  
  
```csharp  
// NOT  
bool result = true;  
if (!result)  
{  
    Console.WriteLine("The condition is true (result is false).");  
}  
else  
{  
    Console.WriteLine("The condition is false (result is true).");  
}  
  
// Short-circuit AND  
int m = 9;  
int n = 7;  
int p = 5;  
if (m >= n && m >= p)  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// AND and NOT  
if (m >= n && !(p > m))  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// Short-circuit OR  
if (m > n || m > p)  
{  
    Console.WriteLine("m isn't the smallest.");  
}  
  
// NOT and OR  
m = 4;  
if (!(m >= n || m >= p))  
{  
    Console.WriteLine("Now m is the smallest.");  
}  
// Output:  
// The condition is false (result is true).  
// Nothing is larger than m.  
// Nothing is larger than m.  
// m isn't the smallest.  
// Now m is the smallest.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="d4259-138">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d4259-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4259-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4259-139">See Also</span></span>  
 [<span data-ttu-id="d4259-140">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d4259-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d4259-141">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d4259-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d4259-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d4259-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d4259-143">?:, operator</span><span class="sxs-lookup"><span data-stu-id="d4259-143">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="d4259-144">if-else, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="d4259-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)  
 [<span data-ttu-id="d4259-145">switch</span><span class="sxs-lookup"><span data-stu-id="d4259-145">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
