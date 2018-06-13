---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595316"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="2d831-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d831-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="2d831-103">Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może posiadać wszystkie możliwe wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2d831-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="2d831-104">Konwertowanie z rozszerzającą — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="2d831-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="2d831-105">Należy określić procedury konwersji `Public Shared` oprócz `Widening`.</span><span class="sxs-lookup"><span data-stu-id="2d831-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="2d831-106">Rozszerzanie konwersji zawsze pomyślnie w czasie wykonywania i nigdy nie pociągnąć za sobą utraty danych.</span><span class="sxs-lookup"><span data-stu-id="2d831-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="2d831-107">Przykłady `Single` do `Double`, `Char` do `String`i na jego typ podstawowy typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="2d831-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="2d831-108">Ostatni konwersji jest rozszerzenia, ponieważ typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego i w związku z tym jest wystąpieniem typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="2d831-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="2d831-109">Odbierającą kodu nie trzeba używać `CType` dla rozszerzanie konwersji, nawet jeśli `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="2d831-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="2d831-110">Słowa kluczowego `Widening` można użyć w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="2d831-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="2d831-111">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2d831-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="2d831-112">Na przykład definicje rozszerzanie i zwężanie konwersji operatorów, zobacz [porady: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2d831-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d831-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d831-113">See Also</span></span>  
 [<span data-ttu-id="2d831-114">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2d831-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="2d831-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="2d831-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="2d831-116">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="2d831-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="2d831-117">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="2d831-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="2d831-118">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="2d831-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="2d831-119">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2d831-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="2d831-120">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="2d831-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
