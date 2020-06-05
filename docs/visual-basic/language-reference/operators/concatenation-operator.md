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
ms.openlocfilehash: d778c0c99d6d074fe8b73aaf3660074643e7e136
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371612"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="52689-102">&amp;Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52689-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="52689-103">Generuje łączenie ciągów dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="52689-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52689-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52689-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="52689-105">Części</span><span class="sxs-lookup"><span data-stu-id="52689-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="52689-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="52689-106">Required.</span></span> <span data-ttu-id="52689-107">Any `String` lub `Object` Variable.</span><span class="sxs-lookup"><span data-stu-id="52689-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="52689-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="52689-108">Required.</span></span> <span data-ttu-id="52689-109">Każde wyrażenie z typem danych, który jest poszerzany do `String` .</span><span class="sxs-lookup"><span data-stu-id="52689-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="52689-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="52689-110">Required.</span></span> <span data-ttu-id="52689-111">Każde wyrażenie z typem danych, który jest poszerzany do `String` .</span><span class="sxs-lookup"><span data-stu-id="52689-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52689-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52689-112">Remarks</span></span>  
 <span data-ttu-id="52689-113">Jeśli typ danych `expression1` lub `expression2` nie jest `String` , ale jest rozszerzony do `String` , jest konwertowany na `String` .</span><span class="sxs-lookup"><span data-stu-id="52689-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="52689-114">Jeśli jeden z typów danych nie jest rozszerzony do `String` , kompilator generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="52689-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="52689-115">Typ danych `result` to `String` .</span><span class="sxs-lookup"><span data-stu-id="52689-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="52689-116">Jeśli co najmniej jedno wyrażenie zwróci wartość [Nothing lub nie](../nothing.md) ma wartości <xref:System.DBNull.Value?displayProperty=nameWithType> , są traktowane jako ciąg o wartości "".</span><span class="sxs-lookup"><span data-stu-id="52689-116">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52689-117">`&`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="52689-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="52689-118">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="52689-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="52689-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="52689-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52689-120">Znak handlowego "i" (&) może również służyć do identyfikowania zmiennych jako typów `Long` .</span><span class="sxs-lookup"><span data-stu-id="52689-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="52689-121">Aby uzyskać więcej informacji, zobacz [Type characters](../../programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="52689-121">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52689-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="52689-122">Example</span></span>  
 <span data-ttu-id="52689-123">W tym przykładzie używa `&` operatora w celu wymuszenia łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="52689-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="52689-124">Wynikiem jest wartość ciągu reprezentująca połączenie dwóch operandów ciągu.</span><span class="sxs-lookup"><span data-stu-id="52689-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="52689-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52689-125">See also</span></span>

- [<span data-ttu-id="52689-126">&= — operator</span><span class="sxs-lookup"><span data-stu-id="52689-126">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="52689-127">Concatenation — Operatory</span><span class="sxs-lookup"><span data-stu-id="52689-127">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="52689-128">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52689-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="52689-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="52689-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="52689-130">Operatory łączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52689-130">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
