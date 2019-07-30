---
title: Tablice
description: Dowiedz się, jak tworzyć tablice i używać F# ich w języku programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 142d2c8d9aa7247e1490867a7bb905e2e7fec41e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630039"
---
# <a name="arrays"></a><span data-ttu-id="3968f-103">Tablice</span><span class="sxs-lookup"><span data-stu-id="3968f-103">Arrays</span></span>

> [!NOTE]
> <span data-ttu-id="3968f-104">Link odwołania do interfejsu API spowoduje przejście do witryny MSDN.</span><span class="sxs-lookup"><span data-stu-id="3968f-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="3968f-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="3968f-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="3968f-106">Tablice są stałymi, niemodyfikowalnymi kolekcjami kolejnych elementów danych, które są tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="3968f-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="3968f-107">Tworzenie tablic</span><span class="sxs-lookup"><span data-stu-id="3968f-107">Creating Arrays</span></span>

<span data-ttu-id="3968f-108">Tablice można tworzyć na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="3968f-108">You can create arrays in several ways.</span></span> <span data-ttu-id="3968f-109">Możesz utworzyć małą tablicę, określając kolejne wartości między `[|` i `|]` i rozdzielone średnikami, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="3968f-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="3968f-110">Można również umieścić każdy element w osobnym wierszu, w którym przypadku separator średników jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3968f-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="3968f-111">Typ elementów tablicy jest wywnioskowany na podstawie używanych literałów i musi być spójny.</span><span class="sxs-lookup"><span data-stu-id="3968f-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="3968f-112">Poniższy kod powoduje błąd, ponieważ 1,0 jest zmiennoprzecinkowa i 2 i 3 są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="3968f-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="3968f-113">Można również użyć wyrażeń sekwencji do tworzenia tablic.</span><span class="sxs-lookup"><span data-stu-id="3968f-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="3968f-114">Poniżej znajduje się przykład, który tworzy tablicę kwadratów liczb całkowitych z zakresu od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="3968f-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="3968f-115">Aby utworzyć tablicę, w której wszystkie elementy są zainicjowane do zera, użyj `Array.zeroCreate`.</span><span class="sxs-lookup"><span data-stu-id="3968f-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a><span data-ttu-id="3968f-116">Uzyskiwanie dostępu do elementów</span><span class="sxs-lookup"><span data-stu-id="3968f-116">Accessing Elements</span></span>

<span data-ttu-id="3968f-117">Możesz uzyskać dostęp do elementów tablicy przy użyciu operatora kropki`.`() i nawiasów `]`kwadratowych (`[` i).</span><span class="sxs-lookup"><span data-stu-id="3968f-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="3968f-118">Indeksy tablicy zaczynają się od 0.</span><span class="sxs-lookup"><span data-stu-id="3968f-118">Array indexes start at 0.</span></span>

<span data-ttu-id="3968f-119">Możesz również uzyskać dostęp do elementów tablicy przy użyciu notacji wycinka, która umożliwia określenie podzakresu tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="3968f-120">Przykłady zapisu wycinka są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="3968f-121">Gdy jest używana notacja wycinka, tworzona jest nowa kopia tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-121">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="3968f-122">Typy tablic i moduły</span><span class="sxs-lookup"><span data-stu-id="3968f-122">Array Types and Modules</span></span>

<span data-ttu-id="3968f-123">Typ wszystkich F# tablic jest typem <xref:System.Array?displayProperty=nameWithType>.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3968f-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3968f-124">W związku F# z tym tablice obsługują wszystkie funkcje dostępne <xref:System.Array?displayProperty=nameWithType>w programie.</span><span class="sxs-lookup"><span data-stu-id="3968f-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3968f-125">Moduł [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) biblioteki obsługuje operacje na tablicach jednowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="3968f-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="3968f-126">Moduły `Array2D`, `Array3D`i zawierająfunkcje,któreobsługująoperacjenatablicachodpowiedniodwa,trzyiczterywymiary.`Array4D`</span><span class="sxs-lookup"><span data-stu-id="3968f-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="3968f-127">Można utworzyć tablice rangi większe niż cztery przy użyciu <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3968f-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="3968f-128">Proste funkcje</span><span class="sxs-lookup"><span data-stu-id="3968f-128">Simple Functions</span></span>

