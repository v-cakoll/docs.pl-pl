---
title: Dlaczego polecamy gRPC dla programistów WCF - gRPC dla programistów WCF
description: Dyskusja, dlaczego gRPC jest dobre dopasowanie dla deweloperów WCF, którzy chcą migrować do nowoczesnych architektur i platform.
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147649"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Dlaczego zalecamy gRPC dla deweloperów WCF

Zanim przejdziemy głęboko do języka i technik gRPC, warto omówić, dlaczego gRPC jest właściwym rozwiązaniem dla deweloperów Windows Communication Foundation (WCF), którzy chcą przeprowadzić migrację do .NET Core.

## <a name="similarity-to-wcf"></a>Podobieństwo do WCF

Mimo że implementacja i podejście są różne dla gRPC, doświadczenie w opracowywaniu i zużywania usług z gRPC powinny być intuicyjne dla deweloperów WCF. Podstawowy cel jest taki sam: umożliwia kod tak, jakby klient i serwer znajdują się na tej samej platformie, bez konieczności martwienia się o sieci.

Obie platformy mają wspólną zasadę deklarowania, a następnie implementowania interfejsu, mimo że proces deklarowania tego interfejsu jest inny. I jak widać w rozdziale 5, różne typy wywołań RPC, że gRPC obsługuje mapę oraz do powiązań dostępnych dla usług WCF.

## <a name="benefits-of-grpc"></a>Zalety gRPC

gRPC stoi nad innymi rozwiązaniami z następujących powodów.

### <a name="performance"></a>Wydajność

Korzystanie z protokołu HTTP/2 zamiast PROTOKOŁU HTTP/1.1 powoduje usunięcie wymogu dotyczącego wiadomości czytelnych dla człowieka i zamiast tego używa mniejszego, szybszego protokołu binarnego. Jest to bardziej efektywne dla komputerów do analizy. HTTP/2 obsługuje również żądania multipleksowania za pośrednictwem jednego połączenia. Ta obsługa umożliwia wysłanie odpowiedzi, gdy tylko będą gotowe, bez konieczności oczekiwania w kolejce. (W HTTP/1.1 ten problem jest znany jako "head-of-line (HOL) blokowanie.") Potrzebujesz mniej zasobów podczas korzystania z gRPC, co sprawia, że jest to dobre rozwiązanie do wykorzystania na urządzeniach mobilnych i w wolniejszych sieciach.

### <a name="interoperability"></a>Współdziałanie

Istnieją narzędzia i biblioteki gRPC dla wszystkich głównych języków i platform programowania, w tym .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby i PHP. Dzięki formatowi binarnego buforów protokołu i wydajnemu generowaniu kodu dla każdej platformy deweloperzy mogą tworzyć wydajne aplikacje, jednocześnie ciesząc się pełną obsługą między platformami.

### <a name="usability-and-productivity"></a>Użyteczność i produktywność

gRPC jest kompleksowym rozwiązaniem RPC. Działa konsekwentnie w wielu językach i na różnych platformach. Zapewnia również doskonałe oprzyrządowanie, z dużą ilością niezbędnego kodu standardowego generowanego automatycznie. Tak więc więcej czasu programisty jest zwalniany, aby skupić się na logice biznesowej.

### <a name="streaming"></a>Przesyłanie strumieniowe

gRPC ma pełne dwukierunkowe przesyłanie strumieniowe, które zapewnia podobną funkcjonalność do usług pełnego dupleksu WCF. Przesyłanie strumieniowe gRPC może działać za pośrednictwem zwykłych połączeń internetowych, modułów równoważenia obciążenia i siatek usługowych.

### <a name="deadlinetimeouts-and-cancellation"></a>Terminy/terminy i anulowanie

gRPC umożliwia klientom określenie maksymalnego czasu zakończenia rpc. Jeśli określony termin zostanie przekroczony, serwer może anulować operację niezależnie od klienta. Terminy i odwołania mogą być propagowane za pomocą dalszych wywołań gRPC, aby pomóc w egzekwowaniu limitów użycia zasobów. Klienci mogą również zatrzymać operacje po przekroczeniu terminu lub wcześniej, jeśli to konieczne (na przykład z powodu interakcji z użytkownikiem).

### <a name="security"></a>Zabezpieczenia

gRPC jest niejawnie bezpieczne, gdy używa HTTP/2 za pośrednictwem tls end-to-end szyfrowanego połączenia. Obsługa uwierzytelniania certyfikatów klienta (zobacz [rozdział 6](security.md)) dodatkowo zwiększa bezpieczeństwo i zaufanie między klientem a serwerem.

>[!div class="step-by-step"]
>[Poprzedni](network-protocols.md)
>[następny](protocol-buffers.md)
