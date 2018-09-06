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
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786047"
---
# <a name="ftp"></a><span data-ttu-id="dfaa8-102">FTP</span><span class="sxs-lookup"><span data-stu-id="dfaa8-102">FTP</span></span>
<span data-ttu-id="dfaa8-103">Program .NET Framework oferuje kompleksowe wsparcie dla protokołu FTP za pomocą <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy.</span><span class="sxs-lookup"><span data-stu-id="dfaa8-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="dfaa8-104">Te klasy są uzyskiwane z <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="dfaa8-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="dfaa8-105">W większości przypadków <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zapewniają wszystko, co jest niezbędne do utworzenia żądania, ale jeśli potrzebujesz dostępu do funkcji specyficznych dla protokołu FTP, widoczne jako właściwości, można rzutowanie typu tych klas do <xref:System.Net.FtpWebRequest> lub <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="dfaa8-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dfaa8-106">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dfaa8-106">Examples</span></span>  
 <span data-ttu-id="dfaa8-107">Aby uzyskać więcej informacji, zobacz następujące tematy: [porady: pobieranie plików przy użyciu protokołu FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [jak: Przekaż pliki przy użyciu protokołu FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), i [porady: wyświetlanie zawartości katalogu przy użyciu protokołu FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="dfaa8-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="dfaa8-108">FTP i serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="dfaa8-108">FTP and proxies</span></span>  
 <span data-ttu-id="dfaa8-109">Jeśli serwer proxy (określony przez <xref:System.Net.FtpWebRequest.Proxy%2A> właściwość) jest serwer proxy HTTP tylko <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, i <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> polecenia są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dfaa8-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfaa8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfaa8-110">See Also</span></span>  
 [<span data-ttu-id="dfaa8-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="dfaa8-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="dfaa8-112">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="dfaa8-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="dfaa8-113">Przykład technologii klienta FTP</span><span class="sxs-lookup"><span data-stu-id="dfaa8-113">FTP Client Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="dfaa8-114">Przykład technologii FTP Explorer</span><span class="sxs-lookup"><span data-stu-id="dfaa8-114">FTP Explorer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="dfaa8-115">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="dfaa8-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
