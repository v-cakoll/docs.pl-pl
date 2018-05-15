---
title: '&#39;Dir&#39; należy najpierw wywołać funkcję z &#39;PathName&#39; argumentu'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="af382-102">&#39;Dir&#39; należy najpierw wywołać funkcję z &#39;PathName&#39; argumentu</span><span class="sxs-lookup"><span data-stu-id="af382-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="af382-103">Wywołanie początkowej `Dir` nie ma funkcji `PathName` argumentu.</span><span class="sxs-lookup"><span data-stu-id="af382-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="af382-104">W pierwszym wywołaniu `Dir` musi zawierać `PathName`, ale kolejnych wywołań `Dir` nie trzeba podawać parametry do pobrania następnej.</span><span class="sxs-lookup"><span data-stu-id="af382-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af382-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="af382-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="af382-106">Podaj `PathName` argument w wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="af382-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af382-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af382-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
