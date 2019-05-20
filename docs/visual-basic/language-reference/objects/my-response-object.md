---
title: My.Response — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0e49a3b5732ee1a3626666ce06e366c4940eca05
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881960"
---
# <a name="myresponse-object"></a><span data-ttu-id="80263-102">My.Response — Obiekt</span><span class="sxs-lookup"><span data-stu-id="80263-102">My.Response Object</span></span>
<span data-ttu-id="80263-103">Pobiera <xref:System.Web.HttpResponse> obiekt skojarzony z <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="80263-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="80263-104">Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje dotyczące tej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="80263-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80263-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80263-105">Remarks</span></span>  
 <span data-ttu-id="80263-106">`My.Response` Obiekt zawiera bieżącą <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną.</span><span class="sxs-lookup"><span data-stu-id="80263-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="80263-107">`My.Response` Obiektu jest dostępna tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="80263-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80263-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="80263-108">Example</span></span>  
 <span data-ttu-id="80263-109">Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i zastosowań `My.Response` obiektu do zapisania go do strony ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="80263-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="80263-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80263-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="80263-111">My.Request, obiekt</span><span class="sxs-lookup"><span data-stu-id="80263-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
