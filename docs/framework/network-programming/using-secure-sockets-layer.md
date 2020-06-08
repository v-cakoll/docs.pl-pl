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
# <a name="using-secure-sockets-layer"></a>Używanie protokołu Secure Sockets Layer
<xref:System.Net>Klasy używają SSL (SSL) do szyfrowania połączenia dla kilku protokołów sieciowych.  
  
 W przypadku połączeń HTTP <xref:System.Net.WebRequest> klasy i <xref:System.Net.WebResponse> używają protokołu SSL do komunikowania się z hostami sieci Web, które obsługują protokół SSL. Decyzja o użyciu protokołu SSL jest podejmowana przez <xref:System.Net.WebRequest> klasę w oparciu o identyfikator URI, który został podany. Jeśli identyfikator URI zaczyna się od ciągu "https:", używany jest protokół SSL. Jeśli identyfikator URI zaczyna się od "http:", używane jest nieszyfrowane połączenie.  
  
 Aby użyć protokołu SSL z protokół transferu plików (FTP), <xref:System.Net.FtpWebRequest.EnableSsl> przed wywołaniem ustaw właściwość na wartość true <xref:System.Net.FtpWebRequest.GetResponse> . Podobnie aby użyć protokołu SSL z protokołem SMTP (Simple Mail Transport Protocol), należy ustawić <xref:System.Net.Mail.SmtpClient.EnableSsl> Właściwość na wartość true przed wysłaniem wiadomości e-mail.  
  
 <xref:System.Net.Security.SslStream>Klasa zapewnia abstrakcję opartą na strumieniu dla protokołu SSL i oferuje wiele metod konfigurowania uzgadniania SSL.  
  
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
