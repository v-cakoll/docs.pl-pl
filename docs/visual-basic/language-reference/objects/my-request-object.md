---
title: My.Request — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 22329bc501c9bb75b1336dd5384ab5b23a98ac21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350677"
---
# <a name="myrequest-object"></a>My.Request — Obiekt
Pobiera obiekt <xref:System.Web.HttpRequest> dla żądanej strony.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.Request` zawiera informacje o bieżącym żądaniu HTTP.  
  
 Obiekt `My.Request` jest dostępny tylko dla aplikacji ASP.NET.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówka z obiektu `My.Request` i używa obiektu `My.Response`, aby zapisać go na stronie ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Web.HttpRequest>
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
