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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d1f621af2b365d229b7b5e62069471af98be267a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394390"
---
# <a name="ntlm-and-kerberos-authentication"></a>Uwierzytelnianie NTLM i uwierzytelnianie Kerberos
Domyślne uwierzytelnianie NTLM i uwierzytelnianie Kerberos korzystanie z poświadczeń użytkownika systemu Microsoft Windows NT, skojarzone z aplikacji wywołującej prób uwierzytelniania z serwerem. Podczas korzystania z uwierzytelniania NTLM innych niż domyślne, aplikacja ustawia typ uwierzytelniania NTLM i używa <xref:System.Net.NetworkCredential> obiektu w celu przekazania nazwę użytkownika, hasło i domenę do hosta, jak pokazano w poniższym przykładzie.  
  
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
  
 Aplikacje, które muszą łączyć się przy użyciu poświadczeń użytkownika aplikacji usług Internet zrobić za pomocą poświadczeń domyślnych użytkownika, jak pokazano w poniższym przykładzie.  
  
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
  
 Moduł uwierzytelniania negotiate Określa, czy serwer zdalny jest przy użyciu protokołu NTLM lub Kerberos i wysyła właściwą odpowiedź.  
  
> [!NOTE]
>  Uwierzytelnianie NTLM nie działa za pośrednictwem serwera proxy.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwierzytelnianie podstawowe i szyfrowane](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Uwierzytelnianie internetowe](../../../docs/framework/network-programming/internet-authentication.md)
