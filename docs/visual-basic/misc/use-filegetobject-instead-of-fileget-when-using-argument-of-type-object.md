---
title: Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022548"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="a64f2-102">Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"</span><span class="sxs-lookup"><span data-stu-id="a64f2-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="a64f2-103">`FileGet` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="a64f2-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="a64f2-104">`FileGetObject` powinny być używane zamiast `FileGet` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="a64f2-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="a64f2-105">Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` oferuje większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="a64f2-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a64f2-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a64f2-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a64f2-107">Zastąp `FileGet` z `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="a64f2-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="a64f2-108">Rzutowanie `Object` argument do bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="a64f2-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64f2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a64f2-109">See also</span></span>

- [<span data-ttu-id="a64f2-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="a64f2-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
