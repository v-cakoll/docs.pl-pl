---
title: AddressOf, operator
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350284"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="866bb-102">AddressOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="866bb-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="866bb-103">Tworzy wystąpienie delegata, które odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="866bb-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="866bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="866bb-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="866bb-105">Części</span><span class="sxs-lookup"><span data-stu-id="866bb-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="866bb-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="866bb-106">Required.</span></span> <span data-ttu-id="866bb-107">Określa procedurę, do której odwołuje się nowo utworzony delegat.</span><span class="sxs-lookup"><span data-stu-id="866bb-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="866bb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="866bb-108">Remarks</span></span>  
 <span data-ttu-id="866bb-109">Operator `AddressOf` tworzy delegata, który wskazuje na podrzędną lub funkcję określoną przez `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="866bb-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="866bb-110">Gdy określona procedura jest metodą wystąpienia, delegat odwołuje się zarówno do wystąpienia, jak i metody.</span><span class="sxs-lookup"><span data-stu-id="866bb-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="866bb-111">Następnie, gdy obiekt delegowany jest wywoływany, wywoływana jest określona metoda określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="866bb-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="866bb-112">Operatora `AddressOf` można używać jako operandu konstruktora delegata lub można go użyć w kontekście, w którym typ delegata może być określony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="866bb-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="866bb-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="866bb-113">Example</span></span>  
 <span data-ttu-id="866bb-114">W tym przykładzie używa operatora `AddressOf`, aby wyznaczyć delegata do obsługi zdarzenia `Click` przycisku.</span><span class="sxs-lookup"><span data-stu-id="866bb-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="866bb-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="866bb-115">Example</span></span>  
 <span data-ttu-id="866bb-116">Poniższy przykład używa operatora `AddressOf`, aby wyznaczyć funkcję uruchamiania dla wątku.</span><span class="sxs-lookup"><span data-stu-id="866bb-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="866bb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="866bb-117">See also</span></span>

- [<span data-ttu-id="866bb-118">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="866bb-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="866bb-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="866bb-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="866bb-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="866bb-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="866bb-121">Delegaci</span><span class="sxs-lookup"><span data-stu-id="866bb-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
