---
title: Protokoły WS-* — gRPC dla deweloperów WCF
description: Przegląd protokołów WS-* obsługiwanych przez funkcję WCF i alternatywy dostępne dla gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c8c06a5e23a4d7859165e1c562032055d63d76f7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503297"
---
# <a name="ws--protocols"></a>Protokoły WS-\*

Jedną z rzeczywistych zalet pracy z programem Windows Communication Foundation (WCF) była obsługa wielu istniejących protokołów _WS-\*_ Standard. W tej sekcji zawarto krótko zależą od tego, jak gRPC zarządza tymi samymi protokołami WS-\*, i omówić dostępne opcje, gdy nie ma żadnych alternatyw.

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>Wymiana metadanych: WS-Policy, WS-Discovery itd.

Usługi SOAP udostępniają dokumenty schematu Web Services Description Language (WSDL) z informacjami, takimi jak formaty danych, operacje lub opcje komunikacji. Ten schemat służy do generowania kodu klienta.

gRPC działa najlepiej, gdy serwery i klienci są generowane na podstawie tych samych `.proto` plików, ale opcjonalne rozszerzenie odbicia serwera zapewnia sposób udostępniania informacji dynamicznych z działającego serwera. Aby uzyskać więcej informacji, zobacz pakiet NuGet [GRPC. odbicie](https://nuget.org/packages/Grpc.Reflection) oraz artykuł dotyczący [odbicia serwera GRPC C# ](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

Protokół WS-Discovery służy do lokalizowania usług w sieci lokalnej. usługi gRPC Services zazwyczaj znajdują się w systemie DNS lub rejestrze usługi, takim jak Consul lub dozorcy.

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>Zabezpieczenia: WS-Security, WS-Federation, szyfrowanie XML i tak dalej

Zabezpieczenia, uwierzytelnianie i autoryzacja zostały omówione bardziej szczegółowo w [rozdziale 6](security.md). Jednak warto zauważyć, że w przeciwieństwie do WCF, gRPC nie obsługuje szyfrowania WS-Security, WS-Federation ani XML. Nawet tak, gRPC zapewnia doskonałe zabezpieczenia. Cały ruch sieciowy gRPC jest szyfrowany automatycznie, gdy używa protokołu HTTP/2 za pośrednictwem protokołu TLS. Certyfikaty x509 można używać do wzajemnego uwierzytelniania klienta/serwera.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC nie zapewnia równoważnej specyfikacji WS-ReliableMessaging. Semantyka ponawiania powinna być obsługiwana w kodzie, prawdopodobnie z biblioteką, taką jak [Polly](https://github.com/App-vNext/Polly). W przypadku korzystania z programu w Kubernetes lub podobnych środowiskach aranżacji [usługi](service-mesh.md) mogą również pomóc w zapewnianiu niezawodnej obsługi komunikatów między usługami.

## <a name="ws-transaction-ws-coordination"></a>WS-Transaction, WS-koordynacyjny

Implementacja transakcji rozproszonych w programie WCF odbywa się przy użyciu Distributed Transaction Coordinator firmy Microsoft (MSDTC). Współpracuje z menedżerami zasobów, które obsługują takie usługi, jak SQL Server, MSMQ lub systemy plików Windows. Nie istnieje jeszcze odpowiednik na świecie współczesnych mikrousług, w części ze względu na szerszy zakres używanych technologii. Aby zapoznać się z omówieniem transakcji, zobacz [dodatek a](appendix.md).

>[!div class="step-by-step"]
>[Poprzednie](error-handling.md)
>[dalej](migrate-wcf-to-grpc.md)
