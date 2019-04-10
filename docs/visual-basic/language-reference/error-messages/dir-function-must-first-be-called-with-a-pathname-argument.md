---
title: Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323645"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="7f159-102">Należy najpierw wywołać funkcję „Dir” z argumentem „PathName”</span><span class="sxs-lookup"><span data-stu-id="7f159-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="7f159-103">Początkowe wywołanie `Dir` nie ma funkcji `PathName` argumentu.</span><span class="sxs-lookup"><span data-stu-id="7f159-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="7f159-104">Pierwsze wywołanie `Dir` musi zawierać `PathName`, ale kolejne wywołania `Dir` nie trzeba podawać parametrów, aby pobrać następny element.</span><span class="sxs-lookup"><span data-stu-id="7f159-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f159-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="7f159-105">To correct this error</span></span>  
  
1. <span data-ttu-id="7f159-106">Podaj `PathName` argumentu w wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f159-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f159-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f159-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
