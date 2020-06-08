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
# <a name="ftp"></a><span data-ttu-id="a9000-103">FTP</span><span class="sxs-lookup"><span data-stu-id="a9000-103">FTP</span></span>

<span data-ttu-id="a9000-104">.NET Framework zapewnia kompleksową pomoc techniczną dla protokołu FTP z <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> klasami i.</span><span class="sxs-lookup"><span data-stu-id="a9000-104">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="a9000-105">Te klasy pochodzą z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="a9000-105">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="a9000-106">W większości przypadków <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> klasy i zapewniają wszystko, co jest niezbędne do wykonania żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu FTP uwidocznionych jako właściwości, można rzutowanie te klasy do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse> .</span><span class="sxs-lookup"><span data-stu-id="a9000-106">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="a9000-107">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a9000-107">Examples</span></span>

<span data-ttu-id="a9000-108">Aby uzyskać więcej informacji, zobacz następujące tematy: [instrukcje: pobieranie plików przy użyciu protokołu FTP](how-to-download-files-with-ftp.md), [instrukcje: przekazywanie plików przy użyciu protokołu FTP](how-to-upload-files-with-ftp.md)i [instrukcje: wyświetlanie zawartości katalogu przy użyciu protokołu FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="a9000-108">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="a9000-109">FTP i serwery proxy</span><span class="sxs-lookup"><span data-stu-id="a9000-109">FTP and proxies</span></span>

<span data-ttu-id="a9000-110">Jeśli serwer proxy (określony przez <xref:System.Net.FtpWebRequest.Proxy%2A> Właściwość) jest serwerem proxy HTTP, <xref:System.Net.WebRequestMethods.Ftp.DownloadFile> <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> obsługiwane są tylko polecenia, i.</span><span class="sxs-lookup"><span data-stu-id="a9000-110">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9000-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9000-111">See also</span></span>

- [<span data-ttu-id="a9000-112">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a9000-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="a9000-113">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="a9000-113">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="a9000-114">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="a9000-114">Using Application Protocols</span></span>](using-application-protocols.md)
