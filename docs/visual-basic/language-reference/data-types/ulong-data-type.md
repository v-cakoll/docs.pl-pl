---
title: ULong — Typ danych (Visual Basic)
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
ms.openlocfilehash: 19a75f056436b858a22588d7ac5f37df5dd326f2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583115"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="0095e-102">ULong — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0095e-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="0095e-103">Przechowuje niepodpisane liczby całkowite 64-bitowe (8-bajtowe) w zakresie wartości z zakresu od 0 do 18446744073709551615 są (więcej niż 1,84 razy 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="0095e-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="0095e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0095e-104">Remarks</span></span>

<span data-ttu-id="0095e-105">Użyj `ULong` typ danych, aby zawierać dane binarne zbyt duże dla `UInteger`, lub największą liczbę wartości bez znaku.</span><span class="sxs-lookup"><span data-stu-id="0095e-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="0095e-106">Wartość domyślna `ULong` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="0095e-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="0095e-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="0095e-107">Literal assignments</span></span>

<span data-ttu-id="0095e-108">Można zadeklarować i zainicjować zmienną `ULong`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="0095e-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0095e-109">Jeśli literał liczby całkowitej znajduje się poza zakresem `ULong` (czyli jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0095e-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="0095e-110">W poniższym przykładzie liczby całkowite równe 7 934 076 125 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `ULong`.</span><span class="sxs-lookup"><span data-stu-id="0095e-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="0095e-111">Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="0095e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0095e-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="0095e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0095e-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0095e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="0095e-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="0095e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0095e-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0095e-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="0095e-116">Literały numeryczne mogą również zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) `UL` lub `ul`, aby zauważyć `ULong` typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0095e-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="0095e-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="0095e-117">Programming tips</span></span>

- <span data-ttu-id="0095e-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="0095e-118">**Negative Numbers.**</span></span> <span data-ttu-id="0095e-119">Ponieważ `ULong` jest typem bez znaku, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="0095e-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="0095e-120">Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `ULong`, Visual Basic konwertuje wyrażenie na `Decimal` jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="0095e-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="0095e-121">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="0095e-121">**CLS Compliance.**</span></span> <span data-ttu-id="0095e-122">@No__t_0 typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="0095e-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="0095e-123">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="0095e-123">**Interop Considerations.**</span></span> <span data-ttu-id="0095e-124">Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `ulong` mogą mieć różną szerokość danych (32 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="0095e-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="0095e-125">Jeśli przekazujesz argument 32-bitowy do takiego składnika, zadeklaruj go jako `UInteger` zamiast `ULong` w zarządzanym kodzie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0095e-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="0095e-126">Ponadto Automatyzacja nie obsługuje 64-bitowych liczb całkowitych w systemie Windows 95, Windows 98, Windows ME lub Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="0095e-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="0095e-127">Nie można przekazać Visual Basicgo argumentu `ULong` do składnika automatyzacji na tych platformach.</span><span class="sxs-lookup"><span data-stu-id="0095e-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="0095e-128">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="0095e-128">**Widening.**</span></span> <span data-ttu-id="0095e-129">Typ danych `ULong` rozszerza `Decimal`, `Single` i `Double`.</span><span class="sxs-lookup"><span data-stu-id="0095e-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="0095e-130">Oznacza to, że można skonwertować `ULong` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="0095e-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="0095e-131">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="0095e-131">**Type Characters.**</span></span> <span data-ttu-id="0095e-132">Dołączanie znaków literału `UL` do literału wymusza `ULong` do typu danych.</span><span class="sxs-lookup"><span data-stu-id="0095e-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="0095e-133">`ULong` nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="0095e-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="0095e-134">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="0095e-134">**Framework Type.**</span></span> <span data-ttu-id="0095e-135">Odpowiedni typ w .NET Framework jest strukturą <xref:System.UInt64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0095e-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0095e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0095e-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="0095e-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="0095e-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0095e-138">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="0095e-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0095e-139">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="0095e-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0095e-140">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="0095e-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="0095e-141">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="0095e-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
