---
title: Użyj &#39;filegetobject —&#39; zamiast &#39;fileget —&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="8c8f6-102">Użyj &#39;filegetobject —&#39; zamiast &#39;fileget —&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;</span><span class="sxs-lookup"><span data-stu-id="8c8f6-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="8c8f6-103">`FileGet` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="8c8f6-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="8c8f6-104">`FileGetObject` powinien być używany zamiast `FileGet` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="8c8f6-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="8c8f6-105">Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` zapewnia większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="8c8f6-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c8f6-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8c8f6-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="8c8f6-107">Zastąp `FileGet` z `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="8c8f6-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="8c8f6-108">Rzutowanie `Object` argument więcej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="8c8f6-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8f6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c8f6-109">See Also</span></span>  
   
 [<span data-ttu-id="8c8f6-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="8c8f6-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
