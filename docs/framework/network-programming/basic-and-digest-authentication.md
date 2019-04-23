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
ms.openlocfilehash: 4f70d2aef3bb064a3df9db9c87671040776332a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089825"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="a39ae-102">Uwierzytelnianie podstawowe i szyfrowane</span><span class="sxs-lookup"><span data-stu-id="a39ae-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="a39ae-103"><xref:System.Net> Wdrożenia podstawowe i uwierzytelnianie szyfrowane jest zgodny z RFC2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane (dostępne na [World Wide Web Consortium](https://www.w3.org) witryny sieci Web).</span><span class="sxs-lookup"><span data-stu-id="a39ae-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="a39ae-104">Aby użyć podstawowa i uwierzytelnianie szyfrowane, aplikacji należy podać nazwę użytkownika i hasło w <xref:System.Net.WebRequest.Credentials%2A> właściwość <xref:System.Net.WebRequest> obiektu, który używa żądanie danych z Internetu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a39ae-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="a39ae-105">Wysyłane podstawowe i uwierzytelnianie szyfrowane dane nie są szyfrowane, dzięki czemu dane są widoczne przez osobę atakującą.</span><span class="sxs-lookup"><span data-stu-id="a39ae-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="a39ae-106">Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane jako niezaszyfrowane i mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="a39ae-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39ae-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a39ae-107">See also</span></span>

- [<span data-ttu-id="a39ae-108">Uwierzytelnianie NTLM i uwierzytelnianie Kerberos</span><span class="sxs-lookup"><span data-stu-id="a39ae-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="a39ae-109">Uwierzytelnianie internetowe</span><span class="sxs-lookup"><span data-stu-id="a39ae-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
