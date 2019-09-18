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
# <a name="using-secure-sockets-layer"></a>Używanie protokołu Secure Sockets Layer
<xref:System.Net> Klasy używają SSL (SSL) do szyfrowania połączenia dla kilku protokołów sieciowych.  
  
 W przypadku połączeń <xref:System.Net.WebRequest> http klasy i <xref:System.Net.WebResponse> używają protokołu SSL do komunikowania się z hostami sieci Web, które obsługują protokół SSL. Decyzja o użyciu protokołu SSL jest podejmowana przez <xref:System.Net.WebRequest> klasę w oparciu o identyfikator URI, który został podany. Jeśli identyfikator URI zaczyna się od ciągu "https:", używany jest protokół SSL. Jeśli identyfikator URI zaczyna się od "http:", używane jest nieszyfrowane połączenie.  
  
 Aby użyć protokołu SSL z protokół transferu plików (FTP), przed <xref:System.Net.FtpWebRequest.EnableSsl> wywołaniem <xref:System.Net.FtpWebRequest.GetResponse>ustaw właściwość na wartość true. Podobnie aby użyć protokołu SSL z protokołem SMTP (Simple Mail Transport Protocol), <xref:System.Net.Mail.SmtpClient.EnableSsl> należy ustawić właściwość na wartość true przed wysłaniem wiadomości e-mail.  
  
 <xref:System.Net.Security.SslStream> Klasa zapewnia abstrakcję opartą na strumieniu dla protokołu SSL i oferuje wiele metod konfigurowania uzgadniania SSL.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do przestrzeni nazw **System.NET** .  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Wybór i sprawdzanie poprawności certyfikatu](certificate-selection-and-validation.md)
