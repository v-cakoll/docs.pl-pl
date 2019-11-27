---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351473"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="62143-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62143-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="62143-103">Wskazuje, że Operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie być w stanie przechowywać niektórych możliwych wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="62143-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="62143-104">Konwertowanie za pomocą słowa kluczowego Narrowing</span><span class="sxs-lookup"><span data-stu-id="62143-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="62143-105">Procedura konwersji musi określać `Public Shared` oprócz `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="62143-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="62143-106">Konwersje wąskie nie zawsze kończą się powodzeniem w czasie wykonywania i mogą kończyć się niepowodzeniem lub spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="62143-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="62143-107">Przykłady `Long` do `Integer`, `String` do `Date`i typ podstawowy dla typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="62143-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="62143-108">Ta ostatnia konwersja jest zawężana, ponieważ typ podstawowy może nie zawierać wszystkich elementów członkowskich typu pochodnego, w związku z czym nie jest wystąpieniem typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="62143-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="62143-109">Jeśli `Option Strict` jest `On`, kod zużywający musi używać `CType` dla wszystkich konwersji zawężających.</span><span class="sxs-lookup"><span data-stu-id="62143-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="62143-110">W tym kontekście można użyć słowa kluczowego `Narrowing`:</span><span class="sxs-lookup"><span data-stu-id="62143-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="62143-111">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="62143-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="62143-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62143-112">See also</span></span>

- [<span data-ttu-id="62143-113">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="62143-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="62143-114">Widening</span><span class="sxs-lookup"><span data-stu-id="62143-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="62143-115">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="62143-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="62143-116">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="62143-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="62143-117">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="62143-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="62143-118">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="62143-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
