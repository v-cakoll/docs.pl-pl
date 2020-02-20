---
title: Dlaczego zalecamy gRPC dla deweloperów WCF — gRPC dla deweloperów WCF
description: Dyskusja o tym, dlaczego gRPC jest dobrze dopasowana dla deweloperów WCF, którzy chcą migrować do nowoczesnych architektur i platform.
ms.date: 09/02/2019
ms.openlocfilehash: fc93ca4c8f2a28dc4d3a0b0466d19c86273b40b8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503329"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Dlaczego zalecamy gRPC dla deweloperów WCF

Zanim szczegółowe się z językiem i technikami gRPC, warto omówić, dlaczego gRPC to odpowiednie rozwiązanie dla deweloperów Windows Communication Foundation (WCF), którzy chcą migrować do platformy .NET Core.

## <a name="similarity-to-wcf"></a>Podobieństwo do WCF

Chociaż implementacja i podejście różnią się w zależności od gRPC, doświadczenia związane z tworzeniem i zużywaniem usług z gRPC powinny być intuicyjne dla deweloperów WCF. Podstawowy cel jest taki sam, jak w przypadku, gdy klient i serwer znajdują się na tej samej platformie, bez konieczności zajmowania się siecią. 

Obie platformy korzystają z zasady deklarującej, a następnie implementującej interfejs, mimo że proces deklarujący ten interfejs jest inny. Podobnie jak zobaczysz w rozdziale 5, różne typy wywołań RPC, które gRPC obsługują mapę dla powiązań dostępnych dla usług WCF.

## <a name="benefits-of-grpc"></a>Zalety gRPC

gRPC znajduje się powyżej innych rozwiązań z następujących powodów.

### <a name="performance"></a>Wydajność

Użycie protokołu HTTP/2 zamiast protokołu HTTP/1.1 powoduje usunięcie wymagania dotyczącego czytelności wiadomości przez człowieka i użycie mniejszego, szybszego protokołu binarnego. Jest to wydajniejsze rozwiązanie do analizowania komputerów. Protokół HTTP/2 obsługuje również multipleksowanie żądań przez pojedyncze połączenie. Ta obsługa umożliwia wysyłanie odpowiedzi zaraz po ich przygotowaniu bez konieczności oczekiwania na kolejkę. (W przypadku protokołu HTTP/1.1 ten problem jest znany jako blokada "szefa linii (HOL)"). Gdy korzystasz z gRPC, potrzebujesz mniejszej ilości zasobów, co sprawia, że jest to dobre rozwiązanie do korzystania z urządzeń przenośnych i wolniejszych sieci.

### <a name="interoperability"></a>Współdziałanie

Istnieją narzędzia i biblioteki gRPC dla wszystkich głównych języków programowania i platform, w tym .NET, Java, Python, go, C++Node. js, Swift, dart, Ruby i php. Dzięki wykorzystaniu protokołów binarnych bufory protokołu i wydajne generowanie kodu dla każdej platformy deweloperzy mogą tworzyć wydajne aplikacje, jednocześnie utrzymując pełną pomoc techniczną dla wielu platform.

### <a name="usability-and-productivity"></a>Użyteczność i produktywność

gRPC to kompleksowe rozwiązanie RPC. Działa spójnie w wielu językach i na różnych platformach. Zapewnia również doskonałe narzędzia, z dużą ilością automatycznie generowanego kodu standardowego. Więc więcej czasu dewelopera jest bezpłatny do skoncentrowania się na logice biznesowej.

### <a name="streaming"></a>Przesyłanie strumieniowe

gRPC ma pełne dwukierunkowe przesyłanie strumieniowe, które zapewnia podobną funkcjonalność usług WCF w pełni dupleks. gRPC Streaming może działać za pośrednictwem zwykłych połączeń internetowych, modułów równoważenia obciążenia i sieci usług.

### <a name="deadlinetimeouts-and-cancellation"></a>Termin/limity czasu i anulowanie

gRPC umożliwia klientom określenie maksymalnego czasu na zakończenie zdalnego wywoływania procedur. W przypadku przekroczenia określonego terminu ostatecznego serwer może anulować operację niezależnie od klienta. Terminy i anulowania mogą być propagowane przez dalsze gRPCe wywołania, aby ułatwić wymuszanie limitów użycia zasobów. Klienci mogą również zatrzymywać operacje po przekroczeniu terminu ostatecznego lub wcześniej (na przykład ze względu na interakcję użytkownika).

### <a name="security"></a>Bezpieczeństwo

gRPC jest niejawnie zabezpieczony, gdy korzysta z protokołu HTTP/2 za pośrednictwem szyfrowania TLS end-to-end. Obsługa uwierzytelniania certyfikatu klienta (zobacz [rozdział 6](security.md)) dalsze zwiększa bezpieczeństwo i zaufanie między klientem a serwerem.

>[!div class="step-by-step"]
>[Poprzednie](network-protocols.md)
>[dalej](protocol-buffers.md)
