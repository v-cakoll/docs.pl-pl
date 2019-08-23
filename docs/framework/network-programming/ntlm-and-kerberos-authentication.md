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
ms.openlocfilehash: b05cd88fcb492ab27e1d311045b72208167508f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963924"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="e4684-102">Uwierzytelnianie NTLM i uwierzytelnianie Kerberos</span><span class="sxs-lookup"><span data-stu-id="e4684-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="e4684-103">Domyślne uwierzytelnianie NTLM i uwierzytelnianie Kerberos używają poświadczeń użytkownika systemu Microsoft Windows NT skojarzonych z aplikacją wywołującą, aby próbować uwierzytelniać się za pomocą serwera.</span><span class="sxs-lookup"><span data-stu-id="e4684-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="e4684-104">W przypadku korzystania z uwierzytelniania NTLM innego niż domyślne aplikacja ustawia typ uwierzytelniania na NTLM i używa <xref:System.Net.NetworkCredential> obiektu do przekazania nazwy użytkownika, hasła i domeny do hosta, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e4684-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e4684-105">Aplikacje, które muszą łączyć się z usługami internetowymi przy użyciu poświadczeń użytkownika aplikacji, mogą to zrobić przy użyciu poświadczeń domyślnych użytkownika, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e4684-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e4684-106">Moduł uwierzytelnianie negocjowane określa, czy serwer zdalny używa uwierzytelniania NTLM, czy Kerberos, i wysyła odpowiednią odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="e4684-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4684-107">Uwierzytelnianie NTLM nie działa przez serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="e4684-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4684-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4684-108">See also</span></span>

- [<span data-ttu-id="e4684-109">Uwierzytelnianie podstawowe i szyfrowane</span><span class="sxs-lookup"><span data-stu-id="e4684-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [<span data-ttu-id="e4684-110">Uwierzytelnianie internetowe</span><span class="sxs-lookup"><span data-stu-id="e4684-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
