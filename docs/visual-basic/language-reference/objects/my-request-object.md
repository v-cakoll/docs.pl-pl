---
title: My. Request — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: da17872acb839cdcdfa7f80c3f58f26dc25d0ab5
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567464"
---
# <a name="myrequest-object"></a><span data-ttu-id="2f909-102">My.Request — Obiekt</span><span class="sxs-lookup"><span data-stu-id="2f909-102">My.Request Object</span></span>
<span data-ttu-id="2f909-103"><xref:System.Web.HttpRequest> Pobiera obiekt dla żądanej strony.</span><span class="sxs-lookup"><span data-stu-id="2f909-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f909-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f909-104">Remarks</span></span>  
 <span data-ttu-id="2f909-105">`My.Request` Obiekt zawiera informacje o bieżącym żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2f909-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="2f909-106">`My.Request` Obiekt jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2f909-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f909-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f909-107">Example</span></span>  
 <span data-ttu-id="2f909-108">Poniższy przykład pobiera kolekcję nagłówka z `My.Request` obiektu i `My.Response` używa obiektu do zapisania go na stronie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2f909-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2f909-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f909-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="2f909-110">My.Response, obiekt</span><span class="sxs-lookup"><span data-stu-id="2f909-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
