---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: abfe1489cb7e0d06b03c308e0704ce6f69ee55da
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433804"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="066d5-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="066d5-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="066d5-103">Określa, że argument jest przenoszona [przez wartość](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), dzięki czemu wywołana procedura lub właściwość nie może zmienić wartości zmiennej bazowej argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="066d5-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="066d5-104">Jeśli modyfikator nie jest określony, ByVal jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="066d5-104">If no modifier is specified, ByVal is the default.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="066d5-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="066d5-105">Remarks</span></span>  
 <span data-ttu-id="066d5-106">`ByVal` Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="066d5-106">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="066d5-107">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="066d5-107">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="066d5-108">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="066d5-108">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="066d5-109">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="066d5-109">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="066d5-110">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="066d5-110">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="066d5-111">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="066d5-111">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="066d5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="066d5-112">Example</span></span>  
 <span data-ttu-id="066d5-113">Poniższy przykład ilustruje użycie `ByVal` mechanizmu przekazywania parametrów z argumentem typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="066d5-113">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="066d5-114">W tym przykładzie argumentem jest `c1`wystąpienie klasy. `Class1`</span><span class="sxs-lookup"><span data-stu-id="066d5-114">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="066d5-115">`ByVal`zapobiega zmienianiu podstawowej wartości argumentu `c1`odwołania przez kod w procedurach, ale nie chroni dostępnych pól i `c1`właściwości.</span><span class="sxs-lookup"><span data-stu-id="066d5-115">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="066d5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="066d5-116">See also</span></span>

- [<span data-ttu-id="066d5-117">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="066d5-117">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="066d5-118">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="066d5-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
