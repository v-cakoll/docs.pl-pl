---
title: My.Request — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372430"
---
# <a name="myrequest-object"></a><span data-ttu-id="677e0-102">My.Request — Obiekt</span><span class="sxs-lookup"><span data-stu-id="677e0-102">My.Request Object</span></span>
<span data-ttu-id="677e0-103">Pobiera <xref:System.Web.HttpRequest> obiekt dla żądanej strony.</span><span class="sxs-lookup"><span data-stu-id="677e0-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677e0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="677e0-104">Remarks</span></span>  
 <span data-ttu-id="677e0-105">`My.Request`Obiekt zawiera informacje o bieżącym ŻĄDANIU http.</span><span class="sxs-lookup"><span data-stu-id="677e0-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="677e0-106">`My.Request`Obiekt jest dostępny tylko dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="677e0-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="677e0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="677e0-107">Example</span></span>  
 <span data-ttu-id="677e0-108">Poniższy przykład pobiera kolekcję nagłówka z `My.Request` obiektu i używa `My.Response` obiektu do zapisania go na stronie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="677e0-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="677e0-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="677e0-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="677e0-110">My.Response — Obiekt</span><span class="sxs-lookup"><span data-stu-id="677e0-110">My.Response Object</span></span>](my-response-object.md)
