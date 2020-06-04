---
title: Short, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415560"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="a43ac-102">Short — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a43ac-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="a43ac-103">Przechowuje 16-bitowe (2-bajtowe) liczby całkowite z zakresu od-32 768 do 32 767.</span><span class="sxs-lookup"><span data-stu-id="a43ac-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a43ac-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a43ac-104">Remarks</span></span>  

 <span data-ttu-id="a43ac-105">Użyj `Short` typu danych, aby zawierać wartości całkowite, które nie wymagają pełnej szerokości danych `Integer` .</span><span class="sxs-lookup"><span data-stu-id="a43ac-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="a43ac-106">W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może ściśle spakować `Short` zmienne i zaoszczędzić użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="a43ac-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="a43ac-107">Wartość domyślna `Short` to 0.</span><span class="sxs-lookup"><span data-stu-id="a43ac-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="a43ac-108">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="a43ac-108">Literal assignments</span></span>

<span data-ttu-id="a43ac-109">Można zadeklarować i zainicjować `Short` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="a43ac-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="a43ac-110">Jeśli literał liczby całkowitej znajduje się poza zakresem `Short` (to jest, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.Int16.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a43ac-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="a43ac-111">W poniższym przykładzie liczby całkowite równe 1 034 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na `Short` wartości.</span><span class="sxs-lookup"><span data-stu-id="a43ac-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="a43ac-112">Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego.</span><span class="sxs-lookup"><span data-stu-id="a43ac-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a43ac-113">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="a43ac-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a43ac-114">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a43ac-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="a43ac-115">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="a43ac-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a43ac-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a43ac-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="a43ac-117">Literały numeryczne mogą również zawierać `S` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Short` Typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a43ac-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="a43ac-118">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="a43ac-118">Programming tips</span></span>

- <span data-ttu-id="a43ac-119">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="a43ac-119">**Widening.**</span></span> <span data-ttu-id="a43ac-120">`Short`Typ danych poszerza do `Integer` ,,, `Long` `Decimal` `Single` lub `Double` .</span><span class="sxs-lookup"><span data-stu-id="a43ac-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="a43ac-121">Oznacza to, że można przekonwertować `Short` na jeden z tych typów, bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="a43ac-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="a43ac-122">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="a43ac-122">**Type Characters.**</span></span> <span data-ttu-id="a43ac-123">Dołączanie znaku typu literału `S` do literału wymusza jego `Short` Typ danych.</span><span class="sxs-lookup"><span data-stu-id="a43ac-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="a43ac-124">`Short`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a43ac-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="a43ac-125">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="a43ac-125">**Framework Type.**</span></span> <span data-ttu-id="a43ac-126">Odpowiedni typ w .NET Framework jest <xref:System.Int16?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="a43ac-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a43ac-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a43ac-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="a43ac-128">Typy danych</span><span class="sxs-lookup"><span data-stu-id="a43ac-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="a43ac-129">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="a43ac-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="a43ac-130">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="a43ac-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="a43ac-131">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="a43ac-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="a43ac-132">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="a43ac-132">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="a43ac-133">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="a43ac-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
