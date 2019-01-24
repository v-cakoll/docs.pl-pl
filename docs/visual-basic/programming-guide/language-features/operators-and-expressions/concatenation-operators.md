---
title: Operatory łączenia w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 90072a3cadccd0c66b66f0ec5ff2dafd3d62eaeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490861"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="5ec8d-102">Operatory łączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec8d-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="5ec8d-103">Concatenation — operatory Dołącz do wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="5ec8d-104">Istnieją dwa operatory łączenia, `+` i `&`.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="5ec8d-105">Zarówno przeprowadzenie operacji łączenia podstawowe, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="5ec8d-106">Te operatory również można łączyć ze sobą `String` zmiennych, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="5ec8d-107">Różnice między dwa operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="5ec8d-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="5ec8d-108">[+ — Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) ma głównym celem dodanie dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="5ec8d-109">Jednak można również połączyć operandy liczbową argumentów ciągu.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="5ec8d-110">`+` Operator ma złożonego zestawu reguł, które określają, czy dodawanie, łączenie, zasygnalizować błąd kompilatora lub zgłosić środowiska wykonawczego <xref:System.InvalidCastException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="5ec8d-111">[& — Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) jest zdefiniowane tylko dla `String` argumentów i zawsze rozszerza się jego operandy `String`, niezależnie od ustawienia `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="5ec8d-112">`&` Operator jest zalecane dla ciągów, ponieważ zdefiniowano wyłącznie dla ciągów i zmniejsza ryzyko generowania konwersję niezamierzone.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="5ec8d-113">Wydajność: Parametry i StringBuilder</span><span class="sxs-lookup"><span data-stu-id="5ec8d-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="5ec8d-114">Jeśli to zrobisz, znaczna liczba manipulacje na ciąg, takie jak konkatenacji, usuwania i zamiany, wydajność może być zysk z <xref:System.Text.StringBuilder> klasy w <xref:System.Text> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="5ec8d-115">Zajmuje dodatkowy instrukcji, aby utworzyć i zainicjować <xref:System.Text.StringBuilder> obiekt i innej instrukcji jego końcowa wartość, aby przekonwertować `String`, ale może odzyskać to czas, ponieważ <xref:System.Text.StringBuilder> może działać szybciej.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec8d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ec8d-116">See also</span></span>
- [<span data-ttu-id="5ec8d-117">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5ec8d-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="5ec8d-118">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec8d-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="5ec8d-119">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec8d-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="5ec8d-120">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec8d-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="5ec8d-121">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec8d-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
