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
# <a name="using-secure-sockets-layer"></a>Używanie protokołu Secure Sockets Layer
Klasy <xref:System.Net> używają warstwy SSL (Secure Sockets Layer) do szyfrowania połączenia dla kilku protokołów sieciowych.  
  
 W przypadku połączeń <xref:System.Net.WebRequest> http <xref:System.Net.WebResponse> i klasy używają protokołu SSL do komunikowania się z hostami internetowymi obsługującymi protokół SSL. Decyzja o użyciu SSL jest <xref:System.Net.WebRequest> podejmowana przez klasę, na podstawie identyfikatora URI jest podana. Jeśli identyfikator URI zaczyna się od "https:", używany jest protokół SSL; jeśli identyfikator URI zaczyna się od "http:", używane jest połączenie niezaszyfrowane.  
  
 Aby użyć protokołu SSL z protokołem <xref:System.Net.FtpWebRequest.EnableSsl> FTP (File <xref:System.Net.FtpWebRequest.GetResponse>Transfer Protocol), ustaw właściwość na true przed wywołaniem . Podobnie, aby użyć protokołu SSL z protokołem SMTP (Simple Mail Transport Protocol), należy ustawić właściwość na <xref:System.Net.Mail.SmtpClient.EnableSsl> wartość true przed wysłaniem wiadomości e-mail.  
  
 Klasa <xref:System.Net.Security.SslStream> zapewnia abstrakcję opartą na strumieniu dla SSL i oferuje wiele sposobów konfigurowania uzgadniania SSL.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Code  
  
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
  
- Odwołania do **System.Net** obszaru nazw.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Wybór i sprawdzanie poprawności certyfikatu](certificate-selection-and-validation.md)
