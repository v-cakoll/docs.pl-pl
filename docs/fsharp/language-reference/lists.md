---
title: Listy
description: Dowiedz F# się więcej na temat list, uporządkowanej, niemodyfikowalnej serii elementów tego samego typu.
ms.date: 05/16/2016
ms.openlocfilehash: 72f1779d7d077da0f1f4804df93fa4ac11f9b2e3
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082912"
---
# <a name="lists"></a><span data-ttu-id="684d5-103">Listy</span><span class="sxs-lookup"><span data-stu-id="684d5-103">Lists</span></span>

> [!NOTE]
> <span data-ttu-id="684d5-104">Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.</span><span class="sxs-lookup"><span data-stu-id="684d5-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="684d5-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="684d5-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="684d5-106">Lista w F# jest uporządkowaną, niemodyfikowalną serią elementów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="684d5-106">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="684d5-107">Aby wykonać podstawowe operacje na listach, użyj funkcji w [module list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="684d5-107">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="684d5-108">Tworzenie i Inicjowanie list</span><span class="sxs-lookup"><span data-stu-id="684d5-108">Creating and Initializing Lists</span></span>

<span data-ttu-id="684d5-109">Możesz zdefiniować listę, jawnie wymieniając elementy, oddzielając je średnikami i ujęte w nawiasy kwadratowe, jak pokazano w poniższym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="684d5-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="684d5-110">Można również umieścić podziały wierszy między elementami, w tym przypadku średniki są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="684d5-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="684d5-111">Druga składnia może spowodować bardziej czytelny kod, gdy wyrażenia inicjowania elementu są dłuższe lub jeśli chcesz dołączyć komentarz dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="684d5-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="684d5-112">Zwykle wszystkie elementy listy muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="684d5-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="684d5-113">Wyjątek polega na tym, że lista, w której elementy są określone jako typ podstawowy może mieć elementy, które są typami pochodnymi.</span><span class="sxs-lookup"><span data-stu-id="684d5-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="684d5-114">W związku z tym następujące elementy są dopuszczalne `Button` , `CheckBox` ponieważ obie `Control`i pochodzą od.</span><span class="sxs-lookup"><span data-stu-id="684d5-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="684d5-115">Można również zdefiniować elementy listy przy użyciu zakresu wskazywanego przez liczby całkowite oddzielone operatorem zakresu (`..`), jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="684d5-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="684d5-116">Pusta lista jest określana przez parę nawiasów kwadratowych, w których nie ma niczego między nimi.</span><span class="sxs-lookup"><span data-stu-id="684d5-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="684d5-117">Możesz również użyć wyrażenia sekwencji, aby utworzyć listę.</span><span class="sxs-lookup"><span data-stu-id="684d5-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="684d5-118">Aby uzyskać więcej informacji, zobacz [wyrażenia sekwencji](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="684d5-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="684d5-119">Na przykład poniższy kod tworzy listę kwadratów liczb całkowitych z zakresu od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="684d5-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="684d5-120">Operatory pracy z listami</span><span class="sxs-lookup"><span data-stu-id="684d5-120">Operators for Working with Lists</span></span>

