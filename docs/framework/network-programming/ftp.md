---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: 0f35cb5c106d041a771d17a6e528cbbc1d38042b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187676"
---
# <a name="ftp"></a>FTP
Program .NET Framework oferuje kompleksowe wsparcie dla protokołu FTP za pomocą <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy. Te klasy są uzyskiwane z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>. W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zapewniają wszystko, co jest niezbędne do utworzenia żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu FTP, widoczne jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Przykłady  
 Aby uzyskać więcej informacji, zobacz następujące tematy: [porady: pobieranie plików przy użyciu protokołu FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [jak: Przekaż pliki przy użyciu protokołu FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), i [porady: wyświetlanie zawartości katalogu przy użyciu protokołu FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP i serwerów proxy  
 Jeśli serwer proxy (określony przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwość) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykład technologii klienta FTP](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [Przykład technologii FTP Explorer](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
