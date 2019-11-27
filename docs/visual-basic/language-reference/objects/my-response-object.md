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
# <a name="myresponse-object"></a>My.Response — Obiekt
Pobiera obiekt <xref:System.Web.HttpResponse> skojarzony z <xref:System.Web.UI.Page>. Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta programu i zawiera informacje o tej odpowiedzi.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.Response` zawiera bieżący obiekt <xref:System.Web.HttpResponse> skojarzony ze stroną.  
  
 Obiekt `My.Response` jest dostępny tylko dla aplikacji ASP.NET.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówka z obiektu `My.Request` i używa obiektu `My.Response`, aby zapisać go na stronie ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Web.HttpResponse>
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
