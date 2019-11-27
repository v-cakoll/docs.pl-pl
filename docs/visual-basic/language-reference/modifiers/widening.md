---
title: Widening
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
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347832"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="62d78-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62d78-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="62d78-103">Wskazuje, że Operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może zawierać wszystkie możliwe wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="62d78-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="62d78-104">Konwertowanie za pomocą słowa kluczowego rozszerzającego</span><span class="sxs-lookup"><span data-stu-id="62d78-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="62d78-105">Procedura konwersji musi określać `Public Shared` oprócz `Widening`.</span><span class="sxs-lookup"><span data-stu-id="62d78-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="62d78-106">Rozszerzanie konwersji zawsze powiedzie się w czasie wykonywania i nigdy nie powiąże się z utratą danych.</span><span class="sxs-lookup"><span data-stu-id="62d78-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="62d78-107">Przykłady `Single` do `Double`, `Char` do `String`i typ pochodny do jego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="62d78-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="62d78-108">Ta ostatnia konwersja jest rozszerzana, ponieważ typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego i w związku z tym jest wystąpieniem typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="62d78-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="62d78-109">Kod zużywający nie musi używać `CType` do rozszerzania konwersji nawet wtedy, gdy `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="62d78-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="62d78-110">W tym kontekście można użyć słowa kluczowego `Widening`:</span><span class="sxs-lookup"><span data-stu-id="62d78-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="62d78-111">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="62d78-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="62d78-112">Aby zapoznać się z przykładami definicji rozszerzania i zawężania operatorów konwersji, zobacz [How to: define Operator konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="62d78-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d78-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62d78-113">See also</span></span>

- [<span data-ttu-id="62d78-114">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="62d78-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="62d78-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="62d78-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="62d78-116">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="62d78-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="62d78-117">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="62d78-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="62d78-118">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="62d78-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="62d78-119">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="62d78-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="62d78-120">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="62d78-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
