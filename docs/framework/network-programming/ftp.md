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
# <a name="ftp"></a><span data-ttu-id="39ec7-102">FTP</span><span class="sxs-lookup"><span data-stu-id="39ec7-102">FTP</span></span>

<span data-ttu-id="39ec7-103">Program .NET Framework oferuje kompleksowe wsparcie dla protokołu FTP za pomocą <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy.</span><span class="sxs-lookup"><span data-stu-id="39ec7-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="39ec7-104">Te klasy są uzyskiwane z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="39ec7-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="39ec7-105">W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zapewniają wszystko, co jest niezbędne do utworzenia żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu FTP, widoczne jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="39ec7-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="39ec7-106">Przykłady</span><span class="sxs-lookup"><span data-stu-id="39ec7-106">Examples</span></span>

<span data-ttu-id="39ec7-107">Więcej informacji znajduje się w następujących tematach: [Instrukcje: Pobieranie plików przy użyciu protokołu FTP](how-to-download-files-with-ftp.md), [jak: Przekazywanie plików za pomocą połączenia FTP](how-to-upload-files-with-ftp.md), i [jak: Wyświetlanie zawartości katalogu przy użyciu protokołu FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="39ec7-107">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="39ec7-108">FTP i serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="39ec7-108">FTP and proxies</span></span>

<span data-ttu-id="39ec7-109">Jeśli serwer proxy (określony przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwość) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="39ec7-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="39ec7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39ec7-110">See also</span></span>

- [<span data-ttu-id="39ec7-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="39ec7-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="39ec7-112">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="39ec7-112">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="39ec7-113">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="39ec7-113">Using Application Protocols</span></span>](using-application-protocols.md)
