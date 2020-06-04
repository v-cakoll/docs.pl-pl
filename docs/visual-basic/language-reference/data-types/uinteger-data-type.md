---
title: UInteger, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 11070f6c7f3259b8c34528eb54d99b031b68f9f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415547"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="7537d-102">UInteger — Typ danych</span><span class="sxs-lookup"><span data-stu-id="7537d-102">UInteger data type</span></span>

<span data-ttu-id="7537d-103">Przechowuje niepodpisane liczby całkowite 32-bitowe (4-bajtowe) w zakresie wartości z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="7537d-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="7537d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7537d-104">Remarks</span></span>

<span data-ttu-id="7537d-105">`UInteger`Typ danych zapewnia największą wartość bez znaku w najbardziej wydajnej szerokości danych.</span><span class="sxs-lookup"><span data-stu-id="7537d-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="7537d-106">Wartość domyślna `UInteger` to 0.</span><span class="sxs-lookup"><span data-stu-id="7537d-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="7537d-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="7537d-107">Literal assignments</span></span>

<span data-ttu-id="7537d-108">Można zadeklarować i zainicjować `UInteger` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="7537d-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="7537d-109">Jeśli literał liczby całkowitej znajduje się poza zakresem `UInteger` (to jest, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7537d-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="7537d-110">W poniższym przykładzie liczby całkowite równe 3 000 000 000 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `UInteger` wartości.</span><span class="sxs-lookup"><span data-stu-id="7537d-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="7537d-111">Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego.</span><span class="sxs-lookup"><span data-stu-id="7537d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="7537d-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="7537d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7537d-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7537d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="7537d-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="7537d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="7537d-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="7537d-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="7537d-116">Literały numeryczne mogą również zawierać `UI` `ui` [znak](../../programming-guide/language-features/data-types/type-characters.md) lub, aby zauważyć `UInteger` Typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7537d-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="7537d-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="7537d-117">Programming tips</span></span>

<span data-ttu-id="7537d-118">`UInteger`Typy i `Integer` zapewniają optymalną wydajność procesora 32-bitowego, ponieważ mniejsze typy całkowite ( `UShort` , `Short` , `Byte` i `SByte` ), nawet jeśli używają mniejszej liczby bitów, poświęć więcej czasu na załadowanie, przechowywanie i pobieranie.</span><span class="sxs-lookup"><span data-stu-id="7537d-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="7537d-119">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="7537d-119">**Negative Numbers.**</span></span> <span data-ttu-id="7537d-120">Ponieważ `UInteger` jest typem bez znaku, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="7537d-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="7537d-121">W przypadku użycia jednoargumentowego operatora minus ( `-` ) w wyrażeniu, którego typem jest typ `UInteger` , Visual Basic konwertuje wyrażenie na `Long` pierwsze.</span><span class="sxs-lookup"><span data-stu-id="7537d-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="7537d-122">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="7537d-122">**CLS Compliance.**</span></span> <span data-ttu-id="7537d-123">`UInteger`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="7537d-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="7537d-124">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="7537d-124">**Interop Considerations.**</span></span> <span data-ttu-id="7537d-125">Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `uint` mogą mieć różną szerokość danych (16 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="7537d-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="7537d-126">Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7537d-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="7537d-127">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="7537d-127">**Widening.**</span></span> <span data-ttu-id="7537d-128">`UInteger`Typ danych poszerza do `Long` ,,, `ULong` `Decimal` `Single` , i `Double` .</span><span class="sxs-lookup"><span data-stu-id="7537d-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="7537d-129">Oznacza to, że można dokonać konwersji `UInteger` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="7537d-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="7537d-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="7537d-130">**Type Characters.**</span></span> <span data-ttu-id="7537d-131">Dołączanie znaków literału `UI` do literału wymusza jego do `UInteger` typu danych.</span><span class="sxs-lookup"><span data-stu-id="7537d-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="7537d-132">`UInteger`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="7537d-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="7537d-133">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="7537d-133">**Framework Type.**</span></span> <span data-ttu-id="7537d-134">Odpowiedni typ w .NET Framework jest <xref:System.UInt32?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="7537d-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="7537d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7537d-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="7537d-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7537d-136">Data Types</span></span>](index.md)
- [<span data-ttu-id="7537d-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7537d-137">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="7537d-138">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="7537d-138">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="7537d-139">Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="7537d-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="7537d-140">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="7537d-140">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