<span data-ttu-id="684d5-121">Możesz dołączyć elementy do listy za pomocą `::` operatora (wady).</span><span class="sxs-lookup"><span data-stu-id="684d5-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="684d5-122">Jeśli `list1` `list2` `[100; 2; 3; 4]`jest `[2; 3; 4]`, poniższy kod tworzy jako.</span><span class="sxs-lookup"><span data-stu-id="684d5-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="684d5-123">Można łączyć listy z zgodnymi typami przy użyciu `@` operatora, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="684d5-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="684d5-124">Jeśli `list1` jest `[2; 3; 4]` i ma`list2` ,ten`list3` kod tworzy jako .`[2; 3; 4; 100; 2; 3; 4]` `[100; 2; 3; 4]`</span><span class="sxs-lookup"><span data-stu-id="684d5-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="684d5-125">Funkcje do wykonywania operacji na listach są dostępne w [module list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="684d5-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="684d5-126">Ponieważ listy w F# są niezmienne, wszelkie operacje modyfikacji generują nowe listy zamiast modyfikować istniejące.</span><span class="sxs-lookup"><span data-stu-id="684d5-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="684d5-127">Listy w F# programie są implementowane jako odrębnie połączone listy, co oznacza, że operacje, które uzyskują dostęp tylko do nagłówka listy, mają wartość o (1), a dostęp do elementów to o (*n*).</span><span class="sxs-lookup"><span data-stu-id="684d5-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="684d5-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="684d5-128">Properties</span></span>

<span data-ttu-id="684d5-129">Typ listy obsługuje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="684d5-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="684d5-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="684d5-130">Property</span></span>|<span data-ttu-id="684d5-131">Type</span><span class="sxs-lookup"><span data-stu-id="684d5-131">Type</span></span>|<span data-ttu-id="684d5-132">Opis</span><span class="sxs-lookup"><span data-stu-id="684d5-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="684d5-133">MTP</span><span class="sxs-lookup"><span data-stu-id="684d5-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="684d5-134">Pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="684d5-134">The first element.</span></span>|
|[<span data-ttu-id="684d5-135">pusty</span><span class="sxs-lookup"><span data-stu-id="684d5-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="684d5-136">Właściwość statyczna zwracająca pustą listę odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="684d5-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="684d5-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="684d5-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="684d5-138">`true`Jeśli lista nie zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="684d5-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="684d5-139">Element</span><span class="sxs-lookup"><span data-stu-id="684d5-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="684d5-140">Element o określonym indeksie (liczony od zera).</span><span class="sxs-lookup"><span data-stu-id="684d5-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="684d5-141">Długość</span><span class="sxs-lookup"><span data-stu-id="684d5-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="684d5-142">Liczba elementów.</span><span class="sxs-lookup"><span data-stu-id="684d5-142">The number of elements.</span></span>|
|[<span data-ttu-id="684d5-143">Drugorzędn</span><span class="sxs-lookup"><span data-stu-id="684d5-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="684d5-144">Lista bez pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="684d5-144">The list without the first element.</span></span>|

<span data-ttu-id="684d5-145">Poniżej przedstawiono kilka przykładów użycia tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="684d5-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="684d5-146">Korzystanie z list</span><span class="sxs-lookup"><span data-stu-id="684d5-146">Using Lists</span></span>

<span data-ttu-id="684d5-147">Programowanie za pomocą list umożliwia wykonywanie złożonych operacji przy użyciu niewielkiej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="684d5-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="684d5-148">W tej sekcji opisano typowe operacje na listach, które są ważne dla programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="684d5-148">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="684d5-149">Rekursja z listami</span><span class="sxs-lookup"><span data-stu-id="684d5-149">Recursion with Lists</span></span>

<span data-ttu-id="684d5-150">Listy są jednoznacznie dostosowane do technik programowania cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="684d5-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="684d5-151">Należy wziąć pod uwagę operację, która musi zostać wykonana dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="684d5-152">Można to zrobić cyklicznie, działając na początku listy, a następnie przekazując ogon listy, czyli mniejszą listę, która składa się z oryginalnej listy bez pierwszego elementu, z powrotem do następnego poziomu rekursji.</span><span class="sxs-lookup"><span data-stu-id="684d5-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="684d5-153">Aby napisać taką funkcję cykliczną, należy użyć operatora wad (`::`) we wzorcu dopasowywania, który umożliwia rozdzielenie nagłówka listy od ogona.</span><span class="sxs-lookup"><span data-stu-id="684d5-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="684d5-154">Poniższy przykład kodu pokazuje, jak używać dopasowywania wzorców do implementowania funkcji cyklicznej, która wykonuje operacje na liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="684d5-155">Poprzedni kod działa dobrze w przypadku małych list, ale dla większych list może przekroczyć stos.</span><span class="sxs-lookup"><span data-stu-id="684d5-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="684d5-156">Poniższy kod Ulepsza ten kod przy użyciu argumentu akumulowana, standardowej techniki pracy z funkcjami cyklicznymi.</span><span class="sxs-lookup"><span data-stu-id="684d5-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="684d5-157">Użycie argumentu akumulowana powoduje cykliczne zakończenie funkcji, która zapisuje przestrzeń stosu.</span><span class="sxs-lookup"><span data-stu-id="684d5-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="684d5-158">Funkcja `RemoveAllMultiples` jest funkcją cykliczną, która przyjmuje dwie listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="684d5-159">Pierwsza lista zawiera numery, których wielokrotność zostanie usunięta, a druga lista to lista, z której mają zostać usunięte liczby.</span><span class="sxs-lookup"><span data-stu-id="684d5-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="684d5-160">W poniższym przykładzie kod używa tej funkcji cyklicznej, aby wyeliminować wszystkie niepodstawowe numery z listy, pozostawiając w wyniku listę numerów pierwszych.</span><span class="sxs-lookup"><span data-stu-id="684d5-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="684d5-161">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-161">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="684d5-162">Funkcje modułu</span><span class="sxs-lookup"><span data-stu-id="684d5-162">Module Functions</span></span>

<span data-ttu-id="684d5-163">[Moduł list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) zawiera funkcje, które uzyskują dostęp do elementów listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="684d5-164">Element główny jest najszybszy i najłatwiejszy do uzyskania dostępu.</span><span class="sxs-lookup"><span data-stu-id="684d5-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="684d5-165">Użyj właściwości [głównego](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) lub listy funkcji modułu [.](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)</span><span class="sxs-lookup"><span data-stu-id="684d5-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="684d5-166">Można uzyskać dostęp do ogona listy za pomocą właściwości [tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) lub funkcji [list. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) .</span><span class="sxs-lookup"><span data-stu-id="684d5-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="684d5-167">Aby znaleźć element według indeksu, użyj funkcji [list. n](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) .</span><span class="sxs-lookup"><span data-stu-id="684d5-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="684d5-168">`List.nth`przechodzi listę.</span><span class="sxs-lookup"><span data-stu-id="684d5-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="684d5-169">W związku z tym to O (*n*).</span><span class="sxs-lookup"><span data-stu-id="684d5-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="684d5-170">Jeśli kod jest często `List.nth` używany, warto rozważyć użycie tablicy zamiast listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="684d5-171">Dostęp do elementów w tablicach ma (1).</span><span class="sxs-lookup"><span data-stu-id="684d5-171">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="684d5-172">Operacje logiczne na listach</span><span class="sxs-lookup"><span data-stu-id="684d5-172">Boolean Operations on Lists</span></span>

<span data-ttu-id="684d5-173">Funkcja [list. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) określa, czy lista zawiera dowolne elementy.</span><span class="sxs-lookup"><span data-stu-id="684d5-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="684d5-174">Funkcja [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) stosuje test logiczny do elementów listy i zwraca `true` , jeśli którykolwiek element spełnia testy.</span><span class="sxs-lookup"><span data-stu-id="684d5-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="684d5-175">[List. exists2 —](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) jest podobny, ale działa na kolejnych parach elementów na dwóch listach.</span><span class="sxs-lookup"><span data-stu-id="684d5-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="684d5-176">Poniższy kod ilustruje użycie `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="684d5-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="684d5-177">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-177">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="684d5-178">Poniższy przykład ilustruje użycie `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="684d5-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="684d5-179">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-179">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="684d5-180">Możesz użyć [list. ForAll](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) , jeśli chcesz sprawdzić, czy wszystkie elementy listy spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="684d5-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="684d5-181">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-181">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="684d5-182">Podobnie, [list. forall2 —](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) określa, czy wszystkie elementy w odpowiednich pozycjach na dwóch listach spełniają wyrażenie logiczne, które obejmuje każdą parę elementów.</span><span class="sxs-lookup"><span data-stu-id="684d5-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="684d5-183">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-183">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="684d5-184">Operacje sortowania na listach</span><span class="sxs-lookup"><span data-stu-id="684d5-184">Sort Operations on Lists</span></span>

<span data-ttu-id="684d5-185">Listy sortowania list [. Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list. SortBy —](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)oraz [list. sortWith —](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) .</span><span class="sxs-lookup"><span data-stu-id="684d5-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="684d5-186">Funkcja sortowania określa, które z tych trzech funkcji mają być używane.</span><span class="sxs-lookup"><span data-stu-id="684d5-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="684d5-187">`List.sort`używa domyślnego porównania ogólnego.</span><span class="sxs-lookup"><span data-stu-id="684d5-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="684d5-188">Porównanie ogólne używa operatorów globalnych opartych na funkcji porównania generycznej do porównywania wartości.</span><span class="sxs-lookup"><span data-stu-id="684d5-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="684d5-189">Wydajnie współpracuje z szeroką gamą typów elementów, takimi jak proste typy liczbowe, krotki, rekordy, związki rozłączne, listy, tablice i dowolny typ, który implementuje `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="684d5-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="684d5-190">Dla typów, które `System.IComparable`implementują, porównanie ogólne `System.IComparable.CompareTo()` używa funkcji.</span><span class="sxs-lookup"><span data-stu-id="684d5-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="684d5-191">Porównanie ogólne działa również z ciągami, ale używa niezależnej od kultury kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="684d5-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="684d5-192">Porównania generycznego nie należy używać w przypadku nieobsługiwanych typów, takich jak typy funkcji.</span><span class="sxs-lookup"><span data-stu-id="684d5-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="684d5-193">Ponadto wydajność domyślnego porównania ogólnego jest Najlepsza dla małych typów strukturalnych; w przypadku większych typów strukturalnych, które muszą być porównywane i sortowane często `System.IComparable` , należy rozważyć zaimplementowanie i `System.IComparable.CompareTo()` zapewnienie wydajnej implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="684d5-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="684d5-194">`List.sortBy`przyjmuje funkcję zwracającą wartość, która jest używana jako kryterium sortowania i `List.sortWith` pobiera funkcję porównania jako argument.</span><span class="sxs-lookup"><span data-stu-id="684d5-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="684d5-195">Te ostatnie dwie funkcje są przydatne podczas pracy z typami, które nie obsługują porównania, lub gdy porównanie wymaga bardziej złożonej semantyki porównania, tak jak w przypadku ciągów z obsługą kultury.</span><span class="sxs-lookup"><span data-stu-id="684d5-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="684d5-196">Poniższy przykład ilustruje użycie `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="684d5-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="684d5-197">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-197">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="684d5-198">Poniższy przykład ilustruje użycie `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="684d5-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="684d5-199">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-199">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="684d5-200">W następnym przykładzie pokazano użycie `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="684d5-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="684d5-201">W tym przykładzie funkcja `compareWidgets` porównywania niestandardowego służy do pierwszego porównania jednego pola typu niestandardowego, a następnie drugiego, gdy wartości pierwszego pola są równe.</span><span class="sxs-lookup"><span data-stu-id="684d5-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="684d5-202">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-202">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="684d5-203">Operacje wyszukiwania na listach</span><span class="sxs-lookup"><span data-stu-id="684d5-203">Search Operations on Lists</span></span>

<span data-ttu-id="684d5-204">Dla list są obsługiwane liczne operacje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="684d5-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="684d5-205">Najprostszy, [list. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umożliwia znalezienie pierwszego elementu, który jest zgodny z danym warunkiem.</span><span class="sxs-lookup"><span data-stu-id="684d5-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="684d5-206">Poniższy przykład kodu demonstruje użycie `List.find` programu w celu znalezienia pierwszego numeru, który jest podzielny przez 5 na liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="684d5-207">Wynik to 5.</span><span class="sxs-lookup"><span data-stu-id="684d5-207">The result is 5.</span></span>

<span data-ttu-id="684d5-208">Jeśli elementy muszą zostać przekształcone w pierwszej kolejności, wywołaj [listę. pobranie](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), która pobiera funkcję, która zwraca opcję, i szuka pierwszej wartości opcji, która jest `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="684d5-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="684d5-209">Zamiast zwracać element, `List.pick` zwraca wynik. `x`</span><span class="sxs-lookup"><span data-stu-id="684d5-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="684d5-210">Jeśli nie zostanie znaleziony pasujący element `List.pick` , `System.Collections.Generic.KeyNotFoundException`zgłosi.</span><span class="sxs-lookup"><span data-stu-id="684d5-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="684d5-211">Poniższy kod ilustruje użycie `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="684d5-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="684d5-212">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-212">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="684d5-213">Inna grupa operacji wyszukiwania, [list. tryFind —](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) i powiązanych funkcji, zwracają wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="684d5-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="684d5-214">Funkcja zwraca pierwszy element listy, który spełnia warunek, jeśli taki element istnieje, ale wartość `None` opcji, jeśli nie. `List.tryFind`</span><span class="sxs-lookup"><span data-stu-id="684d5-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="684d5-215">Lista wariacji [. tryFindIndex —](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) zwraca indeks elementu, jeśli został znaleziony, a nie sam element.</span><span class="sxs-lookup"><span data-stu-id="684d5-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="684d5-216">Te funkcje są zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="684d5-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="684d5-217">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-217">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="684d5-218">Operacje arytmetyczne na listach</span><span class="sxs-lookup"><span data-stu-id="684d5-218">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="684d5-219">Typowe operacje arytmetyczne, takie jak sum i Average, są wbudowane w [moduł listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="684d5-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="684d5-220">Aby można było korzystać z [list. sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), typ elementu listy musi obsługiwać `+` operatora i mieć wartość zerową.</span><span class="sxs-lookup"><span data-stu-id="684d5-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="684d5-221">Wszystkie wbudowane typy arytmetyczne spełniają te warunki.</span><span class="sxs-lookup"><span data-stu-id="684d5-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="684d5-222">Aby można było korzystać z [listy. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musi obsługiwać dzielenie bez reszty, która wyklucza typy całkowite, ale pozwala na używanie zmiennoprzecinkowych typów.</span><span class="sxs-lookup"><span data-stu-id="684d5-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="684d5-223">Funkcje [list. sumBy —](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) i [list. averageBy —](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) przyjmują funkcję jako parametr, a wyniki tej funkcji są używane do obliczania wartości sum lub średniej.</span><span class="sxs-lookup"><span data-stu-id="684d5-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="684d5-224">Poniższy kod ilustruje użycie `List.sum`, `List.sumBy`, i `List.average`.</span><span class="sxs-lookup"><span data-stu-id="684d5-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="684d5-225">Dane wyjściowe to `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="684d5-225">The output is `1.000000`.</span></span>

<span data-ttu-id="684d5-226">Poniższy kod ilustruje użycie `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="684d5-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="684d5-227">Dane wyjściowe to `5.5`.</span><span class="sxs-lookup"><span data-stu-id="684d5-227">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="684d5-228">Listy i krotki</span><span class="sxs-lookup"><span data-stu-id="684d5-228">Lists and Tuples</span></span>

<span data-ttu-id="684d5-229">Listy zawierające krotki mogą być przetwarzane przy użyciu funkcji zip i rozpakowania.</span><span class="sxs-lookup"><span data-stu-id="684d5-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="684d5-230">Te funkcje łączą dwie listy pojedynczych wartości w jedną listę spójnych kolekcji lub dzielą jedną listę krotek na dwie listy pojedynczych wartości.</span><span class="sxs-lookup"><span data-stu-id="684d5-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="684d5-231">Najprostsza funkcja [list. zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) przyjmuje dwie listy pojedynczych elementów i tworzy pojedynczą listę par krotek.</span><span class="sxs-lookup"><span data-stu-id="684d5-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="684d5-232">Inna wersja, [list. zip3 —](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), pobiera trzy listy pojedynczych elementów i tworzy pojedynczą listę spójnych kolekcji, które mają trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="684d5-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="684d5-233">Poniższy przykład kodu demonstruje użycie `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="684d5-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="684d5-234">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-234">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="684d5-235">Poniższy przykład kodu demonstruje użycie `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="684d5-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="684d5-236">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-236">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="684d5-237">Odpowiednie wersje rozpakować, [list. rozpakować](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) i [list. unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), przyjmują listy krotek i listy zwracane w spójnej kolekcji, gdzie pierwsza lista zawiera wszystkie elementy, które wcześniej znajdowały się w każdej kolekcji, a druga lista zawiera drugi element każdego Krotka i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="684d5-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="684d5-238">Poniższy przykład kodu demonstruje użycie [list.](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)rozpakowywanie.</span><span class="sxs-lookup"><span data-stu-id="684d5-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="684d5-239">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-239">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="684d5-240">Poniższy przykład kodu demonstruje użycie [list. unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="684d5-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="684d5-241">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-241">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="684d5-242">Działa na elementach listy</span><span class="sxs-lookup"><span data-stu-id="684d5-242">Operating on List Elements</span></span>

<span data-ttu-id="684d5-243">F#obsługuje różne operacje na elementach listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="684d5-244">Najprostszą jest [Lista. ITER](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), która umożliwia wywoływanie funkcji dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="684d5-245">Wariacje obejmują [list. iter2 —](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), które umożliwiają wykonywanie operacji na elementach dwóch list, [list. iteri —](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), `List.iter` które przypominają, że indeks każdego elementu jest przenoszona jako argument do funkcji, która jest wywoływana dla każdego element oraz [list. iteri2 —](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), który jest kombinacją funkcji `List.iter2` i. `List.iteri`</span><span class="sxs-lookup"><span data-stu-id="684d5-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="684d5-246">Poniższy przykład kodu ilustruje te funkcje.</span><span class="sxs-lookup"><span data-stu-id="684d5-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="684d5-247">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-247">The output is as follows:</span></span>

```console
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

<span data-ttu-id="684d5-248">Inna często używana funkcja, która przekształca elementy listy to [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), która umożliwia zastosowanie funkcji do każdego elementu listy i umieszczenie wszystkich wyników w nowej liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="684d5-249">[List. MAP2 —](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) i [list. map3 —](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) są odmianami, które pobierają wiele list.</span><span class="sxs-lookup"><span data-stu-id="684d5-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="684d5-250">Można również użyć [list. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) i [list. mapi2 —](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), jeśli oprócz elementu, funkcja musi zostać przeniesiona indeks każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="684d5-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="684d5-251">Jedyną różnicą między `List.mapi2` i `List.mapi` jest to `List.mapi2` , że program współpracuje z dwiema listami.</span><span class="sxs-lookup"><span data-stu-id="684d5-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="684d5-252">Poniższy przykład ilustruje [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="684d5-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="684d5-253">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-253">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="684d5-254">W poniższym przykładzie pokazano użycie `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="684d5-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="684d5-255">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-255">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="684d5-256">W poniższym przykładzie pokazano użycie `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="684d5-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="684d5-257">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-257">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="684d5-258">W poniższym przykładzie pokazano użycie `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="684d5-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="684d5-259">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-259">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="684d5-260">W poniższym przykładzie pokazano użycie `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="684d5-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="684d5-261">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-261">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="684d5-262">[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) `List.map`przypomina, z tą różnicą, że każdy element tworzy listę i wszystkie te listy są łączone w ostateczną listę.</span><span class="sxs-lookup"><span data-stu-id="684d5-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="684d5-263">W poniższym kodzie każdy element listy generuje trzy liczby.</span><span class="sxs-lookup"><span data-stu-id="684d5-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="684d5-264">Wszystkie te dane są zbierane w jednej liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="684d5-265">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-265">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="684d5-266">Można również użyć [list. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), który przyjmuje warunek logiczny i tworzy nową listę, która składa się tylko z elementów, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="684d5-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="684d5-267">Lista `[2; 4; 6]`wyników.</span><span class="sxs-lookup"><span data-stu-id="684d5-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="684d5-268">Kombinacja map i filtru, [list. Choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) umożliwia przekształcanie i zaznaczanie elementów w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="684d5-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="684d5-269">`List.choose`stosuje funkcję, która zwraca opcję do każdego elementu listy i zwraca nową listę wyników dla elementów, gdy funkcja zwraca wartość `Some`opcji.</span><span class="sxs-lookup"><span data-stu-id="684d5-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="684d5-270">Poniższy kod ilustruje użycie `List.choose` do zaznaczania wersalików wyrazów z listy wyrazów.</span><span class="sxs-lookup"><span data-stu-id="684d5-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="684d5-271">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="684d5-271">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="684d5-272">Działa na wielu listach</span><span class="sxs-lookup"><span data-stu-id="684d5-272">Operating on Multiple Lists</span></span>

<span data-ttu-id="684d5-273">Listy można łączyć ze sobą.</span><span class="sxs-lookup"><span data-stu-id="684d5-273">Lists can be joined together.</span></span> <span data-ttu-id="684d5-274">Aby dołączyć dwie listy do jednej, użyj [list. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="684d5-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="684d5-275">Aby dołączyć więcej niż dwie listy, użyj [list. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="684d5-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="684d5-276">Operacje składania i skanowania</span><span class="sxs-lookup"><span data-stu-id="684d5-276">Fold and Scan Operations</span></span>

<span data-ttu-id="684d5-277">Niektóre operacje na listach obejmują wzajemne zależności między wszystkimi elementami listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="684d5-278">Operacje składania i skanowania są podobne `List.iter` i `List.map` w przypadku wywołania funkcji dla każdego elementu, ale te operacje zapewniają dodatkowy parametr o nazwie *akumulowana* , który przenosi informacje za pomocą obliczeń.</span><span class="sxs-lookup"><span data-stu-id="684d5-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="684d5-279">Służy `List.fold` do wykonywania obliczeń na liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="684d5-280">Poniższy przykład kodu demonstruje użycie [list. zgięcie](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) do wykonywania różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="684d5-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="684d5-281">Lista jest przesunięta; akumulacja `acc` jest wartością, która jest przenoszona wraz z przeprowadzeniem obliczeń.</span><span class="sxs-lookup"><span data-stu-id="684d5-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="684d5-282">Pierwszy argument przyjmuje wartość akumulowana i element list i zwraca pośredni wynik obliczeń dla tego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="684d5-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="684d5-283">Drugi argument jest początkową wartością akumulowana.</span><span class="sxs-lookup"><span data-stu-id="684d5-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="684d5-284">Wersje tych funkcji, które mają cyfrę w nazwie funkcji, działają na więcej niż jednej liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="684d5-285">Na przykład, [list. fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) wykonuje obliczenia na dwóch listach.</span><span class="sxs-lookup"><span data-stu-id="684d5-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="684d5-286">Poniższy przykład ilustruje użycie `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="684d5-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="684d5-287">`List.fold`and [list. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) różni się, `List.fold` która zwraca końcową wartość dodatkowego parametru, ale `List.scan` zwraca listę wartości pośrednich (wraz z wartością końcową) dodatkowego parametru.</span><span class="sxs-lookup"><span data-stu-id="684d5-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="684d5-288">Każda z tych funkcji zawiera odwrotną odmianę, na przykład [list. foldBack —](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), która różni się w kolejności, w jakiej jest przesunięty listy, i kolejności argumentów.</span><span class="sxs-lookup"><span data-stu-id="684d5-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="684d5-289">Ponadto `List.fold` i`List.foldBack` mają różne odmiany, [list. fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) i [list. foldBack2 —](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), które pobierają dwie listy o równej długości.</span><span class="sxs-lookup"><span data-stu-id="684d5-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="684d5-290">Funkcja, która jest wykonywana dla każdego elementu, może użyć odpowiednich elementów obu list do wykonania pewnej akcji.</span><span class="sxs-lookup"><span data-stu-id="684d5-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="684d5-291">Typy elementów dwóch list mogą być różne, jak w poniższym przykładzie, w którym jedna lista zawiera kwoty transakcji dla konta bankowego, a druga lista zawiera typ transakcji: kaucja lub wycofanie.</span><span class="sxs-lookup"><span data-stu-id="684d5-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="684d5-292">W przypadku obliczeń, takich jak `List.fold` suma `List.foldBack` i ma ten sam skutek, ponieważ wynik nie zależy od kolejności przechodzenia.</span><span class="sxs-lookup"><span data-stu-id="684d5-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="684d5-293">W poniższym przykładzie `List.foldBack` jest używany do dodawania elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="684d5-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="684d5-294">Poniższy przykład zwraca dane do przykładu konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="684d5-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="684d5-295">Tym razem zostanie dodany nowy typ transakcji: Obliczanie odsetek.</span><span class="sxs-lookup"><span data-stu-id="684d5-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="684d5-296">Saldo końcowe jest teraz zależne od kolejności transakcji.</span><span class="sxs-lookup"><span data-stu-id="684d5-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="684d5-297">Lista funkcji [. Redukcja](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) jest nieco taka sama `List.fold` jak `List.scan`i, z tą różnicą, że zamiast przechodzenia do `List.reduce` innego akumulowana, przyjmuje funkcję, która przyjmuje dwa argumenty typu elementu zamiast jednego z nich. argumenty pełnią rolę akumulowana, co oznacza, że przechowuje pośredni wynik obliczeń.</span><span class="sxs-lookup"><span data-stu-id="684d5-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="684d5-298">`List.reduce`zaczyna się od działania pierwszego z dwóch elementów listy, a następnie używa wyniku operacji wraz z następnym elementem.</span><span class="sxs-lookup"><span data-stu-id="684d5-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="684d5-299">Ponieważ nie istnieje oddzielny obiekt, który ma własny typ, może `List.reduce` być używany `List.fold` zamiast tylko wtedy, gdy obiekt, który ma ten sam typ i typ elementu.</span><span class="sxs-lookup"><span data-stu-id="684d5-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="684d5-300">Poniższy kod ilustruje użycie `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="684d5-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="684d5-301">`List.reduce`zgłasza wyjątek, jeśli podana lista nie zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="684d5-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="684d5-302">W poniższym kodzie, pierwsze wywołanie do wyrażenia lambda otrzymuje argumenty 2 i 4 i zwraca 6, a następne wywołanie otrzymuje argumenty 6 i 10, więc wynik wynosi 16.</span><span class="sxs-lookup"><span data-stu-id="684d5-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="684d5-303">Konwertowanie między listami i innymi typami kolekcji</span><span class="sxs-lookup"><span data-stu-id="684d5-303">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="684d5-304">`List` Moduł zawiera funkcje do konwersji do i z obu sekwencji i tablic.</span><span class="sxs-lookup"><span data-stu-id="684d5-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="684d5-305">Aby przekonwertować sekwencję na lub z sekwencji, użyj [list. toSeq —](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) lub [list. ofSeq —](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="684d5-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="684d5-306">Aby przekonwertować na tablicę lub z niej, użyj [list. ToArray —](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) lub [list. ofArray —](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="684d5-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="684d5-307">Dodatkowe operacje</span><span class="sxs-lookup"><span data-stu-id="684d5-307">Additional Operations</span></span>

<span data-ttu-id="684d5-308">Aby uzyskać informacje na temat dodatkowych operacji na listach, zobacz temat Dokumentacja biblioteki [kolekcje. list](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="684d5-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="684d5-309">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="684d5-309">See also</span></span>

- [<span data-ttu-id="684d5-310">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="684d5-310">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="684d5-311">Typy F#</span><span class="sxs-lookup"><span data-stu-id="684d5-311">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="684d5-312">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="684d5-312">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="684d5-313">Tablice</span><span class="sxs-lookup"><span data-stu-id="684d5-313">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="684d5-314">Opcje</span><span class="sxs-lookup"><span data-stu-id="684d5-314">Options</span></span>](options.md)
