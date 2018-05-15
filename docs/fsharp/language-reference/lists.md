---
title: Listy (F#)
description: 'Dowiedz się więcej na temat języka F # list, uporządkowany i modyfikować szereg elementów tego samego typu.'
ms.date: 05/16/2016
ms.openlocfilehash: ea86b3ca94c6414bf5ab60406452f3604838075a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lists"></a><span data-ttu-id="7ff6a-103">Listy</span><span class="sxs-lookup"><span data-stu-id="7ff6a-103">Lists</span></span>

> [!NOTE]
<span data-ttu-id="7ff6a-104">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="7ff6a-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="7ff6a-106">Na liście w F # jest uporządkowany i modyfikować szereg elementów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-106">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="7ff6a-107">Aby wykonywać podstawowe operacje na listach, użyj funkcji w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-107">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>


## <a name="creating-and-initializing-lists"></a><span data-ttu-id="7ff6a-108">Tworzenie i Inicjowanie listy</span><span class="sxs-lookup"><span data-stu-id="7ff6a-108">Creating and Initializing Lists</span></span>
<span data-ttu-id="7ff6a-109">Aby zdefiniować listę, należy jawnie wyświetlania się elementy, oddzielając je średnikami i ujęte w nawiasy kwadratowe, jak pokazano w następującym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="7ff6a-110">Można również wprowadzić podziałów między elementami, w którym to przypadku średniki są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="7ff6a-111">Ostatnie składni może spowodować czytelność kodu, gdy wyrażenia inicjowania elementów są dłuższe lub gdy chcesz dołączyć komentarz dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="7ff6a-112">Zwykle wszystkie elementy listy muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="7ff6a-113">Wyjątkiem jest listy, w jakiej elementy są określane jako typu podstawowego, może mieć elementów, które są typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="7ff6a-114">W związku z tym następujące jest dopuszczalne, ponieważ zarówno `Button` i `CheckBox` pochodzi od `Control`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="7ff6a-115">Można również definiować listy elementów za pomocą zakres wskazywany przez liczb całkowitych rozdzielonych operatora zakresu (`..`), jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="7ff6a-116">Pusta lista jest określana przez parę nawiasy kwadratowe bez żadnych składników między nimi.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="7ff6a-117">Umożliwia utworzenie listy, można użyć wyrażenia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="7ff6a-118">Zobacz [wyrażenia sekwencji](sequences.md#sequence-expressions) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="7ff6a-119">Na przykład poniższy kod tworzy listę kwadratów liczb całkowitych od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="7ff6a-120">Operatory do pracy z listy</span><span class="sxs-lookup"><span data-stu-id="7ff6a-120">Operators for Working with Lists</span></span>
<span data-ttu-id="7ff6a-121">Możesz dołączyć elementy do listy przy użyciu `::` — operator (wad).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="7ff6a-122">Jeśli `list1` jest `[2; 3; 4]`, poniższy kod tworzy `list2` jako `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="7ff6a-123">Można połączyć listy, które mają niezgodne typy przy użyciu `@` operatora, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="7ff6a-124">Jeśli `list1` jest `[2; 3; 4]` i `list2` jest `[100; 2; 3; 4 ]`, ten kod tworzy `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="7ff6a-125">Funkcje do wykonywania operacji na listach są dostępne w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="7ff6a-126">Ponieważ listy w języku F # są niezmienne, wszystkie operacje modyfikowania wygenerować nowe listy zamiast modyfikowania istniejących list.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="7ff6a-127">Listy w F # są zaimplementowane jako list połączonych pojedynczo, co oznacza, że operacje, które uzyskują dostęp tylko head listy są O(1), i dostęp do elementu jest O (*n*).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>


## <a name="properties"></a><span data-ttu-id="7ff6a-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7ff6a-128">Properties</span></span>
<span data-ttu-id="7ff6a-129">Typ listy obsługuje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="7ff6a-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7ff6a-130">Property</span></span>|<span data-ttu-id="7ff6a-131">Typ</span><span class="sxs-lookup"><span data-stu-id="7ff6a-131">Type</span></span>|<span data-ttu-id="7ff6a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="7ff6a-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="7ff6a-133">HEAD</span><span class="sxs-lookup"><span data-stu-id="7ff6a-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="7ff6a-134">Pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-134">The first element.</span></span>|
|[<span data-ttu-id="7ff6a-135">pusty</span><span class="sxs-lookup"><span data-stu-id="7ff6a-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="7ff6a-136">Właściwości statyczne, która zwraca pustą listę odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="7ff6a-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="7ff6a-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="7ff6a-138">`true` Jeśli na liście nie ma żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="7ff6a-139">Element</span><span class="sxs-lookup"><span data-stu-id="7ff6a-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="7ff6a-140">Element pod określony indeks (liczony od zera).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="7ff6a-141">długość</span><span class="sxs-lookup"><span data-stu-id="7ff6a-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="7ff6a-142">Liczba elementów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-142">The number of elements.</span></span>|
|[<span data-ttu-id="7ff6a-143">Tail</span><span class="sxs-lookup"><span data-stu-id="7ff6a-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="7ff6a-144">Lista bez pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-144">The list without the first element.</span></span>|
<span data-ttu-id="7ff6a-145">Poniżej przedstawiono kilka przykładów użycia tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a><span data-ttu-id="7ff6a-146">Używanie list</span><span class="sxs-lookup"><span data-stu-id="7ff6a-146">Using Lists</span></span>
<span data-ttu-id="7ff6a-147">Programowanie przy użyciu list umożliwia wykonywanie złożonych operacji z małej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="7ff6a-148">W tej sekcji opisano typowe operacje na listach, które są ważne dla programowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-148">This section describes common operations on lists that are important to functional programming.</span></span>


### <a name="recursion-with-lists"></a><span data-ttu-id="7ff6a-149">Rekursja z listy</span><span class="sxs-lookup"><span data-stu-id="7ff6a-149">Recursion with Lists</span></span>
<span data-ttu-id="7ff6a-150">Listy są dostosowane do cyklicznego technik programowania.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="7ff6a-151">Należy wziąć pod uwagę operacji, które należy wykonać dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="7ff6a-152">Można nie tego rekursywnie działających na head listy, a następnie przekazywanie tail listy, czyli listę mniejszych, która składa się z oryginalnej listy bez pierwszy element, z powrotem na następny poziom rekursji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="7ff6a-153">Aby napisać funkcję rekursywną, możesz użyć operatora wad (`::`) w dopasowania wzorca, który umożliwia head listy z końcowego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="7ff6a-154">Poniższy przykład kodu pokazuje, jak na potrzeby dopasowywania do wzorca implementacji funkcji cyklicznej, która wykonuje operacje na liście.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="7ff6a-155">Poprzedni kod działa dobrze w przypadku małych list, ale większych list można przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="7ff6a-156">Poniższy kod poprawia dla tego kodu za pomocą argumentu akumulatora standardowa metoda do pracy z funkcjami cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="7ff6a-157">Użycie argumentu akumulatora sprawia, że funkcję z rekursją ogonową, która zapisuje miejsca na stosie.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="7ff6a-158">Funkcja `RemoveAllMultiples` to funkcja cykliczne, która ma dwie listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="7ff6a-159">Pierwsza lista może zawierać cyfry, w których wielokrotności zostaną usunięte, a druga lista znajduje się lista, z którego mają zostać usunięte liczby.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="7ff6a-160">Kod w poniższym przykładzie funkcja tego cyklicznego wyeliminowanie wszystkich innych niż — pierwszych liczb z listy, pozostawiając listę liczb pierwszych w wyniku.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="7ff6a-161">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-161">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="7ff6a-162">Moduł funkcji</span><span class="sxs-lookup"><span data-stu-id="7ff6a-162">Module Functions</span></span>
<span data-ttu-id="7ff6a-163">[Modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) udostępnia funkcje, które uzyskują dostęp do elementów listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="7ff6a-164">Head element jest najszybszym i najprostszym dostępu do.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="7ff6a-165">Użyj właściwości [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) lub funkcji modułu [list.HEAD —](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="7ff6a-166">Tail listy mogą korzystać za pomocą [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) właściwości lub [list.tail —](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="7ff6a-167">Aby znaleźć element przez indeks, użyj [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="7ff6a-168">`List.nth` listy są przesyłane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="7ff6a-169">Dlatego jest O (*n*).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="7ff6a-170">Jeśli używa Twój kod `List.nth` często, warto rozważyć użycie tablicy zamiast listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="7ff6a-171">Dostęp do elementu w tablicach jest O(1).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-171">Element access in arrays is O(1).</span></span>


### <a name="boolean-operations-on-lists"></a><span data-ttu-id="7ff6a-172">Operacji logicznych na listach</span><span class="sxs-lookup"><span data-stu-id="7ff6a-172">Boolean Operations on Lists</span></span>
<span data-ttu-id="7ff6a-173">[List.IsEmpty —](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkcji określa, czy lista ma żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="7ff6a-174">[List.EXISTS —](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) wartość logiczna ma zastosowanie funkcja testów elementów listy i zwraca `true` Jeśli dowolny element spełnia testu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="7ff6a-175">[List.exists2 —](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) jest podobny, ale działa na kolejnych pary elementów listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="7ff6a-176">Poniższy kod przedstawia użycie `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="7ff6a-177">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-177">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="7ff6a-178">W poniższym przykładzie pokazano użycie `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="7ff6a-179">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-179">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="7ff6a-180">Można użyć [list.ForAll —](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Jeśli chcesz sprawdzić, czy wszystkie elementy z listy spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="7ff6a-181">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-181">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="7ff6a-182">Podobnie [list.forall2 —](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Określa, czy wszystkie elementy w odpowiednich miejscach w dwie listy spełniają wyrażenie logiczne, która obejmuje każda para elementów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="7ff6a-183">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-183">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="7ff6a-184">Sortowanie na listach</span><span class="sxs-lookup"><span data-stu-id="7ff6a-184">Sort Operations on Lists</span></span>
<span data-ttu-id="7ff6a-185">[List.sort —](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list.sortby —](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), i [list.sortwith —](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkcje sortować listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="7ff6a-186">Funkcja sortowania określa, która z tych trzech funkcji do użycia.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="7ff6a-187">`List.sort` korzysta z domyślnego ogólnego porównania.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="7ff6a-188">Porównanie ogólnego używa operatorów globalnych na podstawie ogólnego porównanie funkcji do porównywania wartości.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="7ff6a-189">Działa wydajnie wiele różnych typów elementów, takich jak proste typy liczbowe, krotek rekordów, rozłączne, list, tablic i dowolnego typu, który implementuje `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="7ff6a-190">Dla typów które implementują `System.IComparable`, używa standardowego porównania `System.IComparable.CompareTo()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="7ff6a-191">Porównanie ogólnego również działa z ciągów, ale używa sortowania niezależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="7ff6a-192">Porównanie ogólnych nie powinien być używany w nieobsługiwanych typów, takie jak typy funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="7ff6a-193">Ponadto wydajność domyślnym porównaniem ogólnego jest najlepsze dla małych typów strukturalnych. dla większych strukturalnych typów, które muszą być porównywane i sortowane często, rozważ zaimplementowanie `System.IComparable` i wydajne implementacja `System.IComparable.CompareTo()` metody.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="7ff6a-194">`List.sortBy` pobiera funkcję, która zwraca wartość, która jest używana jako kryterium sortowania i `List.sortWith` przyjmuje jako argument funkcji porównania.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="7ff6a-195">Te dwie funkcje te ostatnie są przydatne podczas pracy z typami, które nie obsługują porównywania lub kiedy porównanie wymaga bardziej złożonej semantykę porównania, tak jak w przypadku ciągi kultury aware.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="7ff6a-196">W poniższym przykładzie pokazano użycie `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="7ff6a-197">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-197">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="7ff6a-198">W poniższym przykładzie pokazano użycie `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="7ff6a-199">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-199">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="7ff6a-200">W następnym przykładzie pokazano użycie `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="7ff6a-201">W tym przykładzie funkcja porównywania niestandardowych `compareWidgets` służy do porównywania najpierw jedno pole typu niestandardowego oraz gdy następnie inne wartości pierwszego pola są takie same.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="7ff6a-202">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-202">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="7ff6a-203">Operacje wyszukiwania na listach</span><span class="sxs-lookup"><span data-stu-id="7ff6a-203">Search Operations on Lists</span></span>
<span data-ttu-id="7ff6a-204">Wiele operacji wyszukiwania są obsługiwane dla listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="7ff6a-205">Najprostsza, [list.Find —](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umożliwia znalezienie pierwszy element, który odpowiada dany warunek.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="7ff6a-206">Poniższy przykład kodu pokazuje użycie `List.find` można znaleźć pierwszego liczba, która jest podzielna przez 5 na liście.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="7ff6a-207">Wynik wynosi 5.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-207">The result is 5.</span></span>

<span data-ttu-id="7ff6a-208">Jeśli najpierw musi zostać przekształcone elementy, wywołanie [list.Pick —](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)używającą funkcja zwraca opcję i wygląda pierwszej opcji wartość, która jest `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="7ff6a-209">Zamiast zwracać elementu `List.pick` zwraca wynik `x`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="7ff6a-210">Jeśli nie zostanie znaleziony, `List.pick` zgłasza `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="7ff6a-211">Poniższy kod przedstawia użycie `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="7ff6a-212">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-212">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="7ff6a-213">Innej grupy operacji wyszukiwania [list.tryfind —](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) i powiązane funkcje zwracają wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="7ff6a-214">`List.tryFind` Funkcja zwraca pierwszy element listy, która spełnia warunek, jeśli taki element istnieje, ale wartość opcji `None` , jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="7ff6a-215">Zmiana [list.tryfindindex —](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) zwraca indeks elementu, jeśli został znaleziony, a nie samego elementu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="7ff6a-216">Te funkcje zostały przedstawione w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="7ff6a-217">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-217">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="7ff6a-218">Operacje arytmetyczne na listach</span><span class="sxs-lookup"><span data-stu-id="7ff6a-218">Arithmetic Operations on Lists</span></span>
<span data-ttu-id="7ff6a-219">Typowe operacje arytmetyczne, takie jak sum i średniej są wbudowane w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="7ff6a-220">Aby pracować z [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), musi obsługiwać typ elementu listy `+` operatora i mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="7ff6a-221">Wszystkie wbudowanych typów arytmetycznych spełnia te warunki.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="7ff6a-222">Aby pracować z [list.AVERAGE —](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musi obsługiwać dzielenia bez reszty, co wyklucza typy całkowite, ale pozwala na liczby zmiennoprzecinkowe typy punktów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="7ff6a-223">[List.sumby —](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) i [list.averageby —](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkcje pobierać funkcji jako parametr, a wyniki tej funkcji są używane do obliczania wartości sum lub średnia.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="7ff6a-224">Poniższy kod przedstawia użycie `List.sum`, `List.sumBy`, i `List.average`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="7ff6a-225">Dane wyjściowe `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-225">The output is `1.000000`.</span></span>

<span data-ttu-id="7ff6a-226">Poniższy kod przedstawia użycie `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="7ff6a-227">Dane wyjściowe `5.5`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-227">The output is `5.5`.</span></span>


### <a name="lists-and-tuples"></a><span data-ttu-id="7ff6a-228">Listy i spójnych kolekcji</span><span class="sxs-lookup"><span data-stu-id="7ff6a-228">Lists and Tuples</span></span>
<span data-ttu-id="7ff6a-229">Listy zawierające krotek może manipulować zip i Rozpakuj funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="7ff6a-230">Te funkcje Połącz dwie listy pojedynczych wartości na jednej liście krotek lub podzielić jedną listę krotek na dwóch list z jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="7ff6a-231">Najprostszą [list.zip —](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkcja przyjmuje dwa listę elementów jednego i tworzy jedną listę par spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="7ff6a-232">Inna wersja [list.zip3 —](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), przyjmuje trzy listę elementów jednego i tworzy jedną listę krotek, które mają trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="7ff6a-233">Poniższy przykład kodu pokazuje użycie `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="7ff6a-234">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-234">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="7ff6a-235">Poniższy przykład kodu pokazuje użycie `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="7ff6a-236">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-236">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="7ff6a-237">Odpowiednie Rozpakuj wersje, [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) i [list.unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), wykonaj listę krotek i zwróć list w spójnej kolekcji, których pierwsza lista zawiera wszystkie elementy, które zostały po raz pierwszy w każdej krotki i druga lista zawiera drugi element każda krotka i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="7ff6a-238">Poniższy przykład kodu pokazuje użycie [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="7ff6a-239">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-239">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="7ff6a-240">Poniższy przykład kodu pokazuje użycie [list.unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="7ff6a-241">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-241">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="7ff6a-242">Na liście elementów</span><span class="sxs-lookup"><span data-stu-id="7ff6a-242">Operating on List Elements</span></span>
<span data-ttu-id="7ff6a-243">F # obsługuje wiele operacji na liście elementów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="7ff6a-244">Najprostszą jest [list.ITER —](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), co umożliwia wywołać funkcję dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="7ff6a-245">Zmiany obejmują [list.iter2 —](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), który umożliwia wykonywanie operacji w elementach dwie listy [list.iteri —](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), czyli jak `List.iter` z tą różnicą, że indeks każdego elementu jest przekazywany jako argument do funkcji, która jest wywoływana dla każdego elementu i [list.iteri2 —](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), który jest kombinacją funkcji `List.iter2` i `List.iteri`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="7ff6a-246">Poniższy przykład kodu pokazuje tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="7ff6a-247">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-247">The output is as follows:</span></span>

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

<span data-ttu-id="7ff6a-248">Inną funkcję często używanych, który przekształca elementów listy jest [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), dzięki czemu można zastosować funkcji do każdego elementu listy i wszystkie wyniki do nowej listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="7ff6a-249">[List.map2 —](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) i [list.map3 —](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) są zmiany, które przyjmują wielu list.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="7ff6a-250">Można również użyć [list.MAPI —](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) i [list.mapi2 —](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), jeśli oprócz elementu, funkcja musi być przekazywany indeks każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="7ff6a-251">Jedyną różnicą między `List.mapi2` i `List.mapi` jest to, że `List.mapi2` współpracuje z listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="7ff6a-252">Poniższy przykład przedstawia [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="7ff6a-253">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-253">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="7ff6a-254">W poniższym przykładzie przedstawiono użycie `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="7ff6a-255">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-255">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="7ff6a-256">W poniższym przykładzie przedstawiono użycie `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="7ff6a-257">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-257">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="7ff6a-258">W poniższym przykładzie przedstawiono użycie `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="7ff6a-259">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-259">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="7ff6a-260">W poniższym przykładzie przedstawiono użycie `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="7ff6a-261">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-261">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="7ff6a-262">[List.Collect —](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) przypomina `List.map`, z wyjątkiem, że każdy element tworzy listę i te listy są połączone w listą końcową.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="7ff6a-263">W poniższym kodzie każdego elementu listy generuje trzech cyfr.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="7ff6a-264">Te są wszystkie zebrane na jednej liście.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="7ff6a-265">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-265">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="7ff6a-266">Można również użyć [list.filter —](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), która przyjmuje warunek typu Boolean i tworzy nową listę, która zawiera tylko elementy, które spełniają dany warunek.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="7ff6a-267">Wynikowa lista jest `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="7ff6a-268">Kombinację mapy i Filtruj [list.Choose —](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) pozwala na przekształcanie i wybierz elementy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="7ff6a-269">`List.choose` stosuje funkcję, która zwraca opcji do każdego elementu listy i zwraca nową listę wyników dla elementów, gdy funkcja zwraca wartość opcji `Some`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="7ff6a-270">Poniższy kod przedstawia użycie `List.choose` aby zaznaczyć pisanymi wielkimi literami wyrazy poza listę słów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="7ff6a-271">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7ff6a-271">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="7ff6a-272">Korzysta z wielu list</span><span class="sxs-lookup"><span data-stu-id="7ff6a-272">Operating on Multiple Lists</span></span>
<span data-ttu-id="7ff6a-273">Listy można łączyć ze sobą.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-273">Lists can be joined together.</span></span> <span data-ttu-id="7ff6a-274">Aby przyłączyć się do jednego dwie listy, użyj [list.append —](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="7ff6a-275">Aby dołączyć więcej niż dwie listy, użyj [list.concat —](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a><span data-ttu-id="7ff6a-276">Składanie i operacji skanowania</span><span class="sxs-lookup"><span data-stu-id="7ff6a-276">Fold and Scan Operations</span></span>
<span data-ttu-id="7ff6a-277">Niektóre operacje listy obejmują zależności między wszystkie elementy z listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="7ff6a-278">Operacje złożenia i skanowania są podobne do `List.iter` i `List.map` , wywołaj funkcję dla każdego elementu, ale te operacje zapewnia dodatkowy parametr o nazwie *akumulatora* który przenosi informacje za pomocą obliczenia.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="7ff6a-279">Użyj `List.fold` do przeprowadzenia obliczeń na listę.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="7ff6a-280">Poniższy przykład kodu pokazuje użycie [list.fold —](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) do wykonywania różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="7ff6a-281">Lista jest przesunięta; akumulatora `acc` to wartość, która jest przekazywane w trakcie wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="7ff6a-282">Pierwszy argument akumulatora i elementu listy i zwraca wynik tymczasowe obliczeń dla tego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="7ff6a-283">Drugi argument jest wartością początkową akumulatora.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="7ff6a-284">Wersje te funkcje, które mają cyfrę w nazwie funkcji działać na więcej niż jedną listę.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="7ff6a-285">Na przykład [list.fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) wykonuje obliczenia na dwie listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="7ff6a-286">W poniższym przykładzie pokazano użycie `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="7ff6a-287">`List.fold` i [list.Scan —](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) różnią się w tym `List.fold` zwraca końcowa wartość dodatkowy parametr, ale `List.scan` zwraca listę wartości pośrednich (wraz z końcowej) z dodatkowym parametrem.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="7ff6a-288">Każda z tych funkcji obejmuje odwrotnej zmiany, na przykład [list.foldback —](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), który różni się w kolejności, w której przecina listy i kolejność argumentów.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="7ff6a-289">Ponadto `List.fold` i `List.foldBack` ma zmian, [list.fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) i [list.foldback2 —](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), które wymagają dwie listy o równej długości.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="7ff6a-290">Funkcja wykonująca na każdym elemencie może być wykonanie akcji odpowiednie elementy obu list.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="7ff6a-291">Typy elementu dwie listy mogą być różne, jak w poniższym przykładzie, w której jedna lista zawiera kwoty transakcji dla konta bankowego, i inne lista zawiera typ transakcji: złożenia lub wycofania.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="7ff6a-292">Do obliczenia, takich jak podsumowania `List.fold` i `List.foldBack` mają ten sam efekt, ponieważ wynik nie zależy od rzędu przechodzenie.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="7ff6a-293">W poniższym przykładzie `List.foldBack` służy do dodawania elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="7ff6a-294">Poniższy przykład zwraca przykład konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="7ff6a-295">Teraz zostanie dodany nowy typ transakcji: Obliczanie odsetek.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="7ff6a-296">Saldo końcowe zależy od teraz rzędu transakcji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="7ff6a-297">Funkcja [list.Reduce —](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) jest nieco jak `List.fold` i `List.scan`, ale zamiast przekazywanie wokół oddzielne akumulatora, `List.reduce` przyjmuje funkcję, która przyjmuje dwa argumenty typu zamiast elementu tylko jeden, a jeden z tych argumentów działa jako akumulatora, co oznacza przechowuje pośredni wynikiem obliczenia.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="7ff6a-298">`List.reduce` rozpoczyna się od działających na pierwszych dwóch listy elementów, a następnie używa wynik operacji wraz z następnym elementem.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="7ff6a-299">Ponieważ nie jest osobnym akumulatora, który ma swój własny typ `List.reduce` można użyć zamiast `List.fold` tylko gdy akumulatora i typ elementu być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="7ff6a-300">Poniższy kod przedstawia użycie `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="7ff6a-301">`List.reduce` zgłasza wyjątek, jeśli nie ma żadnych elementów listy.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="7ff6a-302">W poniższym kodzie pierwsze wywołanie w celu wyrażenia lambda podano argumenty 2 i 4 i zwraca 6 i następnego wywołania podano argumenty, 6, 10, dlatego 16.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="7ff6a-303">Konwertowanie pomiędzy listy i inne typy kolekcji</span><span class="sxs-lookup"><span data-stu-id="7ff6a-303">Converting Between Lists and Other Collection Types</span></span>
<span data-ttu-id="7ff6a-304">`List` Moduł zapewnia funkcje do konwertowania do i z tablic i sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7ff6a-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="7ff6a-305">Aby dokonać konwersji do lub z sekwencją, użyj [list.toseq —](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) lub [list.ofseq —](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="7ff6a-306">Aby dokonać konwersji do lub z tablicy, należy użyć [list.toarray —](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) lub [list.ofarray —](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>


### <a name="additional-operations"></a><span data-ttu-id="7ff6a-307">Dodatkowe operacje</span><span class="sxs-lookup"><span data-stu-id="7ff6a-307">Additional Operations</span></span>
<span data-ttu-id="7ff6a-308">Informacje dodatkowe operacje na listach, zobacz temat odwołanie do biblioteki [Collections.list — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="7ff6a-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>


## <a name="see-also"></a><span data-ttu-id="7ff6a-309">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ff6a-309">See Also</span></span>
[<span data-ttu-id="7ff6a-310">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7ff6a-310">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="7ff6a-311">Typy F#</span><span class="sxs-lookup"><span data-stu-id="7ff6a-311">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="7ff6a-312">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="7ff6a-312">Sequences</span></span>](sequences.md)

[<span data-ttu-id="7ff6a-313">Tablice</span><span class="sxs-lookup"><span data-stu-id="7ff6a-313">Arrays</span></span>](arrays.md)

[<span data-ttu-id="7ff6a-314">Opcje</span><span class="sxs-lookup"><span data-stu-id="7ff6a-314">Options</span></span>](options.md)
