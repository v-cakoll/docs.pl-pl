---
title: Uwierzytelnianie podstawowe i szyfrowane
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048900"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="c4f80-102">Uwierzytelnianie podstawowe i szyfrowane</span><span class="sxs-lookup"><span data-stu-id="c4f80-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="c4f80-103"><xref:System.Net> Implementacja uwierzytelniania podstawowego i szyfrowanego jest zgodna z RFC2617 — uwierzytelnianie http: Uwierzytelnianie podstawowe i szyfrowane (dostępne w witrynie sieci Web [organizacja World Wide Web Consortium](https://www.w3.org) ).</span><span class="sxs-lookup"><span data-stu-id="c4f80-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="c4f80-104">Aby można było korzystać z uwierzytelniania podstawowego i szyfrowanego, aplikacja musi podać nazwę użytkownika i hasło we <xref:System.Net.WebRequest.Credentials%2A> właściwości <xref:System.Net.WebRequest> obiektu, którego używa do żądania danych z Internetu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4f80-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
> <span data-ttu-id="c4f80-105">Dane wysyłane z uwierzytelnianiem podstawowym i szyfrowanym nie są szyfrowane, więc dane mogą być widoczne przez atakującej.</span><span class="sxs-lookup"><span data-stu-id="c4f80-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="c4f80-106">Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane w postaci jasnej i mogą być przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="c4f80-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f80-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4f80-107">See also</span></span>

- [<span data-ttu-id="c4f80-108">Uwierzytelnianie NTLM i uwierzytelnianie Kerberos</span><span class="sxs-lookup"><span data-stu-id="c4f80-108">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="c4f80-109">Uwierzytelnianie internetowe</span><span class="sxs-lookup"><span data-stu-id="c4f80-109">Internet Authentication</span></span>](internet-authentication.md)
