---
title: "Najlepsze rozwiązania dotyczące klas System.Net"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 90722abbdb4568be115c0ac77007d5f18984df6f
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2018
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="2273a-102">Najlepsze rozwiązania dotyczące klas System.Net</span><span class="sxs-lookup"><span data-stu-id="2273a-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="2273a-103">Poniższe zalecenia pomogą używać klas zawartych w <xref:System.Net> do ich najważniejsze korzyści:</span><span class="sxs-lookup"><span data-stu-id="2273a-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="2273a-104">Najlepsze rozwiązania zabezpieczeń TLS (Transport Layer), zobacz [zabezpieczeń TLS (Transport Layer) najlepsze rozwiązania z .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="2273a-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="2273a-105">Użyj <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> Jeśli to możliwe, zamiast rzutowanie typów do klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2273a-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="2273a-106">Aplikacje używające **WebRequest** i **WebResponse** można korzystać z nowych protokołów internetowych bez konieczności zmiany szeroką gamę kodu.</span><span class="sxs-lookup"><span data-stu-id="2273a-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="2273a-107">Podczas pisania aplikacji programu ASP.NET, działające na serwerze przy użyciu **System.Net** klas, często jest lepsze z punktu widzenia wydajności, aby użyć metod asynchronicznych dla <xref:System.Net.WebRequest.GetResponse%2A> i <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="2273a-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="2273a-108">Liczba połączeń otwarty do zasobu internetowego może mieć znaczący wpływ na wydajność sieci i przepływności.</span><span class="sxs-lookup"><span data-stu-id="2273a-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="2273a-109">**System.Net** domyślnie używa dwóch połączeń każdej aplikacji na hoście.</span><span class="sxs-lookup"><span data-stu-id="2273a-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="2273a-110">Ustawienie <xref:System.Net.ServicePoint.ConnectionLimit%2A> właściwości w <xref:System.Net.ServicePoint> dla aplikacji można zwiększyć tę liczbę na określonym hoście.</span><span class="sxs-lookup"><span data-stu-id="2273a-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="2273a-111">Ustawienie <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> właściwości można zwiększyć to ustawienie domyślne dla wszystkich hostów.</span><span class="sxs-lookup"><span data-stu-id="2273a-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="2273a-112">Podczas zapisywania protokoły poziomu gniazda, spróbuj użyć <xref:System.Net.Sockets.TcpClient> lub <xref:System.Net.Sockets.UdpClient> Jeśli to możliwe, zamiast bezpośrednio do zapisywania <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="2273a-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="2273a-113">Te klasy klienta dwóch hermetyzować Tworzenie gniazda TCP i UDP bez konieczności obsługi szczegóły połączenia.</span><span class="sxs-lookup"><span data-stu-id="2273a-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="2273a-114">Podczas uzyskiwania dostępu do witryn, które wymagają poświadczeń, użyj <xref:System.Net.CredentialCache> klasy w celu utworzenia pamięci podręcznej poświadczeń, a nie zapewniania kontaktu z każdym żądaniem.</span><span class="sxs-lookup"><span data-stu-id="2273a-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="2273a-115">**CredentialCache** klasy wyszukiwania w pamięci podręcznej, aby znaleźć odpowiednie poświadczenia, aby zaprezentować żądanie, co uwalnia możesz odpowiedzialności tworzenia i prezentowania poświadczeń na podstawie adresu URL.</span><span class="sxs-lookup"><span data-stu-id="2273a-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2273a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2273a-116">See Also</span></span>  
 [<span data-ttu-id="2273a-117">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2273a-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
