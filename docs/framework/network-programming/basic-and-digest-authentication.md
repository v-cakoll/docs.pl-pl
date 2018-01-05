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
ms.workload: dotnet
ms.openlocfilehash: 7ca66a65c05da3d515358c0fdb26682fa4ec1438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="basic-and-digest-authentication"></a>Podstawowe oraz uwierzytelnianie szyfrowane
<xref:System.Net> Implementacji basic i uwierzytelnianie szyfrowane jest zgodny z RFC2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego (dostępne w witrynie sieci Web konsorcjum World Wide Web pod www.w3.org).  
  
 Podstawowe i uwierzytelnianie szyfrowane, aplikacja musi udostępniać nazwy użytkownika i hasło w <xref:System.Net.WebRequest.Credentials%2A> właściwość <xref:System.Net.WebRequest> obiekt używający żądanie danych z Internetu, jak pokazano w poniższym przykładzie.  
  
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
>  Wysyłane podstawowe i uwierzytelnianie szyfrowane dane nie są szyfrowane, więc dane są widoczne dla atakujący dokonuje. Ponadto podstawowe poświadczenia uwierzytelniania (nazwa użytkownika i hasło) są wysyłane w zwykłym i może zostać przechwycony.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Uwierzytelnianie internetowe](../../../docs/framework/network-programming/internet-authentication.md)
