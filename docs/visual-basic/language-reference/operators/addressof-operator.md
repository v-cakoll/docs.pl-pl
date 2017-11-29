---
title: "AddressOf — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="90fbd-102">AddressOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90fbd-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="90fbd-103">Tworzy wystąpienia delegata procedury, która odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="90fbd-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90fbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90fbd-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="90fbd-105">Części</span><span class="sxs-lookup"><span data-stu-id="90fbd-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="90fbd-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="90fbd-106">Required.</span></span> <span data-ttu-id="90fbd-107">Określa procedurę, aby odwoływać się procedury nowo utworzonego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="90fbd-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90fbd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90fbd-108">Remarks</span></span>  
 <span data-ttu-id="90fbd-109">`AddressOf` Operator tworzy delegata funkcji, które wskazuje funkcji określonej przez `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="90fbd-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="90fbd-110">Gdy określonej procedury jest metodą wystąpienia następnie delegata funkcji odwołuje się do wystąpienia i metody.</span><span class="sxs-lookup"><span data-stu-id="90fbd-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="90fbd-111">Następnie gdy jest wywoływany delegat funkcji określonej metody określone wystąpienie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="90fbd-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="90fbd-112">`AddressOf` Operator może być używany jako argument konstruktora delegata lub mogą być używane w kontekście, w którym można ustalić typu obiektu delegowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="90fbd-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90fbd-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="90fbd-113">Example</span></span>  
 <span data-ttu-id="90fbd-114">W tym przykładzie użyto `AddressOf` operatora, aby wyznaczyć pełnomocnika, aby obsłużyć `Click` zdarzeń przycisku.</span><span class="sxs-lookup"><span data-stu-id="90fbd-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="90fbd-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="90fbd-115">Example</span></span>  
 <span data-ttu-id="90fbd-116">W poniższym przykładzie użyto `AddressOf` operatora, aby wyznaczyć funkcja uruchomienia wątku.</span><span class="sxs-lookup"><span data-stu-id="90fbd-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="90fbd-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90fbd-117">See Also</span></span>  
 [<span data-ttu-id="90fbd-118">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="90fbd-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="90fbd-119">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="90fbd-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="90fbd-120">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="90fbd-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="90fbd-121">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="90fbd-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
