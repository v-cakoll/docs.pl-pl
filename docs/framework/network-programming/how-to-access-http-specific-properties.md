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
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="44b80-102">Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="44b80-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="44b80-103">W tym przykładzie pokazano, jak wyłączyć HTTP **Keep-alive** zachowanie i Pobierz wersję protokołu numer z serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="44b80-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b80-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="44b80-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="44b80-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="44b80-105">Compiling the Code</span></span>  
 <span data-ttu-id="44b80-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="44b80-106">This example requires:</span></span>  
  
- <span data-ttu-id="44b80-107">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="44b80-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b80-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44b80-108">See also</span></span>

- [<span data-ttu-id="44b80-109">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="44b80-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="44b80-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="44b80-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="44b80-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="44b80-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
