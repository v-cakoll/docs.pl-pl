---
title: Używanie protokołu Secure Sockets Layer
ms.date: 03/30/2017
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
ms.openlocfilehash: ef2abc7574aea1b4f77ff93545ad84678c66ce48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046901"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="f88b2-102">Używanie protokołu Secure Sockets Layer</span><span class="sxs-lookup"><span data-stu-id="f88b2-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="f88b2-103">Klasy <xref:System.Net> używają warstwy SSL (Secure Sockets Layer) do szyfrowania połączenia dla kilku protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="f88b2-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="f88b2-104">W przypadku połączeń <xref:System.Net.WebRequest> http <xref:System.Net.WebResponse> i klasy używają protokołu SSL do komunikowania się z hostami internetowymi obsługującymi protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="f88b2-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="f88b2-105">Decyzja o użyciu SSL jest <xref:System.Net.WebRequest> podejmowana przez klasę, na podstawie identyfikatora URI jest podana.</span><span class="sxs-lookup"><span data-stu-id="f88b2-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="f88b2-106">Jeśli identyfikator URI zaczyna się od "https:", używany jest protokół SSL; jeśli identyfikator URI zaczyna się od "http:", używane jest połączenie niezaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="f88b2-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="f88b2-107">Aby użyć protokołu SSL z protokołem <xref:System.Net.FtpWebRequest.EnableSsl> FTP (File <xref:System.Net.FtpWebRequest.GetResponse>Transfer Protocol), ustaw właściwość na true przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="f88b2-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="f88b2-108">Podobnie, aby użyć protokołu SSL z protokołem SMTP (Simple Mail Transport Protocol), należy ustawić właściwość na <xref:System.Net.Mail.SmtpClient.EnableSsl> wartość true przed wysłaniem wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="f88b2-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="f88b2-109">Klasa <xref:System.Net.Security.SslStream> zapewnia abstrakcję opartą na strumieniu dla SSL i oferuje wiele sposobów konfigurowania uzgadniania SSL.</span><span class="sxs-lookup"><span data-stu-id="f88b2-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f88b2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f88b2-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="f88b2-111">Code</span><span class="sxs-lookup"><span data-stu-id="f88b2-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f88b2-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f88b2-112">Compiling the Code</span></span>  
 <span data-ttu-id="f88b2-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f88b2-113">This example requires:</span></span>  
  
- <span data-ttu-id="f88b2-114">Odwołania do **System.Net** obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="f88b2-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f88b2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f88b2-115">See also</span></span>

- [<span data-ttu-id="f88b2-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="f88b2-116">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="f88b2-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f88b2-117">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="f88b2-118">Wybór i sprawdzanie poprawności certyfikatu</span><span class="sxs-lookup"><span data-stu-id="f88b2-118">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
