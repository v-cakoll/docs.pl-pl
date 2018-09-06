---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e5dc6ee0f2c832e3274a1e58808acfdb56ae804c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862981"
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
