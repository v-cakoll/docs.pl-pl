---
title: Alias — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839746"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="a3b8c-102">Alias — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3b8c-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="a3b8c-103">Wskazuje, że procedura zewnętrzna ma inną nazwę w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="a3b8c-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3b8c-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3b8c-104">Remarks</span></span>  
 <span data-ttu-id="a3b8c-105">Słowa kluczowego `Alias` można użyć w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="a3b8c-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="a3b8c-106">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a3b8c-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="a3b8c-107">W poniższym przykładzie słowo kluczowe `Alias` jest używane do przekazania nazwy funkcji w pliku advapi32.dll, `GetUserNameA`, zamiast której w tym przykładzie występuje funkcja `getUserName`.</span><span class="sxs-lookup"><span data-stu-id="a3b8c-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="a3b8c-108">Funkcja `getUserName` jest wywoływana w poleceniu Sub `getUser`, powodując wyświetlenie nazwy bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3b8c-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a3b8c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3b8c-109">See also</span></span>

- [<span data-ttu-id="a3b8c-110">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="a3b8c-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
