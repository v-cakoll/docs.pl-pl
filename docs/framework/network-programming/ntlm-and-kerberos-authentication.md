---
title: Uwierzytelnianie NTLM i uwierzytelnianie Kerberos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: 372101763bdd84b454e6e2db3ec6cf0ebdf3f991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180698"
---
# <a name="ntlm-and-kerberos-authentication"></a>Uwierzytelnianie NTLM i uwierzytelnianie Kerberos
Domyślne uwierzytelnianie NTLM i uwierzytelnianie Kerberos używają poświadczeń użytkownika systemu Microsoft Windows NT skojarzonych z aplikacją wywołującą w celu podjęcia próby uwierzytelnienia na serwerze. W przypadku korzystania z uwierzytelniania NTLM nie domyślnego, aplikacja ustawia <xref:System.Net.NetworkCredential> typ uwierzytelniania na NTLM i używa obiektu do przekazywania nazwy użytkownika, hasła i domeny do hosta, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 Aplikacje, które muszą łączyć się z usługami internetowymi przy użyciu poświadczeń użytkownika aplikacji, mogą to zrobić za pomocą domyślnych poświadczeń użytkownika, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 Moduł uwierzytelniania negocjacji określa, czy serwer zdalny używa uwierzytelniania NTLM lub Kerberos, i wysyła odpowiednią odpowiedź.  
  
> [!NOTE]
> Uwierzytelnianie NTLM nie działa za pośrednictwem serwera proxy.  
  
## <a name="see-also"></a>Zobacz też

- [Uwierzytelnianie podstawowe i szyfrowane](basic-and-digest-authentication.md)
- [Uwierzytelnianie internetowe](internet-authentication.md)
