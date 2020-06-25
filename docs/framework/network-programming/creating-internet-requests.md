---
title: Tworzenie żądań internetowych
description: Dowiedz się, jak aplikacje tworzą wystąpienia WebRequest za pośrednictwem metody WebRequest. Create, która tworzy klasę pochodną na podstawie przeprowadzonego do niego schematu URI.
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
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325638"
---
# <a name="create-internet-requests"></a><span data-ttu-id="873f3-103">Utwórz żądania internetowe</span><span class="sxs-lookup"><span data-stu-id="873f3-103">Create internet requests</span></span>

<span data-ttu-id="873f3-104">Aplikacje tworzą <xref:System.Net.WebRequest> wystąpienia za pomocą <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="873f3-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="873f3-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>to metoda statyczna, która tworzy klasę pochodną <xref:System.Net.WebRequest> w oparciu o schemat identyfikatora URI, do którego został przesłany.</span><span class="sxs-lookup"><span data-stu-id="873f3-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> is a static method that creates a class derived from <xref:System.Net.WebRequest> based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="873f3-106">Żądania sieci Web, plików i FTP</span><span class="sxs-lookup"><span data-stu-id="873f3-106">Web, file, and FTP requests</span></span>

<span data-ttu-id="873f3-107">.NET Framework udostępnia <xref:System.Net.HttpWebRequest> klasę, która pochodzi od `WebRequest` , do obsługi żądań HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="873f3-107">.NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from `WebRequest`, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="873f3-108">W większości przypadków `WebRequest` Klasa zawiera wszystkie właściwości, które są potrzebne do wykonania żądania. jednak w razie potrzeby można rzutować `WebRequest` obiekty utworzone przez `WebRequest.Create` metodę na `HttpWebRequest` Typ, aby uzyskać dostęp do właściwości żądania specyficznego dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="873f3-108">In most cases, the `WebRequest` class provides all the properties you need to make a request; however, if necessary, you can cast `WebRequest` objects created by the `WebRequest.Create` method to the `HttpWebRequest` type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="873f3-109">Podobnie `HttpWebResponse` obiekt obsługuje odpowiedzi z żądań HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="873f3-109">Similarly, the `HttpWebResponse` object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="873f3-110">Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP `HttpWebResponse` obiektu, należy rzutować `WebResponse` obiekty na `HttpWebResponse` Typ.</span><span class="sxs-lookup"><span data-stu-id="873f3-110">To access the HTTP-specific properties of the `HttpWebResponse` object, you need to cast `WebResponse` objects to the `HttpWebResponse` type.</span></span>  
  
<span data-ttu-id="873f3-111">.NET Framework udostępnia również <xref:System.Net.FileWebRequest> klasy i <xref:System.Net.FileWebResponse> obsługujące żądania dla zasobów, które używają schematu identyfikatora URI "File:".</span><span class="sxs-lookup"><span data-stu-id="873f3-111">.NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="873f3-112">Podobnie <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> klasy i są udostępniane do obsługi żądań dotyczących zasobów, które używają schematu "FTP:".</span><span class="sxs-lookup"><span data-stu-id="873f3-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="873f3-113">Jeśli Twoje żądanie dotyczy zasobu korzystającego z dowolnego z tych schematów, można użyć `WebRequest.Create` metody, aby uzyskać obiekt, z którego ma być wysłane żądanie.</span><span class="sxs-lookup"><span data-stu-id="873f3-113">If your request is for a resource that uses any of these schemes, you can use the `WebRequest.Create` method to obtain an object with which to make your request.</span></span>  
  
<span data-ttu-id="873f3-114">Aby obsługiwać żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z `WebRequest` i `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="873f3-114">To handle requests that use other application-level protocols, implement protocol-specific classes derived from `WebRequest` and `WebResponse`.</span></span> <span data-ttu-id="873f3-115">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="873f3-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873f3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="873f3-116">See also</span></span>

- [<span data-ttu-id="873f3-117">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="873f3-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="873f3-118">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="873f3-118">Requesting Data</span></span>](requesting-data.md)
