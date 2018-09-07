---
title: Uinteger — typ danych (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df89c099042de8acef687a5fd11fc0dbf7de86a7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083500"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="1b359-102">UInteger — Typ danych</span><span class="sxs-lookup"><span data-stu-id="1b359-102">UInteger data type</span></span>

<span data-ttu-id="1b359-103">Przechowuje 32-bitowe (4-bajtową) liczb całkowitych bez znaku z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="1b359-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b359-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b359-104">Remarks</span></span>

 <span data-ttu-id="1b359-105">`UInteger` — Typ danych zapewnia największą wartość bez znaku w najbardziej efektywny sposób szerokość danych.</span><span class="sxs-lookup"><span data-stu-id="1b359-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="1b359-106">Wartość domyślna `UInteger` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="1b359-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="1b359-107">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="1b359-107">Literal assignments</span></span>

<span data-ttu-id="1b359-108">Można zadeklarować i zainicjować `UInteger` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="1b359-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="1b359-109">Jeśli literał liczby całkowitej jest poza zakresem `UInteger` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1b359-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="1b359-110">W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `UInteger` wartości.</span><span class="sxs-lookup"><span data-stu-id="1b359-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="1b359-111">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="1b359-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="1b359-112">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="1b359-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1b359-113">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="1b359-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="1b359-114">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="1b359-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="1b359-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1b359-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="1b359-116">Literały numeryczne mogą również obejmować `UI` lub `ui` [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `UInteger` typu danych, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="1b359-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="1b359-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="1b359-117">Programming tips</span></span>

 <span data-ttu-id="1b359-118">`UInteger` i `Integer` typy danych zapewnić optymalną wydajność na 32-bitowym procesorze, ponieważ mniejszych typów całkowitych (`UShort`, `Short`, `Byte`, i `SByte`), nawet jeśli korzystają z mniejszą liczbą bitów, zajmują więcej czasu Ładowanie, przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="1b359-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="1b359-119">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="1b359-119">**Negative Numbers.**</span></span> <span data-ttu-id="1b359-120">Ponieważ `UInteger` jest typ bez znaku, go nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="1b359-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="1b359-121">Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `UInteger`, Visual Basic konwertuje wyrażenie które ma `Long` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="1b359-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="1b359-122">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="1b359-122">**CLS Compliance.**</span></span> <span data-ttu-id="1b359-123">`UInteger` Typem danych nie jest częścią [specyfikacja Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="1b359-123">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="1b359-124">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="1b359-124">**Interop Considerations.**</span></span> <span data-ttu-id="1b359-125">Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, takich jak wpisywany `uint` mogą mieć różną szerokość danych (16 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="1b359-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="1b359-126">Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b359-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="1b359-127">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="1b359-127">**Widening.**</span></span> <span data-ttu-id="1b359-128">`UInteger` — Typ danych rozszerza się na `Long`, `ULong`, `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="1b359-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="1b359-129">Oznacza to, że możesz przekonwertować `UInteger` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="1b359-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="1b359-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="1b359-130">**Type Characters.**</span></span> <span data-ttu-id="1b359-131">Dołącza znaki literalne `UI` do literału wymusza `UInteger` typu danych.</span><span class="sxs-lookup"><span data-stu-id="1b359-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="1b359-132">`UInteger` nie ma identyfikatora typ znaku.</span><span class="sxs-lookup"><span data-stu-id="1b359-132">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="1b359-133">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="1b359-133">**Framework Type.**</span></span> <span data-ttu-id="1b359-134">Odpowiedni typ w .NET Framework jest <xref:System.UInt32?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="1b359-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b359-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b359-135">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="1b359-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1b359-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="1b359-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="1b359-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="1b359-138">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="1b359-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="1b359-139">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="1b359-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="1b359-140">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="1b359-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
