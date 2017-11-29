---
title: Boolean Data Type (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="8d232-102">Boolean Data Type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d232-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="8d232-103">Wartości blokad, które mogą być tylko `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="8d232-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="8d232-104">Słowa kluczowe `True` i `False` odpowiadają dwa stany `Boolean` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="8d232-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d232-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d232-105">Remarks</span></span>  
 <span data-ttu-id="8d232-106">Użyj [typu Boolean danych (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) zawierają wartości dwustanowy, takie jak PRAWDA/FAŁSZ tak/nie lub Wł. / wył.</span><span class="sxs-lookup"><span data-stu-id="8d232-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="8d232-107">Wartość domyślna `Boolean` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="8d232-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="8d232-108">`Boolean`wartości nie są przechowywane jako liczby, a nie mają równoważne numery przechowywane wartości.</span><span class="sxs-lookup"><span data-stu-id="8d232-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="8d232-109">Nigdy nie powinien pisania kodu, który polega na równoważne wartości numerycznych `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="8d232-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="8d232-110">Jeśli to możliwe, należy ograniczyć użycie `Boolean` zmienne do wartości logiczne, dla których są przeznaczone.</span><span class="sxs-lookup"><span data-stu-id="8d232-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="8d232-111">Konwersje typu</span><span class="sxs-lookup"><span data-stu-id="8d232-111">Type Conversions</span></span>  
 <span data-ttu-id="8d232-112">Gdy Visual Basic konwertuje wartości typu danych liczbowych `Boolean`, staje się 0 `False` i stać się wszystkie inne wartości `True`.</span><span class="sxs-lookup"><span data-stu-id="8d232-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="8d232-113">Gdy konwertuje Visual Basic `Boolean` wartości na typy liczbowe `False` staje się 0 i `True` staje się wartość -1.</span><span class="sxs-lookup"><span data-stu-id="8d232-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="8d232-114">Podczas konwertowania między `Boolean` wartości i numeryczne typy danych, należy pamiętać, że metody konwersji .NET Framework nie zawsze utworzyć takie same wyniki jak słowa kluczowe konwersji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8d232-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="8d232-115">Jest to spowodowane konwersji Visual Basic zachowuje zachowania zgodność z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="8d232-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="8d232-116">Aby uzyskać więcej informacji, zobacz "Boolean typu jest nie Konwertuj do liczbowego typu dokładnie" w [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="8d232-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="8d232-117">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="8d232-117">Programming Tips</span></span>  
  
-   <span data-ttu-id="8d232-118">**Wartości ujemne.**</span><span class="sxs-lookup"><span data-stu-id="8d232-118">**Negative Numbers.**</span></span> <span data-ttu-id="8d232-119">`Boolean`nie jest typu liczbowego i nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="8d232-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="8d232-120">W żadnym przypadku nie należy używać `Boolean` do przechowywania wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="8d232-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="8d232-121">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="8d232-121">**Type Characters.**</span></span> <span data-ttu-id="8d232-122">`Boolean`nie ma znak literalny typu ani znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="8d232-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="8d232-123">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="8d232-123">**Framework Type.**</span></span> <span data-ttu-id="8d232-124">Danego typu w programie .NET Framework jest <xref:System.Boolean?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="8d232-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d232-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d232-125">Example</span></span>  
 <span data-ttu-id="8d232-126">W poniższym przykładzie `runningVB` jest `Boolean` zmiennej, która przechowuje prostą ustawienie tak/nie.</span><span class="sxs-lookup"><span data-stu-id="8d232-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d232-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d232-127">See Also</span></span>  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [<span data-ttu-id="8d232-128">Typy danych</span><span class="sxs-lookup"><span data-stu-id="8d232-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="8d232-129">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="8d232-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="8d232-130">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8d232-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="8d232-131">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="8d232-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="8d232-132">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="8d232-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="8d232-133">CType — funkcja</span><span class="sxs-lookup"><span data-stu-id="8d232-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
