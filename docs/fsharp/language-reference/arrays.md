---
title: Tablice (F#)
description: 'Dowiedz się, jak utworzyć i korzystanie z tablic w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 2cd887b8385235185afb9099c3142a572efe3f41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="arrays"></a><span data-ttu-id="7b73f-103">Tablice</span><span class="sxs-lookup"><span data-stu-id="7b73f-103">Arrays</span></span>

> [!NOTE]
<span data-ttu-id="7b73f-104">Łącze odwołania API spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="7b73f-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="7b73f-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="7b73f-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="7b73f-106">Tablice są kolekcjami stałym rozmiarze, liczony od zera, modyfikowalną elementów kolejnych danych, które znajdują się tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="7b73f-107">Tworzenie tablic</span><span class="sxs-lookup"><span data-stu-id="7b73f-107">Creating Arrays</span></span>
<span data-ttu-id="7b73f-108">Tablice można utworzyć na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-108">You can create arrays in several ways.</span></span> <span data-ttu-id="7b73f-109">Można utworzyć tablicy małych poprzez wyszczególnienie kolejnych wartości między `[|` i `|]` i oddzielone średnikami, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="7b73f-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="7b73f-110">Można również wprowadzić każdego elementu w osobnym wierszu, w którego przypadku średnik stanowiący separator jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7b73f-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="7b73f-111">Typ elementów tablicy jest wywnioskowany na podstawie literałów używane i muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="7b73f-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="7b73f-112">Poniższy kod powoduje błąd, ponieważ 1.0 jest zmiennoprzecinkową i 2 i 3 są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="7b73f-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="7b73f-113">Wyrażenia sekwencji służy także do tworzenia tablic.</span><span class="sxs-lookup"><span data-stu-id="7b73f-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="7b73f-114">Poniżej przedstawiono przykład, w którym tworzy tablicę kwadratów liczb całkowitych od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="7b73f-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="7b73f-115">Do utworzenia tablicy, w którym wszystkie elementy są inicjowane na wartość zero, użyj `Array.zeroCreate`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a><span data-ttu-id="7b73f-116">Uzyskiwanie dostępu do elementów</span><span class="sxs-lookup"><span data-stu-id="7b73f-116">Accessing Elements</span></span>

<span data-ttu-id="7b73f-117">Dostęp do elementów tablicy przy użyciu operator kropki (`.`) i nawiasów (`[` i `]`).</span><span class="sxs-lookup"><span data-stu-id="7b73f-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="7b73f-118">Indeksy tablicy rozpoczynają się od 0.</span><span class="sxs-lookup"><span data-stu-id="7b73f-118">Array indexes start at 0.</span></span>

<span data-ttu-id="7b73f-119">Można także przejść elementów tablicy przy użyciu notacji wycinek, który umożliwia określenie Podzakres tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="7b73f-120">Przykłady notacji wycinka.</span><span class="sxs-lookup"><span data-stu-id="7b73f-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="7b73f-121">W przypadku notacji wycinek zostanie utworzona kopia nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-121">When slice notation is used, a new copy of the array is created.</span></span>


## <a name="array-types-and-modules"></a><span data-ttu-id="7b73f-122">Typy tablicy i modułów</span><span class="sxs-lookup"><span data-stu-id="7b73f-122">Array Types and Modules</span></span>
<span data-ttu-id="7b73f-123">Wszystkie tablice F # jest typem .NET Framework <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b73f-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7b73f-124">W związku z tym F # tablice obsługują wszystkie funkcje dostępne w programie <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b73f-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="7b73f-125">Moduł biblioteki [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) obsługuje operacje na tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="7b73f-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="7b73f-126">Moduły `Array2D`, `Array3D`, i `Array4D` zawierają funkcje obsługujące operacje w tablicach dwa, trzy i czterema wymiarami.</span><span class="sxs-lookup"><span data-stu-id="7b73f-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="7b73f-127">Można utworzyć tablic o randze większej niż cztery przy użyciu <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b73f-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="7b73f-128">Proste funkcje</span><span class="sxs-lookup"><span data-stu-id="7b73f-128">Simple Functions</span></span>
<span data-ttu-id="7b73f-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) pobiera element.</span><span class="sxs-lookup"><span data-stu-id="7b73f-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="7b73f-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) zapewnia długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="7b73f-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) Ustawia element określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="7b73f-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="7b73f-132">W poniższym przykładzie przedstawiono użycie tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="7b73f-133">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b73f-133">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="7b73f-134">Funkcji służących do tworzenia tablic</span><span class="sxs-lookup"><span data-stu-id="7b73f-134">Functions That Create Arrays</span></span>

