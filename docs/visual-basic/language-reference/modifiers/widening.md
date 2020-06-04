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
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359906"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="69162-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69162-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="69162-103">Wskazuje, że Operator konwersji ( `CType` ) konwertuje klasę lub strukturę do typu, który może zawierać wszystkie możliwe wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="69162-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="69162-104">Konwertowanie za pomocą słowa kluczowego rozszerzającego</span><span class="sxs-lookup"><span data-stu-id="69162-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="69162-105">Procedura konwersji musi być określona `Public Shared` poza `Widening` .</span><span class="sxs-lookup"><span data-stu-id="69162-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="69162-106">Rozszerzanie konwersji zawsze powiedzie się w czasie wykonywania i nigdy nie powiąże się z utratą danych.</span><span class="sxs-lookup"><span data-stu-id="69162-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="69162-107">Przykłady to `Single` `Double` , `Char` do `String` i typ pochodny do jego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="69162-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="69162-108">Ta ostatnia konwersja jest rozszerzana, ponieważ typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego i w związku z tym jest wystąpieniem typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="69162-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="69162-109">Kod zużywający nie musi być używany `CType` do rozszerzania konwersji, nawet jeśli `Option Strict` jest `On` .</span><span class="sxs-lookup"><span data-stu-id="69162-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="69162-110">`Widening`Słowo kluczowe może być używane w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="69162-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="69162-111">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="69162-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="69162-112">Aby zapoznać się z przykładami definicji rozszerzania i zawężania operatorów konwersji, zobacz [How to: define Operator konwersji](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="69162-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69162-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69162-113">See also</span></span>

- [<span data-ttu-id="69162-114">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="69162-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="69162-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="69162-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="69162-116">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="69162-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="69162-117">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="69162-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="69162-118">CType — Funkcja</span><span class="sxs-lookup"><span data-stu-id="69162-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="69162-119">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="69162-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="69162-120">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="69162-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
