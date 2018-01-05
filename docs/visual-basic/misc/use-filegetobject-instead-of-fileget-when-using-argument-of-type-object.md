---
title: "Użyj &#39; Filegetobject — &#39; zamiast &#39; Fileget — &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="02835-102">Użyj &#39; Filegetobject — &#39; zamiast &#39; Fileget — &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;</span><span class="sxs-lookup"><span data-stu-id="02835-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="02835-103">`FileGet` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="02835-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="02835-104">`FileGetObject`powinien być używany zamiast `FileGet` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="02835-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="02835-105">Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` zapewnia większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="02835-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02835-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="02835-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="02835-107">Zastąp `FileGet` z `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="02835-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="02835-108">Rzutowanie `Object` argument więcej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="02835-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02835-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02835-109">See Also</span></span>  
   
 [<span data-ttu-id="02835-110">My.Computer.FileSystem —</span><span class="sxs-lookup"><span data-stu-id="02835-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
