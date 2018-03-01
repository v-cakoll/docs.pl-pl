---
title: "Typ &#39; &lt;nazwa_zmiennej&gt;&#39; nie można go wywnioskować, ponieważ granice pętli i zmienna krok nie poszerzyć na ten sam typ."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="95c0d-102">Typ &#39; &lt;nazwa_zmiennej&gt;&#39; nie można go wywnioskować, ponieważ granice pętli i zmienna krok nie poszerzyć na ten sam typ.</span><span class="sxs-lookup"><span data-stu-id="95c0d-102">Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="95c0d-103">Napisano `For...Next` pętli, w którym kompilator nie można wywnioskować typu danych dla zmienna sterująca pętli, ponieważ są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="95c0d-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
-   <span data-ttu-id="95c0d-104">Typ danych zmienna sterująca pętli nie zostanie określony z `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="95c0d-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
-   <span data-ttu-id="95c0d-105">Granice pętli i zmienna krok zawiera co najmniej dwóch typów.</span><span class="sxs-lookup"><span data-stu-id="95c0d-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
-   <span data-ttu-id="95c0d-106">Istnieje ma standardowych konwersji typów danych.</span><span class="sxs-lookup"><span data-stu-id="95c0d-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="95c0d-107">W związku z tym kompilator nie można wywnioskować typu danych zmienna sterująca pętli for.</span><span class="sxs-lookup"><span data-stu-id="95c0d-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="95c0d-108">W poniższym przykładzie zmienna kroku jest znak i granice pętli są obie liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="95c0d-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="95c0d-109">Ten błąd jest zgłaszany, ponieważ nie istnieje konwersja standardowa między znakami i liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="95c0d-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="95c0d-110">**Identyfikator błędu:** BC30982</span><span class="sxs-lookup"><span data-stu-id="95c0d-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="95c0d-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="95c0d-111">To correct this error</span></span>  
  
-   <span data-ttu-id="95c0d-112">Zmień typy granice pętli i zmienna krok w razie potrzeby, tak, aby co najmniej jeden z nich jest typ innych rozszerzane.</span><span class="sxs-lookup"><span data-stu-id="95c0d-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="95c0d-113">W poprzednim przykładzie, należy zmienić typ `stepVar` do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="95c0d-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="95c0d-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="95c0d-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   <span data-ttu-id="95c0d-115">Użyj konwersji jawnej, aby przekonwertować granice pętli i zmienna krok do odpowiednich typów.</span><span class="sxs-lookup"><span data-stu-id="95c0d-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="95c0d-116">W powyższym przykładzie `Val` funkcja `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="95c0d-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="95c0d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95c0d-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="95c0d-118">Dla... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="95c0d-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="95c0d-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="95c0d-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="95c0d-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="95c0d-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="95c0d-121">Option Infer — instrukcja</span><span class="sxs-lookup"><span data-stu-id="95c0d-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="95c0d-122">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="95c0d-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="95c0d-123">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="95c0d-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
