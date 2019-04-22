---
title: Instrukcja nie jest prawidłowa wewnątrz metody / wielowierszowego wyrażenia lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 994cafc44a37d16d0f70caec560f530c6a836ec0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841566"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="f6974-102">Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f6974-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="f6974-103">Wykonywanie instrukcji nie jest prawidłowy w ramach `Sub`, `Function`, właściwość `Get`, lub właściwości `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="f6974-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="f6974-104">Niektóre instrukcje mogą być umieszczone na poziomie modułu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="f6974-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="f6974-105">Inne, takie jak `Option Strict`, musi znajdować się na poziomie przestrzeni nazw i poprzedzać wszystkie inne deklaracje.</span><span class="sxs-lookup"><span data-stu-id="f6974-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="f6974-106">**Identyfikator błędu:** BC30024</span><span class="sxs-lookup"><span data-stu-id="f6974-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6974-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f6974-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f6974-108">Usuń instrukcję od procedury.</span><span class="sxs-lookup"><span data-stu-id="f6974-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6974-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6974-109">See also</span></span>

- [<span data-ttu-id="f6974-110">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f6974-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f6974-111">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f6974-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="f6974-112">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f6974-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="f6974-113">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f6974-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
