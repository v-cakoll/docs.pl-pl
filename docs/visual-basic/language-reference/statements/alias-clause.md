---
title: Alias — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 9cf97402d0b0a6cd16dd75a970c1d29a2fcc30a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498573"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="f5c12-102">Alias — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5c12-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="f5c12-103">Wskazuje, że procedura zewnętrzna ma inną nazwę w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="f5c12-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5c12-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5c12-104">Remarks</span></span>  
 <span data-ttu-id="f5c12-105">Słowa kluczowego `Alias` można użyć w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="f5c12-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="f5c12-106">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f5c12-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="f5c12-107">W poniższym przykładzie słowo kluczowe `Alias` jest używane do przekazania nazwy funkcji w pliku advapi32.dll, `GetUserNameA`, zamiast której w tym przykładzie występuje funkcja `getUserName`.</span><span class="sxs-lookup"><span data-stu-id="f5c12-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="f5c12-108">Funkcja `getUserName` jest wywoływana w poleceniu Sub `getUser`, powodując wyświetlenie nazwy bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f5c12-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c12-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5c12-109">See also</span></span>
- [<span data-ttu-id="f5c12-110">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f5c12-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
