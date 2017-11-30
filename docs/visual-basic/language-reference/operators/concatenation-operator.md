---
title: "&amp;— Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="b1e55-102">&amp;— Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e55-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="b1e55-103">Tworzy połączenie ciągów dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b1e55-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1e55-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b1e55-105">Części</span><span class="sxs-lookup"><span data-stu-id="b1e55-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b1e55-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b1e55-106">Required.</span></span> <span data-ttu-id="b1e55-107">Wszelkie `String` lub `Object` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b1e55-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="b1e55-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b1e55-108">Required.</span></span> <span data-ttu-id="b1e55-109">Dowolne wyrażenie z typem danych rozszerzająca do `String`.</span><span class="sxs-lookup"><span data-stu-id="b1e55-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b1e55-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b1e55-110">Required.</span></span> <span data-ttu-id="b1e55-111">Dowolne wyrażenie z typem danych rozszerzająca do `String`.</span><span class="sxs-lookup"><span data-stu-id="b1e55-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1e55-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1e55-112">Remarks</span></span>  
 <span data-ttu-id="b1e55-113">Jeśli typ danych miary `expression1` lub `expression2` nie jest `String` , ale rozszerzenie do `String`, jest konwertowana na `String`.</span><span class="sxs-lookup"><span data-stu-id="b1e55-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="b1e55-114">Jeśli jeden z typów danych nie są rozszerzane `String`, kompilator generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="b1e55-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="b1e55-115">Typ danych miary `result` jest `String`.</span><span class="sxs-lookup"><span data-stu-id="b1e55-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="b1e55-116">Jeśli jeden lub oba wyrażenia mają [nic](../../../visual-basic/language-reference/nothing.md) lub mieć wartość <xref:System.DBNull.Value?displayProperty=nameWithType>, są traktowane jako ciąg o wartości "".</span><span class="sxs-lookup"><span data-stu-id="b1e55-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1e55-117">`&` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b1e55-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b1e55-118">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="b1e55-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b1e55-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b1e55-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1e55-120">Handlowe "i" (&) znaków mogą służyć do identyfikowania zmienne jako typ `Long`.</span><span class="sxs-lookup"><span data-stu-id="b1e55-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="b1e55-121">Aby uzyskać więcej informacji, zobacz [znaków typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="b1e55-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e55-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1e55-122">Example</span></span>  
 <span data-ttu-id="b1e55-123">W tym przykładzie użyto `&` operatora, aby wymusić ciągów.</span><span class="sxs-lookup"><span data-stu-id="b1e55-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="b1e55-124">Wynik jest wartością ciągu reprezentujący łączenia operandów dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="b1e55-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b1e55-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1e55-125">See Also</span></span>  
 [<span data-ttu-id="b1e55-126">& = — operator</span><span class="sxs-lookup"><span data-stu-id="b1e55-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="b1e55-127">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="b1e55-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="b1e55-128">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1e55-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b1e55-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b1e55-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b1e55-130">Operatory łączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1e55-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
