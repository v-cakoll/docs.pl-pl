---
title: My. Response — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567452"
---
# <a name="myresponse-object"></a><span data-ttu-id="a95ab-102">My.Response — Obiekt</span><span class="sxs-lookup"><span data-stu-id="a95ab-102">My.Response Object</span></span>
<span data-ttu-id="a95ab-103">Pobiera obiekt skojarzony z <xref:System.Web.UI.Page>. <xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="a95ab-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="a95ab-104">Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta programu i zawiera informacje o tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a95ab-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a95ab-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a95ab-105">Remarks</span></span>  
 <span data-ttu-id="a95ab-106">Obiekt zawiera bieżący <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną. `My.Response`</span><span class="sxs-lookup"><span data-stu-id="a95ab-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="a95ab-107">`My.Response` Obiekt jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a95ab-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a95ab-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a95ab-108">Example</span></span>  
 <span data-ttu-id="a95ab-109">Poniższy przykład pobiera kolekcję nagłówka z `My.Request` obiektu i `My.Response` używa obiektu do zapisania go na stronie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a95ab-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a95ab-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a95ab-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="a95ab-111">My.Request, obiekt</span><span class="sxs-lookup"><span data-stu-id="a95ab-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
