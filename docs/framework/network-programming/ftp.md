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
# <a name="ftp"></a><span data-ttu-id="3ac79-102">FTP</span><span class="sxs-lookup"><span data-stu-id="3ac79-102">FTP</span></span>

<span data-ttu-id="3ac79-103">.NET Framework zapewnia kompleksową obsługę protokołu <xref:System.Net.FtpWebRequest> FTP z i <xref:System.Net.FtpWebResponse> klas.</span><span class="sxs-lookup"><span data-stu-id="3ac79-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="3ac79-104">Klasy te pochodzą <xref:System.Net.WebRequest> z <xref:System.Net.WebResponse>i .</span><span class="sxs-lookup"><span data-stu-id="3ac79-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="3ac79-105">W większości przypadków <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i klasy zapewniają wszystko, co jest niezbędne do żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych <xref:System.Net.FtpWebRequest> dla <xref:System.Net.FtpWebResponse>FTP udostępniane jako właściwości, można typecast tych klas do lub . .</span><span class="sxs-lookup"><span data-stu-id="3ac79-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="3ac79-106">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3ac79-106">Examples</span></span>

<span data-ttu-id="3ac79-107">Aby uzyskać więcej informacji, zobacz następujące tematy: [Jak: Pobieranie plików z FTP](how-to-download-files-with-ftp.md), [Jak: Przekazywanie plików z FTP](how-to-upload-files-with-ftp.md)i [Jak: Lista zawartości katalogu z FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="3ac79-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="3ac79-108">FTP i serwery proxy</span><span class="sxs-lookup"><span data-stu-id="3ac79-108">FTP and proxies</span></span>

<span data-ttu-id="3ac79-109">Jeśli serwer proxy (określony <xref:System.Net.FtpWebRequest.Proxy%2A> przez właściwość) jest <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>serwerem proxy HTTP, obsługiwane są tylko polecenia , <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> .</span><span class="sxs-lookup"><span data-stu-id="3ac79-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ac79-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ac79-110">See also</span></span>

- [<span data-ttu-id="3ac79-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="3ac79-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="3ac79-112">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="3ac79-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="3ac79-113">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="3ac79-113">Using Application Protocols</span></span>](using-application-protocols.md)