<span data-ttu-id="7b73f-135">Niektóre funkcje tworzenie tablic bez konieczności istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="7b73f-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) Tworzy nowy tablica, która nie zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="7b73f-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) tworzy tablicę określonego rozmiaru i ustawia wszystkie elementy podanych wartości.</span><span class="sxs-lookup"><span data-stu-id="7b73f-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="7b73f-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) tworzy tablicę, wymiar i funkcji, aby wygenerować elementy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="7b73f-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) tworzy tablicę, w której wszystkie elementy są inicjowane z wartością zero dla typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="7b73f-140">Poniższy kod przedstawia tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="7b73f-141">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b73f-141">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="7b73f-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) Tworzy nową macierz, który zawiera elementy, które są kopiowane z istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="7b73f-143">Zwróć uwagę, że kopia kopia pobieżna, co oznacza, że jeśli typ elementu jest typem referencyjnym, skopiowane tylko odwołanie, nie źródłowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="7b73f-144">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="7b73f-145">Dane wyjściowe poprzedniego kodu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="7b73f-145">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="7b73f-146">Ciąg `Test1` pojawia się tylko w pierwszym tablicy, ponieważ operacja tworzenia nowego elementu zastępuje odwołania w `firstArray` , ale nie ma wpływu na oryginalnym odwołania na pusty ciąg, który jest nadal znajdują się w `secondArray`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="7b73f-147">Ciąg `Test2` pojawia się w obu tablic, ponieważ `Insert` operacji na <xref:System.Text.StringBuilder?displayProperty=nameWithType> typu ma wpływ na podstawową <xref:System.Text.StringBuilder?displayProperty=nameWithType> obiektu, który odwołuje się do obu tablic.</span><span class="sxs-lookup"><span data-stu-id="7b73f-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="7b73f-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generuje nowy tablicy Podzakres tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="7b73f-149">Należy określić Podzakres przez podanie początkowego indeksu i długości.</span><span class="sxs-lookup"><span data-stu-id="7b73f-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="7b73f-150">Poniższy kod przedstawia użycie `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="7b73f-151">Dane wyjściowe zawierają czy subarray rozpoczyna się od elementu 5 i zawiera 10 elementów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="7b73f-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) Tworzy nową macierz przez dwie tablice istniejące połączenie.</span><span class="sxs-lookup"><span data-stu-id="7b73f-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="7b73f-153">Poniższy kod przedstawia **Array.append —**.</span><span class="sxs-lookup"><span data-stu-id="7b73f-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="7b73f-154">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-154">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="7b73f-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) wybiera elementy tablicy do uwzględnienia w nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="7b73f-156">Poniższy kod przedstawia `Array.choose`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="7b73f-157">Należy pamiętać, że typ elementu tablicy nie trzeba pasuje do typu wartość zwracana w typ opcji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="7b73f-158">W tym przykładzie jest typ elementu `int` i opcją jest wynikiem funkcji wielomianu `elem*elem - 1`, jako zmiennoprzecinkową numer punktu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="7b73f-159">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-159">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="7b73f-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) Uruchamia funkcję na każdy element tablicy istniejącej tablicy, a następnie zbiera elementy generowane przez funkcję i łączy je do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="7b73f-161">Poniższy kod przedstawia `Array.collect`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="7b73f-162">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-162">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="7b73f-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) pobiera sekwencję tablic i łączy je do jednej macierzy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="7b73f-164">Poniższy kod przedstawia `Array.concat`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="7b73f-165">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-165">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="7b73f-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) pobiera funkcję warunek typu Boolean i generuje nowy tablica, która zawiera tylko elementy z tablicy wejściowej, dla którego warunku jest PRAWDA.</span><span class="sxs-lookup"><span data-stu-id="7b73f-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="7b73f-167">Poniższy kod przedstawia `Array.filter`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="7b73f-168">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-168">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="7b73f-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) Tworzy nową macierz odwracanie kolejności istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="7b73f-170">Poniższy kod przedstawia `Array.rev`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="7b73f-171">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-171">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="7b73f-172">Można łatwo łączyć funkcji w module tablicy, które Przekształcanie tablic za pomocą operatora potoku (`|>`), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7b73f-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="7b73f-173">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7b73f-173">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="7b73f-174">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="7b73f-174">Multidimensional Arrays</span></span>

<span data-ttu-id="7b73f-175">Można utworzyć tablicy wielowymiarowej, ale nie składnię zapisywania literał tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="7b73f-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="7b73f-176">Użyj operatora [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) do utworzenia tablicy z sekwencji sekwencji elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="7b73f-177">Sekwencje mogą być Literały tablicy lub listy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="7b73f-178">Na przykład poniższy kod tworzy jest tablicą dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="7b73f-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="7b73f-179">Można także użyć funkcji [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) zainicjować tablice dwóch wymiarów i podobne funkcje są dostępne dla tablic trzech do czterech wymiarów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="7b73f-180">Te funkcje pobierać funkcję, która służy do tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="7b73f-181">Aby utworzyć jest tablicą dwuwymiarową, który zawiera elementy, ustaw wartość początkową zamiast określania funkcję, użyj [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) funkcja, która jest również dostępna dla stałych maksymalnie cztery wymiary.</span><span class="sxs-lookup"><span data-stu-id="7b73f-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="7b73f-182">Poniższy przykład kodu najpierw przedstawiono sposób tworzenia tablicy tablic zawierających odpowiednie elementy, a następnie używa `Array2D.init` do generowania żądaną tablicą dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="7b73f-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="7b73f-183">Tablica indeksowanie i fragmentacji składnia jest obsługiwana dla tablic maksymalnie 4 rangę.</span><span class="sxs-lookup"><span data-stu-id="7b73f-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="7b73f-184">Po określeniu indeksu w wielu wymiarów umożliwia przecinkami oddzielnych indeksów, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
<span data-ttu-id="7b73f-185">Typ jest tablicą dwuwymiarową jest zapisywany jako `<type>[,]` (na przykład `int[,]`, `double[,]`), i typ jest tablicą trójwymiarową jest zapisywany jako `<type>[,,]`, i tak dalej dla tablic wyższej wymiarów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="7b73f-186">Tylko podzbiór funkcji dostępnych dla tablice jednowymiarowe jest również dostępna dla tablic wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="7b73f-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="7b73f-187">Aby uzyskać więcej informacji, zobacz [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), i [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="7b73f-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="7b73f-188">Dzielenie tablicy i tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="7b73f-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="7b73f-189">W tablicy dwuwymiarowa (macierz) można wyodrębnić podrzędne macierzy Określanie zakresów i używając symbolu wieloznacznego (`*`) znaku do określenia całych wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="7b73f-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="7b73f-190">Począwszy od F # 3.1 można Rozłóż tablicy wielowymiarowej na subarrays sama lub starsza wymiaru.</span><span class="sxs-lookup"><span data-stu-id="7b73f-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="7b73f-191">Na przykład można uzyskać wektora z macierzy, określając pojedynczy wiersz lub kolumnę.</span><span class="sxs-lookup"><span data-stu-id="7b73f-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="7b73f-192">Możesz użyć tej funkcji tworzenia wycinków składni dla typów, które implementuje element operatory dostępu i przeciążony `GetSlice` metody.</span><span class="sxs-lookup"><span data-stu-id="7b73f-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="7b73f-193">Na przykład poniższy kod tworzy typ macierzy opakowuje tablicy 2D F #, implementuje właściwości elementu w celu zapewnienia obsługi indeksowanie tablicy, która implementuje trzy wersje tych `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="7b73f-194">Jeśli ten kod może pełnić rolę szablonu dla typów z macierzy, możesz użyć wszystkich operacji skalowania, które opisano w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="7b73f-195">Funkcji logicznych w tablicach</span><span class="sxs-lookup"><span data-stu-id="7b73f-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="7b73f-196">Funkcje [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) i [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) testować elementy w jedną lub dwie tablice, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7b73f-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="7b73f-197">Te funkcje przyjmować funkcja testu i zwracać `true` w przypadku elementu (lub element pary dla `Array.exists2`) który spełnia warunek.</span><span class="sxs-lookup"><span data-stu-id="7b73f-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="7b73f-198">Poniższy kod przedstawia użycie `Array.exists` i `Array.exists2`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="7b73f-199">W tych przykładach nowe funkcje są tworzone przez zastosowanie tylko jeden z argumentów w tych przypadkach argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="7b73f-200">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-200">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="7b73f-201">Podobnie, funkcja [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testów tablicy do ustalenia, czy każdy element ma spełnia warunek typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="7b73f-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="7b73f-202">Zmiana [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) jest samo przy użyciu funkcja logiczna, która obejmuje elementy z dwiema tablicami o równej długości.</span><span class="sxs-lookup"><span data-stu-id="7b73f-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="7b73f-203">Poniższy kod przedstawia użycie tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="7b73f-204">Poniżej przedstawiono dane wyjściowe dla tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="7b73f-204">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="7b73f-205">Wyszukiwanie tablic</span><span class="sxs-lookup"><span data-stu-id="7b73f-205">Searching Arrays</span></span>

