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
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372067"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="9ef66-102">AddressOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ef66-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="9ef66-103">Tworzy wystąpienie delegata, które odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="9ef66-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ef66-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="9ef66-105">Części</span><span class="sxs-lookup"><span data-stu-id="9ef66-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="9ef66-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9ef66-106">Required.</span></span> <span data-ttu-id="9ef66-107">Określa procedurę, do której odwołuje się nowo utworzony delegat.</span><span class="sxs-lookup"><span data-stu-id="9ef66-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ef66-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ef66-108">Remarks</span></span>  
 <span data-ttu-id="9ef66-109">`AddressOf`Operator tworzy delegata, który wskazuje element Sub lub Function określony przez `procedurename` .</span><span class="sxs-lookup"><span data-stu-id="9ef66-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="9ef66-110">Gdy określona procedura jest metodą wystąpienia, delegat odwołuje się zarówno do wystąpienia, jak i metody.</span><span class="sxs-lookup"><span data-stu-id="9ef66-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="9ef66-111">Następnie, gdy obiekt delegowany jest wywoływany, wywoływana jest określona metoda określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9ef66-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="9ef66-112">`AddressOf`Operatora można używać jako operandu konstruktora delegata lub może być używany w kontekście, w którym typ delegata może być określony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="9ef66-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ef66-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ef66-113">Example</span></span>  
 <span data-ttu-id="9ef66-114">Ten przykład używa `AddressOf` operatora, aby wyznaczyć delegata do obsługi `Click` zdarzenia przycisku.</span><span class="sxs-lookup"><span data-stu-id="9ef66-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="9ef66-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ef66-115">Example</span></span>  
 <span data-ttu-id="9ef66-116">Poniższy przykład używa operatora, `AddressOf` Aby wyznaczyć funkcję uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="9ef66-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9ef66-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ef66-117">See also</span></span>

- [<span data-ttu-id="9ef66-118">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="9ef66-118">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="9ef66-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9ef66-119">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="9ef66-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9ef66-120">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="9ef66-121">Delegaci</span><span class="sxs-lookup"><span data-stu-id="9ef66-121">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
