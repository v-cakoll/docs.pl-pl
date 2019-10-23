---
title: Jak gRPC podejście RPC-gRPC dla deweloperów WCF
description: Porównanie najważniejszych funkcji usługi WCF z gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 36d51b96796f274811bfeea64c159afcc9bce301
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770684"
---
# <a name="how-grpc-approaches-rpc"></a>Obsługa zdalnych wywołań procedur przez usługę gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation (WCF) i gRPC są zarówno implementacjami wzorca *zdalnego wywołania procedury* (RPC), które mają na celu wykonywanie wywołań do usług uruchomionych na innym komputerze lub w innym procesie, tak jakby były tylko wywołania metody w aplikacji klienckiej. Chociaż cele WCF i gRPC są takie same, szczegóły implementacji są zupełnie inne.

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
