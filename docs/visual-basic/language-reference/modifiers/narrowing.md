---
title: Narrowing (Visual Basic)
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
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838853"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="18752-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18752-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="18752-103">Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie posiadać pewnych możliwych wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="18752-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="18752-104">Konwertowanie za pomocą słowa kluczowego zawężającej</span><span class="sxs-lookup"><span data-stu-id="18752-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="18752-105">Należy określić procedury konwersji `Public Shared` oprócz `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="18752-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="18752-106">Konwersje zawężające nie zawsze sukces w czasie wykonywania i może zakończyć się niepowodzeniem lub pociągnąć za sobą utratę danych.</span><span class="sxs-lookup"><span data-stu-id="18752-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="18752-107">Należą do nich `Long` do `Integer`, `String` do `Date`, a typ podstawowy typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="18752-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="18752-108">Ta ostatnia konwersja jest zawężenie, ponieważ typ podstawowy nie może zawierać wszystkie elementy członkowskie w typie pochodnym i dlatego nie jest wystąpieniem typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="18752-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="18752-109">Jeśli `Option Strict` jest `On`, wykorzystywanie kodu należy użyć `CType` dla wszystkich konwersji zawężających.</span><span class="sxs-lookup"><span data-stu-id="18752-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="18752-110">Słowa kluczowego `Narrowing` można użyć w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="18752-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="18752-111">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="18752-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="18752-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18752-112">See also</span></span>

- [<span data-ttu-id="18752-113">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="18752-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="18752-114">Widening</span><span class="sxs-lookup"><span data-stu-id="18752-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="18752-115">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="18752-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="18752-116">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="18752-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="18752-117">Funkcja CType</span><span class="sxs-lookup"><span data-stu-id="18752-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="18752-118">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="18752-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
