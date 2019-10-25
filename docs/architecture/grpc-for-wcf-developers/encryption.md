---
title: Szyfrowanie i zabezpieczenia sieci — gRPC dla deweloperów WCF
description: Niektóre uwagi dotyczące zabezpieczeń sieci i szyfrowania w programie gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 67ee1ffaf00ea0cc6b771ede9f49b6a691af0968
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846674"
---
# <a name="encryption-and-network-security"></a>Szyfrowanie i zabezpieczenia sieci

Model zabezpieczeń sieci WCF jest obszerny i skomplikowany, w tym zabezpieczenia na poziomie transportu za pośrednictwem protokołu HTTPS lub TLS-over-TCP i zabezpieczenia na poziomie komunikatów przy użyciu specyfikacji WS-Security do szyfrowania poszczególnych komunikatów.

gRPC pozostawia zabezpieczone sieci do podstawowego protokołu HTTP/2, który można zabezpieczyć przy użyciu zwykłych certyfikatów TLS.

Przeglądarki sieci Web Niemniej korzystają z połączeń TLS dla protokołu HTTP/2, ale większość klientów programistycznych, w tym. `HttpClient`sieci, mogą używać protokołu HTTP/2 za pośrednictwem nieszyfrowanych połączeń. `HttpClient` *Domyślnie* wymaga szyfrowania, ale można je zastąpić przy użyciu przełącznika <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

W przypadku publicznych interfejsów API należy zawsze używać połączeń TLS i zapewnić prawidłowe certyfikaty dla usług z odpowiedniego urzędu SSL. Usługa [LetsEncrypt](https://letsencrypt.org) oferuje bezpłatne, zautomatyzowane certyfikaty SSL i większość infrastruktury hostingu obecnie obsługuje standard LetsEncrypt z typowymi wtyczkami lub rozszerzeniami.

W przypadku usług wewnętrznych w sieci firmowej należy rozważyć użycie protokołu TLS do zabezpieczenia ruchu sieciowego do i z usług gRPC.

Komunikacja między mikrousługami w klastrze, takim jak Kubernetes, lub Docker Swarm, jest ogólnie automatycznie szyfrowana przez warstwę sieciową kontenera, więc implementacja protokołu TLS w usługach działających wyłącznie w takim klastrze nie jest konieczna. Więcej informacji na ten temat znajduje się w sekcji "siatka usług" w następnym rozdziale.

Jeśli konieczne jest użycie jawnej protokołu TLS między usługami działającymi w Kubernetes, należy rozważyć użycie urzędu certyfikacji w klastrze i kontrolera Menedżera certyfikatów, takiego jak [Menedżer](https://docs.cert-manager.io/en/latest/) certyfikatów, do przypisywania automatycznie certyfikatów do usług w czasie wdrażania.

>[!div class="step-by-step"]
>[Poprzedni](channel-credentials.md)
>[Następny](grpc-in-production.md)
