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
ms.openlocfilehash: 2a4915796310e4f6899d833f20bc5260e0ee032b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643130"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="ee99c-102">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="ee99c-102">Creating Internet Requests</span></span>
<span data-ttu-id="ee99c-103">Tworzenie aplikacji <xref:System.Net.WebRequest> wystąpień za pośrednictwem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ee99c-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ee99c-104">Jest to metoda statyczna, który tworzy klasę pochodną **WebRequest** oparte na schemat identyfikatora URI przekazywany do niego.</span><span class="sxs-lookup"><span data-stu-id="ee99c-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="ee99c-105">W sieci Web, plików i żądań FTP</span><span class="sxs-lookup"><span data-stu-id="ee99c-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="ee99c-106">Program .NET Framework oferuje <xref:System.Net.HttpWebRequest> klasy, która jest pochodną **WebRequest**, do obsługi żądań HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ee99c-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="ee99c-107">W większości przypadków **WebRequest** klasa udostępnia wszystkie właściwości, musisz wysłać żądanie; Jednakże, jeśli to konieczne, można rzutować **WebRequest** obiekty utworzone przez **WebRequest.Create**  metody **HttpWebRequest** typ, aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP żądania.</span><span class="sxs-lookup"><span data-stu-id="ee99c-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="ee99c-108">Podobnie **HttpWebResponse** obiektu obsługuje odpowiedzi z żądań HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ee99c-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="ee99c-109">Aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP z **HttpWebResponse** obiektu, należy rzutować **elementu WebResponse** obiekty do **HttpWebResponse** typu.</span><span class="sxs-lookup"><span data-stu-id="ee99c-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="ee99c-110">.NET Framework udostępnia również <xref:System.Net.FileWebRequest> i <xref:System.Net.FileWebResponse> klasy do obsługi żądań zasobów, które używają "plików:" Schemat identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="ee99c-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="ee99c-111">Podobnie <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy są dostarczane do obsługi żądań zasobów, które używają "ftp:" schematu.</span><span class="sxs-lookup"><span data-stu-id="ee99c-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="ee99c-112">Jeśli żądanie jest dla zasobu, który wykorzystuje dowolne z tych systemów, możesz użyć **WebRequest.Create** metody do uzyskiwania obiektu, z którą ma zostać Prześlij żądanie.</span><span class="sxs-lookup"><span data-stu-id="ee99c-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="ee99c-113">Do obsługi żądań, które używają inne protokoły poziomu aplikacji, którą należy wdrożyć klasy pochodne klasy specyficzne dla protokołu **WebRequest** i **elementu WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="ee99c-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="ee99c-114">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="ee99c-114">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee99c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee99c-115">See also</span></span>

- [<span data-ttu-id="ee99c-116">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="ee99c-116">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="ee99c-117">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="ee99c-117">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
