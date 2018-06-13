---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e491754b1c6c96e6afa9b172200cfb564307a8a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395077"
---
# <a name="ftp"></a>FTP
.NET Framework zapewnia kompleksowe obsługę protokołu FTP z <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy. Te klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>. W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy udostępniają wszystkie, które są niezbędne do wysłania żądania, ale jeśli potrzebny jest dostęp do funkcji specyficznych dla FTP udostępniony jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Przykłady  
 Aby uzyskać więcej informacji, zobacz następujące tematy: [porady: pobieranie plików przy użyciu FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [jak: przekazywanie plików przy użyciu FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), i [jak: listy zawartości katalogu przy użyciu FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP i serwerów proxy  
 Jeśli serwer proxy (określonego przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwości) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykładowe technologii klienta FTP](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [Przykładowy technologii Eksplorator FTP](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
