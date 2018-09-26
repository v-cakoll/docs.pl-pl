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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 987e2294f1e34eb3a4da1e31285868877338ccf4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111675"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="f769d-102">Najlepsze rozwiązania dotyczące klas System.Net</span><span class="sxs-lookup"><span data-stu-id="f769d-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="f769d-103">Poniższe zalecenia pomogą należy używać klas znajdujących się w <xref:System.Net> do ich Najważniejsze zalety:</span><span class="sxs-lookup"><span data-stu-id="f769d-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="f769d-104">Najlepsze rozwiązania dotyczące zabezpieczeń TLS (Transport Layer), zobacz [zabezpieczeń TLS (Transport Layer) najlepszych rozwiązań za pomocą .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="f769d-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="f769d-105">Użyj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> zawsze, gdy jest to możliwe, zamiast rzutowania typu do klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f769d-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="f769d-106">Aplikacje, które używają **WebRequest** i **elementu WebResponse** korzystać z zalet nowe protokoły internetowe bez konieczności wprowadzania zmian w kodzie rozbudowane.</span><span class="sxs-lookup"><span data-stu-id="f769d-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="f769d-107">Podczas pisania aplikacji platformy ASP.NET, korzystających z serwerem za pomocą **przestrzeni nazw System.Net** klas, często lepiej jest, z punktu widzenia wydajności można używać metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="f769d-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="f769d-108">Liczba połączeń otwarty do zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepustowość.</span><span class="sxs-lookup"><span data-stu-id="f769d-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="f769d-109">**Przestrzeni nazw System.Net** domyślnie używa dwóch połączeń dla jednej aplikacji na każdym hoście.</span><span class="sxs-lookup"><span data-stu-id="f769d-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="f769d-110">Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwość <xref:System.Net.ServicePoint> dla aplikacji można zwiększyć tę liczbę dla konkretnego hosta.</span><span class="sxs-lookup"><span data-stu-id="f769d-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="f769d-111">Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości można zwiększyć to ustawienie domyślne dla wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="f769d-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="f769d-112">Podczas pisania protokoły poziomu gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub <xref:System.Net.Sockets.UdpClient> zawsze, gdy jest to możliwe, zamiast zapisywania bezpośrednio do <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="f769d-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="f769d-113">W ramach tych zajęć dwóch klientów hermetyzować Tworzenie gniazda TCP i UDP, bez konieczności obsługi szczegółów połączenia.</span><span class="sxs-lookup"><span data-stu-id="f769d-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="f769d-114">Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń, użyj <xref:System.Net.CredentialCache> klasy w celu utworzenia pamięci podręcznej poświadczeń, a nie dostarczanie każde żądanie.</span><span class="sxs-lookup"><span data-stu-id="f769d-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="f769d-115">**CredentialCache** klasy wyszukuje w pamięci podręcznej, aby znaleźć odpowiednie poświadczenia, aby przedstawić z żądaniem zwalniania należy z odpowiedzialność za tworzenie i prezentowanie poświadczeń opartych na adres URL.</span><span class="sxs-lookup"><span data-stu-id="f769d-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f769d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f769d-116">See Also</span></span>  
 [<span data-ttu-id="f769d-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f769d-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
