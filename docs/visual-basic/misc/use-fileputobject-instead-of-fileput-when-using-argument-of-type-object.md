---
title: "Użyj &#39; FilePutObject &#39; zamiast &#39; FilePut &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="b75da-102">Użyj &#39; FilePutObject &#39; zamiast &#39; FilePut &#39; przy korzystaniu z argumentu typu &#39; obiekt &#39;</span><span class="sxs-lookup"><span data-stu-id="b75da-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="b75da-103">`FilePut` Metoda zawiera argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="b75da-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="b75da-104">`FilePutObject`powinien być używany zamiast `FilePut` Aby uniknąć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="b75da-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b75da-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b75da-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b75da-106">Zastąp `FilePut` z `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="b75da-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="b75da-107">Rzutowanie `Object` argument więcej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b75da-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="b75da-108">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b75da-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75da-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b75da-109">See Also</span></span>  
 [<span data-ttu-id="b75da-110">NIE w kompilacji: FilePutObject — funkcja</span><span class="sxs-lookup"><span data-stu-id="b75da-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="b75da-111">My.Computer.FileSystem — obiekt</span><span class="sxs-lookup"><span data-stu-id="b75da-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="b75da-112">My.Computer.FileSystem.WriteAllBytes — metoda</span><span class="sxs-lookup"><span data-stu-id="b75da-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
