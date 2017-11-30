---
title: "Przy użyciu bezpiecznych gniazd warstwy"
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
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b4cdc21b9ecfdb1bb37f26f82200b211967043c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="9f680-102">Przy użyciu bezpiecznych gniazd warstwy</span><span class="sxs-lookup"><span data-stu-id="9f680-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="9f680-103"><xref:System.Net> Klasy użyj protokół Secure Sockets Layer (SSL) do szyfrowania połączenia dla kilku protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="9f680-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="9f680-104">W przypadku połączeń http <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy używają protokołu SSL do komunikowania się z hostami sieci web, które obsługują protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="9f680-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="9f680-105">Decyzja do używania protokołu SSL jest tworzone przez <xref:System.Net.WebRequest> klasy oparte na identyfikator URI jest on podawany.</span><span class="sxs-lookup"><span data-stu-id="9f680-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="9f680-106">Jeśli identyfikator URI, który rozpoczyna się od "https:", używany jest protokół SSL; Jeśli identyfikator URI rozpoczyna się od ciągu "http:", nieszyfrowanego połączenia jest używany.</span><span class="sxs-lookup"><span data-stu-id="9f680-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="9f680-107">Aby używać protokołu SSL z protokołem FTP (File Transfer), ustaw <xref:System.Net.FtpWebRequest.EnableSsl> właściwości na wartość true, przed wywołaniem <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="9f680-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="9f680-108">Podobnie do używania protokołu SSL z transportu protokołu SMTP (Simple Mail), należy ustawić <xref:System.Net.Mail.SmtpClient.EnableSsl> właściwości na wartość true przed wysłaniem wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="9f680-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the e-mail.</span></span>  
  
 <span data-ttu-id="9f680-109"><xref:System.Net.Security.SslStream> Klasy zapewnia abstrakcji strumienia SSL i oferuje wiele sposobów konfigurowania procedury uzgadniania protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="9f680-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f680-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f680-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="9f680-111">Kod</span><span class="sxs-lookup"><span data-stu-id="9f680-111">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f680-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9f680-112">Compiling the Code</span></span>  
 <span data-ttu-id="9f680-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9f680-113">This example requires:</span></span>  
  
-   <span data-ttu-id="9f680-114">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9f680-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f680-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f680-115">See Also</span></span>  
 [<span data-ttu-id="9f680-116">Zabezpieczenia w programowaniu usługi sieciowej</span><span class="sxs-lookup"><span data-stu-id="9f680-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [<span data-ttu-id="9f680-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f680-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="9f680-118">Wybór certyfikatu i sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="9f680-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
