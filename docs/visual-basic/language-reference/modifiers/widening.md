---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a><span data-ttu-id="fcfd6-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcfd6-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="fcfd6-103">Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może posiadać wszystkie możliwe wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fcfd6-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="fcfd6-104">Konwertowanie z rozszerzającą — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="fcfd6-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="fcfd6-105">Należy określić procedury konwersji `Public Shared` oprócz `Widening`.</span><span class="sxs-lookup"><span data-stu-id="fcfd6-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="fcfd6-106">Rozszerzanie konwersji zawsze pomyślnie w czasie wykonywania i nigdy nie pociągnąć za sobą utraty danych.</span><span class="sxs-lookup"><span data-stu-id="fcfd6-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="fcfd6-107">Przykłady `Single` do `Double`, `Char` do `String`i na jego typ podstawowy typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="fcfd6-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="fcfd6-108">Ostatni konwersji jest rozszerzenia, ponieważ typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego i w związku z tym jest wystąpieniem typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="fcfd6-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="fcfd6-109">Odbierającą kodu nie trzeba używać `CType` dla rozszerzanie konwersji, nawet jeśli `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="fcfd6-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="fcfd6-110">`Widening` Można użyć słowa kluczowego, w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="fcfd6-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="fcfd6-111">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fcfd6-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="fcfd6-112">Na przykład definicje rozszerzanie i zwężanie konwersji operatorów, zobacz [porady: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="fcfd6-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfd6-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcfd6-113">See Also</span></span>  
 [<span data-ttu-id="fcfd6-114">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fcfd6-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="fcfd6-115">Zawężanie</span><span class="sxs-lookup"><span data-stu-id="fcfd6-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="fcfd6-116">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="fcfd6-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="fcfd6-117">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="fcfd6-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="fcfd6-118">CType — funkcja</span><span class="sxs-lookup"><span data-stu-id="fcfd6-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="fcfd6-119">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fcfd6-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="fcfd6-120">Porady: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="fcfd6-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
