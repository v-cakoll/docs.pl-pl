---
title: Użyj &#39;FilePutObject&#39; zamiast &#39;FilePut&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="639a3-102">Użyj &#39;FilePutObject&#39; zamiast &#39;FilePut&#39; przy korzystaniu z argumentu typu &#39;obiektu&#39;</span><span class="sxs-lookup"><span data-stu-id="639a3-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="639a3-103">`FilePut` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="639a3-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="639a3-104">`FilePutObject` powinien być używany zamiast `FilePut` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="639a3-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="639a3-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="639a3-105">To correct this error</span></span>  
  
-   <span data-ttu-id="639a3-106">Zastąp `FilePut` z `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="639a3-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="639a3-107">Rzutowanie `Object` argument więcej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="639a3-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="639a3-108">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="639a3-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639a3-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="639a3-109">See Also</span></span>  
   
 [<span data-ttu-id="639a3-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="639a3-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="639a3-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="639a3-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
