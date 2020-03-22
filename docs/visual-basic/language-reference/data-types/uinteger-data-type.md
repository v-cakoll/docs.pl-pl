---
title: UInteger — Typ danych
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
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400786"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="f9dc1-102">UInteger — Typ danych</span><span class="sxs-lookup"><span data-stu-id="f9dc1-102">UInteger data type</span></span>

<span data-ttu-id="f9dc1-103">Przechowuje niepodpisane 32-bitowe (4-bajtowe) liczby całkowite o wartości od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9dc1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9dc1-104">Remarks</span></span>

<span data-ttu-id="f9dc1-105">Typ `UInteger` danych zapewnia największą niepodpisaną wartość w najbardziej wydajnej szerokości danych.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="f9dc1-106">Wartość domyślna `UInteger` to 0.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="f9dc1-107">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="f9dc1-107">Literal assignments</span></span>

<span data-ttu-id="f9dc1-108">Można zadeklarować i `UInteger` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="f9dc1-109">Jeśli litera liczba całkowita znajduje się `UInteger` poza zakresem (oznacza <xref:System.UInt32.MinValue?displayProperty=nameWithType> to, <xref:System.UInt32.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="f9dc1-110">W poniższym przykładzie liczby całkowite równe 3,000,000,000, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `UInteger` wartości.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="f9dc1-111">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f9dc1-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f9dc1-113">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="f9dc1-114">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f9dc1-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f9dc1-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="f9dc1-116">Literały liczbowe mogą również `UI` `ui` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) lub `UInteger` typ oznaczania typu danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="f9dc1-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="f9dc1-117">Programming tips</span></span>

<span data-ttu-id="f9dc1-118">`UInteger` Typy `Integer` danych zapewniają optymalną wydajność procesora 32-bitowego, ponieważ`UShort` `Short`mniejsze `Byte`typy całkowite ( , , , i `SByte`), nawet jeśli używają mniejszej liczby bitów, zajmuje więcej czasu na ładowanie, przechowywanie i pobieranie.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="f9dc1-119">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="f9dc1-119">**Negative Numbers.**</span></span> <span data-ttu-id="f9dc1-120">Ponieważ `UInteger` jest typem niepodpisanym, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="f9dc1-121">Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `UInteger`visual basic konwertuje wyrażenie na `Long` pierwsze.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="f9dc1-122">**Zgodność z CLS.**</span><span class="sxs-lookup"><span data-stu-id="f9dc1-122">**CLS Compliance.**</span></span> <span data-ttu-id="f9dc1-123">Typ `UInteger` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="f9dc1-124">**Zagadnienia międzyoperacyjne.**</span><span class="sxs-lookup"><span data-stu-id="f9dc1-124">**Interop Considerations.**</span></span> <span data-ttu-id="f9dc1-125">Jeśli są interfacing z składników nie zostały napisane dla .NET Framework, na przykład automatyzacji lub COM obiektów, należy pamiętać, że typy, takie jak `uint` może mieć inną szerokość danych (16 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="f9dc1-126">Jeśli przekazujesz 16-bitowy argument do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="f9dc1-127">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="f9dc1-127">**Widening.**</span></span> <span data-ttu-id="f9dc1-128">Typ `UInteger` danych rozszerza `Long`się `ULong` `Decimal`do `Single`, `Double`, , i .</span><span class="sxs-lookup"><span data-stu-id="f9dc1-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="f9dc1-129">Oznacza to, `UInteger` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="f9dc1-130">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="f9dc1-130">**Type Characters.**</span></span> <span data-ttu-id="f9dc1-131">Dołączenie znaków `UI` typu literału do literału `UInteger` wymusza go do typu danych.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="f9dc1-132">`UInteger`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="f9dc1-133">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="f9dc1-133">**Framework Type.**</span></span> <span data-ttu-id="f9dc1-134">Odpowiedni typ w .NET Framework <xref:System.UInt32?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9dc1-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9dc1-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="f9dc1-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="f9dc1-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f9dc1-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="f9dc1-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f9dc1-138">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f9dc1-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f9dc1-139">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="f9dc1-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="f9dc1-140">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="f9dc1-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
