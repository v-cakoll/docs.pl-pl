---
title: Jak gRPC podejście RPC-gRPC dla deweloperów WCF
description: Porównanie najważniejszych funkcji usługi WCF z gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 1ebfd102217c9685c5ff5200386c642b2017e98f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968117"
---
# <a name="how-grpc-approaches-rpc"></a>Obsługa zdalnych wywołań procedur przez usługę gRPC

Windows Communication Foundation (WCF) i gRPC są implementacjami wzorca *zdalnego wywołania procedury* (RPC), które mają na celu wykonywanie wywołań do usług uruchomionych na innym komputerze lub w innym procesie, podobnie jak w przypadku wywołania metody w aplikacji klienckiej. Chociaż cele WCF i gRPC są takie same, szczegóły implementacji są zupełnie inne.

W poniższej tabeli opisano, jak kluczowe funkcje WCF odnoszą się do gRPC i gdzie można znaleźć bardziej szczegółowe wyjaśnienia w pozostałej części książki.

| Funkcje | WCF | gRPC |
| -------- | --- | ---- |
| Jakim | Oddzielny kod biznesowy od implementacji sieci | Oddzielny kod biznesowy od definicji interfejsu i implementacji sieci |
| Definiowanie usług i komunikatów (rozdział 3-4)  | Kontrakt usługi, kontrakt operacji i kontrakt danych | Używa pliku proto do deklarowania usług i komunikatów |
| Język (rozdział 3-5) | Kontrakty, C# w których zapisano lub Visual Basic | Język buforowania protokołu |
| Format przewodu (rozdział 3) | Konfigurowalne, w tym SOAP/XML, zwykły kod XML, JSON, dane binarne platformy .NET itd. | Format binarny buforu protokołu (chociaż możliwe jest użycie innych formatów).
| Współdziałanie (rozdział 4) | W przypadku korzystania z protokołu SOAP za pośrednictwem protokołu HTTP | Oficjalne wsparcie: .NET, Java, Python, JavaScript, C/C++, go, Rust, Ruby, Swift, dart, php. Nieoficjalne wsparcie dla innych języków ze społeczności. |
| Sieć (rozdział 4) | Skonfigurowane w czasie wykonywania. Przełączanie między NetTCP, HTTP, MSMQ i tak dalej. | Protokół HTTP/2, obecnie za pośrednictwem protokołu TCP, tylko z ASP.NET Core gRPC. |
| Podejście (rozdział 4) | Generowanie środowiska uruchomieniowego/deserialization serializacji i kodu sieciowego w klasach bazowych | Generowanie czasu kompilacji/deserialization serializacji i kodu sieciowego w klasach bazowych |
| Zabezpieczenia (rozdział 6) | Uwierzytelnianie, zabezpieczenia WS-Security, szyfrowanie komunikatów | Poświadczenia, ASP.NET Core zabezpieczenia, sieci TLS |

>[!div class="step-by-step"]
>[Poprzedni](grpc-overview.md)
>[Następny](interface-definition-language.md)
