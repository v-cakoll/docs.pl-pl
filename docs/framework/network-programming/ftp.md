---
title: FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d7b169a6de494d10fa332ebf5f2aa315ae69653a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ftp"></a>FTP
.NET Framework zapewnia kompleksowe obsługę protokołu FTP z <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy. Te klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>. W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy udostępniają wszystkie, które są niezbędne do wysłania żądania, ale jeśli potrzebny jest dostęp do funkcji specyficznych dla FTP udostępniony jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Przykłady  
 Aby uzyskać więcej informacji, zobacz następujące tematy: [porady: pobieranie plików przy użyciu FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [jak: przekazywanie plików przy użyciu FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), i [jak: listy zawartości katalogu przy użyciu FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP i serwerów proxy  
 Jeśli serwer proxy (określonego przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwości) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do Internetu za pośrednictwem serwera Proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Przykłady programowania w języku sieci](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykładowe technologii klienta FTP](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [Przykładowy technologii Eksplorator FTP](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [Przy użyciu protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
