---
title: My.Request — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 88c3a9a01b50a97b556fa94026df391248bdf912
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595891"
---
# <a name="myrequest-object"></a><span data-ttu-id="cbf12-102">My.Request — Obiekt</span><span class="sxs-lookup"><span data-stu-id="cbf12-102">My.Request Object</span></span>
<span data-ttu-id="cbf12-103">Pobiera <xref:System.Web.HttpRequest> obiektu dla żądanej strony.</span><span class="sxs-lookup"><span data-stu-id="cbf12-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbf12-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbf12-104">Remarks</span></span>  
 <span data-ttu-id="cbf12-105">`My.Request` Zawiera informacje o bieżącym żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="cbf12-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="cbf12-106">`My.Request` Obiekt jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbf12-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbf12-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbf12-107">Example</span></span>  
 <span data-ttu-id="cbf12-108">Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i używa `My.Response` obiektu do zapisania go do strony ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbf12-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="cbf12-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbf12-109">See Also</span></span>  
 <xref:System.Web.HttpRequest>  
 [<span data-ttu-id="cbf12-110">My.Response, obiekt</span><span class="sxs-lookup"><span data-stu-id="cbf12-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
