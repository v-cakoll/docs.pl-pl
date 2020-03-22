---
title: ULong, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400702"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="456e7-102">UDlić typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="456e7-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="456e7-103">Posiada niepodpisane 64-bitowe (8-bajtowe) liczby całkowite o wartości od 0 do 18 446 744 073 709 551 615 (ponad 1,84 razy 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="456e7-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="456e7-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="456e7-104">Remarks</span></span>

<span data-ttu-id="456e7-105">Użyj `ULong` typu danych, aby zawierać `UInteger`dane binarne zbyt duże dla lub największe możliwe niepodpisane wartości całkowite.</span><span class="sxs-lookup"><span data-stu-id="456e7-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="456e7-106">Wartość domyślna `ULong` to 0.</span><span class="sxs-lookup"><span data-stu-id="456e7-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="456e7-107">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="456e7-107">Literal assignments</span></span>

<span data-ttu-id="456e7-108">Można zadeklarować i `ULong` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="456e7-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="456e7-109">Jeśli litera liczba całkowita znajduje się `ULong` poza zakresem (oznacza <xref:System.UInt64.MinValue?displayProperty=nameWithType> to, <xref:System.UInt64.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="456e7-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="456e7-110">W poniższym przykładzie liczby całkowite równe 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `ULong` wartości.</span><span class="sxs-lookup"><span data-stu-id="456e7-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="456e7-111">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="456e7-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="456e7-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="456e7-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="456e7-113">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="456e7-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="456e7-114">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="456e7-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="456e7-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="456e7-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="456e7-116">Literały liczbowe mogą również `UL` `ul` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) lub `ULong` typ oznaczania typu danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="456e7-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="456e7-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="456e7-117">Programming tips</span></span>

- <span data-ttu-id="456e7-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="456e7-118">**Negative Numbers.**</span></span> <span data-ttu-id="456e7-119">Ponieważ `ULong` jest typem niepodpisanym, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="456e7-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="456e7-120">Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `ULong`visual basic konwertuje wyrażenie na `Decimal` pierwsze.</span><span class="sxs-lookup"><span data-stu-id="456e7-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="456e7-121">**Zgodność z CLS.**</span><span class="sxs-lookup"><span data-stu-id="456e7-121">**CLS Compliance.**</span></span> <span data-ttu-id="456e7-122">Typ `ULong` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="456e7-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="456e7-123">**Zagadnienia międzyoperacyjne.**</span><span class="sxs-lookup"><span data-stu-id="456e7-123">**Interop Considerations.**</span></span> <span data-ttu-id="456e7-124">Jeśli są interfacing z składników nie zostały napisane dla .NET Framework, na przykład automatyzacji lub COM obiektów, należy pamiętać, że typy, takie jak `ulong` może mieć inną szerokość danych (32 bity) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="456e7-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="456e7-125">Jeśli przekazujesz 32-bitowy argument do takiego składnika, zadeklaruj go jako `UInteger` zamiast `ULong` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="456e7-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="456e7-126">Ponadto automatyzacja nie obsługuje 64-bitowych liczby całkowite w systemach Windows 95, Windows 98, Windows ME lub Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="456e7-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="456e7-127">Nie można przekazać `ULong` argumentu języka Visual Basic do składnika automatyzacji na tych platformach.</span><span class="sxs-lookup"><span data-stu-id="456e7-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="456e7-128">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="456e7-128">**Widening.**</span></span> <span data-ttu-id="456e7-129">Typ `ULong` danych rozszerza `Decimal`się `Single`na `Double`, i .</span><span class="sxs-lookup"><span data-stu-id="456e7-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="456e7-130">Oznacza to, `ULong` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="456e7-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="456e7-131">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="456e7-131">**Type Characters.**</span></span> <span data-ttu-id="456e7-132">Dołączenie znaków `UL` typu literału do literału `ULong` wymusza go do typu danych.</span><span class="sxs-lookup"><span data-stu-id="456e7-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="456e7-133">`ULong`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="456e7-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="456e7-134">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="456e7-134">**Framework Type.**</span></span> <span data-ttu-id="456e7-135">Odpowiedni typ w .NET Framework <xref:System.UInt64?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="456e7-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="456e7-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="456e7-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="456e7-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="456e7-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="456e7-138">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="456e7-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="456e7-139">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="456e7-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="456e7-140">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="456e7-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="456e7-141">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="456e7-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
