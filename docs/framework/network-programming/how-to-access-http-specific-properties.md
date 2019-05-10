---
title: 'Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 044a48aaffbd2d4ef490405a65236b17ecca1fbf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645811"
---
# <a name="how-to-access-http-specific-properties"></a>Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP
W tym przykładzie pokazano, jak wyłączyć HTTP **Keep-alive** zachowanie i Pobierz wersję protokołu numer z serwera sieci Web.  
  
## <a name="example"></a>Przykład  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =   
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
- [HTTP](../../../docs/framework/network-programming/http.md)
