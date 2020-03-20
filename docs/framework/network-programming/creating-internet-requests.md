---
title: Tworzenie żądań internetowych
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048620"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="09b56-102">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="09b56-102">Creating Internet Requests</span></span>
<span data-ttu-id="09b56-103">Aplikacje <xref:System.Net.WebRequest> tworzą wystąpienia <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="09b56-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09b56-104">Jest to metoda statyczna, która tworzy klasę pochodną **WebRequest** na podstawie schematu URI przekazany do niego.</span><span class="sxs-lookup"><span data-stu-id="09b56-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="09b56-105">Żądania sieci Web, plików i FTP</span><span class="sxs-lookup"><span data-stu-id="09b56-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="09b56-106">.NET Framework udostępnia <xref:System.Net.HttpWebRequest> klasę, która jest pochodną **WebRequest**, do obsługi żądań HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="09b56-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="09b56-107">W większości przypadków **WebRequest** klasa zapewnia wszystkie właściwości potrzebne do żądania; jednak w razie potrzeby można rzutować **WebRequest** obiektów utworzonych przez **WebRequest.Create** metody do **HttpWebRequest** typu dostępu do właściwości specyficznych dla protokołu HTTP żądania.</span><span class="sxs-lookup"><span data-stu-id="09b56-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="09b56-108">Podobnie obiekt **HttpWebResponse** obsługuje odpowiedzi z żądań HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="09b56-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="09b56-109">Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP **HttpWebResponse** obiektu, należy rzutować **WebResponse** obiektów do **httpWebResponse** typu.</span><span class="sxs-lookup"><span data-stu-id="09b56-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="09b56-110">.NET Framework udostępnia <xref:System.Net.FileWebRequest> również <xref:System.Net.FileWebResponse> i klasy do obsługi żądań dla zasobów, które używają schematu URI "file:".</span><span class="sxs-lookup"><span data-stu-id="09b56-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="09b56-111">Podobnie <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy są dostarczane do obsługi żądań dla zasobów, które używają schematu "ftp:".</span><span class="sxs-lookup"><span data-stu-id="09b56-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="09b56-112">Jeśli żądanie dotyczy zasobu, który używa dowolnego z tych schematów, można użyć **WebRequest.Create** metody, aby uzyskać obiekt, za pomocą którego można złożyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="09b56-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="09b56-113">Aby obsłużyć żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z **WebRequest** i **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="09b56-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="09b56-114">Aby uzyskać więcej informacji, zobacz [Programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="09b56-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b56-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09b56-115">See also</span></span>

- [<span data-ttu-id="09b56-116">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="09b56-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="09b56-117">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="09b56-117">Requesting Data</span></span>](requesting-data.md)
