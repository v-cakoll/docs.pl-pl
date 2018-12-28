---
title: Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: df7d7c54992984bcb1684e41f60ae8361a3aed03
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53774228"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="1db1c-102">Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"</span><span class="sxs-lookup"><span data-stu-id="1db1c-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="1db1c-103">`FilePut` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="1db1c-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="1db1c-104">`FilePutObject` powinny być używane zamiast `FilePut` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="1db1c-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1db1c-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1db1c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1db1c-106">Zastąp `FilePut` z `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="1db1c-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="1db1c-107">Rzutowanie `Object` argument do bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="1db1c-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="1db1c-108">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1db1c-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db1c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1db1c-109">See Also</span></span>  
   
 [<span data-ttu-id="1db1c-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="1db1c-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="1db1c-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="1db1c-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
