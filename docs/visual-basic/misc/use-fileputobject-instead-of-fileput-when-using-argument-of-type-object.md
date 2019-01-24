---
title: Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725561"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="dae76-102">Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"</span><span class="sxs-lookup"><span data-stu-id="dae76-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="dae76-103">`FilePut` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="dae76-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="dae76-104">`FilePutObject` powinny być używane zamiast `FilePut` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="dae76-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dae76-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dae76-105">To correct this error</span></span>  
  
-   <span data-ttu-id="dae76-106">Zastąp `FilePut` z `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="dae76-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="dae76-107">Rzutowanie `Object` argument do bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="dae76-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="dae76-108">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="dae76-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae76-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dae76-109">See also</span></span>

- [<span data-ttu-id="dae76-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="dae76-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="dae76-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="dae76-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
