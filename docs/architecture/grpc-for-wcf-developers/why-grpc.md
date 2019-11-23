---
title: Dlaczego gRPC jest zalecane dla deweloperów WCF — gRPC dla deweloperów WCF
description: Dyskusja o tym, dlaczego gRPC jest dobrze dopasowana dla deweloperów WCF, którzy chcą migrować do nowoczesnych architektur i platform.
ms.date: 09/02/2019
ms.openlocfilehash: da712e1ceee92f0a1a2661252dcda602f5dde9a0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966946"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a>Dlaczego usługa gRPC jest zalecana dla deweloperów WCF

Przed przekazaniem do języka i technik gRPC warto omówić, dlaczego gRPC jest odpowiednim rozwiązaniem dla deweloperów WCF, którzy chcą migrować do programu .NET Core, z uwzględnieniem dostępnych rozwiązań.

## <a name="similarity-to-wcf"></a>Podobieństwo do WCF

Mimo że jego implementacja i podejście są inne, rzeczywiste środowisko tworzenia i zużywania usług z gRPC powinno być bardzo intuicyjne dla deweloperów programu WCF. Podstawowy cel, dzięki któremu można się zakodować tak, jakby klient i serwer znajdowały się na tej samej platformie, bez konieczności zajmowania się siecią, jest taka sama. Obie platformy korzystają z zasady deklarującej, a następnie implementującej interfejs, mimo że proces deklarujący ten interfejs jest inny. Jak widać w rozdziale 5, różne typy wywołań RPC obsługiwane przez mapę gRPC są bardzo dobrze dostępne dla różnych powiązań dostępnych dla usług WCF.

## <a name="benefits-of-grpc"></a>Zalety gRPC

Dodatkowe powody, dla których gRPC się powyżej innych rozwiązań, są następujące:

### <a name="performance"></a>Wydajność

Jak już wspomniano, przy użyciu protokołu HTTP/2, a nie protokołu HTTP/1.1, program usuwa wymagania dla wiadomości z możliwością czytania przez człowieka, a zamiast tego wykorzystuje mniejszy szybszy protokół binarny. Jest to wydajniejsze rozwiązanie do analizowania komputerów. Protokół HTTP/2 obsługuje również multipleksowanie żądań przez pojedyncze połączenie, które umożliwia wysyłanie odpowiedzi, gdy tylko są gotowe, bez konieczności oczekiwania na kolejkę (problem w protokole HTTP/1.1 znany jako blokowanie "nagłówek"). W przypadku korzystania z programu gRPC potrzeba mniejszej ilości zasobów, co sprawia, że jest to dobre rozwiązanie do korzystania z urządzeń przenośnych i wolniejszych sieci.

### <a name="interoperability"></a>Współdziałanie

Istnieją narzędzia i biblioteki gRPC dla wszystkich głównych języków programowania i platform, w tym .NET, Java, Python, go, C++Node. js, Swift, dart, Ruby i php. Dzięki wykorzystaniu protokołów binarnych bufory protokołu i wydajne generowanie kodu dla każdej platformy deweloperzy mogą tworzyć wydajne aplikacje, jednocześnie utrzymując pełną pomoc techniczną dla wielu platform.

### <a name="usability-and-productivity"></a>Użyteczność i produktywność

gRPC to kompleksowe rozwiązanie RPC. Działa on spójnie z wieloma językami i platformami oraz udostępnia doskonałe narzędzia, z dużą ilością niezbędnego automatycznie generowanego kodu, więc więcej czasu dewelopera jest bezpłatny do skoncentrowania się na logice biznesowej.

### <a name="streaming"></a>Przesyłanie strumieniowe

gRPC ma pełne dwukierunkowe przesyłanie strumieniowe, które zapewnia bardzo podobną funkcjonalność usługi WCF w zakresie pełnego dupleksu. gRPC Streaming może działać za pośrednictwem zwykłych połączeń internetowych, modułów równoważenia obciążenia i sieci usług.

### <a name="deadlinetimeouts-and-cancellation"></a>Termin/limity czasu i anulowanie

gRPC umożliwia klientom określenie maksymalnego czasu na ukończenie zdalnego wywoływania procedur. Jeśli określony termin zostanie przekroczony, serwer może anulować operację niezależnie od klienta. Terminy i anulowania mogą być propagowane przez dalsze gRPCe wywołania, aby ułatwić wymuszanie limitów użycia zasobów. Klienci mogą również przerywać operacje po przekroczeniu terminu ostatecznego lub wcześniej (np. ze względu na interakcję użytkownika).

### <a name="security"></a>Zabezpieczenia

gRPC jest niejawnie zabezpieczony przy użyciu protokołu HTTP/2 za pośrednictwem szyfrowania TLS end-to-end. Obsługa uwierzytelniania certyfikatu klienta (zobacz rozdział 6) dalsze zwiększa bezpieczeństwo i zaufanie między klientem a serwerem.

>[!div class="step-by-step"]
>[Poprzedni](network-protocols.md)
>[Następny](protocol-buffers.md)
