---
title: Jak gRPC podejście RPC-gRPC dla deweloperów WCF
description: Porównanie najważniejszych funkcji usługi WCF z gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: b924d2f20b54de2d6476a0b27626d5dd7fd0986f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711476"
---
# <a name="how-grpc-approaches-rpc"></a>Obsługa zdalnych wywołań procedur przez usługę gRPC

Windows Communication Foundation (WCF) i gRPC są implementacją wzorca *zdalnego wywołania procedury* (RPC). Ten wzorzec ma na celu nawiązywanie połączeń z usługami uruchomionymi na innym komputerze lub w innym procesie, podobnie jak wywołania metod w aplikacji klienckiej. Chociaż cele WCF i gRPC są takie same, szczegóły implementacji są zupełnie inne.

W poniższej tabeli przedstawiono sposób odnoszący się do programu gRPC i informacje o tym, gdzie znajdują się bardziej szczegółowe wyjaśnienia.

| Funkcje | WCF | gRPC |
| -------- | --- | ---- |
| Jakim | Oddzielny kod biznesowy od implementacji sieci. | Oddzielny kod biznesowy od definicji interfejsu i implementacji sieci. |
| Definiowanie usług i komunikatów (rozdziały 3-4)  | Kontrakt usługi, kontrakt operacji i kontrakt danych. | Używa pliku proto do deklarowania usług i komunikatów. |
| Język (rozdziały 3-5) | Kontrakty, C# w których napisano lub Visual Basic. | Język buforowania protokołu. |
| Format przewodu (rozdział 3) | Konfigurowalne, w tym SOAP/XML, zwykłe dane XML, JSON i dane binarne platformy .NET. | Format binarny buforu protokołu (chociaż możliwe jest użycie innych formatów).
| Współdziałanie (rozdział 4) | W przypadku korzystania z protokołu SOAP za pośrednictwem protokołu HTTP. | Oficjalne wsparcie: .NET, Java, Python, JavaScript, C/C++, go, Rust, Ruby, Swift, dart, php. Nieoficjalne wsparcie dla innych języków ze społeczności. |
| Sieć (rozdział 4) | Skonfigurowane w czasie wykonywania. Przełączanie między NetTCP, HTTP i MSMQ. | Protokół HTTP/2, obecnie za pośrednictwem protokołu TCP, tylko z ASP.NET Core gRPC. |
| Podejście (rozdział 4) | Generowanie kodu serializacji, deserializacji i sieci w środowisku uruchomieniowym w klasach bazowych. | Generowanie w czasie kompilacji serializacji, deserializacji i kodu sieciowego w klasach bazowych. |
| Zabezpieczenia (rozdział 6) | Uwierzytelnianie, WS-Security, szyfrowanie wiadomości. | Poświadczenia, ASP.NET Core zabezpieczenia i sieci TLS. |

>[!div class="step-by-step"]
>[Poprzednie](grpc-overview.md)
>[dalej](interface-definition-language.md)
