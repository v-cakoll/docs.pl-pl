---
title: '&amp; — Operator (Visual Basic)'
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
ms.openlocfilehash: dd85363447e9b405241d608550d9484b4760a739
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817282"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="c3a34-102">&amp; — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3a34-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="c3a34-103">Tworzy połączenie ciągów dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="c3a34-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a34-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3a34-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c3a34-105">Części</span><span class="sxs-lookup"><span data-stu-id="c3a34-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="c3a34-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c3a34-106">Required.</span></span> <span data-ttu-id="c3a34-107">Wszelkie `String` lub `Object` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c3a34-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="c3a34-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c3a34-108">Required.</span></span> <span data-ttu-id="c3a34-109">Dowolne wyrażenie z typem danych, która rozszerza się na `String`.</span><span class="sxs-lookup"><span data-stu-id="c3a34-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="c3a34-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c3a34-110">Required.</span></span> <span data-ttu-id="c3a34-111">Dowolne wyrażenie z typem danych, która rozszerza się na `String`.</span><span class="sxs-lookup"><span data-stu-id="c3a34-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a34-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3a34-112">Remarks</span></span>  
 <span data-ttu-id="c3a34-113">Jeśli typ danych `expression1` lub `expression2` nie `String` , ale rozszerza się na `String`, jest konwertowany na `String`.</span><span class="sxs-lookup"><span data-stu-id="c3a34-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="c3a34-114">Jeśli jeden z typów danych nie mogą zostać poszerzone do `String`, kompilator generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="c3a34-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="c3a34-115">Typ danych `result` jest `String`.</span><span class="sxs-lookup"><span data-stu-id="c3a34-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="c3a34-116">Jeśli jeden lub oba wyrażenia mają [nic](../../../visual-basic/language-reference/nothing.md) lub mieć wartość <xref:System.DBNull.Value?displayProperty=nameWithType>, będą one traktowane jako ciąg znaków o wartości "".</span><span class="sxs-lookup"><span data-stu-id="c3a34-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3a34-117">`&` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c3a34-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c3a34-118">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="c3a34-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c3a34-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c3a34-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3a34-120">Handlowe "i" (&) znak może również służyć do identyfikowania zmienne jako typ `Long`.</span><span class="sxs-lookup"><span data-stu-id="c3a34-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="c3a34-121">Aby uzyskać więcej informacji, zobacz [znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="c3a34-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3a34-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3a34-122">Example</span></span>  
 <span data-ttu-id="c3a34-123">W tym przykładzie użyto `&` operatora, aby wymusić ciągów.</span><span class="sxs-lookup"><span data-stu-id="c3a34-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="c3a34-124">Wynik jest wartością ciągu reprezentujący łączenie ciąg dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="c3a34-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c3a34-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3a34-125">See also</span></span>

- [<span data-ttu-id="c3a34-126">&=, operator</span><span class="sxs-lookup"><span data-stu-id="c3a34-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="c3a34-127">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="c3a34-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="c3a34-128">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3a34-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c3a34-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="c3a34-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c3a34-130">Operatory łączenia w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3a34-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
