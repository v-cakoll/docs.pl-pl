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
---
# <a name="ftp"></a><span data-ttu-id="d13a6-102">FTP</span><span class="sxs-lookup"><span data-stu-id="d13a6-102">FTP</span></span>
<span data-ttu-id="d13a6-103">.NET Framework zapewnia kompleksowe obsługę protokołu FTP z <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy.</span><span class="sxs-lookup"><span data-stu-id="d13a6-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="d13a6-104">Te klasy pochodne <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="d13a6-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="d13a6-105">W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy udostępniają wszystkie, które są niezbędne do wysłania żądania, ale jeśli potrzebny jest dostęp do funkcji specyficznych dla FTP udostępniony jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="d13a6-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d13a6-106">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d13a6-106">Examples</span></span>  
 <span data-ttu-id="d13a6-107">Aby uzyskać więcej informacji, zobacz następujące tematy: [porady: pobieranie plików przy użyciu FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [jak: przekazywanie plików przy użyciu FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), i [jak: listy zawartości katalogu przy użyciu FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="d13a6-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="d13a6-108">FTP i serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="d13a6-108">FTP and proxies</span></span>  
 <span data-ttu-id="d13a6-109">Jeśli serwer proxy (określonego przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwości) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d13a6-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13a6-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d13a6-110">See Also</span></span>  
 [<span data-ttu-id="d13a6-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="d13a6-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="d13a6-112">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="d13a6-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="d13a6-113">Przykładowe technologii klienta FTP</span><span class="sxs-lookup"><span data-stu-id="d13a6-113">FTP Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="d13a6-114">Przykładowy technologii Eksplorator FTP</span><span class="sxs-lookup"><span data-stu-id="d13a6-114">FTP Explorer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="d13a6-115">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="d13a6-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
