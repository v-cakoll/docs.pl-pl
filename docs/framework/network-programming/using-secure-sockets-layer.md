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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135808"
---
# <a name="using-secure-sockets-layer"></a>Używanie protokołu Secure Sockets Layer
<xref:System.Net> Klasy korzystać protokół Secure Sockets Layer (SSL), aby szyfrować połączenia dla kilku protokołów sieciowych.  
  
 W przypadku połączeń http <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy komunikować się z hostami w sieci web, które obsługują protokół SSL za pomocą protokołu SSL. W przypadku podjęcia decyzji, które używają protokołu SSL przez <xref:System.Net.WebRequest> klasy, w oparciu o identyfikator URI będzie mieć. Jeśli identyfikator URI rozpoczyna się od "https:", jest używany protokół SSL; Jeśli identyfikator URI rozpoczyna się od "http:", jest używany połączenia nieszyfrowanego.  
  
 Aby używać protokołu SSL przy użyciu protokołu FTP (File Transfer), należy ustawić <xref:System.Net.FtpWebRequest.EnableSsl> właściwości na wartość true, przed wywołaniem <xref:System.Net.FtpWebRequest.GetResponse>. Podobnie, aby używać protokołu SSL za pomocą transportu protokołu SMTP (Simple Mail), należy ustawić <xref:System.Net.Mail.SmtpClient.EnableSsl> właściwości na wartość true, przed wysłaniem wiadomości e-mail.  
  
 <xref:System.Net.Security.SslStream> Klasa udostępnia strumień abstrakcji dla protokołu SSL i oferuje wiele sposobów konfigurowania uzgadniania protokołu SSL.  
  
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
  
-   Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)
- [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
- [Wybór i sprawdzanie poprawności certyfikatu](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