<span data-ttu-id="7b73f-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) przyjmuje funkcja logiczna i zwraca pierwszy element, dla którego funkcja zwraca `true`, lub zgłasza <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Jeśli zostanie znaleziony żaden element, który spełnia warunek.</span><span class="sxs-lookup"><span data-stu-id="7b73f-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="7b73f-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) przypomina `Array.find`, ale zwraca indeks elementu zamiast elementu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="7b73f-208">Poniższy kod używa `Array.find` i `Array.findIndex` zlokalizować liczby, która jest idealny kwadrat i doskonałe modułu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="7b73f-209">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b73f-209">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="7b73f-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) przypomina `Array.find`, ale jej wynikiem jest typ opcji i zwraca `None` Jeśli zostanie znaleziony żaden element.</span><span class="sxs-lookup"><span data-stu-id="7b73f-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="7b73f-211">`Array.tryFind` należy użyć zamiast `Array.find` Jeśli nie wiesz, czy pasujący element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="7b73f-212">Podobnie [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) przypomina [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) z tą różnicą, że typ opcji jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="7b73f-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="7b73f-213">Jeśli element nie zostanie znaleziony, ta opcja jest `None`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="7b73f-214">Poniższy kod przedstawia użycie `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="7b73f-215">Ten kod jest zależny od poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="7b73f-216">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b73f-216">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="7b73f-217">Użyj [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) potrzebne do transformacji elementu oprócz znalezieniem.</span><span class="sxs-lookup"><span data-stu-id="7b73f-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="7b73f-218">Wynik jest pierwszym elementem, dla którego funkcja zwraca przekształcony element jako wartość opcji lub `None` Jeśli zostanie znaleziony żaden taki element.</span><span class="sxs-lookup"><span data-stu-id="7b73f-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="7b73f-219">Poniższy kod przedstawia użycie `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="7b73f-220">W takim przypadku zamiast wyrażenia lambda kilka funkcji pomocnika lokalnego są definiowane w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="7b73f-221">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b73f-221">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="7b73f-222">Wykonywanie obliczeń w tablicach</span><span class="sxs-lookup"><span data-stu-id="7b73f-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="7b73f-223">[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) Funkcja zwraca średnią każdego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="7b73f-224">Jest ograniczony do elementu typów, które obsługują dokładne dzielenie przez całkowitą, która obejmuje zmiennoprzecinkowych typów, ale nie jest spójne typy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="7b73f-225">[ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) Funkcja zwraca średnią wyników wywołania funkcji dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="7b73f-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="7b73f-226">Do tablicy typu całkowitego, można użyć `Array.averageBy` i funkcji konwersji każdy element zmiennoprzecinkowej punktu typu obliczenia.</span><span class="sxs-lookup"><span data-stu-id="7b73f-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="7b73f-227">Użyj [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) lub [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) można pobrać elementu maksymalnego lub minimalnego, jeśli typ elementu obsługuje.</span><span class="sxs-lookup"><span data-stu-id="7b73f-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="7b73f-228">Podobnie [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) i [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) Zezwalaj funkcja do wykonania, najpierw, możliwe, że do przekształcenia do typu, który obsługuje porównania.</span><span class="sxs-lookup"><span data-stu-id="7b73f-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="7b73f-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) Dodaje elementy tablicy i [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) wywołuje funkcję dla każdego elementu i dodaje wyniki ze sobą.</span><span class="sxs-lookup"><span data-stu-id="7b73f-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="7b73f-230">Aby wykonać funkcję dla każdego elementu w tablicy bez przechowywania zwracanych wartości, należy użyć [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span><span class="sxs-lookup"><span data-stu-id="7b73f-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="7b73f-231">Dla funkcji z dwiema tablicami o równej długości obejmujące użyj [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span><span class="sxs-lookup"><span data-stu-id="7b73f-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="7b73f-232">Jeśli należy zapewnić tablicę wyniki funkcji, użyj [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) lub [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), który działa na dwóch tablic naraz.</span><span class="sxs-lookup"><span data-stu-id="7b73f-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="7b73f-233">Zmiany [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) i [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) Zezwalaj na indeks elementu do uczestniczenia w obliczenia; dotyczy to także [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) i [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="7b73f-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="7b73f-234">Funkcje [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), i [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) wykonania algorytmy, które obejmują wszystkie elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="7b73f-235">Podobnie, zmiany [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) i [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) wykonać obliczenia na dwóch tablic.</span><span class="sxs-lookup"><span data-stu-id="7b73f-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="7b73f-236">Te funkcje umożliwiające wykonywanie obliczeń odpowiadają funkcji należących do tej samej nazwie w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="7b73f-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="7b73f-237">Przykłady użycia można znaleźć [wymieniono](lists.md).</span><span class="sxs-lookup"><span data-stu-id="7b73f-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="7b73f-238">Modyfikowanie tablic</span><span class="sxs-lookup"><span data-stu-id="7b73f-238">Modifying Arrays</span></span>

<span data-ttu-id="7b73f-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) Ustawia element określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="7b73f-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="7b73f-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) Określa zakres elementów w tablicy do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="7b73f-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="7b73f-241">Poniższy kod stanowi przykład `Array.fill`.</span><span class="sxs-lookup"><span data-stu-id="7b73f-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="7b73f-242">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7b73f-242">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="7b73f-243">Można użyć [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) do skopiowania podsekcji tablicy do innej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="7b73f-244">Konwertowanie do i z innych typów</span><span class="sxs-lookup"><span data-stu-id="7b73f-244">Converting to and from Other Types</span></span>

<span data-ttu-id="7b73f-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) tworzy tablicę z listy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="7b73f-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) tworzy tablicę z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7b73f-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="7b73f-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) i [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) konwertować na inne typy kolekcji z typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="7b73f-248">Sortowanie tablic</span><span class="sxs-lookup"><span data-stu-id="7b73f-248">Sorting Arrays</span></span>

<span data-ttu-id="7b73f-249">Użyj [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) Sortowanie tablicy za pomocą funkcji standardowego porównania.</span><span class="sxs-lookup"><span data-stu-id="7b73f-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="7b73f-250">Użyj [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) Określ funkcję, która generuje wartość, określany jako *klucza*, aby posortować przy użyciu funkcji standardowego porównania dla klucza.</span><span class="sxs-lookup"><span data-stu-id="7b73f-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="7b73f-251">Użyj [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) Jeśli chcesz podać funkcji niestandardowych porównania.</span><span class="sxs-lookup"><span data-stu-id="7b73f-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="7b73f-252">`Array.sort`, `Array.sortBy`, i `Array.sortWith` zwracają posortowana tablica jako nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="7b73f-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="7b73f-253">Zmiany [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), i [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modyfikowania istniejącej tablicy zamiast zwracać nową.</span><span class="sxs-lookup"><span data-stu-id="7b73f-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="7b73f-254">Tablice i spójnych kolekcji</span><span class="sxs-lookup"><span data-stu-id="7b73f-254">Arrays and Tuples</span></span>

<span data-ttu-id="7b73f-255">Funkcje [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) i [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) przekonwertować tablice par krotki krotek, tablic i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="7b73f-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="7b73f-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) i [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) przypominają one działać z krotek trzy elementy lub krotek trzech tablic.</span><span class="sxs-lookup"><span data-stu-id="7b73f-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="7b73f-257">Równoległe obliczenia w tablicach</span><span class="sxs-lookup"><span data-stu-id="7b73f-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="7b73f-258">Moduł [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) zawiera funkcje umożliwiające wykonywanie równoległe obliczenia w tablicach.</span><span class="sxs-lookup"><span data-stu-id="7b73f-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="7b73f-259">Ten moduł nie jest dostępne w aplikacjach, które odnoszą się do wersji programu .NET Framework, przed w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="7b73f-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b73f-260">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b73f-260">See Also</span></span>
[<span data-ttu-id="7b73f-261">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7b73f-261">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="7b73f-262">F #; Typy</span><span class="sxs-lookup"><span data-stu-id="7b73f-262">F#; Types</span></span>](fsharp-types.md)
