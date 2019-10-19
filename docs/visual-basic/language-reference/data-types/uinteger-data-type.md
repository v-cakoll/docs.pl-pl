---
title: UInteger — — Typ danych (Visual Basic)
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
ms.openlocfilehash: 1ae0cbd3a518bf863a3c57f50934837a486d2901
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583135"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="f0a9e-102">UInteger — Typ danych</span><span class="sxs-lookup"><span data-stu-id="f0a9e-102">UInteger data type</span></span>

<span data-ttu-id="f0a9e-103">Przechowuje niepodpisane liczby całkowite 32-bitowe (4-bajtowe) w zakresie wartości z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0a9e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0a9e-104">Remarks</span></span>

<span data-ttu-id="f0a9e-105">Typ danych `UInteger` zapewnia największą wartość bez znaku w najbardziej wydajnej szerokości danych.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="f0a9e-106">Wartość domyślna `UInteger` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="f0a9e-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="f0a9e-107">Literal assignments</span></span>

<span data-ttu-id="f0a9e-108">Można zadeklarować i zainicjować zmienną `UInteger`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="f0a9e-109">Jeśli literał liczby całkowitej znajduje się poza zakresem `UInteger` (czyli jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="f0a9e-110">W poniższym przykładzie liczby całkowite równe 3 000 000 000 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="f0a9e-111">Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f0a9e-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f0a9e-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="f0a9e-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f0a9e-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f0a9e-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="f0a9e-116">Literały numeryczne mogą również zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) `UI` lub `ui`, aby zauważyć `UInteger` typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="f0a9e-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="f0a9e-117">Programming tips</span></span>

<span data-ttu-id="f0a9e-118">Typy danych `UInteger` i `Integer` zapewniają optymalną wydajność procesora 32-bitowego, ponieważ mniejsze typy całkowite (`UShort`, `Short`, `Byte` i `SByte`), nawet jeśli używają mniejszej liczby bitów, Załaduj więcej czasu , przechowuj i pobieraj.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="f0a9e-119">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="f0a9e-119">**Negative Numbers.**</span></span> <span data-ttu-id="f0a9e-120">Ponieważ `UInteger` jest typem bez znaku, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="f0a9e-121">Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `UInteger`, Visual Basic konwertuje wyrażenie na `Long` jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="f0a9e-122">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="f0a9e-122">**CLS Compliance.**</span></span> <span data-ttu-id="f0a9e-123">@No__t_0 typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="f0a9e-124">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="f0a9e-124">**Interop Considerations.**</span></span> <span data-ttu-id="f0a9e-125">Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `uint` mogą mieć różną szerokość danych (16 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="f0a9e-126">Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="f0a9e-127">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="f0a9e-127">**Widening.**</span></span> <span data-ttu-id="f0a9e-128">Typ danych `UInteger` poszerza do `Long`, `ULong`, `Decimal`, `Single` i `Double`.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="f0a9e-129">Oznacza to, że można skonwertować `UInteger` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="f0a9e-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="f0a9e-130">**Type Characters.**</span></span> <span data-ttu-id="f0a9e-131">Dołączanie znaków literału `UI` do literału wymusza `UInteger` do typu danych.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="f0a9e-132">`UInteger` nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="f0a9e-133">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="f0a9e-133">**Framework Type.**</span></span> <span data-ttu-id="f0a9e-134">Odpowiedni typ w .NET Framework jest strukturą <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0a9e-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0a9e-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0a9e-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="f0a9e-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="f0a9e-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f0a9e-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="f0a9e-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f0a9e-138">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f0a9e-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f0a9e-139">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="f0a9e-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="f0a9e-140">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="f0a9e-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
