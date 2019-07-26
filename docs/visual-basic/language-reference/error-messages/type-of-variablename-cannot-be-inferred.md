---
title: Nie można wywnioskować typu elementu „<variablename>”, ponieważ granice pętli i zmienna step nie mogą zostać poszerzone do tego samego typu
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512708"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="7cf1a-102">Nie można wywnioskować typu "\<VariableName >", ponieważ granice pętli i zmienna kroku nie są rozszerzane do tego samego typu</span><span class="sxs-lookup"><span data-stu-id="7cf1a-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="7cf1a-103">Zapisano `For...Next` pętlę, w której kompilator nie może wywnioskować typu danych dla zmiennej kontroli pętli, ponieważ spełnione są następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="7cf1a-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="7cf1a-104">Typ danych zmiennej sterującej pętli nie jest określony z `As` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="7cf1a-105">Granice pętli i zmienna kroku zawierają co najmniej dwa typy danych.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="7cf1a-106">Między typami danych nie istnieje żadna konwersja standardowa.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="7cf1a-107">W związku z tym kompilator nie może wywnioskować typu danych zmiennej sterującej pętli.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="7cf1a-108">W poniższym przykładzie zmienna kroku jest znakiem, a granice pętli są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="7cf1a-109">Ponieważ nie istnieje standardowa konwersja między znakami i liczbami całkowitymi, ten błąd jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="7cf1a-110">**Identyfikator błędu:** BC30982</span><span class="sxs-lookup"><span data-stu-id="7cf1a-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7cf1a-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="7cf1a-111">To correct this error</span></span>

- <span data-ttu-id="7cf1a-112">W razie potrzeby zmień typy granic pętli i zmiennej krokowej, tak aby co najmniej jedna z nich została poszerzona.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="7cf1a-113">W poprzednim przykładzie Zmień typ `stepVar` na. `Integer`</span><span class="sxs-lookup"><span data-stu-id="7cf1a-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="7cf1a-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="7cf1a-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="7cf1a-115">Użyj funkcji jawnej konwersji, aby przekonwertować granice pętli i zmienną krokową na odpowiednie typy.</span><span class="sxs-lookup"><span data-stu-id="7cf1a-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="7cf1a-116">W poprzednim przykładzie Zastosuj `Val` funkcję do. `stepVar`</span><span class="sxs-lookup"><span data-stu-id="7cf1a-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="7cf1a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cf1a-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="7cf1a-118">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7cf1a-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="7cf1a-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="7cf1a-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="7cf1a-120">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="7cf1a-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7cf1a-121">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7cf1a-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="7cf1a-122">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7cf1a-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="7cf1a-123">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="7cf1a-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
