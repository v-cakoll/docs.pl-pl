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
ms.openlocfilehash: 5e534eac2300327d4c54c5ce93d8b2c6c538e794
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832501"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="884c0-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="884c0-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="884c0-103">Określa, że argument jest przekazywany w taki sposób, że wywoływana procedura lub właściwość nie można zmienić wartość zmiennej bazowego argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="884c0-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="884c0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="884c0-104">Remarks</span></span>  
 <span data-ttu-id="884c0-105">`ByVal` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="884c0-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="884c0-106">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="884c0-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="884c0-107">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="884c0-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="884c0-108">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="884c0-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="884c0-109">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="884c0-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="884c0-110">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="884c0-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="884c0-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="884c0-111">Example</span></span>  
 <span data-ttu-id="884c0-112">W poniższym przykładzie pokazano użycie `ByVal` parametru, przekazując mechanizm, za pomocą argumentu typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="884c0-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="884c0-113">W tym przykładzie argument jest `c1`, wystąpienie klasy `Class1`.</span><span class="sxs-lookup"><span data-stu-id="884c0-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="884c0-114">`ByVal` uniemożliwia zmienianie podstawowej wartości argument odwołania przez kod w procedurach `c1`, ale nie chroni dostępnych pól i właściwości działania `c1`.</span><span class="sxs-lookup"><span data-stu-id="884c0-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="884c0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="884c0-115">See also</span></span>

- [<span data-ttu-id="884c0-116">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="884c0-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="884c0-117">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="884c0-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
