---
title: Szyfrowanie i zabezpieczenia sieci — gRPC dla deweloperów WCF
description: Niektóre uwagi dotyczące zabezpieczeń sieci i szyfrowania w programie gRPC
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542774"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="2ab53-103">Szyfrowanie i zabezpieczenia sieci</span><span class="sxs-lookup"><span data-stu-id="2ab53-103">Encryption and network security</span></span>

<span data-ttu-id="2ab53-104">Model zabezpieczeń sieci dla Windows Communication Foundation (WCF) jest obszerny i skomplikowany.</span><span class="sxs-lookup"><span data-stu-id="2ab53-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="2ab53-105">Obejmuje to zabezpieczenia na poziomie transportu przy użyciu protokołu HTTPS lub TLS-over-TCP oraz zabezpieczeń na poziomie komunikatów przy użyciu specyfikacji WS-Security do szyfrowania poszczególnych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="2ab53-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="2ab53-106">gRPC pozostawia zabezpieczenia sieciowe do podstawowego protokołu HTTP/2, który można zabezpieczyć przy użyciu certyfikatów TLS.</span><span class="sxs-lookup"><span data-stu-id="2ab53-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="2ab53-107">Przeglądarki sieci Web Niemniej korzystają z połączeń TLS dla protokołu HTTP/2, ale większość klientów programistycznych, w tym. `HttpClient`sieci, mogą używać protokołu HTTP/2 za pośrednictwem nieszyfrowanych połączeń.</span><span class="sxs-lookup"><span data-stu-id="2ab53-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="2ab53-108">`HttpClient` domyślnie wymaga szyfrowania, ale można je zastąpić przy użyciu przełącznika <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="2ab53-108">`HttpClient` does require encryption by default, but you can override this by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="2ab53-109">W przypadku publicznych interfejsów API należy zawsze używać połączeń TLS i zapewnić prawidłowe certyfikaty dla usług z odpowiedniego urzędu SSL.</span><span class="sxs-lookup"><span data-stu-id="2ab53-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="2ab53-110">Usługa [LetsEncrypt](https://letsencrypt.org) oferuje bezpłatne, zautomatyzowane certyfikaty SSL i większość infrastruktury hostingu obecnie obsługuje standard LetsEncrypt z typowymi wtyczkami lub rozszerzeniami.</span><span class="sxs-lookup"><span data-stu-id="2ab53-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="2ab53-111">W przypadku usług wewnętrznych w sieci firmowej należy rozważyć użycie protokołu TLS do zabezpieczenia ruchu sieciowego do i z usług gRPC.</span><span class="sxs-lookup"><span data-stu-id="2ab53-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="2ab53-112">Jeśli konieczne jest użycie jawnej protokołu TLS między usługami działającymi w Kubernetes, należy rozważyć użycie urzędu certyfikacji w klastrze i kontrolera Menedżera certyfikatów, takiego jak [Menedżer](https://docs.cert-manager.io/en/latest/)certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2ab53-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="2ab53-113">Następnie można automatycznie przypisywać certyfikaty do usług w czasie wdrażania.</span><span class="sxs-lookup"><span data-stu-id="2ab53-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2ab53-114">[Poprzednie](channel-credentials.md)
>[dalej](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="2ab53-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
