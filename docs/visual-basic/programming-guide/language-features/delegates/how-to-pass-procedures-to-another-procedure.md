---
title: 'Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305250"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="2f6b1-102">Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f6b1-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="2f6b1-103">Ten przykład pokazuje, jak używać delegatów do przekazania procedury do innej procedury.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="2f6b1-104">Delegat to typ, który można używać jak dowolny inny typ w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="2f6b1-105">`AddressOf` Operator zwraca obiekt delegowany po zastosowaniu do nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="2f6b1-106">W tym przykładzie ma procedury przy użyciu parametru delegata, który można wykonać odwołanie do innej procedury, otrzymany wraz z `AddressOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="2f6b1-107">Utwórz delegata i procedur dopasowania</span><span class="sxs-lookup"><span data-stu-id="2f6b1-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="2f6b1-108">Utwórz delegata, o nazwie `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="2f6b1-109">Utwórz procedurę o nazwie `AddNumbers` parametrów i zwracanej wartości, która odpowiadają `MathOperator`, dzięki czemu sygnatury są zgodne.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="2f6b1-110">Utwórz procedurę o nazwie `SubtractNumbers` za pomocą podpisu, który odpowiada `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="2f6b1-111">Utwórz procedurę o nazwie `DelegateTest` przyjmującej obiekt delegowany, jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="2f6b1-112">Ta procedura może akceptować odwołania do `AddNumbers` lub `SubtractNumbers`, ponieważ pasuje do ich podpisy `MathOperator` podpisu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="2f6b1-113">Utwórz procedurę o nazwie `Test` wywołująca `DelegateTest` drugi raz z delegat dla obiektu `AddNumbers` jako parametr, a następnie z obiektem delegowanym dla `SubtractNumbers` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="2f6b1-114">Gdy `Test` jest wywoływana, najpierw wyświetla wynik `AddNumbers` działającym na `5` i `3`, czyli 8.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="2f6b1-115">Następnie wynik `SubtractNumbers` na `9` i `3` jest wyświetlany, czyli 6.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6b1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f6b1-116">See also</span></span>

- [<span data-ttu-id="2f6b1-117">Delegaty</span><span class="sxs-lookup"><span data-stu-id="2f6b1-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="2f6b1-118">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="2f6b1-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="2f6b1-119">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2f6b1-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="2f6b1-120">Instrukcje: Wywoływanie metody delegata</span><span class="sxs-lookup"><span data-stu-id="2f6b1-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
