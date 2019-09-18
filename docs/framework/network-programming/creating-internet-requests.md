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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048620"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="8807f-102">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="8807f-102">Creating Internet Requests</span></span>
<span data-ttu-id="8807f-103">Aplikacje tworzą <xref:System.Net.WebRequest> wystąpienia <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="8807f-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8807f-104">Jest to metoda statyczna, która tworzy klasę pochodną od **żądania WebRequest** na podstawie schematu identyfikatora URI, do którego został przesłany.</span><span class="sxs-lookup"><span data-stu-id="8807f-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="8807f-105">Żądania sieci Web, plików i FTP</span><span class="sxs-lookup"><span data-stu-id="8807f-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="8807f-106">.NET Framework dostarcza <xref:System.Net.HttpWebRequest> klasę, która pochodzi od **żądania WebRequest**, do obsługi żądań HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="8807f-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="8807f-107">W większości przypadków Klasa **WebRequest** zawiera wszystkie właściwości potrzebne do zgłoszenia żądania. Jednak w razie potrzeby można rzutować obiekty **WebRequest** utworzone przez metodę **WebRequest. Create** na typ **HttpWebRequest** , aby uzyskać dostęp do właściwości żądania specyficznego dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8807f-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="8807f-108">Podobnie obiekt **HttpWebResponse** obsługuje odpowiedzi z żądań HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="8807f-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="8807f-109">Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP obiektu **HttpWebResponse** , należy rzutować obiekty **WebResponse** na typ **HttpWebResponse** .</span><span class="sxs-lookup"><span data-stu-id="8807f-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="8807f-110">.NET Framework udostępnia <xref:System.Net.FileWebRequest> również klasy i <xref:System.Net.FileWebResponse> obsługujące żądania dla zasobów, które używają "plik:" Schemat identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="8807f-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="8807f-111">Podobnie klasy <xref:System.Net.FtpWebResponse> i są udostępniane do obsługi żądań dotyczących zasobów, które używają schematu "FTP:". <xref:System.Net.FtpWebRequest></span><span class="sxs-lookup"><span data-stu-id="8807f-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="8807f-112">Jeśli Twoje żądanie dotyczy zasobu korzystającego z dowolnego z tych schematów, można użyć metody **WebRequest. Create** w celu uzyskania obiektu, z którym ma zostać wysłane żądanie.</span><span class="sxs-lookup"><span data-stu-id="8807f-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="8807f-113">Aby obsługiwać żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z **WebRequest** i **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="8807f-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="8807f-114">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="8807f-114">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8807f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8807f-115">See also</span></span>

- [<span data-ttu-id="8807f-116">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="8807f-116">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="8807f-117">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="8807f-117">Requesting Data</span></span>](requesting-data.md)
