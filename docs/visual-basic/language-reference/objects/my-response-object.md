---
title: My.Response — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350659"
---
# <a name="myresponse-object"></a><span data-ttu-id="7165d-102">My.Response — Obiekt</span><span class="sxs-lookup"><span data-stu-id="7165d-102">My.Response Object</span></span>
<span data-ttu-id="7165d-103">Pobiera obiekt <xref:System.Web.HttpResponse> skojarzony z <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="7165d-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="7165d-104">Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta programu i zawiera informacje o tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7165d-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7165d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7165d-105">Remarks</span></span>  
 <span data-ttu-id="7165d-106">Obiekt `My.Response` zawiera bieżący obiekt <xref:System.Web.HttpResponse> skojarzony ze stroną.</span><span class="sxs-lookup"><span data-stu-id="7165d-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="7165d-107">Obiekt `My.Response` jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7165d-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7165d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7165d-108">Example</span></span>  
 <span data-ttu-id="7165d-109">Poniższy przykład pobiera kolekcję nagłówka z obiektu `My.Request` i używa obiektu `My.Response`, aby zapisać go na stronie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7165d-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7165d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7165d-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="7165d-111">My.Request, obiekt</span><span class="sxs-lookup"><span data-stu-id="7165d-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
