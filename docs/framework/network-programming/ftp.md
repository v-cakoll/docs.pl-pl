---
title: FTP - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642883"
---
# <a name="ftp"></a>FTP

.NET Framework zapewnia kompleksową obsługę protokołu <xref:System.Net.FtpWebRequest> FTP z i <xref:System.Net.FtpWebResponse> klas. Klasy te pochodzą <xref:System.Net.WebRequest> z <xref:System.Net.WebResponse>i . W większości przypadków <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i klasy zapewniają wszystko, co jest niezbędne do żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych <xref:System.Net.FtpWebRequest> dla <xref:System.Net.FtpWebResponse>FTP udostępniane jako właściwości, można typecast tych klas do lub . .

## <a name="examples"></a>Przykłady

Aby uzyskać więcej informacji, zobacz następujące tematy: [Jak: Pobieranie plików z FTP](how-to-download-files-with-ftp.md), [Jak: Przekazywanie plików z FTP](how-to-upload-files-with-ftp.md)i [Jak: Lista zawartości katalogu z FTP](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP i serwery proxy

Jeśli serwer proxy (określony <xref:System.Net.FtpWebRequest.Proxy%2A> przez właściwość) jest <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>serwerem proxy HTTP, obsługiwane są tylko polecenia , <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> .

## <a name="see-also"></a>Zobacz też

- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
