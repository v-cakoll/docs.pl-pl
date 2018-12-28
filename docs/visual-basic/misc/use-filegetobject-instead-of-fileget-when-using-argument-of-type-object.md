---
title: Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768014"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="a4208-102">Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"</span><span class="sxs-lookup"><span data-stu-id="a4208-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="a4208-103">`FileGet` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="a4208-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="a4208-104">`FileGetObject` powinny być używane zamiast `FileGet` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="a4208-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="a4208-105">Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` oferuje większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="a4208-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4208-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a4208-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a4208-107">Zastąp `FileGet` z `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="a4208-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="a4208-108">Rzutowanie `Object` argument do bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="a4208-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4208-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4208-109">See Also</span></span>  
   
 [<span data-ttu-id="a4208-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="a4208-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
