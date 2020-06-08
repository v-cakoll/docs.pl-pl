---
title: Używanie protokołu Secure Sockets Layer
description: Dowiedz się więcej o tym, jak System.Net i rozszerzające klasy używają SSL do szyfrowania połączenia dla kilku protokołów sieciowych w .NET Framework.
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
ms.openlocfilehash: 67330962382e768849cbf67d5f412ea80f65569d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501992"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="e983c-103">Używanie protokołu Secure Sockets Layer</span><span class="sxs-lookup"><span data-stu-id="e983c-103">Using Secure Sockets Layer</span></span>
<span data-ttu-id="e983c-104"><xref:System.Net>Klasy używają SSL (SSL) do szyfrowania połączenia dla kilku protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="e983c-104">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="e983c-105">W przypadku połączeń HTTP <xref:System.Net.WebRequest> klasy i <xref:System.Net.WebResponse> używają protokołu SSL do komunikowania się z hostami sieci Web, które obsługują protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="e983c-105">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="e983c-106">Decyzja o użyciu protokołu SSL jest podejmowana przez <xref:System.Net.WebRequest> klasę w oparciu o identyfikator URI, który został podany.</span><span class="sxs-lookup"><span data-stu-id="e983c-106">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="e983c-107">Jeśli identyfikator URI zaczyna się od ciągu "https:", używany jest protokół SSL. Jeśli identyfikator URI zaczyna się od "http:", używane jest nieszyfrowane połączenie.</span><span class="sxs-lookup"><span data-stu-id="e983c-107">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="e983c-108">Aby użyć protokołu SSL z protokół transferu plików (FTP), <xref:System.Net.FtpWebRequest.EnableSsl> przed wywołaniem ustaw właściwość na wartość true <xref:System.Net.FtpWebRequest.GetResponse> .</span><span class="sxs-lookup"><span data-stu-id="e983c-108">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="e983c-109">Podobnie aby użyć protokołu SSL z protokołem SMTP (Simple Mail Transport Protocol), należy ustawić <xref:System.Net.Mail.SmtpClient.EnableSsl> Właściwość na wartość true przed wysłaniem wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="e983c-109">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="e983c-110"><xref:System.Net.Security.SslStream>Klasa zapewnia abstrakcję opartą na strumieniu dla protokołu SSL i oferuje wiele metod konfigurowania uzgadniania SSL.</span><span class="sxs-lookup"><span data-stu-id="e983c-110">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e983c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e983c-111">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="e983c-112">Kod</span><span class="sxs-lookup"><span data-stu-id="e983c-112">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e983c-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e983c-113">Compiling the Code</span></span>  
 <span data-ttu-id="e983c-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e983c-114">This example requires:</span></span>  
  
- <span data-ttu-id="e983c-115">Odwołania do przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="e983c-115">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e983c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e983c-116">See also</span></span>

- [<span data-ttu-id="e983c-117">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="e983c-117">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="e983c-118">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e983c-118">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="e983c-119">Wybór i sprawdzanie poprawności certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e983c-119">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
