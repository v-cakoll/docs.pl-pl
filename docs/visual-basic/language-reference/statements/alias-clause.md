---
title: Alias, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408474"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="3d4c2-102">Alias — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d4c2-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="3d4c2-103">Wskazuje, że procedura zewnętrzna ma inną nazwę w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="3d4c2-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d4c2-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d4c2-104">Remarks</span></span>  
 <span data-ttu-id="3d4c2-105">`Alias`Słowo kluczowe może być używane w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="3d4c2-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="3d4c2-106">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3d4c2-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="3d4c2-107">W poniższym przykładzie `Alias` słowo kluczowe jest używane do podania nazwy funkcji w advapi32. dll, `GetUserNameA` która `getUserName` jest używana zamiast w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3d4c2-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="3d4c2-108">Funkcja `getUserName` jest wywoływana w sub `getUser` , która wyświetla nazwę bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d4c2-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="3d4c2-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d4c2-109">See also</span></span>

- [<span data-ttu-id="3d4c2-110">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3d4c2-110">Keywords</span></span>](../keywords/index.md)
