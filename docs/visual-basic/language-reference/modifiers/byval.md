---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: c4cdafafa6bae3246c0512e28f94fde7e88d230b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373027"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="cee3d-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cee3d-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="cee3d-103">Określa, że argument jest przenoszona [przez wartość](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), dzięki czemu wywołana procedura lub właściwość nie może zmienić wartości zmiennej bazowej argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cee3d-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="cee3d-104">Jeśli modyfikator nie jest określony, ByVal jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="cee3d-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="cee3d-105">Ponieważ jest to ustawienie domyślne, nie trzeba jawnie określać `ByVal` słowa kluczowego w sygnaturach metod.</span><span class="sxs-lookup"><span data-stu-id="cee3d-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="cee3d-106">Ma ona na celu generowanie kodu zakłócenia i często prowadzi do niedomyślnego `ByRef` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cee3d-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="cee3d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cee3d-107">Remarks</span></span>
 <span data-ttu-id="cee3d-108">`ByVal`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="cee3d-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="cee3d-109">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cee3d-109">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="cee3d-110">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cee3d-110">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="cee3d-111">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cee3d-111">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="cee3d-112">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cee3d-112">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="cee3d-113">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cee3d-113">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="cee3d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cee3d-114">Example</span></span>
 <span data-ttu-id="cee3d-115">Poniższy przykład ilustruje użycie `ByVal` mechanizmu przekazywania parametrów z argumentem typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="cee3d-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="cee3d-116">W tym przykładzie argumentem jest `c1` wystąpienie klasy `Class1` .</span><span class="sxs-lookup"><span data-stu-id="cee3d-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="cee3d-117">`ByVal`zapobiega zmienianiu podstawowej wartości argumentu odwołania przez kod w procedurach, `c1` ale nie chroni dostępnych pól i właściwości `c1` .</span><span class="sxs-lookup"><span data-stu-id="cee3d-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="cee3d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cee3d-118">See also</span></span>

- [<span data-ttu-id="cee3d-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cee3d-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="cee3d-120">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="cee3d-120">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
