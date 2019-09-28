---
title: AddressOf — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591654"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="9a25e-102">AddressOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a25e-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="9a25e-103">Tworzy wystąpienie delegata, które odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="9a25e-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a25e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a25e-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="9a25e-105">Części</span><span class="sxs-lookup"><span data-stu-id="9a25e-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="9a25e-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a25e-106">Required.</span></span> <span data-ttu-id="9a25e-107">Określa procedurę, do której odwołuje się nowo utworzony delegat.</span><span class="sxs-lookup"><span data-stu-id="9a25e-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a25e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a25e-108">Remarks</span></span>  
 <span data-ttu-id="9a25e-109">Operator `AddressOf` tworzy delegata, który wskazuje na podrzędną lub funkcję określoną przez `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="9a25e-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="9a25e-110">Gdy określona procedura jest metodą wystąpienia, delegat odwołuje się zarówno do wystąpienia, jak i metody.</span><span class="sxs-lookup"><span data-stu-id="9a25e-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="9a25e-111">Następnie, gdy obiekt delegowany jest wywoływany, wywoływana jest określona metoda określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9a25e-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="9a25e-112">Operatora `AddressOf` można użyć jako operandu konstruktora delegata lub można go użyć w kontekście, w którym typ delegata może być określony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="9a25e-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a25e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a25e-113">Example</span></span>  
 <span data-ttu-id="9a25e-114">W tym przykładzie używa operatora `AddressOf`, aby wyznaczyć delegata do obsługi zdarzenia `Click` przycisku.</span><span class="sxs-lookup"><span data-stu-id="9a25e-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="9a25e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a25e-115">Example</span></span>  
 <span data-ttu-id="9a25e-116">Poniższy przykład używa operatora `AddressOf`, aby wyznaczyć funkcję uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="9a25e-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9a25e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a25e-117">See also</span></span>

- [<span data-ttu-id="9a25e-118">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a25e-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="9a25e-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a25e-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="9a25e-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a25e-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9a25e-121">Delegaty</span><span class="sxs-lookup"><span data-stu-id="9a25e-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
