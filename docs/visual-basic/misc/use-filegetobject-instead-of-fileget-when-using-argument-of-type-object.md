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
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="19489-102">Użyj &#39; Filegetobject — &#39; zamiast &#39; Fileget — &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;</span><span class="sxs-lookup"><span data-stu-id="19489-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="19489-103">`FileGet` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="19489-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="19489-104">`FileGetObject`powinien być używany zamiast `FileGet` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="19489-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="19489-105">Należy zauważyć, że funkcje oferowane przez `My.Computer.Filesystem` zapewnia większą łatwość użycia i wydajności niż albo `FileGet` lub `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="19489-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19489-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="19489-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="19489-107">Zastąp `FileGet` z `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="19489-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="19489-108">Rzutowanie `Object` argument więcej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="19489-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19489-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19489-109">See Also</span></span>  
 [<span data-ttu-id="19489-110">NIE w kompilacji: Filegetobject — funkcja</span><span class="sxs-lookup"><span data-stu-id="19489-110">NOT IN BUILD: FileGetObject Function</span></span>](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [<span data-ttu-id="19489-111">My.Computer.FileSystem — obiekt</span><span class="sxs-lookup"><span data-stu-id="19489-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
