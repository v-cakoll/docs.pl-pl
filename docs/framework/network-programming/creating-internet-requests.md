---
title: Tworzenie żądań internetowych
description: Dowiedz się, jak aplikacje tworzą wystąpienia WebRequest za pośrednictwem WebRequest. Create, metoda statyczna, która tworzy klasę pochodną opartą na schemacie URI przekazaną do niego.
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
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502629"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="84930-103">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="84930-103">Creating Internet Requests</span></span>
<span data-ttu-id="84930-104">Aplikacje tworzą <xref:System.Net.WebRequest> wystąpienia za pomocą <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="84930-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84930-105">Jest to metoda statyczna, która tworzy klasę pochodną od **żądania WebRequest** na podstawie schematu identyfikatora URI, do którego został przesłany.</span><span class="sxs-lookup"><span data-stu-id="84930-105">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="84930-106">Żądania sieci Web, plików i FTP</span><span class="sxs-lookup"><span data-stu-id="84930-106">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="84930-107">.NET Framework dostarcza <xref:System.Net.HttpWebRequest> klasę, która pochodzi od **żądania WebRequest**, do obsługi żądań HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="84930-107">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="84930-108">W większości przypadków Klasa **WebRequest** zawiera wszystkie właściwości potrzebne do zgłoszenia żądania. Jednak w razie potrzeby można rzutować obiekty **WebRequest** utworzone przez metodę **WebRequest. Create** na typ **HttpWebRequest** , aby uzyskać dostęp do właściwości żądania specyficznego dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="84930-108">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="84930-109">Podobnie obiekt **HttpWebResponse** obsługuje odpowiedzi z żądań HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="84930-109">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="84930-110">Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP obiektu **HttpWebResponse** , należy rzutować obiekty **WebResponse** na typ **HttpWebResponse** .</span><span class="sxs-lookup"><span data-stu-id="84930-110">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="84930-111">.NET Framework udostępnia również <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> klasy i obsługujące żądania dla zasobów, które używają schematu identyfikatora URI "File:".</span><span class="sxs-lookup"><span data-stu-id="84930-111">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="84930-112">Podobnie <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> klasy i są udostępniane do obsługi żądań dotyczących zasobów, które używają schematu "FTP:".</span><span class="sxs-lookup"><span data-stu-id="84930-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="84930-113">Jeśli Twoje żądanie dotyczy zasobu korzystającego z dowolnego z tych schematów, można użyć metody **WebRequest. Create** w celu uzyskania obiektu, z którym ma zostać wysłane żądanie.</span><span class="sxs-lookup"><span data-stu-id="84930-113">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="84930-114">Aby obsługiwać żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z **WebRequest** i **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="84930-114">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="84930-115">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="84930-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84930-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84930-116">See also</span></span>

- [<span data-ttu-id="84930-117">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="84930-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="84930-118">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="84930-118">Requesting Data</span></span>](requesting-data.md)
