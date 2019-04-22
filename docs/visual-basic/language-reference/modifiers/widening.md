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
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825316"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="5563c-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5563c-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="5563c-103">Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może pomieścić wszystkie możliwe wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5563c-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="5563c-104">Konwertowanie za pomocą rozszerzającą — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="5563c-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="5563c-105">Należy określić procedury konwersji `Public Shared` oprócz `Widening`.</span><span class="sxs-lookup"><span data-stu-id="5563c-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="5563c-106">Konwersje rozszerzające zawsze kończą się pomyślnie w czasie wykonywania i nigdy nie pociągnąć za sobą utratę danych.</span><span class="sxs-lookup"><span data-stu-id="5563c-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="5563c-107">Należą do nich `Single` do `Double`, `Char` do `String`, a jego typ podstawowy typ pochodny.</span><span class="sxs-lookup"><span data-stu-id="5563c-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="5563c-108">Ta ostatnia konwersja jest rozszerzanie, ponieważ typ pochodny zawiera wszystkie elementy członkowskie w typie podstawowym, a więc jest wystąpieniem typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5563c-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="5563c-109">Kod konsumencki nie trzeba używać `CType` do poszerzenia konwersje, nawet jeśli `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="5563c-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="5563c-110">Słowa kluczowego `Widening` można użyć w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="5563c-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="5563c-111">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5563c-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="5563c-112">Na przykład definicje rozszerzanie i zwężanie konwersji, operatorów, zobacz [jak: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5563c-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5563c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5563c-113">See also</span></span>

- [<span data-ttu-id="5563c-114">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5563c-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="5563c-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="5563c-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="5563c-116">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="5563c-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5563c-117">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="5563c-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="5563c-118">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="5563c-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="5563c-119">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5563c-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="5563c-120">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="5563c-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
