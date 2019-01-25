---
title: Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723397"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="c51b9-102">Użyj "Filegetobject —" zamiast "FileGet", jeśli korzystasz z argumentu typu "Object"</span><span class="sxs-lookup"><span data-stu-id="c51b9-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="c51b9-103">`FileGet` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="c51b9-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="c51b9-104">`FileGetObject` powinny być używane zamiast `FileGet` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="c51b9-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="c51b9-105">Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` oferuje większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c51b9-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c51b9-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c51b9-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="c51b9-107">Zastąp `FileGet` z `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c51b9-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="c51b9-108">Rzutowanie `Object` argument do bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="c51b9-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51b9-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c51b9-109">See also</span></span>

- [<span data-ttu-id="c51b9-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c51b9-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
