---
title: My.Response — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: d5f49529a2593093a234babc22f64b591ea3cc61
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479815"
---
# <a name="myresponse-object"></a><span data-ttu-id="0b781-102">My.Response — Obiekt</span><span class="sxs-lookup"><span data-stu-id="0b781-102">My.Response Object</span></span>
<span data-ttu-id="0b781-103">Pobiera <xref:System.Web.HttpResponse> obiekt skojarzony z <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="0b781-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="0b781-104">Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje dotyczące tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="0b781-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b781-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b781-105">Remarks</span></span>  
 <span data-ttu-id="0b781-106">`My.Response` Obiekt zawiera bieżącą <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną.</span><span class="sxs-lookup"><span data-stu-id="0b781-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="0b781-107">`My.Response` Obiektu jest dostępna tylko dla [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b781-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b781-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b781-108">Example</span></span>  
 <span data-ttu-id="0b781-109">Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i zastosowań `My.Response` obiektu do zapisania go do strony ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0b781-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="0b781-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b781-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="0b781-111">My.Request, obiekt</span><span class="sxs-lookup"><span data-stu-id="0b781-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
