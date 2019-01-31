---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282597"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="70114-102">Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”</span><span class="sxs-lookup"><span data-stu-id="70114-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="70114-103">Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu.</span><span class="sxs-lookup"><span data-stu-id="70114-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="70114-104">Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.</span><span class="sxs-lookup"><span data-stu-id="70114-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70114-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="70114-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="70114-106">Podaj `PathName` argumentu w wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="70114-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70114-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70114-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
