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
ms.openlocfilehash: 9d8515b6d5b0caf3552ed05a7e0cd4a271efaf54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830347"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="2579c-102">AddressOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2579c-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="2579c-103">Tworzy wystąpienie delegata procedury, która odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="2579c-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2579c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2579c-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="2579c-105">Części</span><span class="sxs-lookup"><span data-stu-id="2579c-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="2579c-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2579c-106">Required.</span></span> <span data-ttu-id="2579c-107">Określa procedury być przywoływane przez delegata nowo utworzone procedury.</span><span class="sxs-lookup"><span data-stu-id="2579c-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2579c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2579c-108">Remarks</span></span>  
 <span data-ttu-id="2579c-109">`AddressOf` Operatora, tworzy delegata funkcji, który wskazuje na funkcji określonej przez `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="2579c-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="2579c-110">Gdy określonej procedury jest metodą wystąpienia następnie delegata funkcji, który odwołuje się do wystąpienia i metody.</span><span class="sxs-lookup"><span data-stu-id="2579c-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="2579c-111">Następnie podczas wywoływania delegata funkcji określonej metody określone wystąpienie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2579c-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="2579c-112">`AddressOf` Operator może służyć jako argument konstruktora delegata lub mogą być używane w kontekście, w którym można określić typ delegata przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="2579c-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2579c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="2579c-113">Example</span></span>  
 <span data-ttu-id="2579c-114">W tym przykładzie użyto `AddressOf` operatora, aby wyznaczyć delegata do obsługi `Click` zdarzenia przycisku.</span><span class="sxs-lookup"><span data-stu-id="2579c-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="2579c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2579c-115">Example</span></span>  
 <span data-ttu-id="2579c-116">W poniższym przykładzie użyto `AddressOf` operatora, aby wyznaczyć funkcji uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="2579c-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="2579c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2579c-117">See also</span></span>

- [<span data-ttu-id="2579c-118">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2579c-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="2579c-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2579c-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="2579c-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2579c-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2579c-121">Delegaty</span><span class="sxs-lookup"><span data-stu-id="2579c-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
