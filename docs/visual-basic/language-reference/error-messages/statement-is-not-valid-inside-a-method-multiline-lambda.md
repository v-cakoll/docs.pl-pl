---
title: "Instrukcja nie jest prawidłowa wewnątrz metody wielowierszowego wyrażenia lambda"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords: BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80673fc7a1497b4148a6505d29581c6403115558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="1a61a-102">Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="1a61a-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="1a61a-103">Instrukcja nie jest prawidłowy w ramach `Sub`, `Function`, właściwość `Get`, lub właściwości `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="1a61a-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="1a61a-104">Niektóre instrukcji można umieścić na poziomie modułu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="1a61a-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="1a61a-105">Inne, takie jak `Option Strict`, musi znajdować się na poziomie przestrzeni nazw i poprzedzać wszystkie inne deklaracje.</span><span class="sxs-lookup"><span data-stu-id="1a61a-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="1a61a-106">**Identyfikator błędu:** BC30024</span><span class="sxs-lookup"><span data-stu-id="1a61a-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a61a-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1a61a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="1a61a-108">Usuń instrukcji z procedury.</span><span class="sxs-lookup"><span data-stu-id="1a61a-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a61a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a61a-109">See Also</span></span>  
 [<span data-ttu-id="1a61a-110">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a61a-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="1a61a-111">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a61a-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="1a61a-112">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a61a-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="1a61a-113">Set — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a61a-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
