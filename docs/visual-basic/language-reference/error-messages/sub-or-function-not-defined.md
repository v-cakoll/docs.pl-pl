---
title: Procedura lub funkcja nie jest zdefiniowana
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="2b1f3-102">Procedura lub funkcja nie jest zdefiniowana</span><span class="sxs-lookup"><span data-stu-id="2b1f3-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="2b1f3-103">A `Sub` lub `Function` musi być zdefiniowana, aby można było można wywołać.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="2b1f3-104">Możliwe przyczyny tego błędu:</span><span class="sxs-lookup"><span data-stu-id="2b1f3-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="2b1f3-105">Błąd pisowni Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="2b1f3-106">Próba wywołania procedury z innego projektu bez jawnie dodać odwołanie do tego projektu w **odwołania** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="2b1f3-107">Określanie procedury, która jest niewidoczna dla procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="2b1f3-108">Deklarowanie procedury biblioteki dołączanej (dynamicznie DLL) systemu Windows lub procedury zasobu kodu Macintosh, który nie jest określony zasób biblioteki lub kodu.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b1f3-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2b1f3-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="2b1f3-110">Upewnij się, że nazwa procedury została wpisana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="2b1f3-111">Znajdź nazwę projektu zawierającego procedury, która ma wywołać w **odwołania** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="2b1f3-112">Jeśli nie ma, kliknij przycisk **Przeglądaj** przycisk, aby wyszukać.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="2b1f3-113">Zaznacz pole wyboru po lewej nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2b1f3-114">Sprawdź nazwę procedury.</span><span class="sxs-lookup"><span data-stu-id="2b1f3-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1f3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b1f3-115">See Also</span></span>  
 [<span data-ttu-id="2b1f3-116">Error — typy</span><span class="sxs-lookup"><span data-stu-id="2b1f3-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="2b1f3-117">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="2b1f3-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="2b1f3-118">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="2b1f3-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="2b1f3-119">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="2b1f3-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
