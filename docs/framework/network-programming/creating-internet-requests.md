---
title: "Tworzenie żądania internetowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 52f1fc2601aca9b4d823d42ed961fcf007e5e5ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-internet-requests"></a><span data-ttu-id="e89a6-102">Tworzenie żądania internetowe</span><span class="sxs-lookup"><span data-stu-id="e89a6-102">Creating Internet Requests</span></span>
<span data-ttu-id="e89a6-103">Tworzenie aplikacji <xref:System.Net.WebRequest> wystąpienia za pośrednictwem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e89a6-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e89a6-104">To jest metodą statyczną, która tworzy klasę pochodzącą od **WebRequest** oparte na schemat identyfikatora URI przekazywania.</span><span class="sxs-lookup"><span data-stu-id="e89a6-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="e89a6-105">Sieci Web, plików i żądań FTP</span><span class="sxs-lookup"><span data-stu-id="e89a6-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="e89a6-106">Platforma .NET Framework zapewnia <xref:System.Net.HttpWebRequest> klasy, która jest pochodną **WebRequest**, do obsługi żądań HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e89a6-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="e89a6-107">W większości przypadków **WebRequest** klasy zawiera wszystkie właściwości, musisz wysłać żądanie; jednak, w razie potrzeby można rzutować **WebRequest** obiekty utworzone przez **WebRequest.Create**  metodę **HttpWebRequest** typ, aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP żądania.</span><span class="sxs-lookup"><span data-stu-id="e89a6-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="e89a6-108">Podobnie **HttpWebResponse** obiektu obsługuje odpowiedzi z żądań HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e89a6-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="e89a6-109">Aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP **HttpWebResponse** obiektu, należy rzutować **WebResponse** obiekty do **HttpWebResponse** typu.</span><span class="sxs-lookup"><span data-stu-id="e89a6-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="e89a6-110">.NET Framework są także <xref:System.Net.FileWebRequest> i <xref:System.Net.FileWebResponse> klasy do obsługi żądań zasobów, które używają "plików:" schemat identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="e89a6-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="e89a6-111">Podobnie <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy są dostarczane do obsługi żądań zasobów, które używają "ftp:" schematu.</span><span class="sxs-lookup"><span data-stu-id="e89a6-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="e89a6-112">Jeśli żądanie dotyczy z zasobem, który wykorzystuje dowolne z tych systemów, możesz użyć **WebRequest.Create** metodę, aby uzyskać obiekt, z którym z żądania.</span><span class="sxs-lookup"><span data-stu-id="e89a6-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="e89a6-113">Do obsługi żądań, które używają inne protokoły poziomu aplikacji, musisz wdrożyć pochodzi od klasy oparte na protokole **WebRequest** i **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="e89a6-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="e89a6-114">Aby uzyskać więcej informacji, zobacz [programowania podłączany protokołów](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="e89a6-114">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89a6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e89a6-115">See Also</span></span>  
 [<span data-ttu-id="e89a6-116">Porady: dane przy użyciu klasy WebRequest żądania</span><span class="sxs-lookup"><span data-stu-id="e89a6-116">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [<span data-ttu-id="e89a6-117">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="e89a6-117">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
