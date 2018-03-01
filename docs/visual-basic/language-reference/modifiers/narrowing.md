---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="56b49-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56b49-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="56b49-103">Oznacza to, że operator konwersji (`CType`) konwertuje klasę lub strukturę do typu, który może nie posiadać pewnych możliwych wartości oryginalnej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="56b49-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="56b49-104">Konwertowanie z zawężającej — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="56b49-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="56b49-105">Należy określić procedury konwersji `Public Shared` oprócz `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="56b49-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="56b49-106">Zawężanie konwersji nie zawsze pomyślnie w czasie wykonywania i może się nie powieść lub pociągnąć za sobą utraty danych.</span><span class="sxs-lookup"><span data-stu-id="56b49-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="56b49-107">Przykłady `Long` do `Integer`, `String` do `Date`oraz typem bazowym typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="56b49-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="56b49-108">Ta konwersja ostatniego jest zawężenie, ponieważ typ podstawowy nie może zawierać wszystkie elementy członkowskie typu pochodnego i w związku z tym nie jest wystąpieniem typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="56b49-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="56b49-109">Jeśli `Option Strict` jest `On`, wykorzystywanie kodu musi używać `CType` dla wszystkich konwersji zawężającej.</span><span class="sxs-lookup"><span data-stu-id="56b49-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="56b49-110">`Narrowing` Można użyć słowa kluczowego, w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="56b49-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="56b49-111">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="56b49-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="56b49-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56b49-112">See Also</span></span>  
 [<span data-ttu-id="56b49-113">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="56b49-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="56b49-114">Rozszerzanie</span><span class="sxs-lookup"><span data-stu-id="56b49-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="56b49-115">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="56b49-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="56b49-116">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="56b49-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="56b49-117">CType — funkcja</span><span class="sxs-lookup"><span data-stu-id="56b49-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="56b49-118">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="56b49-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
