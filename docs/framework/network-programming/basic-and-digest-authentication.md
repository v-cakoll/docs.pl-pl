---
title: Podstawowe oraz uwierzytelnianie szyfrowane
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a72635cb77f23e2b87abb54f3f6a4438a3019f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="69e87-102">Podstawowe oraz uwierzytelnianie szyfrowane</span><span class="sxs-lookup"><span data-stu-id="69e87-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="69e87-103"><xref:System.Net> Implementacji basic i uwierzytelnianie szyfrowane jest zgodny z RFC2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego (dostępne w witrynie sieci Web konsorcjum World Wide Web pod www.w3.org).</span><span class="sxs-lookup"><span data-stu-id="69e87-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the World Wide Web Consortium's Web site at www.w3.org).</span></span>  
  
 <span data-ttu-id="69e87-104">Podstawowe i uwierzytelnianie szyfrowane, aplikacja musi udostępniać nazwy użytkownika i hasło w <xref:System.Net.WebRequest.Credentials%2A> właściwość <xref:System.Net.WebRequest> obiekt używający żądanie danych z Internetu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="69e87-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="69e87-105">Wysyłane podstawowe i uwierzytelnianie szyfrowane dane nie są szyfrowane, więc dane są widoczne dla atakujący dokonuje.</span><span class="sxs-lookup"><span data-stu-id="69e87-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="69e87-106">Ponadto podstawowe poświadczenia uwierzytelniania (nazwa użytkownika i hasło) są wysyłane w zwykłym i może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="69e87-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e87-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69e87-107">See Also</span></span>  
 [<span data-ttu-id="69e87-108">Uwierzytelnianie NTLM i uwierzytelnianie Kerberos</span><span class="sxs-lookup"><span data-stu-id="69e87-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [<span data-ttu-id="69e87-109">Uwierzytelnianie Internet</span><span class="sxs-lookup"><span data-stu-id="69e87-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
