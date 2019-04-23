---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767893"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="4b31c-102">Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”</span><span class="sxs-lookup"><span data-stu-id="4b31c-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="4b31c-103">Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu.</span><span class="sxs-lookup"><span data-stu-id="4b31c-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="4b31c-104">Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.</span><span class="sxs-lookup"><span data-stu-id="4b31c-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4b31c-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4b31c-105">To correct this error</span></span>  
  
1. <span data-ttu-id="4b31c-106">Podaj `PathName` argumentu w wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b31c-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b31c-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b31c-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
