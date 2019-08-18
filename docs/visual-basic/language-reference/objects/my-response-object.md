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
# <a name="myresponse-object"></a>My.Response — Obiekt
Pobiera obiekt skojarzony z <xref:System.Web.UI.Page>. <xref:System.Web.HttpResponse> Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta programu i zawiera informacje o tej odpowiedzi.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt zawiera bieżący <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną. `My.Response`  
  
 `My.Response` Obiekt jest dostępny tylko dla aplikacji ASP.NET.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówka z `My.Request` obiektu i `My.Response` używa obiektu do zapisania go na stronie ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Web.HttpResponse>
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
