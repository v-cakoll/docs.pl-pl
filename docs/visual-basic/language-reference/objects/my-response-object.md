---
title: My.Response — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 2f72f493d99c1e0b0469150c041649486e5ed124
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794995"
---
# <a name="myresponse-object"></a>My.Response — Obiekt
Pobiera <xref:System.Web.HttpResponse> obiekt skojarzony z <xref:System.Web.UI.Page>. Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje dotyczące tej odpowiedzi.  
  
## <a name="remarks"></a>Uwagi  
 `My.Response` Obiekt zawiera bieżącą <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną.  
  
 `My.Response` Obiektu jest dostępna tylko dla [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i zastosowań `My.Response` obiektu do zapisania go do strony ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Web.HttpResponse>
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
