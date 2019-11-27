---
title: '&amp;, operator'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336054"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="f57f9-102">Operator &amp; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57f9-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="f57f9-103">Generuje łączenie ciągów dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f57f9-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f57f9-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f57f9-105">Części</span><span class="sxs-lookup"><span data-stu-id="f57f9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f57f9-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f57f9-106">Required.</span></span> <span data-ttu-id="f57f9-107">Dowolna `String` lub `Object` zmienna.</span><span class="sxs-lookup"><span data-stu-id="f57f9-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f57f9-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f57f9-108">Required.</span></span> <span data-ttu-id="f57f9-109">Każde wyrażenie z typem danych, które poszerza do `String`.</span><span class="sxs-lookup"><span data-stu-id="f57f9-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f57f9-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f57f9-110">Required.</span></span> <span data-ttu-id="f57f9-111">Każde wyrażenie z typem danych, które poszerza do `String`.</span><span class="sxs-lookup"><span data-stu-id="f57f9-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f57f9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f57f9-112">Remarks</span></span>  
 <span data-ttu-id="f57f9-113">Jeśli typ danych `expression1` lub `expression2` nie jest `String`, ale rozszerza do `String`, zostanie przekonwertowany na `String`.</span><span class="sxs-lookup"><span data-stu-id="f57f9-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="f57f9-114">Jeśli jeden z typów danych nie zostanie rozszerzony do `String`, kompilator generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="f57f9-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="f57f9-115">Typ danych `result` jest `String`.</span><span class="sxs-lookup"><span data-stu-id="f57f9-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="f57f9-116">Jeśli co najmniej jedno wyrażenie zwróci wartość [Nothing lub nie](../../../visual-basic/language-reference/nothing.md) ma wartości <xref:System.DBNull.Value?displayProperty=nameWithType>, są traktowane jako ciąg o wartości "".</span><span class="sxs-lookup"><span data-stu-id="f57f9-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f57f9-117">Operator `&` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f57f9-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f57f9-118">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f57f9-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f57f9-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f57f9-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f57f9-120">Znak handlowego "i" (&) może również służyć do identyfikowania zmiennych jako typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="f57f9-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="f57f9-121">Aby uzyskać więcej informacji, zobacz [Type characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="f57f9-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f57f9-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f57f9-122">Example</span></span>  
 <span data-ttu-id="f57f9-123">W tym przykładzie używa operatora `&`, aby wymusić łączenie ciągów.</span><span class="sxs-lookup"><span data-stu-id="f57f9-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="f57f9-124">Wynikiem jest wartość ciągu reprezentująca połączenie dwóch operandów ciągu.</span><span class="sxs-lookup"><span data-stu-id="f57f9-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f57f9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f57f9-125">See also</span></span>

- [<span data-ttu-id="f57f9-126">&=, operator</span><span class="sxs-lookup"><span data-stu-id="f57f9-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="f57f9-127">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="f57f9-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="f57f9-128">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f57f9-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f57f9-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="f57f9-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f57f9-130">Operatory łączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f57f9-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
