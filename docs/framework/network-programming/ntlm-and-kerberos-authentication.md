---
title: Uwierzytelnianie NTLM i uwierzytelniania Kerberos
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
ms.openlocfilehash: 254ffea79612c10f147984dda37d0117edbf9e3e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190297"
---
# <a name="ntlm-and-kerberos-authentication"></a>Uwierzytelnianie NTLM i uwierzytelniania Kerberos
Domyślne uwierzytelnianie NTLM i uwierzytelnianie Kerberos należy użyć poświadczeń użytkownika systemu Microsoft Windows NT, które są skojarzone z aplikacji wywołującej prób uwierzytelniania z serwerem. Korzystając z uwierzytelniania NTLM innych niż domyślne, aplikacja ustawia typ uwierzytelniania NTLM i używa <xref:System.Net.NetworkCredential> obiekt, aby przekazać nazwę użytkownika, hasło i domenę na hoście, jak pokazano w poniższym przykładzie.  
  
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
  
 Aplikacje, które muszą połączyć się z usługami Internet przy użyciu poświadczeń użytkownika aplikacji to zrobić przy użyciu poświadczeń domyślnych użytkownika, jak pokazano w poniższym przykładzie.  
  
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
  
 Moduł uwierzytelniania negotiate Określa, czy serwer zdalny używa uwierzytelniania NTLM i Kerberos i wysyła właściwą odpowiedź.  
  
> [!NOTE]
>  Uwierzytelnianie NTLM nie działa za pośrednictwem serwera proxy.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwierzytelnianie podstawowe i szyfrowane](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Uwierzytelnianie internetowe](../../../docs/framework/network-programming/internet-authentication.md)
