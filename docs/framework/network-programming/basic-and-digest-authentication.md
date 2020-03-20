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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048900"
---
# <a name="basic-and-digest-authentication"></a>Uwierzytelnianie podstawowe i szyfrowane
Implementacja <xref:System.Net> uwierzytelniania podstawowego i szyfrowego jest zgodna z rfc2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane (dostępne na stronie internetowej [world wide web consortium).](https://www.w3.org)  
  
 Aby użyć uwierzytelniania podstawowego i szyfrowanego, aplikacja <xref:System.Net.WebRequest.Credentials%2A> musi <xref:System.Net.WebRequest> podać nazwę użytkownika i hasło we właściwości obiektu, który używa do żądania danych z Internetu, jak pokazano w poniższym przykładzie.  
  
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
> Dane wysyłane za pomocą uwierzytelniania podstawowego i szyfrowanego nie są szyfrowane, więc dane mogą być widoczne przez przeciwnika. Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane w sposób czysty i mogą zostać przechwycone.  
  
## <a name="see-also"></a>Zobacz też

- [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](ntlm-and-kerberos-authentication.md)
- [Uwierzytelnianie internetowe](internet-authentication.md)
