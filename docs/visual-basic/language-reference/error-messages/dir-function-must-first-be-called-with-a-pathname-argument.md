---
title: "&#39; Dir &#39; należy najpierw wywołać funkcję w z &#39; Nazwa ścieżki &#39; argument"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="5d358-102">&#39; Dir &#39; należy najpierw wywołać funkcję w z &#39; Nazwa ścieżki &#39; argument</span><span class="sxs-lookup"><span data-stu-id="5d358-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="5d358-103">Wywołanie początkowej `Dir` nie ma funkcji `PathName` argumentu.</span><span class="sxs-lookup"><span data-stu-id="5d358-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="5d358-104">W pierwszym wywołaniu `Dir` musi zawierać `PathName`, ale kolejnych wywołań `Dir` nie trzeba podawać parametry do pobrania następnej.</span><span class="sxs-lookup"><span data-stu-id="5d358-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d358-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5d358-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="5d358-106">Podaj `PathName` argument w wywołaniu funkcji.</span><span class="sxs-lookup"><span data-stu-id="5d358-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d358-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d358-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
