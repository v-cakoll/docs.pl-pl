---
title: My.Request — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: a9af211df358b8c87cc9735f05d18c191b49500e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716198"
---
# <a name="myrequest-object"></a><span data-ttu-id="d1a46-102">My.Request — Obiekt</span><span class="sxs-lookup"><span data-stu-id="d1a46-102">My.Request Object</span></span>
<span data-ttu-id="d1a46-103">Pobiera <xref:System.Web.HttpRequest> obiektu dla żądanej strony.</span><span class="sxs-lookup"><span data-stu-id="d1a46-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1a46-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1a46-104">Remarks</span></span>  
 <span data-ttu-id="d1a46-105">`My.Request` Obiekt zawiera informacje o bieżącym żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d1a46-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="d1a46-106">`My.Request` Obiekt jest dostępny tylko w przypadku aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d1a46-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a46-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1a46-107">Example</span></span>  
 <span data-ttu-id="d1a46-108">Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i zastosowań `My.Response` obiektu do zapisania go do strony ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d1a46-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="d1a46-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1a46-109">See also</span></span>
- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="d1a46-110">My.Response, obiekt</span><span class="sxs-lookup"><span data-stu-id="d1a46-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
