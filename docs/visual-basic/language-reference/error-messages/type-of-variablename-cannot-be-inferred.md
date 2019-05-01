---
title: Nie można wywnioskować typu elementu „<variablename>”, ponieważ granice pętli i zmienna step nie mogą zostać poszerzone do tego samego typu
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: e90e881546c12df2c8b19ff03a4d4c7304c4596c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052680"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="9da43-102">Typ "\<nazwa_zmiennej >" nie można wywnioskować, ponieważ granice pętli i zmienna Step nie mogą zostać poszerzone do tego samego typu</span><span class="sxs-lookup"><span data-stu-id="9da43-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="9da43-103">Zostały napisane `For...Next` pętli, w którym kompilator nie można wywnioskować typu danych dla zmienna sterująca pętli, ponieważ są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9da43-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
- <span data-ttu-id="9da43-104">Typ danych zmienna sterująca pętli nie zostanie określony z `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9da43-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
- <span data-ttu-id="9da43-105">Granice pętli i zmienna zawiera co najmniej dwa typy danych.</span><span class="sxs-lookup"><span data-stu-id="9da43-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
- <span data-ttu-id="9da43-106">Nie standardowa występują konwersje między typami danych.</span><span class="sxs-lookup"><span data-stu-id="9da43-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="9da43-107">W związku z tym kompilator nie można wywnioskować typu danych zmienna sterująca pętli.</span><span class="sxs-lookup"><span data-stu-id="9da43-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="9da43-108">W poniższym przykładzie zmienna jest znakiem i granice pętli są oba liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="9da43-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="9da43-109">Ponieważ istnieje standardowa konwersja między znakami i liczb całkowitych, ten błąd jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="9da43-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="9da43-110">**Identyfikator błędu:** BC30982</span><span class="sxs-lookup"><span data-stu-id="9da43-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9da43-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9da43-111">To correct this error</span></span>  
  
- <span data-ttu-id="9da43-112">Zmień typy granice pętli i zmienna zgodnie z potrzebami, tak, aby co najmniej jeden z nich to typ, który inne mogą zostać poszerzone do.</span><span class="sxs-lookup"><span data-stu-id="9da43-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="9da43-113">W poprzednim przykładzie, należy zmienić typ `stepVar` do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9da43-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="9da43-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="9da43-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
- <span data-ttu-id="9da43-115">Użyj funkcji konwersji jawnej konwertować granice pętli i zmienna na odpowiednie typy.</span><span class="sxs-lookup"><span data-stu-id="9da43-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="9da43-116">W poprzednim przykładzie, należy zastosować `Val` funkcja `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="9da43-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9da43-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9da43-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="9da43-118">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9da43-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="9da43-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="9da43-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="9da43-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="9da43-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9da43-121">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9da43-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="9da43-122">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="9da43-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9da43-123">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="9da43-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
