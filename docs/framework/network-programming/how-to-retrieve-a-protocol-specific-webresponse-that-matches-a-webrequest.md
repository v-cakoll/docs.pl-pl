---
title: 'Instrukcje: Pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 3b3b523d6248b3c61a0994728b035bc6f02d5cf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745353"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Instrukcje: Pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest
W tym przykładzie pokazano, jak można pobrać elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest.  
  
## <a name="example"></a>Przykład  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
