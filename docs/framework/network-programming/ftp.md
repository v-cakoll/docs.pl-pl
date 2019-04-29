---
title: FTP — .NET
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d945f03077a863d9e1baa6b59fe8a908566aba5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642883"
---
# <a name="ftp"></a>FTP

Program .NET Framework oferuje kompleksowe wsparcie dla protokołu FTP za pomocą <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy. Te klasy są uzyskiwane z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>. W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zapewniają wszystko, co jest niezbędne do utworzenia żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu FTP, widoczne jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.

## <a name="examples"></a>Przykłady

Więcej informacji znajduje się w następujących tematach: [Instrukcje: Pobieranie plików przy użyciu protokołu FTP](how-to-download-files-with-ftp.md), [jak: Przekazywanie plików za pomocą połączenia FTP](how-to-upload-files-with-ftp.md), i [jak: Wyświetlanie zawartości katalogu przy użyciu protokołu FTP](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP i serwerów proxy

Jeśli serwer proxy (określony przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwość) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.

## <a name="see-also"></a>Zobacz także

- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
