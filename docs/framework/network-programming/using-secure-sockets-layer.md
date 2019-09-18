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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046901"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="7c132-102">Używanie protokołu Secure Sockets Layer</span><span class="sxs-lookup"><span data-stu-id="7c132-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="7c132-103"><xref:System.Net> Klasy używają SSL (SSL) do szyfrowania połączenia dla kilku protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="7c132-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="7c132-104">W przypadku połączeń <xref:System.Net.WebRequest> http klasy i <xref:System.Net.WebResponse> używają protokołu SSL do komunikowania się z hostami sieci Web, które obsługują protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="7c132-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="7c132-105">Decyzja o użyciu protokołu SSL jest podejmowana przez <xref:System.Net.WebRequest> klasę w oparciu o identyfikator URI, który został podany.</span><span class="sxs-lookup"><span data-stu-id="7c132-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="7c132-106">Jeśli identyfikator URI zaczyna się od ciągu "https:", używany jest protokół SSL. Jeśli identyfikator URI zaczyna się od "http:", używane jest nieszyfrowane połączenie.</span><span class="sxs-lookup"><span data-stu-id="7c132-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="7c132-107">Aby użyć protokołu SSL z protokół transferu plików (FTP), przed <xref:System.Net.FtpWebRequest.EnableSsl> wywołaniem <xref:System.Net.FtpWebRequest.GetResponse>ustaw właściwość na wartość true.</span><span class="sxs-lookup"><span data-stu-id="7c132-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="7c132-108">Podobnie aby użyć protokołu SSL z protokołem SMTP (Simple Mail Transport Protocol), <xref:System.Net.Mail.SmtpClient.EnableSsl> należy ustawić właściwość na wartość true przed wysłaniem wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="7c132-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="7c132-109"><xref:System.Net.Security.SslStream> Klasa zapewnia abstrakcję opartą na strumieniu dla protokołu SSL i oferuje wiele metod konfigurowania uzgadniania SSL.</span><span class="sxs-lookup"><span data-stu-id="7c132-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c132-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c132-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="7c132-111">Kod</span><span class="sxs-lookup"><span data-stu-id="7c132-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c132-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7c132-112">Compiling the Code</span></span>  
 <span data-ttu-id="7c132-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7c132-113">This example requires:</span></span>  
  
- <span data-ttu-id="7c132-114">Odwołania do przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="7c132-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c132-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c132-115">See also</span></span>

- [<span data-ttu-id="7c132-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="7c132-116">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="7c132-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7c132-117">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="7c132-118">Wybór i sprawdzanie poprawności certyfikatu</span><span class="sxs-lookup"><span data-stu-id="7c132-118">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
