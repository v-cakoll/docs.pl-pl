---
title: Procedura lub funkcja nie jest zdefiniowana
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349576"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="c15ca-102">Procedura lub funkcja nie jest zdefiniowana</span><span class="sxs-lookup"><span data-stu-id="c15ca-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="c15ca-103">A `Sub` or `Function` must be defined in order to be called.</span><span class="sxs-lookup"><span data-stu-id="c15ca-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="c15ca-104">Possible causes of this error include:</span><span class="sxs-lookup"><span data-stu-id="c15ca-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="c15ca-105">Misspelling the procedure name.</span><span class="sxs-lookup"><span data-stu-id="c15ca-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="c15ca-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span><span class="sxs-lookup"><span data-stu-id="c15ca-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="c15ca-107">Specifying a procedure that is not visible to the calling procedure.</span><span class="sxs-lookup"><span data-stu-id="c15ca-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="c15ca-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span><span class="sxs-lookup"><span data-stu-id="c15ca-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c15ca-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c15ca-109">To correct this error</span></span>  
  
1. <span data-ttu-id="c15ca-110">Make sure that the procedure name is spelled correctly.</span><span class="sxs-lookup"><span data-stu-id="c15ca-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="c15ca-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span><span class="sxs-lookup"><span data-stu-id="c15ca-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="c15ca-112">If it does not appear, click the **Browse** button to search for it.</span><span class="sxs-lookup"><span data-stu-id="c15ca-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="c15ca-113">Select the check box to the left of the project name, and then click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c15ca-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="c15ca-114">Check the name of the routine.</span><span class="sxs-lookup"><span data-stu-id="c15ca-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c15ca-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c15ca-115">See also</span></span>

- [<span data-ttu-id="c15ca-116">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="c15ca-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="c15ca-117">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="c15ca-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="c15ca-118">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c15ca-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c15ca-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c15ca-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
