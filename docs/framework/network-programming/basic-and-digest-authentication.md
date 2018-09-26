---
title: Podstawowe i uwierzytelnianie szyfrowane
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 66b20c299252ff1f218a8131758e2cf03640aac6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090100"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="c2313-102">Podstawowe i uwierzytelnianie szyfrowane</span><span class="sxs-lookup"><span data-stu-id="c2313-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="c2313-103"><xref:System.Net> Wdrożenia podstawowe i uwierzytelnianie szyfrowane jest zgodny z RFC2617 — uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane (dostępne w witrynie sieci Web konsorcjum World Wide Web, pod www.w3.org).</span><span class="sxs-lookup"><span data-stu-id="c2313-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the World Wide Web Consortium's Web site at www.w3.org).</span></span>  
  
 <span data-ttu-id="c2313-104">Aby użyć podstawowa i uwierzytelnianie szyfrowane, aplikacji należy podać nazwę użytkownika i hasło w <xref:System.Net.WebRequest.Credentials%2A> właściwość <xref:System.Net.WebRequest> obiektu, który używa żądanie danych z Internetu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c2313-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="c2313-105">Wysyłane podstawowe i uwierzytelnianie szyfrowane dane nie są szyfrowane, dzięki czemu dane są widoczne przez osobę atakującą.</span><span class="sxs-lookup"><span data-stu-id="c2313-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="c2313-106">Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane jako niezaszyfrowane i mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="c2313-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2313-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2313-107">See Also</span></span>  
 [<span data-ttu-id="c2313-108">Uwierzytelnianie NTLM i uwierzytelnianie Kerberos</span><span class="sxs-lookup"><span data-stu-id="c2313-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [<span data-ttu-id="c2313-109">Uwierzytelnianie internetowe</span><span class="sxs-lookup"><span data-stu-id="c2313-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
