---
title: My.Request — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: f2c43afb723944293907d0efbb4cf3cc66a40e1e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932553"
---
# <a name="myrequest-object"></a><span data-ttu-id="51cf8-102">My.Request — Obiekt</span><span class="sxs-lookup"><span data-stu-id="51cf8-102">My.Request Object</span></span>
<span data-ttu-id="51cf8-103">Pobiera <xref:System.Web.HttpRequest> obiektu dla żądanej strony.</span><span class="sxs-lookup"><span data-stu-id="51cf8-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51cf8-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51cf8-104">Remarks</span></span>  
 <span data-ttu-id="51cf8-105">`My.Request` Obiekt zawiera informacje o bieżącym żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="51cf8-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="51cf8-106">`My.Request` Obiekt jest dostępny tylko w przypadku aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="51cf8-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cf8-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="51cf8-107">Example</span></span>  
 <span data-ttu-id="51cf8-108">Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i zastosowań `My.Response` obiektu do zapisania go do strony ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="51cf8-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="51cf8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51cf8-109">See Also</span></span>  
 <xref:System.Web.HttpRequest>  
 [<span data-ttu-id="51cf8-110">My.Response, obiekt</span><span class="sxs-lookup"><span data-stu-id="51cf8-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
