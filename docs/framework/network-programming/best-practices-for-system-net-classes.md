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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048890"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="516ef-102">Najlepsze rozwiązania dotyczące klas System.Net</span><span class="sxs-lookup"><span data-stu-id="516ef-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="516ef-103">Poniższe zalecenia ułatwią korzystanie z klas zawartych w programie w <xref:System.Net> celu uzyskania najlepszej korzyści:</span><span class="sxs-lookup"><span data-stu-id="516ef-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="516ef-104">W przypadku najlepszych rozwiązań Transport Layer Security (TLS) zobacz [Transport Layer Security (TLS) Best Practices with .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="516ef-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="516ef-105">Używaj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> wszędzie tam, gdzie to możliwe, zamiast typu rzutowania na klasy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="516ef-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="516ef-106">Aplikacje korzystające z **WebRequest** i **WebResponse** mogą korzystać z nowych protokołów internetowych bez konieczności wprowadzania szczegółowych zmian w kodzie.</span><span class="sxs-lookup"><span data-stu-id="516ef-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="516ef-107">Podczas pisania aplikacji ASP.NET, które działają na serwerze przy użyciu klas **System.NET** , często są one lepsze od punktu widzenia wydajności, aby użyć metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="516ef-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="516ef-108">Liczba połączeń otwartych w ramach zasobu internetowego może mieć znaczny wpływ na wydajność sieci i przepływność.</span><span class="sxs-lookup"><span data-stu-id="516ef-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="516ef-109">**System.NET** domyślnie używa dwóch połączeń dla każdej aplikacji na hosta.</span><span class="sxs-lookup"><span data-stu-id="516ef-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="516ef-110"><xref:System.Net.ServicePoint.ConnectionLimit%2A> Ustawienie właściwości<xref:System.Net.ServicePoint> w aplikacji może zwiększyć ten numer dla określonego hosta.</span><span class="sxs-lookup"><span data-stu-id="516ef-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="516ef-111"><xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> Ustawienie właściwości może zwiększyć wartość domyślną dla wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="516ef-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="516ef-112">Podczas pisania protokołów na poziomie gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub, <xref:System.Net.Sockets.UdpClient> Jeśli to możliwe, zamiast pisać bezpośrednio do. <xref:System.Net.Sockets.Socket></span><span class="sxs-lookup"><span data-stu-id="516ef-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="516ef-113">Te dwie klasy klienckie hermetyzują tworzenie gniazd TCP i UDP bez konieczności obsługi szczegółów połączenia.</span><span class="sxs-lookup"><span data-stu-id="516ef-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="516ef-114">Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń <xref:System.Net.CredentialCache> , należy użyć klasy do utworzenia pamięci podręcznej poświadczeń, a nie dostarczenia ich do każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="516ef-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="516ef-115">Klasa **CredentialCache** przeszukuje pamięć podręczną, aby znaleźć odpowiednie poświadczenia do zaprezentowania z żądaniem, co uwalnia z odpowiedzialności za tworzenie i prezentowanie poświadczeń na podstawie adresu URL.</span><span class="sxs-lookup"><span data-stu-id="516ef-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516ef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="516ef-116">See also</span></span>

- [<span data-ttu-id="516ef-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="516ef-117">Network Programming in the .NET Framework</span></span>](index.md)
