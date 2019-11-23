---
title: Szyfrowanie i zabezpieczenia sieci — gRPC dla deweloperów WCF
description: Niektóre uwagi dotyczące zabezpieczeń sieci i szyfrowania w programie gRPC
ms.date: 09/02/2019
ms.openlocfilehash: fd993a2d75e97011c6c92cee02c24c5358a211ad
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967777"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="f5b80-103">Szyfrowanie i zabezpieczenia sieci</span><span class="sxs-lookup"><span data-stu-id="f5b80-103">Encryption and network security</span></span>

<span data-ttu-id="f5b80-104">Model zabezpieczeń sieci WCF jest obszerny i skomplikowany, w tym zabezpieczenia na poziomie transportu za pośrednictwem protokołu HTTPS lub TLS-over-TCP i zabezpieczenia na poziomie komunikatów przy użyciu specyfikacji WS-Security do szyfrowania poszczególnych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f5b80-104">WCF's network security model is extensive and complex, including transport-level security using HTTPS or TLS-over-TCP, and message-level security using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="f5b80-105">gRPC pozostawia zabezpieczone sieci do podstawowego protokołu HTTP/2, który można zabezpieczyć przy użyciu zwykłych certyfikatów TLS.</span><span class="sxs-lookup"><span data-stu-id="f5b80-105">gRPC leaves secure networking to the underlying HTTP/2 protocol, which can be secured using regular TLS certificates.</span></span>

<span data-ttu-id="f5b80-106">Przeglądarki sieci Web Niemniej korzystają z połączeń TLS dla protokołu HTTP/2, ale większość klientów programistycznych, w tym. `HttpClient`sieci, mogą używać protokołu HTTP/2 za pośrednictwem nieszyfrowanych połączeń.</span><span class="sxs-lookup"><span data-stu-id="f5b80-106">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="f5b80-107">`HttpClient` *Domyślnie* wymaga szyfrowania, ale można je zastąpić przy użyciu przełącznika <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="f5b80-107">`HttpClient` *does* require encryption by default, but you can override this using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="f5b80-108">W przypadku publicznych interfejsów API należy zawsze używać połączeń TLS i zapewnić prawidłowe certyfikaty dla usług z odpowiedniego urzędu SSL.</span><span class="sxs-lookup"><span data-stu-id="f5b80-108">For public APIs, you should always use TLS connections and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="f5b80-109">Usługa [LetsEncrypt](https://letsencrypt.org) oferuje bezpłatne, zautomatyzowane certyfikaty SSL i większość infrastruktury hostingu obecnie obsługuje standard LetsEncrypt z typowymi wtyczkami lub rozszerzeniami.</span><span class="sxs-lookup"><span data-stu-id="f5b80-109">[LetsEncrypt](https://letsencrypt.org) provide free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="f5b80-110">W przypadku usług wewnętrznych w sieci firmowej należy rozważyć użycie protokołu TLS do zabezpieczenia ruchu sieciowego do i z usług gRPC.</span><span class="sxs-lookup"><span data-stu-id="f5b80-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="f5b80-111">Komunikacja między mikrousługami w klastrze, takim jak Kubernetes, lub Docker Swarm, jest ogólnie automatycznie szyfrowana przez warstwę sieciową kontenera, więc implementacja protokołu TLS w usługach działających wyłącznie w takim klastrze nie jest konieczna.</span><span class="sxs-lookup"><span data-stu-id="f5b80-111">Communication between microservices in a cluster like Kubernetes or Docker Swarm is in general automatically encrypted by the container networking layer, so implementing TLS in services running exclusively in such a cluster isn't necessary.</span></span> <span data-ttu-id="f5b80-112">Więcej informacji na ten temat znajduje się w sekcji "siatka usług" w następnym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="f5b80-112">There will be more on this subject in the "Service Mesh" section of the next chapter.</span></span>

<span data-ttu-id="f5b80-113">Jeśli konieczne jest użycie jawnej protokołu TLS między usługami działającymi w Kubernetes, należy rozważyć użycie urzędu certyfikacji w klastrze i kontrolera Menedżera certyfikatów, takiego jak [Menedżer](https://docs.cert-manager.io/en/latest/) certyfikatów, do przypisywania automatycznie certyfikatów do usług w czasie wdrażania.</span><span class="sxs-lookup"><span data-stu-id="f5b80-113">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster Certificate Authority and a Certificate Manager Controller like [cert-manager](https://docs.cert-manager.io/en/latest/) to assign automatically certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f5b80-114">[Poprzedni](channel-credentials.md)
>[Następny](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="f5b80-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
