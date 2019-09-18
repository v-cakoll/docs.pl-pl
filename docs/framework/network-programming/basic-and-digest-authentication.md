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
# <a name="basic-and-digest-authentication"></a>Uwierzytelnianie podstawowe i szyfrowane
<xref:System.Net> Implementacja uwierzytelniania podstawowego i szyfrowanego jest zgodna z RFC2617 — uwierzytelnianie http: Uwierzytelnianie podstawowe i szyfrowane (dostępne w witrynie sieci Web [organizacja World Wide Web Consortium](https://www.w3.org) ).  
  
 Aby można było korzystać z uwierzytelniania podstawowego i szyfrowanego, aplikacja musi podać nazwę użytkownika i hasło we <xref:System.Net.WebRequest.Credentials%2A> właściwości <xref:System.Net.WebRequest> obiektu, którego używa do żądania danych z Internetu, jak pokazano w poniższym przykładzie.  
  
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
> Dane wysyłane z uwierzytelnianiem podstawowym i szyfrowanym nie są szyfrowane, więc dane mogą być widoczne przez atakującej. Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane w postaci jasnej i mogą być przechwytywane.  
  
## <a name="see-also"></a>Zobacz także

- [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](ntlm-and-kerberos-authentication.md)
- [Uwierzytelnianie internetowe](internet-authentication.md)
