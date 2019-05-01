---
title: Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022522"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="fb0e5-102">Użyj "FilePutObject" zamiast "FilePut, jeśli korzystasz z argumentu typu"Object"</span><span class="sxs-lookup"><span data-stu-id="fb0e5-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="fb0e5-103">`FilePut` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="fb0e5-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="fb0e5-104">`FilePutObject` powinny być używane zamiast `FilePut` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="fb0e5-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb0e5-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fb0e5-105">To correct this error</span></span>  
  
- <span data-ttu-id="fb0e5-106">Zastąp `FilePut` z `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="fb0e5-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="fb0e5-107">Rzutowanie `Object` argument do bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fb0e5-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="fb0e5-108">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="fb0e5-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0e5-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb0e5-109">See also</span></span>

- [<span data-ttu-id="fb0e5-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="fb0e5-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="fb0e5-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="fb0e5-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
