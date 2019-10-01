---
title: Sub — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701333"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="4ba6c-102">Sub — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ba6c-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="4ba6c-103">Deklaruje parametry i kod, który definiuje podprocedure wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ba6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ba6c-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="4ba6c-105">Części</span><span class="sxs-lookup"><span data-stu-id="4ba6c-105">Parts</span></span>  
  
|<span data-ttu-id="4ba6c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="4ba6c-106">Term</span></span>|<span data-ttu-id="4ba6c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="4ba6c-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="4ba6c-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-108">Optional.</span></span> <span data-ttu-id="4ba6c-109">Lista nazw zmiennych lokalnych, które reprezentują parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="4ba6c-110">Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="4ba6c-111">Aby uzyskać więcej informacji, zobacz [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4ba6c-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="4ba6c-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-112">Required.</span></span> <span data-ttu-id="4ba6c-113">Pojedyncza instrukcja.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="4ba6c-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-114">Required.</span></span> <span data-ttu-id="4ba6c-115">Lista instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ba6c-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ba6c-116">Remarks</span></span>  
 <span data-ttu-id="4ba6c-117">*Wyrażenie lambda* jest podprocedurą, która nie ma nazwy i która wykonuje co najmniej jedną instrukcję.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="4ba6c-118">Wyrażenia lambda można użyć w dowolnym miejscu, w którym można użyć typu delegata, z wyjątkiem argumentu `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="4ba6c-119">Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) i [Swobodna konwersja delegata](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="4ba6c-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="4ba6c-120">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="4ba6c-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="4ba6c-121">Składnia wyrażenia lambda jest podobna do standardowej procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="4ba6c-122">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="4ba6c-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="4ba6c-123">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="4ba6c-124">Wyrażenie lambda nie może mieć modyfikatora, takiego jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="4ba6c-125">Treść wyrażenia lambda pojedynczego wiersza musi być instrukcją, a nie wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="4ba6c-126">Treść może składać się z wywołania procedury Sub, ale nie wywołania procedury funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="4ba6c-127">W wyrażeniu lambda wszystkie parametry muszą mieć określone typy danych lub wszystkie parametry muszą zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="4ba6c-128">Parametry opcjonalne i `ParamArray` są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="4ba6c-129">Parametry ogólne są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ba6c-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ba6c-130">Example</span></span>  
 <span data-ttu-id="4ba6c-131">Poniżej znajduje się przykład wyrażenia lambda, które zapisuje wartość w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="4ba6c-132">Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4ba6c-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="4ba6c-133">Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4ba6c-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4ba6c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ba6c-134">See also</span></span>

- [<span data-ttu-id="4ba6c-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4ba6c-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4ba6c-136">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="4ba6c-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="4ba6c-137">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4ba6c-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4ba6c-138">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="4ba6c-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="4ba6c-139">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="4ba6c-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
