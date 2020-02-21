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
# <a name="encryption-and-network-security"></a>Szyfrowanie i zabezpieczenia sieci

Model zabezpieczeń sieci dla Windows Communication Foundation (WCF) jest obszerny i skomplikowany. Obejmuje to zabezpieczenia na poziomie transportu przy użyciu protokołu HTTPS lub TLS-over-TCP oraz zabezpieczeń na poziomie komunikatów przy użyciu specyfikacji WS-Security do szyfrowania poszczególnych komunikatów.

gRPC pozostawia zabezpieczenia sieciowe do podstawowego protokołu HTTP/2, który można zabezpieczyć przy użyciu certyfikatów TLS.

Przeglądarki sieci Web Niemniej korzystają z połączeń TLS dla protokołu HTTP/2, ale większość klientów programistycznych, w tym. `HttpClient`sieci, mogą używać protokołu HTTP/2 za pośrednictwem nieszyfrowanych połączeń. `HttpClient` domyślnie wymaga szyfrowania, ale można je zastąpić przy użyciu przełącznika <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

W przypadku publicznych interfejsów API należy zawsze używać połączeń TLS i zapewnić prawidłowe certyfikaty dla usług z odpowiedniego urzędu SSL. Usługa [LetsEncrypt](https://letsencrypt.org) oferuje bezpłatne, zautomatyzowane certyfikaty SSL i większość infrastruktury hostingu obecnie obsługuje standard LetsEncrypt z typowymi wtyczkami lub rozszerzeniami.

W przypadku usług wewnętrznych w sieci firmowej należy rozważyć użycie protokołu TLS do zabezpieczenia ruchu sieciowego do i z usług gRPC.

Jeśli konieczne jest użycie jawnej protokołu TLS między usługami działającymi w Kubernetes, należy rozważyć użycie urzędu certyfikacji w klastrze i kontrolera Menedżera certyfikatów, takiego jak [Menedżer](https://docs.cert-manager.io/en/latest/)certyfikatów. Następnie można automatycznie przypisywać certyfikaty do usług w czasie wdrażania.

>[!div class="step-by-step"]
>[Poprzednie](channel-credentials.md)
>[dalej](grpc-in-production.md)
