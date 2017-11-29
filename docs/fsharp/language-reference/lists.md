---
title: Listy (F#)
description: "Dowiedz się więcej na temat języka F # list, uporządkowany i modyfikować szereg elementów tego samego typu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a1a6075f-064d-4aee-8222-2b59ff16cc12
ms.openlocfilehash: 5802a5a1c48ad05c1765c4c0fa2e8a81a92dee8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="lists"></a><span data-ttu-id="26957-104">Listy</span><span class="sxs-lookup"><span data-stu-id="26957-104">Lists</span></span>

> [!NOTE]
<span data-ttu-id="26957-105">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="26957-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="26957-106">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="26957-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="26957-107">Na liście w F # jest uporządkowany i modyfikować szereg elementów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="26957-107">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="26957-108">Aby wykonywać podstawowe operacje na listach, użyj funkcji w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="26957-108">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>


## <a name="creating-and-initializing-lists"></a><span data-ttu-id="26957-109">Tworzenie i Inicjowanie listy</span><span class="sxs-lookup"><span data-stu-id="26957-109">Creating and Initializing Lists</span></span>
<span data-ttu-id="26957-110">Aby zdefiniować listę, należy jawnie wyświetlania się elementy, oddzielając je średnikami i ujęte w nawiasy kwadratowe, jak pokazano w następującym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="26957-110">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="26957-111">Można również wprowadzić podziałów między elementami, w którym to przypadku średniki są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="26957-111">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="26957-112">Ostatnie składni może spowodować czytelność kodu, gdy wyrażenia inicjowania elementów są dłuższe lub gdy chcesz dołączyć komentarz dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="26957-112">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="26957-113">Zwykle wszystkie elementy listy muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="26957-113">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="26957-114">Wyjątkiem jest listy, w jakiej elementy są określane jako typu podstawowego, może mieć elementów, które są typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="26957-114">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="26957-115">W związku z tym następujące jest dopuszczalne, ponieważ zarówno `Button` i `CheckBox` pochodzi od `Control`.</span><span class="sxs-lookup"><span data-stu-id="26957-115">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="26957-116">Można również definiować listy elementów za pomocą zakres wskazywany przez liczb całkowitych rozdzielonych operatora zakresu (`..`), jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="26957-116">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="26957-117">Pusta lista jest określana przez parę nawiasy kwadratowe bez żadnych składników między nimi.</span><span class="sxs-lookup"><span data-stu-id="26957-117">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="26957-118">Umożliwia utworzenie listy, można użyć wyrażenia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="26957-118">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="26957-119">Zobacz [wyrażenia sekwencji](sequences.md#sequence-expressions) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="26957-119">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="26957-120">Na przykład poniższy kod tworzy listę kwadratów liczb całkowitych od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="26957-120">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="26957-121">Operatory do pracy z listy</span><span class="sxs-lookup"><span data-stu-id="26957-121">Operators for Working with Lists</span></span>
<span data-ttu-id="26957-122">Możesz dołączyć elementy do listy przy użyciu `::` — operator (wad).</span><span class="sxs-lookup"><span data-stu-id="26957-122">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="26957-123">Jeśli `list1` jest `[2; 3; 4]`, poniższy kod tworzy `list2` jako `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="26957-123">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="26957-124">Można połączyć listy, które mają niezgodne typy przy użyciu `@` operatora, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="26957-124">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="26957-125">Jeśli `list1` jest `[2; 3; 4]` i `list2` jest `[100; 2; 3; 4 ]`, ten kod tworzy `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="26957-125">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="26957-126">Funkcje do wykonywania operacji na listach są dostępne w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="26957-126">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="26957-127">Ponieważ listy w języku F # są niezmienne, wszystkie operacje modyfikowania wygenerować nowe listy zamiast modyfikowania istniejących list.</span><span class="sxs-lookup"><span data-stu-id="26957-127">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="26957-128">Listy w F # są zaimplementowane jako list połączonych pojedynczo, co oznacza, że operacje, które uzyskują dostęp tylko head listy są O(1), i dostęp do elementu jest O (*n*).</span><span class="sxs-lookup"><span data-stu-id="26957-128">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>


## <a name="properties"></a><span data-ttu-id="26957-129">Właściwości</span><span class="sxs-lookup"><span data-stu-id="26957-129">Properties</span></span>
<span data-ttu-id="26957-130">Typ listy obsługuje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="26957-130">The list type supports the following properties:</span></span>

|<span data-ttu-id="26957-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="26957-131">Property</span></span>|<span data-ttu-id="26957-132">Typ</span><span class="sxs-lookup"><span data-stu-id="26957-132">Type</span></span>|<span data-ttu-id="26957-133">Opis</span><span class="sxs-lookup"><span data-stu-id="26957-133">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="26957-134">HEAD</span><span class="sxs-lookup"><span data-stu-id="26957-134">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="26957-135">Pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="26957-135">The first element.</span></span>|
|[<span data-ttu-id="26957-136">Pusty</span><span class="sxs-lookup"><span data-stu-id="26957-136">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="26957-137">Właściwości statyczne, która zwraca pustą listę odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="26957-137">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="26957-138">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="26957-138">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="26957-139">`true`Jeśli na liście nie ma żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="26957-139">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="26957-140">Element</span><span class="sxs-lookup"><span data-stu-id="26957-140">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="26957-141">Element pod określony indeks (liczony od zera).</span><span class="sxs-lookup"><span data-stu-id="26957-141">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="26957-142">Długość</span><span class="sxs-lookup"><span data-stu-id="26957-142">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="26957-143">Liczba elementów.</span><span class="sxs-lookup"><span data-stu-id="26957-143">The number of elements.</span></span>|
|[<span data-ttu-id="26957-144">Tail</span><span class="sxs-lookup"><span data-stu-id="26957-144">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="26957-145">Lista bez pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="26957-145">The list without the first element.</span></span>|
<span data-ttu-id="26957-146">Poniżej przedstawiono kilka przykładów użycia tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="26957-146">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a><span data-ttu-id="26957-147">Używanie list</span><span class="sxs-lookup"><span data-stu-id="26957-147">Using Lists</span></span>
<span data-ttu-id="26957-148">Programowanie przy użyciu list umożliwia wykonywanie złożonych operacji z małej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="26957-148">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="26957-149">W tej sekcji opisano typowe operacje na listach, które są ważne dla programowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="26957-149">This section describes common operations on lists that are important to functional programming.</span></span>


### <a name="recursion-with-lists"></a><span data-ttu-id="26957-150">Rekursja z listy</span><span class="sxs-lookup"><span data-stu-id="26957-150">Recursion with Lists</span></span>
<span data-ttu-id="26957-151">Listy są dostosowane do cyklicznego technik programowania.</span><span class="sxs-lookup"><span data-stu-id="26957-151">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="26957-152">Należy wziąć pod uwagę operacji, które należy wykonać dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="26957-152">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="26957-153">Można nie tego rekursywnie działających na head listy, a następnie przekazywanie tail listy, czyli listę mniejszych, która składa się z oryginalnej listy bez pierwszy element, z powrotem na następny poziom rekursji.</span><span class="sxs-lookup"><span data-stu-id="26957-153">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="26957-154">Aby napisać funkcję rekursywną, możesz użyć operatora wad (`::`) w dopasowania wzorca, który umożliwia head listy z końcowego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="26957-154">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="26957-155">Poniższy przykład kodu pokazuje, jak na potrzeby dopasowywania do wzorca implementacji funkcji cyklicznej, która wykonuje operacje na liście.</span><span class="sxs-lookup"><span data-stu-id="26957-155">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="26957-156">Poprzedni kod działa dobrze w przypadku małych list, ale większych list można przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="26957-156">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="26957-157">Poniższy kod poprawia dla tego kodu za pomocą argumentu akumulatora standardowa metoda do pracy z funkcjami cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="26957-157">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="26957-158">Użycie argumentu akumulatora sprawia, że funkcję z rekursją ogonową, która zapisuje miejsca na stosie.</span><span class="sxs-lookup"><span data-stu-id="26957-158">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="26957-159">Funkcja `RemoveAllMultiples` to funkcja cykliczne, która ma dwie listy.</span><span class="sxs-lookup"><span data-stu-id="26957-159">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="26957-160">Pierwsza lista może zawierać cyfry, w których wielokrotności zostaną usunięte, a druga lista znajduje się lista, z którego mają zostać usunięte liczby.</span><span class="sxs-lookup"><span data-stu-id="26957-160">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="26957-161">Kod w poniższym przykładzie funkcja tego cyklicznego wyeliminowanie wszystkich innych niż — pierwszych liczb z listy, pozostawiając listę liczb pierwszych w wyniku.</span><span class="sxs-lookup"><span data-stu-id="26957-161">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="26957-162">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-162">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="26957-163">Moduł funkcji</span><span class="sxs-lookup"><span data-stu-id="26957-163">Module Functions</span></span>
<span data-ttu-id="26957-164">[Modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) udostępnia funkcje, które uzyskują dostęp do elementów listy.</span><span class="sxs-lookup"><span data-stu-id="26957-164">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="26957-165">Head element jest najszybszym i najprostszym dostępu do.</span><span class="sxs-lookup"><span data-stu-id="26957-165">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="26957-166">Użyj właściwości [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) lub funkcji modułu [list.HEAD —](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="26957-166">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="26957-167">Tail listy mogą korzystać za pomocą [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) właściwości lub [list.tail —](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkcji.</span><span class="sxs-lookup"><span data-stu-id="26957-167">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="26957-168">Aby znaleźć element przez indeks, użyj [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkcji.</span><span class="sxs-lookup"><span data-stu-id="26957-168">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="26957-169">`List.nth`listy są przesyłane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="26957-169">`List.nth` traverses the list.</span></span> <span data-ttu-id="26957-170">Dlatego jest O (*n*).</span><span class="sxs-lookup"><span data-stu-id="26957-170">Therefore, it is O(*n*).</span></span> <span data-ttu-id="26957-171">Jeśli używa Twój kod `List.nth` często, warto rozważyć użycie tablicy zamiast listy.</span><span class="sxs-lookup"><span data-stu-id="26957-171">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="26957-172">Dostęp do elementu w tablicach jest O(1).</span><span class="sxs-lookup"><span data-stu-id="26957-172">Element access in arrays is O(1).</span></span>


### <a name="boolean-operations-on-lists"></a><span data-ttu-id="26957-173">Operacji logicznych na listach</span><span class="sxs-lookup"><span data-stu-id="26957-173">Boolean Operations on Lists</span></span>
<span data-ttu-id="26957-174">[List.IsEmpty —](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkcji określa, czy lista ma żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="26957-174">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="26957-175">[List.EXISTS —](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) wartość logiczna ma zastosowanie funkcja testów elementów listy i zwraca `true` Jeśli dowolny element spełnia testu.</span><span class="sxs-lookup"><span data-stu-id="26957-175">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="26957-176">[List.exists2 —](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) jest podobny, ale działa na kolejnych pary elementów listy.</span><span class="sxs-lookup"><span data-stu-id="26957-176">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="26957-177">Poniższy kod przedstawia użycie `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="26957-177">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="26957-178">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-178">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="26957-179">W poniższym przykładzie pokazano użycie `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="26957-179">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="26957-180">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-180">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="26957-181">Można użyć [list.ForAll —](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Jeśli chcesz sprawdzić, czy wszystkie elementy z listy spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="26957-181">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="26957-182">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-182">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="26957-183">Podobnie [list.forall2 —](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Określa, czy wszystkie elementy w odpowiednich miejscach w dwie listy spełniają wyrażenie logiczne, która obejmuje każda para elementów.</span><span class="sxs-lookup"><span data-stu-id="26957-183">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="26957-184">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-184">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="26957-185">Sortowanie na listach</span><span class="sxs-lookup"><span data-stu-id="26957-185">Sort Operations on Lists</span></span>
<span data-ttu-id="26957-186">[List.sort —](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list.sortby —](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), i [list.sortwith —](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkcje sortować listy.</span><span class="sxs-lookup"><span data-stu-id="26957-186">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="26957-187">Funkcja sortowania określa, która z tych trzech funkcji do użycia.</span><span class="sxs-lookup"><span data-stu-id="26957-187">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="26957-188">`List.sort`korzysta z domyślnego ogólnego porównania.</span><span class="sxs-lookup"><span data-stu-id="26957-188">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="26957-189">Porównanie ogólnego używa operatorów globalnych na podstawie ogólnego porównanie funkcji do porównywania wartości.</span><span class="sxs-lookup"><span data-stu-id="26957-189">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="26957-190">Działa wydajnie wiele różnych typów elementów, takich jak proste typy liczbowe, krotek rekordów, rozłączne, list, tablic i dowolnego typu, który implementuje `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="26957-190">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="26957-191">Dla typów które implementują `System.IComparable`, używa standardowego porównania `System.IComparable.CompareTo()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="26957-191">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="26957-192">Porównanie ogólnego również działa z ciągów, ale używa sortowania niezależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="26957-192">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="26957-193">Porównanie ogólnych nie powinien być używany w nieobsługiwanych typów, takie jak typy funkcji.</span><span class="sxs-lookup"><span data-stu-id="26957-193">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="26957-194">Ponadto wydajność domyślnym porównaniem ogólnego jest najlepsze dla małych typów strukturalnych. dla większych strukturalnych typów, które muszą być porównywane i sortowane często, rozważ zaimplementowanie `System.IComparable` i wydajne implementacja `System.IComparable.CompareTo()` metody.</span><span class="sxs-lookup"><span data-stu-id="26957-194">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="26957-195">`List.sortBy`pobiera funkcję, która zwraca wartość, która jest używana jako kryterium sortowania i `List.sortWith` przyjmuje jako argument funkcji porównania.</span><span class="sxs-lookup"><span data-stu-id="26957-195">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="26957-196">Te dwie funkcje te ostatnie są przydatne podczas pracy z typami, które nie obsługują porównywania lub kiedy porównanie wymaga bardziej złożonej semantykę porównania, tak jak w przypadku ciągi kultury aware.</span><span class="sxs-lookup"><span data-stu-id="26957-196">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="26957-197">W poniższym przykładzie pokazano użycie `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="26957-197">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="26957-198">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-198">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="26957-199">W poniższym przykładzie pokazano użycie `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="26957-199">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="26957-200">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-200">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="26957-201">W następnym przykładzie pokazano użycie `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="26957-201">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="26957-202">W tym przykładzie funkcja porównywania niestandardowych `compareWidgets` służy do porównywania najpierw jedno pole typu niestandardowego oraz gdy następnie inne wartości pierwszego pola są takie same.</span><span class="sxs-lookup"><span data-stu-id="26957-202">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="26957-203">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-203">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="26957-204">Operacje wyszukiwania na listach</span><span class="sxs-lookup"><span data-stu-id="26957-204">Search Operations on Lists</span></span>
<span data-ttu-id="26957-205">Wiele operacji wyszukiwania są obsługiwane dla listy.</span><span class="sxs-lookup"><span data-stu-id="26957-205">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="26957-206">Najprostsza, [list.Find —](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umożliwia znalezienie pierwszy element, który odpowiada dany warunek.</span><span class="sxs-lookup"><span data-stu-id="26957-206">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="26957-207">Poniższy przykład kodu pokazuje użycie `List.find` można znaleźć pierwszego liczba, która jest podzielna przez 5 na liście.</span><span class="sxs-lookup"><span data-stu-id="26957-207">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="26957-208">Wynik wynosi 5.</span><span class="sxs-lookup"><span data-stu-id="26957-208">The result is 5.</span></span>

<span data-ttu-id="26957-209">Jeśli najpierw musi zostać przekształcone elementy, wywołanie [list.Pick —](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)używającą funkcja zwraca opcję i wygląda pierwszej opcji wartość, która jest `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="26957-209">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="26957-210">Zamiast zwracać elementu `List.pick` zwraca wynik `x`.</span><span class="sxs-lookup"><span data-stu-id="26957-210">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="26957-211">Jeśli nie zostanie znaleziony, `List.pick` zgłasza `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="26957-211">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="26957-212">Poniższy kod przedstawia użycie `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="26957-212">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="26957-213">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-213">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="26957-214">Innej grupy operacji wyszukiwania [list.tryfind —](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) i powiązane funkcje zwracają wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="26957-214">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="26957-215">`List.tryFind` Funkcja zwraca pierwszy element listy, która spełnia warunek, jeśli taki element istnieje, ale wartość opcji `None` , jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="26957-215">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="26957-216">Zmiana [list.tryfindindex —](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) zwraca indeks elementu, jeśli został znaleziony, a nie samego elementu.</span><span class="sxs-lookup"><span data-stu-id="26957-216">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="26957-217">Te funkcje zostały przedstawione w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="26957-217">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="26957-218">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-218">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="26957-219">Operacje arytmetyczne na listach</span><span class="sxs-lookup"><span data-stu-id="26957-219">Arithmetic Operations on Lists</span></span>
<span data-ttu-id="26957-220">Typowe operacje arytmetyczne, takie jak sum i średniej są wbudowane w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="26957-220">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="26957-221">Aby pracować z [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), musi obsługiwać typ elementu listy `+` operatora i mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="26957-221">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="26957-222">Wszystkie wbudowanych typów arytmetycznych spełnia te warunki.</span><span class="sxs-lookup"><span data-stu-id="26957-222">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="26957-223">Aby pracować z [list.AVERAGE —](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musi obsługiwać dzielenia bez reszty, co wyklucza typy całkowite, ale pozwala na liczby zmiennoprzecinkowe typy punktów.</span><span class="sxs-lookup"><span data-stu-id="26957-223">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="26957-224">[List.sumby —](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) i [list.averageby —](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkcje pobierać funkcji jako parametr, a wyniki tej funkcji są używane do obliczania wartości sum lub średnia.</span><span class="sxs-lookup"><span data-stu-id="26957-224">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="26957-225">Poniższy kod przedstawia użycie `List.sum`, `List.sumBy`, i `List.average`.</span><span class="sxs-lookup"><span data-stu-id="26957-225">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="26957-226">Dane wyjściowe `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="26957-226">The output is `1.000000`.</span></span>

<span data-ttu-id="26957-227">Poniższy kod przedstawia użycie `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="26957-227">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="26957-228">Dane wyjściowe `5.5`.</span><span class="sxs-lookup"><span data-stu-id="26957-228">The output is `5.5`.</span></span>


### <a name="lists-and-tuples"></a><span data-ttu-id="26957-229">Listy i spójnych kolekcji</span><span class="sxs-lookup"><span data-stu-id="26957-229">Lists and Tuples</span></span>
<span data-ttu-id="26957-230">Listy zawierające krotek może manipulować zip i Rozpakuj funkcji.</span><span class="sxs-lookup"><span data-stu-id="26957-230">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="26957-231">Te funkcje Połącz dwie listy pojedynczych wartości na jednej liście krotek lub podzielić jedną listę krotek na dwóch list z jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="26957-231">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="26957-232">Najprostszą [list.zip —](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkcja przyjmuje dwa listę elementów jednego i tworzy jedną listę par spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="26957-232">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="26957-233">Inna wersja [list.zip3 —](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), przyjmuje trzy listę elementów jednego i tworzy jedną listę krotek, które mają trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="26957-233">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="26957-234">Poniższy przykład kodu pokazuje użycie `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="26957-234">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="26957-235">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-235">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="26957-236">Poniższy przykład kodu pokazuje użycie `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="26957-236">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="26957-237">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-237">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="26957-238">Odpowiednie Rozpakuj wersje, [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) i [list.unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), wykonaj listę krotek i zwróć list w spójnej kolekcji, których pierwsza lista zawiera wszystkie elementy, które zostały po raz pierwszy w każdej krotki i druga lista zawiera drugi element każda krotka i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="26957-238">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="26957-239">Poniższy przykład kodu pokazuje użycie [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="26957-239">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="26957-240">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-240">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="26957-241">Poniższy przykład kodu pokazuje użycie [list.unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="26957-241">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="26957-242">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-242">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="26957-243">Na liście elementów</span><span class="sxs-lookup"><span data-stu-id="26957-243">Operating on List Elements</span></span>
<span data-ttu-id="26957-244">F # obsługuje wiele operacji na liście elementów.</span><span class="sxs-lookup"><span data-stu-id="26957-244">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="26957-245">Najprostszą jest [list.ITER —](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), co umożliwia wywołać funkcję dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="26957-245">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="26957-246">Zmiany obejmują [list.iter2 —](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), który umożliwia wykonywanie operacji w elementach dwie listy [list.iteri —](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), czyli jak `List.iter` z tą różnicą, że indeks każdego elementu jest przekazywany jako argument do funkcji, która jest wywoływana dla każdego elementu i [list.iteri2 —](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), który jest kombinacją funkcji `List.iter2` i `List.iteri`.</span><span class="sxs-lookup"><span data-stu-id="26957-246">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="26957-247">Poniższy przykład kodu pokazuje tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="26957-247">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="26957-248">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-248">The output is as follows:</span></span>

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="26957-249">Inną funkcję często używanych, który przekształca elementów listy jest [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), dzięki czemu można zastosować funkcji do każdego elementu listy i wszystkie wyniki do nowej listy.</span><span class="sxs-lookup"><span data-stu-id="26957-249">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="26957-250">[List.map2 —](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) i [list.map3 —](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) są zmiany, które przyjmują wielu list.</span><span class="sxs-lookup"><span data-stu-id="26957-250">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="26957-251">Można również użyć [list.MAPI —](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) i [list.mapi2 —](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), jeśli oprócz elementu, funkcja musi być przekazywany indeks każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="26957-251">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="26957-252">Jedyną różnicą między `List.mapi2` i `List.mapi` jest to, że `List.mapi2` współpracuje z listy.</span><span class="sxs-lookup"><span data-stu-id="26957-252">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="26957-253">Poniższy przykład przedstawia [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="26957-253">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="26957-254">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-254">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="26957-255">W poniższym przykładzie przedstawiono użycie `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="26957-255">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="26957-256">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-256">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="26957-257">W poniższym przykładzie przedstawiono użycie `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="26957-257">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="26957-258">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-258">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="26957-259">W poniższym przykładzie przedstawiono użycie `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="26957-259">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="26957-260">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-260">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="26957-261">W poniższym przykładzie przedstawiono użycie `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="26957-261">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="26957-262">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-262">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="26957-263">[List.Collect —](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) przypomina `List.map`, z wyjątkiem, że każdy element tworzy listę i te listy są połączone w listą końcową.</span><span class="sxs-lookup"><span data-stu-id="26957-263">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="26957-264">W poniższym kodzie każdego elementu listy generuje trzech cyfr.</span><span class="sxs-lookup"><span data-stu-id="26957-264">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="26957-265">Te są wszystkie zebrane na jednej liście.</span><span class="sxs-lookup"><span data-stu-id="26957-265">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="26957-266">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-266">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="26957-267">Można również użyć [list.filter —](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), która przyjmuje warunek typu Boolean i tworzy nową listę, która zawiera tylko elementy, które spełniają dany warunek.</span><span class="sxs-lookup"><span data-stu-id="26957-267">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="26957-268">Wynikowa lista jest `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="26957-268">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="26957-269">Kombinację mapy i Filtruj [list.Choose —](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) pozwala na przekształcanie i wybierz elementy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="26957-269">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="26957-270">`List.choose`stosuje funkcję, która zwraca opcji do każdego elementu listy i zwraca nową listę wyników dla elementów, gdy funkcja zwraca wartość opcji `Some`.</span><span class="sxs-lookup"><span data-stu-id="26957-270">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="26957-271">Poniższy kod przedstawia użycie `List.choose` aby zaznaczyć pisanymi wielkimi literami wyrazy poza listę słów.</span><span class="sxs-lookup"><span data-stu-id="26957-271">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="26957-272">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="26957-272">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="26957-273">Korzysta z wielu list</span><span class="sxs-lookup"><span data-stu-id="26957-273">Operating on Multiple Lists</span></span>
<span data-ttu-id="26957-274">Listy można łączyć ze sobą.</span><span class="sxs-lookup"><span data-stu-id="26957-274">Lists can be joined together.</span></span> <span data-ttu-id="26957-275">Aby przyłączyć się do jednego dwie listy, użyj [list.append —](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="26957-275">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="26957-276">Aby dołączyć więcej niż dwie listy, użyj [list.concat —](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="26957-276">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a><span data-ttu-id="26957-277">Składanie i operacji skanowania</span><span class="sxs-lookup"><span data-stu-id="26957-277">Fold and Scan Operations</span></span>
<span data-ttu-id="26957-278">Niektóre operacje listy obejmują zależności między wszystkie elementy z listy.</span><span class="sxs-lookup"><span data-stu-id="26957-278">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="26957-279">Operacje złożenia i skanowania są podobne do `List.iter` i `List.map` , wywołaj funkcję dla każdego elementu, ale te operacje zapewnia dodatkowy parametr o nazwie *akumulatora* który przenosi informacje za pomocą obliczenia.</span><span class="sxs-lookup"><span data-stu-id="26957-279">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="26957-280">Użyj `List.fold` do przeprowadzenia obliczeń na listę.</span><span class="sxs-lookup"><span data-stu-id="26957-280">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="26957-281">Poniższy przykład kodu pokazuje użycie [list.fold —](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) do wykonywania różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="26957-281">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="26957-282">Lista jest przesunięta; akumulatora `acc` to wartość, która jest przekazywane w trakcie wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="26957-282">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="26957-283">Pierwszy argument akumulatora i elementu listy i zwraca wynik tymczasowe obliczeń dla tego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="26957-283">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="26957-284">Drugi argument jest wartością początkową akumulatora.</span><span class="sxs-lookup"><span data-stu-id="26957-284">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="26957-285">Wersje te funkcje, które mają cyfrę w nazwie funkcji działać na więcej niż jedną listę.</span><span class="sxs-lookup"><span data-stu-id="26957-285">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="26957-286">Na przykład [list.fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) wykonuje obliczenia na dwie listy.</span><span class="sxs-lookup"><span data-stu-id="26957-286">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="26957-287">W poniższym przykładzie pokazano użycie `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="26957-287">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="26957-288">`List.fold`i [list.Scan —](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) różnią się w tym `List.fold` zwraca końcowa wartość dodatkowy parametr, ale `List.scan` zwraca listę wartości pośrednich (wraz z końcowej) z dodatkowym parametrem.</span><span class="sxs-lookup"><span data-stu-id="26957-288">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="26957-289">Każda z tych funkcji obejmuje odwrotnej zmiany, na przykład [list.foldback —](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), który różni się w kolejności, w której przecina listy i kolejność argumentów.</span><span class="sxs-lookup"><span data-stu-id="26957-289">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="26957-290">Ponadto `List.fold` i `List.foldBack` ma zmian, [list.fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) i [list.foldback2 —](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), które wymagają dwie listy o równej długości.</span><span class="sxs-lookup"><span data-stu-id="26957-290">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="26957-291">Funkcja wykonująca na każdym elemencie może być wykonanie akcji odpowiednie elementy obu list.</span><span class="sxs-lookup"><span data-stu-id="26957-291">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="26957-292">Typy elementu dwie listy mogą być różne, jak w poniższym przykładzie, w której jedna lista zawiera kwoty transakcji dla konta bankowego, i inne lista zawiera typ transakcji: złożenia lub wycofania.</span><span class="sxs-lookup"><span data-stu-id="26957-292">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="26957-293">Do obliczenia, takich jak podsumowania `List.fold` i `List.foldBack` mają ten sam efekt, ponieważ wynik nie zależy od rzędu przechodzenie.</span><span class="sxs-lookup"><span data-stu-id="26957-293">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="26957-294">W poniższym przykładzie `List.foldBack` służy do dodawania elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="26957-294">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="26957-295">Poniższy przykład zwraca przykład konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="26957-295">The following example returns to the bank account example.</span></span> <span data-ttu-id="26957-296">Teraz zostanie dodany nowy typ transakcji: Obliczanie odsetek.</span><span class="sxs-lookup"><span data-stu-id="26957-296">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="26957-297">Saldo końcowe zależy od teraz rzędu transakcji.</span><span class="sxs-lookup"><span data-stu-id="26957-297">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="26957-298">Funkcja [list.Reduce —](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) jest nieco jak `List.fold` i `List.scan`, ale zamiast przekazywanie wokół oddzielne akumulatora, `List.reduce` przyjmuje funkcję, która przyjmuje dwa argumenty typu zamiast elementu tylko jeden, a jeden z tych argumentów działa jako akumulatora, co oznacza przechowuje pośredni wynikiem obliczenia.</span><span class="sxs-lookup"><span data-stu-id="26957-298">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="26957-299">`List.reduce`rozpoczyna się od działających na pierwszych dwóch listy elementów, a następnie używa wynik operacji wraz z następnym elementem.</span><span class="sxs-lookup"><span data-stu-id="26957-299">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="26957-300">Ponieważ nie jest osobnym akumulatora, który ma swój własny typ `List.reduce` można użyć zamiast `List.fold` tylko gdy akumulatora i typ elementu być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="26957-300">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="26957-301">Poniższy kod przedstawia użycie `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="26957-301">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="26957-302">`List.reduce`zgłasza wyjątek, jeśli nie ma żadnych elementów listy.</span><span class="sxs-lookup"><span data-stu-id="26957-302">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="26957-303">W poniższym kodzie pierwsze wywołanie w celu wyrażenia lambda podano argumenty 2 i 4 i zwraca 6 i następnego wywołania podano argumenty, 6, 10, dlatego 16.</span><span class="sxs-lookup"><span data-stu-id="26957-303">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="26957-304">Konwertowanie pomiędzy listy i inne typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="26957-304">Converting Between Lists and Other Collection Types</span></span>
<span data-ttu-id="26957-305">`List` Moduł zapewnia funkcje do konwertowania do i z tablic i sekwencji.</span><span class="sxs-lookup"><span data-stu-id="26957-305">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="26957-306">Aby dokonać konwersji do lub z sekwencją, użyj [list.toseq —](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) lub [list.ofseq —](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="26957-306">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="26957-307">Aby dokonać konwersji do lub z tablicy, należy użyć [list.toarray —](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) lub [list.ofarray —](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="26957-307">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>


### <a name="additional-operations"></a><span data-ttu-id="26957-308">Dodatkowe operacje</span><span class="sxs-lookup"><span data-stu-id="26957-308">Additional Operations</span></span>
<span data-ttu-id="26957-309">Informacje dodatkowe operacje na listach, zobacz temat odwołanie do biblioteki [Collections.list — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="26957-309">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>


## <a name="see-also"></a><span data-ttu-id="26957-310">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26957-310">See Also</span></span>
[<span data-ttu-id="26957-311">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="26957-311">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="26957-312">Typy F #</span><span class="sxs-lookup"><span data-stu-id="26957-312">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="26957-313">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="26957-313">Sequences</span></span>](sequences.md)

[<span data-ttu-id="26957-314">Tablice</span><span class="sxs-lookup"><span data-stu-id="26957-314">Arrays</span></span>](arrays.md)

[<span data-ttu-id="26957-315">Opcje</span><span class="sxs-lookup"><span data-stu-id="26957-315">Options</span></span>](options.md)
