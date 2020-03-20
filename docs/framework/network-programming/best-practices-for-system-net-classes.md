---
title: Najlepsze rozwiązania dotyczące klas System.Net
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: c7324dcbc27c95c7d799592700d46c195e7d952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048890"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="6d0f0-102">Najlepsze rozwiązania dotyczące klas System.Net</span><span class="sxs-lookup"><span data-stu-id="6d0f0-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="6d0f0-103">Poniższe zalecenia pomogą Ci korzystać <xref:System.Net> z klas zawartych w ich najlepsze korzyści:</span><span class="sxs-lookup"><span data-stu-id="6d0f0-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="6d0f0-104">Aby zapoznać się z najlepszymi rozwiązaniami dotyczących zabezpieczeń warstwy transportu (TLS), zobacz [Najważniejsze wskazówki dotyczące zabezpieczeń warstwy transportu (TLS) w ramach .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="6d0f0-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="6d0f0-105">Użyj <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i, gdy jest to możliwe, zamiast rzutowania typu do klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="6d0f0-106">Aplikacje korzystające z **webrequest** i **WebResponse** mogą korzystać z nowych protokołów internetowych bez konieczności szeroko zakrojonych zmian kodu.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="6d0f0-107">Podczas pisania ASP.NET aplikacji, które działają na serwerze przy użyciu **klas System.Net,** często lepiej jest, z punktu widzenia wydajności, używać metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="6d0f0-108">Liczba połączeń otwartych dla zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepływność.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="6d0f0-109">**System.Net** domyślnie używa dwóch połączeń na aplikację na hosta.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="6d0f0-110">Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwości w <xref:System.Net.ServicePoint> aplikacji może zwiększyć tę liczbę dla określonego hosta.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="6d0f0-111">Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości może zwiększyć tę wartość domyślną dla wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="6d0f0-112">Podczas pisania protokołów na poziomie <xref:System.Net.Sockets.TcpClient> gniazda, spróbuj użyć lub <xref:System.Net.Sockets.UdpClient> w miarę <xref:System.Net.Sockets.Socket>możliwości zamiast pisać bezpośrednio do .</span><span class="sxs-lookup"><span data-stu-id="6d0f0-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="6d0f0-113">Te dwie klasy klienta hermetyzują tworzenie gniazd TCP i UDP bez konieczności obsługi szczegółów połączenia.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="6d0f0-114">Podczas uzyskiwania dostępu do witryn, <xref:System.Net.CredentialCache> które wymagają poświadczeń, należy użyć klasy do utworzenia pamięci podręcznej poświadczeń, a nie dostarczanie im z każdym żądaniem.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="6d0f0-115">**CredentialCache** Klasy przeszukuje pamięci podręcznej, aby znaleźć odpowiednie poświadczenia do przedstawienia z żądaniem, zwalniając użytkownika z odpowiedzialności tworzenia i prezentowania poświadczeń na podstawie adresu URL.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d0f0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d0f0-116">See also</span></span>

- [<span data-ttu-id="6d0f0-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6d0f0-117">Network Programming in the .NET Framework</span></span>](index.md)
