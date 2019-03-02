---
title: My.Request — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 7a4e292968cf1d30977b8cacdc8f77152e5cc770
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200965"
---
# <a name="myrequest-object"></a>My.Request — Obiekt
Pobiera <xref:System.Web.HttpRequest> obiektu dla żądanej strony.  
  
## <a name="remarks"></a>Uwagi  
 `My.Request` Obiekt zawiera informacje o bieżącym żądaniu HTTP.  
  
 `My.Request` Obiekt jest dostępny tylko w przypadku aplikacji ASP.NET.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera kolekcję nagłówków z `My.Request` obiektu i zastosowań `My.Response` obiektu do zapisania go do strony ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Web.HttpRequest>
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
