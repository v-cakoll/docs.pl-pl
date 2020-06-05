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
# <a name="myrequest-object"></a>My.Request — Obiekt
Pobiera <xref:System.Web.HttpRequest> obiekt dla żądanej strony.  
  
## <a name="remarks"></a>Uwagi  
 `My.Request`Obiekt zawiera informacje o bieżącym ŻĄDANIU http.  
  
 `My.Request`Obiekt jest dostępny tylko dla aplikacji ASP.NET.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówka z `My.Request` obiektu i używa `My.Response` obiektu do zapisania go na stronie ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Web.HttpRequest>
- [My.Response — Obiekt](my-response-object.md)
