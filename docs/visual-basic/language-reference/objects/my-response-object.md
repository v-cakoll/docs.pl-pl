---
title: My.Response — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372466"
---
# <a name="myresponse-object"></a>My.Response — Obiekt
Pobiera <xref:System.Web.HttpResponse> obiekt skojarzony z <xref:System.Web.UI.Page> . Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta programu i zawiera informacje o tej odpowiedzi.  
  
## <a name="remarks"></a>Uwagi  
 `My.Response`Obiekt zawiera bieżący <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną.  
  
 `My.Response`Obiekt jest dostępny tylko dla aplikacji ASP.NET.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówka z `My.Request` obiektu i używa `My.Response` obiektu do zapisania go na stronie ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Web.HttpResponse>
- [My.Request — Obiekt](my-request-object.md)
