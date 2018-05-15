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
ms.openlocfilehash: ab268e513e6f019ed651c94deb5e423cfcca7587
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="2da75-102">Operatory łączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2da75-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="2da75-103">Operatory łączenia dołączenie wielu ciągów w jednym ciągu.</span><span class="sxs-lookup"><span data-stu-id="2da75-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="2da75-104">Istnieją dwa operatory łączenia, `+` i `&`.</span><span class="sxs-lookup"><span data-stu-id="2da75-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="2da75-105">Zarówno przeprowadzenia operacji łączenia podstawowe, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2da75-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="2da75-106">Tych operatorów również można łączyć ze sobą `String` zmiennych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2da75-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="2da75-107">Różnice między dwa operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="2da75-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="2da75-108">[Operatora +](../../../../visual-basic/language-reference/operators/addition-operator.md) ma swoje podstawowe przeznaczenie dodanie dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="2da75-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="2da75-109">Jednak można również łączyć liczbowych argumenty ciągu argumentów.</span><span class="sxs-lookup"><span data-stu-id="2da75-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="2da75-110">`+` Operator ma złożonego zestawu reguł, które określają, czy dodać, Połącz, sygnału wystąpi błąd kompilatora lub zgłaszać środowiska wykonawczego <xref:System.InvalidCastException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2da75-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="2da75-111">[& — Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) jest zdefiniowana tylko dla `String` argumentów i zawsze rozszerzenie argumentów do `String`, niezależnie od ustawienia `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="2da75-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="2da75-112">`&` Operator jest zalecane dla ciągów, ponieważ zdefiniowano wyłącznie do ciągów i zmniejsza ryzyko generowania niezamierzone konwersji.</span><span class="sxs-lookup"><span data-stu-id="2da75-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="2da75-113">Wydajność: String i StringBuilder</span><span class="sxs-lookup"><span data-stu-id="2da75-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="2da75-114">Jeśli to zrobisz, duża liczba manipulacje na ciąg znaków, takich jak łączenie, usuwanie i wystąpienia, wydajność może zysków z <xref:System.Text.StringBuilder> klasy w <xref:System.Text> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2da75-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="2da75-115">Trwa dodatkowe instrukcje Utwórz i zainicjuj <xref:System.Text.StringBuilder> obiektu, a inny instrukcji można przekonwertować jego wartości końcowej na `String`, ale tym razem może odzyskać, ponieważ <xref:System.Text.StringBuilder> może działać szybciej.</span><span class="sxs-lookup"><span data-stu-id="2da75-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da75-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2da75-116">See Also</span></span>  
 [<span data-ttu-id="2da75-117">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2da75-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="2da75-118">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2da75-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [<span data-ttu-id="2da75-119">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2da75-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="2da75-120">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2da75-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="2da75-121">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2da75-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
