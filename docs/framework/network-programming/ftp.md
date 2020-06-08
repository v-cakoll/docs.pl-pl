---
title: FTP — .NET
description: Zapoznaj się z kompleksową pomocą techniczną protokołu FTP, który zapewnia .NET Framework przy użyciu klas FtpWebRequest i FtpWebResponse.
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d21ca43cd1041df358dc5e2add9560fb33e85d83
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502590"
---
# <a name="ftp"></a>FTP

.NET Framework zapewnia kompleksową pomoc techniczną dla protokołu FTP z <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> klasami i. Te klasy pochodzą z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> . W większości przypadków <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> klasy i zapewniają wszystko, co jest niezbędne do wykonania żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu FTP uwidocznionych jako właściwości, można rzutowanie te klasy do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse> .

## <a name="examples"></a>Przykłady

Aby uzyskać więcej informacji, zobacz następujące tematy: [instrukcje: pobieranie plików przy użyciu protokołu FTP](how-to-download-files-with-ftp.md), [instrukcje: przekazywanie plików przy użyciu protokołu FTP](how-to-upload-files-with-ftp.md)i [instrukcje: wyświetlanie zawartości katalogu przy użyciu protokołu FTP](how-to-list-directory-contents-with-ftp.md).

## <a name="ftp-and-proxies"></a>FTP i serwery proxy

Jeśli serwer proxy (określony przez <xref:System.Net.FtpWebRequest.Proxy%2A> Właściwość) jest serwerem proxy HTTP, <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> obsługiwane są tylko polecenia, i.

## <a name="see-also"></a>Zobacz także

- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
