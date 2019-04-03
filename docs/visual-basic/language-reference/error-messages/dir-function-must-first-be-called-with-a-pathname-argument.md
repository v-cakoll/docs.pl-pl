---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1a5d6ed145199ae995a98b6c1180fa3aedf9942c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834163"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="986e6-102">Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”</span><span class="sxs-lookup"><span data-stu-id="986e6-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="986e6-103">Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu.</span><span class="sxs-lookup"><span data-stu-id="986e6-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="986e6-104">Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.</span><span class="sxs-lookup"><span data-stu-id="986e6-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="986e6-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="986e6-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="986e6-106">Podaj `PathName` argumentu w wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="986e6-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986e6-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="986e6-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
