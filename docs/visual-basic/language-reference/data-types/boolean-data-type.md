---
title: Boolean, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347847"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="38692-102">Boolean Data Type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38692-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="38692-103">Przechowuje wartości, które mogą być tylko `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="38692-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="38692-104">Słowa kluczowe `True` i `False` odpowiadają dwóm stanom `Boolean` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="38692-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38692-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38692-105">Remarks</span></span>  

 <span data-ttu-id="38692-106">Użyj [typu danych Boolean (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) , aby zawierać wartości dwustanowe, takie jak true/false, yes/no lub on/off.</span><span class="sxs-lookup"><span data-stu-id="38692-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="38692-107">Wartość domyślna `Boolean` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="38692-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="38692-108">wartości `Boolean` nie są przechowywane jako liczby, a przechowywane wartości nie mają być równoważne z liczbami.</span><span class="sxs-lookup"><span data-stu-id="38692-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="38692-109">Nigdy nie należy pisać kodu, który opiera się na odpowiednich wartościach liczbowych dla `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="38692-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="38692-110">Jeśli to możliwe, należy ograniczyć użycie zmiennych `Boolean` do wartości logicznych, dla których zostały zaprojektowane.</span><span class="sxs-lookup"><span data-stu-id="38692-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="38692-111">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="38692-111">Type Conversions</span></span>  

 <span data-ttu-id="38692-112">Gdy Visual Basic konwertuje wartości liczbowe typu danych na `Boolean`, 0 staje się `False` i wszystkie pozostałe wartości stają się `True`.</span><span class="sxs-lookup"><span data-stu-id="38692-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="38692-113">Gdy Visual Basic konwertuje wartości `Boolean` na typy liczbowe, `False` staje się 0, a `True` staje się-1.</span><span class="sxs-lookup"><span data-stu-id="38692-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="38692-114">Podczas konwertowania wartości `Boolean` i liczbowych typów danych, należy pamiętać, że metody konwersji .NET Framework nie zawsze generują te same wyniki, co w przypadku słów kluczowych konwersji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38692-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="38692-115">Dzieje się tak, ponieważ konwersja Visual Basic zachowuje zachowanie zgodne z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="38692-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="38692-116">Aby uzyskać więcej informacji, zobacz "typ Boolean nie jest dokładnie konwertowany na typ liczbowy" w temacie [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="38692-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="38692-117">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="38692-117">Programming Tips</span></span>  
  
- <span data-ttu-id="38692-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="38692-118">**Negative Numbers.**</span></span> <span data-ttu-id="38692-119">`Boolean` nie jest typem liczbowym i nie może reprezentować wartości ujemnej.</span><span class="sxs-lookup"><span data-stu-id="38692-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="38692-120">W każdym przypadku nie należy używać `Boolean` do przechowywania wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="38692-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="38692-121">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="38692-121">**Type Characters.**</span></span> <span data-ttu-id="38692-122">`Boolean` nie ma znaku typu literału lub typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="38692-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="38692-123">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="38692-123">**Framework Type.**</span></span> <span data-ttu-id="38692-124">Odpowiedni typ w .NET Framework jest strukturą <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38692-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38692-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="38692-125">Example</span></span>  

 <span data-ttu-id="38692-126">W poniższym przykładzie `runningVB` jest zmienną `Boolean`, która przechowuje proste ustawienie tak/nie.</span><span class="sxs-lookup"><span data-stu-id="38692-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="38692-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38692-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="38692-128">Typy danych</span><span class="sxs-lookup"><span data-stu-id="38692-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="38692-129">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="38692-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="38692-130">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="38692-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="38692-131">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="38692-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="38692-132">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="38692-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="38692-133">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="38692-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