<span data-ttu-id="3968f-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)Pobiera element.</span><span class="sxs-lookup"><span data-stu-id="3968f-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="3968f-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)podaje długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="3968f-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)Ustawia element na określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="3968f-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="3968f-132">Poniższy przykład kodu ilustruje sposób korzystania z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="3968f-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="3968f-133">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-133">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="3968f-134">Funkcje tworzące tablice</span><span class="sxs-lookup"><span data-stu-id="3968f-134">Functions That Create Arrays</span></span>

<span data-ttu-id="3968f-135">Kilka funkcji tworzy tablice bez konieczności stosowania istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="3968f-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)tworzy nową tablicę, która nie zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="3968f-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="3968f-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)Tworzy tablicę o określonym rozmiarze i ustawia wszystkie elementy na dostarczone wartości.</span><span class="sxs-lookup"><span data-stu-id="3968f-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="3968f-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)Tworzy tablicę z uwzględnieniem wymiaru i funkcji w celu wygenerowania elementów.</span><span class="sxs-lookup"><span data-stu-id="3968f-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="3968f-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)Tworzy tablicę, w której wszystkie elementy są inicjowane jako wartość zerowa dla typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="3968f-140">Poniższy kod ilustruje te funkcje.</span><span class="sxs-lookup"><span data-stu-id="3968f-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="3968f-141">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-141">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="3968f-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)tworzy nową tablicę zawierającą elementy, które są kopiowane z istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="3968f-143">Należy pamiętać, że kopia jest kopią skróconą, co oznacza, że jeśli typem elementu jest typ referencyjny, kopiowane jest tylko odwołanie, a nie obiekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="3968f-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="3968f-144">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3968f-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="3968f-145">Dane wyjściowe powyższego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-145">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="3968f-146">Ciąg `Test1` pojawia się tylko w pierwszej tablicy, ponieważ operacja tworzenia nowego elementu zastępuje odwołanie w `firstArray` , ale nie wpływa na pierwotne odwołanie do pustego ciągu, który nadal występuje w `secondArray`.</span><span class="sxs-lookup"><span data-stu-id="3968f-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="3968f-147">Ciąg `Test2` pojawia się w obu tablicach, `Insert` ponieważ operacja na <xref:System.Text.StringBuilder?displayProperty=nameWithType> typie ma wpływ na <xref:System.Text.StringBuilder?displayProperty=nameWithType> obiekt źródłowy, do którego odwołuje się obie tablice.</span><span class="sxs-lookup"><span data-stu-id="3968f-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="3968f-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)generuje nową tablicę z podzakresu tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="3968f-149">Należy określić Podzakres, podając początkowy indeks i długość.</span><span class="sxs-lookup"><span data-stu-id="3968f-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="3968f-150">Poniższy kod ilustruje użycie `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="3968f-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="3968f-151">Dane wyjściowe pokazują, że podtablica zaczyna się od elementu 5 i zawiera 10 elementów.</span><span class="sxs-lookup"><span data-stu-id="3968f-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="3968f-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)tworzy nową tablicę przez połączenie dwóch istniejących tablic.</span><span class="sxs-lookup"><span data-stu-id="3968f-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="3968f-153">Poniższy kod ilustruje **tablicę Array. Append**.</span><span class="sxs-lookup"><span data-stu-id="3968f-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="3968f-154">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-154">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="3968f-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)wybiera elementy tablicy do uwzględnienia w nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="3968f-156">Poniższy kod ilustruje `Array.choose`.</span><span class="sxs-lookup"><span data-stu-id="3968f-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="3968f-157">Należy zauważyć, że typ elementu tablicy nie musi być zgodny z typem wartości zwracanej w typie opcji.</span><span class="sxs-lookup"><span data-stu-id="3968f-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="3968f-158">W tym przykładzie typ elementu to `int` i opcja jest wynikiem funkcji wielomianu, `elem*elem - 1`jako liczby zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="3968f-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="3968f-159">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-159">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="3968f-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)uruchamia określoną funkcję dla każdego elementu tablicy istniejącej tablicy, a następnie zbiera elementy wygenerowane przez funkcję i łączy je w nową tablicę.</span><span class="sxs-lookup"><span data-stu-id="3968f-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="3968f-161">Poniższy kod ilustruje `Array.collect`.</span><span class="sxs-lookup"><span data-stu-id="3968f-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="3968f-162">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-162">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="3968f-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)wykonuje sekwencję tablic i łączy je w jedną tablicę.</span><span class="sxs-lookup"><span data-stu-id="3968f-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="3968f-164">Poniższy kod ilustruje `Array.concat`.</span><span class="sxs-lookup"><span data-stu-id="3968f-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="3968f-165">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-165">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="3968f-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)przyjmuje funkcję warunku logicznego i generuje nową tablicę zawierającą tylko te elementy z tablicy wejściowej, dla których warunek ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="3968f-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="3968f-167">Poniższy kod ilustruje `Array.filter`.</span><span class="sxs-lookup"><span data-stu-id="3968f-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="3968f-168">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-168">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="3968f-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)generuje nową tablicę przez odwracanie kolejności istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="3968f-170">Poniższy kod ilustruje `Array.rev`.</span><span class="sxs-lookup"><span data-stu-id="3968f-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="3968f-171">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-171">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="3968f-172">Można łatwo połączyć funkcje w module Array, które przekształcają tablice za pomocą operatora potoku (`|>`), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3968f-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="3968f-173">Dane wyjściowe to</span><span class="sxs-lookup"><span data-stu-id="3968f-173">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="3968f-174">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="3968f-174">Multidimensional Arrays</span></span>

<span data-ttu-id="3968f-175">Można utworzyć tablicę wielowymiarową, ale nie ma składni do pisania wielowymiarowego literału tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="3968f-176">Użyj operatora [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) , aby utworzyć tablicę z sekwencji sekwencji elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="3968f-177">Sekwencje mogą być literałami tablicowymi lub listami.</span><span class="sxs-lookup"><span data-stu-id="3968f-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="3968f-178">Na przykład poniższy kod tworzy tablicę dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="3968f-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="3968f-179">Można również użyć funkcji [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) , aby zainicjować tablice dwóch wymiarów, a podobne funkcje są dostępne dla tablic trzech i czterech wymiarów.</span><span class="sxs-lookup"><span data-stu-id="3968f-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="3968f-180">Funkcje te przyjmują funkcję, która jest używana do tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="3968f-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="3968f-181">Aby utworzyć dwuwymiarową tablicę, która zawiera elementy ustawione na wartość początkową zamiast określania funkcji, należy użyć [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) funkcji, która jest również dostępna dla tablic do czterech wymiarów.</span><span class="sxs-lookup"><span data-stu-id="3968f-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="3968f-182">Poniższy przykład kodu najpierw pokazuje, jak utworzyć tablicę tablic zawierających wymagane elementy, a następnie użyć `Array2D.init` do wygenerowania odpowiedniej tablicy dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="3968f-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="3968f-183">Składnia indeksowania tablicy i skalowanie wycinków jest obsługiwana w przypadku tablic o wartości do rangi 4.</span><span class="sxs-lookup"><span data-stu-id="3968f-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="3968f-184">Po określeniu indeksu w wielu wymiarach, należy użyć przecinków do oddzielenia indeksów, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3968f-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="3968f-185">Typ tablicy dwuwymiarowej `<type>[,]` jest zapisywana jako (na `int[,]`przykład, `double[,]`), a typ trójwymiarowej tablicy jest zapisywana jako `<type>[,,]`itd. dla tablic o wyższych wymiarach.</span><span class="sxs-lookup"><span data-stu-id="3968f-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="3968f-186">Tylko podzestaw funkcji dostępnych dla tablic jednowymiarowych jest również dostępny dla tablic wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="3968f-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="3968f-187">Aby uzyskać więcej informacji, [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)zobacz [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d) [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d),, i [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="3968f-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="3968f-188">Dzielenie tablic i tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="3968f-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="3968f-189">W tablicy dwuwymiarowej (macierzy) można wyodrębnić tablicę podrzędną, określając zakresy i używając znaku wieloznacznego (`*`) w celu określenia całych wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="3968f-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="3968f-190">Od F# 3,1 można rozłożyć tablicę wielowymiarową na podtablice tego samego lub niższego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="3968f-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="3968f-191">Na przykład można uzyskać wektor z macierzy, określając pojedynczy wiersz lub kolumnę.</span><span class="sxs-lookup"><span data-stu-id="3968f-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="3968f-192">Można użyć tej składni wycinków dla typów, które implementują operatory dostępu do elementów i `GetSlice` przeciążone metody.</span><span class="sxs-lookup"><span data-stu-id="3968f-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="3968f-193">Na przykład poniższy kod tworzy typ macierzy, która otacza tablicę F# 2D, implementuje właściwość elementu w celu zapewnienia obsługi indeksowania tablicy i implementuje trzy wersje programu. `GetSlice`</span><span class="sxs-lookup"><span data-stu-id="3968f-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="3968f-194">Jeśli możesz użyć tego kodu jako szablonu dla typów macierzy, możesz użyć wszystkich operacji tworzenia wycinków, które opisano w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3968f-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="3968f-195">Funkcje logiczne w tablicach</span><span class="sxs-lookup"><span data-stu-id="3968f-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="3968f-196">Elementy [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) Functions [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) i test są odpowiednio w jednej lub dwóch tablicach.</span><span class="sxs-lookup"><span data-stu-id="3968f-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="3968f-197">Te funkcje przyjmują funkcję testową i `true` zwracają, jeśli istnieje element (lub para elementów dla `Array.exists2`), który spełnia warunek.</span><span class="sxs-lookup"><span data-stu-id="3968f-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="3968f-198">Poniższy kod ilustruje użycie `Array.exists` i. `Array.exists2`</span><span class="sxs-lookup"><span data-stu-id="3968f-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="3968f-199">W tych przykładach nowe funkcje są tworzone przez zastosowanie tylko jednego z argumentów, w takich przypadkach, argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="3968f-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="3968f-200">Dane wyjściowe powyższego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-200">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="3968f-201">Podobnie funkcja [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testuje tablicę, aby określić, czy każdy element spełnia warunek logiczny.</span><span class="sxs-lookup"><span data-stu-id="3968f-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="3968f-202">Odmiana [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) wykonuje tę samą czynność przy użyciu funkcji logicznej, która obejmuje elementy dwóch tablic o równej długości.</span><span class="sxs-lookup"><span data-stu-id="3968f-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="3968f-203">Poniższy kod ilustruje sposób korzystania z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="3968f-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="3968f-204">Dane wyjściowe dla tych przykładów są następujące.</span><span class="sxs-lookup"><span data-stu-id="3968f-204">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="3968f-205">Wyszukiwanie tablic</span><span class="sxs-lookup"><span data-stu-id="3968f-205">Searching Arrays</span></span>

<span data-ttu-id="3968f-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)przyjmuje funkcję logiczną i zwraca pierwszy element, dla którego funkcja zwraca `true`, lub <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> wywołuje Jeśli nie zostanie znaleziony żaden element, który spełnia warunek.</span><span class="sxs-lookup"><span data-stu-id="3968f-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="3968f-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)jest podobne `Array.find`, z tą różnicą, że zwraca indeks elementu zamiast samego elementu.</span><span class="sxs-lookup"><span data-stu-id="3968f-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="3968f-208">Poniższy kod używa `Array.find` i `Array.findIndex` , aby zlokalizować liczbę, która jest idealnym kwadratem i idealnym modułem.</span><span class="sxs-lookup"><span data-stu-id="3968f-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="3968f-209">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-209">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="3968f-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)jest podobne `Array.find`, z tą różnicą, że jej wynik jest typem opcji i `None` zwraca, jeśli nie znaleziono żadnego elementu.</span><span class="sxs-lookup"><span data-stu-id="3968f-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="3968f-211">`Array.tryFind`powinien być używany zamiast `Array.find` gdy nie wiadomo, czy pasujący element znajduje się w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="3968f-212">Podobnie, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) jest taka [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) , jak z tą różnicą, że typ opcji jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="3968f-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="3968f-213">Jeśli nie zostanie znaleziony żaden element, opcja jest `None`.</span><span class="sxs-lookup"><span data-stu-id="3968f-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="3968f-214">Poniższy kod ilustruje użycie `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="3968f-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="3968f-215">Ten kod zależy od poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="3968f-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="3968f-216">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-216">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="3968f-217">Użyj [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) , gdy chcesz przekształcić element, a także go znaleźć.</span><span class="sxs-lookup"><span data-stu-id="3968f-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="3968f-218">Wynikiem jest pierwszy element, dla którego funkcja zwraca przekształcony element jako wartość opcji lub `None` Jeśli nie można znaleźć takiego elementu.</span><span class="sxs-lookup"><span data-stu-id="3968f-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="3968f-219">Poniższy kod ilustruje użycie `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="3968f-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="3968f-220">W tym przypadku zamiast wyrażenia lambda, kilka lokalnych funkcji pomocniczych jest zdefiniowanych do uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="3968f-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="3968f-221">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-221">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="3968f-222">Wykonywanie obliczeń w tablicach</span><span class="sxs-lookup"><span data-stu-id="3968f-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="3968f-223">[`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) Funkcja zwraca średnią każdego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="3968f-224">Jest ono ograniczone do typów elementów, które obsługują dokładne dzielenie przez liczbę całkowitą, która obejmuje typy zmiennoprzecinkowe, ale nie typy całkowite.</span><span class="sxs-lookup"><span data-stu-id="3968f-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="3968f-225">[`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) Funkcja zwraca średnią wyników wywołania funkcji dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="3968f-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="3968f-226">W przypadku tablicy typu całkowitego można użyć `Array.averageBy` funkcji i przekonwertować każdy element na typ zmiennoprzecinkowy obliczenia.</span><span class="sxs-lookup"><span data-stu-id="3968f-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="3968f-227">Użyj [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) [lub`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) , aby uzyskać maksimum lub minimum elementu, jeśli jest obsługiwany przez typ elementu.</span><span class="sxs-lookup"><span data-stu-id="3968f-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="3968f-228">[`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) Podobnie i [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) Zezwalaj na wykonywanie funkcji jako pierwszej, na przykład w celu przekształcenia do typu, który obsługuje porównanie.</span><span class="sxs-lookup"><span data-stu-id="3968f-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="3968f-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)dodaje elementy tablicy i [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) wywołuje funkcję dla każdego elementu i dodaje wyniki ze sobą.</span><span class="sxs-lookup"><span data-stu-id="3968f-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="3968f-230">Aby wykonać funkcję dla każdego elementu w tablicy bez przechowywania wartości zwracanych, użyj [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span><span class="sxs-lookup"><span data-stu-id="3968f-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="3968f-231">Dla funkcji obejmującej dwie tablice o równej długości Użyj [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span><span class="sxs-lookup"><span data-stu-id="3968f-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="3968f-232">Jeśli trzeba również zachować tablicę wyników funkcji, użyj [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) lub [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), która działa w dwóch tablicach w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="3968f-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="3968f-233">Różnice [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) i [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) zezwalają na indeks elementu, który ma być uwzględniony w obliczeniach; taka sama wartość [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) dotyczy i [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="3968f-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="3968f-234">Algorytmy [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09)Functions [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d) [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [,`Array.reduceBack`,,](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9) [i`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) Execute, które obejmują wszystkie elementy tablicy. [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)</span><span class="sxs-lookup"><span data-stu-id="3968f-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="3968f-235">Podobnie, różnice [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) i [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) wykonywanie obliczeń na dwóch tablicach.</span><span class="sxs-lookup"><span data-stu-id="3968f-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="3968f-236">Te funkcje do wykonywania obliczeń odpowiadają funkcjom o tej samej nazwie w [module list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="3968f-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="3968f-237">Aby zapoznać się z przykładami użycia, zobacz [listy](lists.md).</span><span class="sxs-lookup"><span data-stu-id="3968f-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="3968f-238">Modyfikowanie tablic</span><span class="sxs-lookup"><span data-stu-id="3968f-238">Modifying Arrays</span></span>

<span data-ttu-id="3968f-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)Ustawia element na określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="3968f-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="3968f-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)ustawia zakres elementów w tablicy do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="3968f-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="3968f-241">Poniższy kod zawiera przykład `Array.fill`.</span><span class="sxs-lookup"><span data-stu-id="3968f-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="3968f-242">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="3968f-242">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="3968f-243">Można użyć [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) , aby skopiować podsekcję jednej tablicy do innej tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="3968f-244">Konwertowanie na i z innych typów</span><span class="sxs-lookup"><span data-stu-id="3968f-244">Converting to and from Other Types</span></span>

<span data-ttu-id="3968f-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)Tworzy tablicę z listy.</span><span class="sxs-lookup"><span data-stu-id="3968f-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="3968f-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)Tworzy tablicę z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3968f-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="3968f-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)i [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) Konwertuj na inne typy kolekcji z typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="3968f-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="3968f-248">Sortowanie tablic</span><span class="sxs-lookup"><span data-stu-id="3968f-248">Sorting Arrays</span></span>

<span data-ttu-id="3968f-249">Użyj [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) , aby posortować tablicę przy użyciu funkcji porównania generycznej.</span><span class="sxs-lookup"><span data-stu-id="3968f-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="3968f-250">Użyj [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) , aby określić funkcję, która generuje wartość, która jest określana jako *klucz*, aby sortować przy użyciu funkcji porównywania generycznego w kluczu.</span><span class="sxs-lookup"><span data-stu-id="3968f-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="3968f-251">Użyj [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) , jeśli chcesz podać niestandardową funkcję porównania.</span><span class="sxs-lookup"><span data-stu-id="3968f-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="3968f-252">`Array.sort`, `Array.sortBy` i`Array.sortWith` wszystkie zwracają posortowaną tablicę jako nową tablicę.</span><span class="sxs-lookup"><span data-stu-id="3968f-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="3968f-253">Zmiany [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)i [modyfikująistniejącątablicęzamiastzwracaćnowe.`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b)</span><span class="sxs-lookup"><span data-stu-id="3968f-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="3968f-254">Tablice i krotki</span><span class="sxs-lookup"><span data-stu-id="3968f-254">Arrays and Tuples</span></span>

<span data-ttu-id="3968f-255">Funkcje [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) [i`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) konwertują tablice par krotek na krotki tablic i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="3968f-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="3968f-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)i [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) są podobne, z tą różnicą, że współpracują z krotkami trzech elementów lub krotekmi trzech tablic.</span><span class="sxs-lookup"><span data-stu-id="3968f-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="3968f-257">Obliczenia równoległe w tablicach</span><span class="sxs-lookup"><span data-stu-id="3968f-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="3968f-258">Moduł [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) zawiera funkcje do wykonywania obliczeń równoległych w tablicach.</span><span class="sxs-lookup"><span data-stu-id="3968f-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="3968f-259">Ten moduł nie jest dostępny w aplikacjach przeznaczonych dla wersji .NET Framework wcześniejszych niż wersja 4.</span><span class="sxs-lookup"><span data-stu-id="3968f-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="3968f-260">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3968f-260">See also</span></span>

- [<span data-ttu-id="3968f-261">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="3968f-261">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3968f-262">Typy F#</span><span class="sxs-lookup"><span data-stu-id="3968f-262">F# Types</span></span>](fsharp-types.md)
