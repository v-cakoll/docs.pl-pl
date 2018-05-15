---
title: My.Response — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0a907d74112586e7b88c5a0a6f40080455454d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="myresponse-object"></a><span data-ttu-id="6625a-102">My.Response — Obiekt</span><span class="sxs-lookup"><span data-stu-id="6625a-102">My.Response Object</span></span>
<span data-ttu-id="6625a-103">Pobiera <xref:System.Web.HttpResponse> obiekt skojarzony z <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="6625a-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="6625a-104">Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje o tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6625a-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6625a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6625a-105">Remarks</span></span>  
 <span data-ttu-id="6625a-106">`My.Response` Obiektu zawiera bieżącą <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną.</span><span class="sxs-lookup"><span data-stu-id="6625a-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="6625a-107">`My.Response` Obiekt jest dostępny tylko dla [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6625a-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6625a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6625a-108">Example</span></span>  
 <span data-ttu-id="6625a-109">Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i używa `My.Response` obiektu do zapisania go do strony ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6625a-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="6625a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6625a-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="6625a-111">My.Request, obiekt</span><span class="sxs-lookup"><span data-stu-id="6625a-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
