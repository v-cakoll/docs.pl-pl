---
title: Procedura lub funkcja nie jest zdefiniowana
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 4627f8ddb979780481feadbef06225baf6a7c0ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532178"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="ed6fd-102">Procedura lub funkcja nie jest zdefiniowana</span><span class="sxs-lookup"><span data-stu-id="ed6fd-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="ed6fd-103">A `Sub` lub `Function` muszą być zdefiniowane w celu wywołana.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="ed6fd-104">Możliwe przyczyny tego błędu:</span><span class="sxs-lookup"><span data-stu-id="ed6fd-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="ed6fd-105">Błąd w pisowni nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="ed6fd-106">Podjęcie próby wywołać procedurę z innego projektu bez jawnie dodać odwołanie do tego projektu w **odwołania** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="ed6fd-107">Określenie procedury, która jest niewidoczna dla procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="ed6fd-108">Deklarowanie procedury biblioteki dołączanej (dynamicznie DLL) Windows lub dla komputerów Macintosh zasobów kod procedury, która nie jest określony zasób biblioteki lub kodu.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed6fd-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ed6fd-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="ed6fd-110">Upewnij się, że poprawna nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="ed6fd-111">Znajdowanie nazwy do projektu zawierającego procedury, aby wywołać w **odwołania** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="ed6fd-112">Jeśli nie zostanie wyświetlony, kliknij przycisk **Przeglądaj** przycisk, aby ją wyszukać.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="ed6fd-113">Zaznacz pole wyboru po lewej stronie nazwy projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ed6fd-114">Sprawdź nazwę procedury.</span><span class="sxs-lookup"><span data-stu-id="ed6fd-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6fd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed6fd-115">See also</span></span>
- [<span data-ttu-id="ed6fd-116">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="ed6fd-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="ed6fd-117">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="ed6fd-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="ed6fd-118">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ed6fd-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ed6fd-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ed6fd-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
