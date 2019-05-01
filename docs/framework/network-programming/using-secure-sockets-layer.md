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
ms.openlocfilehash: a0af2fa8bbe2efb2dc4fb3d1177c4950dcec87cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796776"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="55d50-102">Używanie protokołu Secure Sockets Layer</span><span class="sxs-lookup"><span data-stu-id="55d50-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="55d50-103"><xref:System.Net> Klasy korzystać protokół Secure Sockets Layer (SSL), aby szyfrować połączenia dla kilku protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="55d50-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="55d50-104">W przypadku połączeń http <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy komunikować się z hostami w sieci web, które obsługują protokół SSL za pomocą protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="55d50-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="55d50-105">W przypadku podjęcia decyzji, które używają protokołu SSL przez <xref:System.Net.WebRequest> klasy, w oparciu o identyfikator URI będzie mieć.</span><span class="sxs-lookup"><span data-stu-id="55d50-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="55d50-106">Jeśli identyfikator URI rozpoczyna się od "https:", jest używany protokół SSL; Jeśli identyfikator URI rozpoczyna się od "http:", jest używany połączenia nieszyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="55d50-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="55d50-107">Aby używać protokołu SSL przy użyciu protokołu FTP (File Transfer), należy ustawić <xref:System.Net.FtpWebRequest.EnableSsl> właściwości na wartość true, przed wywołaniem <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="55d50-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="55d50-108">Podobnie, aby używać protokołu SSL za pomocą transportu protokołu SMTP (Simple Mail), należy ustawić <xref:System.Net.Mail.SmtpClient.EnableSsl> właściwości na wartość true, przed wysłaniem wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="55d50-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="55d50-109"><xref:System.Net.Security.SslStream> Klasa udostępnia strumień abstrakcji dla protokołu SSL i oferuje wiele sposobów konfigurowania uzgadniania protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="55d50-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d50-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="55d50-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="55d50-111">Kod</span><span class="sxs-lookup"><span data-stu-id="55d50-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="55d50-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="55d50-112">Compiling the Code</span></span>  
 <span data-ttu-id="55d50-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="55d50-113">This example requires:</span></span>  
  
- <span data-ttu-id="55d50-114">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="55d50-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d50-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55d50-115">See also</span></span>

- [<span data-ttu-id="55d50-116">Zabezpieczenia w programowaniu sieciowym</span><span class="sxs-lookup"><span data-stu-id="55d50-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
- [<span data-ttu-id="55d50-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="55d50-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="55d50-118">Wybór i sprawdzanie poprawności certyfikatu</span><span class="sxs-lookup"><span data-stu-id="55d50-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
