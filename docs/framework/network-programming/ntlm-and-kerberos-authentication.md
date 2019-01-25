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
ms.openlocfilehash: 4b93bce3560aaf5e0c888324e74129b5cb62262e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515839"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="cf4e1-102">Uwierzytelnianie NTLM i uwierzytelniania Kerberos</span><span class="sxs-lookup"><span data-stu-id="cf4e1-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="cf4e1-103">Domyślne uwierzytelnianie NTLM i uwierzytelnianie Kerberos należy użyć poświadczeń użytkownika systemu Microsoft Windows NT, które są skojarzone z aplikacji wywołującej prób uwierzytelniania z serwerem.</span><span class="sxs-lookup"><span data-stu-id="cf4e1-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="cf4e1-104">Korzystając z uwierzytelniania NTLM innych niż domyślne, aplikacja ustawia typ uwierzytelniania NTLM i używa <xref:System.Net.NetworkCredential> obiekt, aby przekazać nazwę użytkownika, hasło i domenę na hoście, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf4e1-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="cf4e1-105">Aplikacje, które muszą połączyć się z usługami Internet przy użyciu poświadczeń użytkownika aplikacji to zrobić przy użyciu poświadczeń domyślnych użytkownika, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cf4e1-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="cf4e1-106">Moduł uwierzytelniania negotiate Określa, czy serwer zdalny używa uwierzytelniania NTLM i Kerberos i wysyła właściwą odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="cf4e1-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf4e1-107">Uwierzytelnianie NTLM nie działa za pośrednictwem serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="cf4e1-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4e1-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf4e1-108">See also</span></span>
- [<span data-ttu-id="cf4e1-109">Uwierzytelnianie podstawowe i szyfrowane</span><span class="sxs-lookup"><span data-stu-id="cf4e1-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [<span data-ttu-id="cf4e1-110">Uwierzytelnianie internetowe</span><span class="sxs-lookup"><span data-stu-id="cf4e1-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
