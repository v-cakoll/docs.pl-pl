---
title: "My.Response — Obiekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76d0e701107add0d5bd468ba7a829759739e0cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="myresponse-object"></a>My.Response — Obiekt
Pobiera <xref:System.Web.HttpResponse> obiekt skojarzony z <xref:System.Web.UI.Page>. Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje o tej odpowiedzi.  
  
## <a name="remarks"></a>Uwagi  
 `My.Response` Obiektu zawiera bieżącą <xref:System.Web.HttpResponse> obiekt skojarzony ze stroną.  
  
 `My.Response` Obiekt jest dostępny tylko dla [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i używa `My.Response` obiektu do zapisania go do strony ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Web.HttpResponse>  
 [My.Request — obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
