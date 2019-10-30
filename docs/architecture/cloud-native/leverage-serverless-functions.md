---
title: Korzystanie z funkcji bezserwerowych
description: Korzystanie z bezserwerowych i Azure Functions w aplikacjach natywnych w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 77ddef0eb8844ea1b55cd2fc5ec8aa12593c8631
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087112"
---
# <a name="leveraging-serverless-functions"></a>Korzystanie z funkcji bezserwerowych

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W spektrum zarządzania pełnymi maszynami i systemami operacyjnymi, aby korzystać z możliwości chmury, bez użycia serwera na najwyższej stronie, w którym użytkownik jest odpowiedzialny za kod, i płacisz tylko wtedy, gdy kod jest uruchomiony. Azure Functions zapewnia sposób tworzenia funkcji bezserwerowych w aplikacjach.

## <a name="what-is-serverless"></a>Co to jest bezserwerowe?

Obliczanie bezserwerowe nie oznacza, że nie jest to serwer z uruchomioną aplikacją — kod nadal działa na serwerze. Rozróżnienie polega na tym, że zespół programistyczny aplikacji nie musi już zagospodarować infrastrukturą serwera. Rozwiązania do przetwarzania bezserwerowe, takie jak Azure Functions ułatwienia, zwiększają produktywność i umożliwiają organizacjom Optymalizowanie swoich zasobów i skoncentrowanie się na dostarczaniu rozwiązań.

Obliczenia bez użycia serwera używają bezstanowych kontenerów wyzwalanych przez zdarzenia do hostowania aplikacji lub części aplikacji. Platformy bezserwerowe mogą skalować w poziomie i w programie, aby zaspokoić zapotrzebowanie w miarę potrzeb. Platformy, takie jak Azure Functions, mają łatwy bezpośredni dostęp do innych usług platformy Azure, takich jak kolejki, zdarzenia i magazyn.

## <a name="what-challenges-are-solved-by-serverless"></a>Jakie wyzwania są rozwiązywane przez serwer?

Bezserwerowy jest ostatecznym abstrakcją od uruchamiania własnego sprzętu. Deweloperzy mogą skupić się wyłącznie na pisaniu kodu w celu rozwiązywania problemów z działalnością biznesową, bez obaw dla żadnego z następujących zadań, które mogły być niezbędne podczas hostowania własnych serwerów:

- Kupowanie maszyn i licencji na oprogramowanie
- Obudowa, zabezpieczanie, Konfigurowanie i konserwowanie maszyn oraz wymagań dotyczących sieci, mocy i A/C
- Poprawianie i uaktualnianie systemów operacyjnych i oprogramowania
- Konfigurowanie serwerów sieci Web lub usług maszynowych do hostowania oprogramowania aplikacji
- Konfigurowanie oprogramowania aplikacji w ramach jego platformy

Wiele firm wykorzystuje dziesiątki członków personelu i przydziela duże budżety do obsługi tych zagadnień dotyczących infrastruktury sprzętu. Po prostu przechodzenie do chmury eliminuje niektóre z tych obaw. Przesunięcie aplikacji do bezserwerowego spowoduje eliminację reszty.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Jakie scenariusze są odpowiednie dla bezserwerowego?

Bezserwerowo używa pojedynczych funkcji, które są wywoływane w odpowiedzi na jakiś wyzwalacz. Sprawia to, że są one idealne do przetwarzania zadań w tle.

Na przykład aplikacja może wymagać wysłania wiadomości e-mail w ramach przetwarzania żądania. Zamiast wysyłać wiadomości e-mail w ramach obsługi żądania sieci Web, szczegóły wiadomości e-mail mogą być umieszczane w kolejce, a funkcja platformy Azure może zostać użyta w celu pobrania komunikatu i wysłania wiadomości e-mail. Wiele różnych elementów aplikacji, a nawet wiele aplikacji, może korzystać z tej samej funkcji platformy Azure, co zapewnia lepszą wydajność i skalowalność aplikacji i używanie [poziomu obciążenia opartego na kolejce](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) , aby uniknąć wąskich gardeł związanych z Wysyłanie wiadomości e-mail.

Chociaż [wzorzec wydawcy/subskrybenta](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) między aplikacjami i Azure Functions jest najbardziej typowym wzorcem, możliwe jest użycie innych wzorców. Azure Functions mogą być wyzwalane przez inne zdarzenia, takie jak zmiany w usłudze Azure Blob Storage. Aplikacja, która obsługuje przekazywanie obrazów, może mieć funkcję platformy Azure odpowiedzialną za tworzenie obrazów miniatur lub zmienianie rozmiaru przekazanych obrazów na spójne wymiary lub Optymalizacja rozmiaru obrazu. Wszystkie te funkcje mogą być wyzwalane bezpośrednio przez wstawianie do Blob Storage platformy Azure, zachowując złożoność i obciążenie w samej aplikacji.

Wiele aplikacji ma długotrwałe procesy w ramach przepływów pracy. Często te zadania są wykonywane w ramach interakcji użytkownika z aplikacją, wymuszają użytkownikowi oczekiwanie i negatywny wpływ na ich środowisko pracy. Operacje obliczeniowe bez użycia serwera zapewniają doskonały sposób wykonywania wolniejszych zadań poza pętlą interakcji użytkownika. te zadania mogą łatwo skalować się z zapotrzebowaniem, nie wymagając, aby cała aplikacja była skalowana.

## <a name="when-should-you-avoid-serverless"></a>Kiedy należy unikać bezserwerowego?

Operacje obliczeniowe bez użycia serwera są najlepszym rozwiązaniem w przypadku zadań, które nie blokują interfejsu użytkownika. Oznacza to, że nie są idealnym rozwiązaniem do bezpośredniego hostowania aplikacji sieci Web ani interfejsów API sieci Web. Głównym powodem tego jest to, że rozwiązania bezserwerowe są obsługiwane i skalowane na żądanie. Gdy potrzebne jest nowe wystąpienie funkcji, zwanej *zimnym rozpoczęciem*, zajmie czas udostępniania. Ten czas jest zwykle kilka sekund, ale może być dłuższy w zależności od różnych czynników. Pojedyncze wystąpienie może często być utrzymywane na czas nieokreślony (na przykład przez okresowe zgłaszanie żądania), ale problem zimnego startu pozostaje, jeśli liczba wystąpień potrzebna do skalowania w górę.

![zimny](./media/cold-start-warm-start.png)
początek i rozgrzany **rysunek 3-10**. Zimne rozpoczęcie i rozgrzane.

Jeśli potrzebujesz uniknąć całkowitego startu, możesz wybrać opcję przełączenia z [planu zużycia do dedykowanego planu](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Możesz również [skonfigurować co najmniej jedno wystąpienie wstępnie rozgrzane](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) w planie Premium, aby móc dodać kolejne wystąpienia, które jest już gotowe do użycia. Te opcje mogą złagodzić jedno z najważniejszych problemów związanych z przetwarzaniem bez użycia serwera.

Należy również zazwyczaj unikać bezserwerowego wykonywania długotrwałych zadań. Są one najlepsze dla małych fragmentów pracy, które mogą być szybko wykonywane. Większość platform bezserwerowych wymaga, aby poszczególne funkcje zostały wykonane w ciągu kilku minut. Azure Functions wartość domyślna to 5-minutowego czasu trwania (można skonfigurować maksymalnie 10 minut). Plan Azure Functions Premium umożliwia ograniczenie tego problemu, a także ustawienie domyślnego limitu czasu na 30 minut i umożliwienie skonfigurowania nieograniczonego wyższego limitu.

Na koniec korzystanie z bezserwerowego dla niektórych zadań w aplikacji zwiększa złożoność. Często najlepiej jest utworzyć architekt aplikacji w modułowym, luźno połączonym, a następnie ustalić, czy nie ma możliwości bezserwerowej oferty, która zapewnia dodatkową złożoność wartościowa. Wiele mniejszych aplikacji działa dobrze w jednym, wbudowanym wdrożeniu, bez konieczności stosowania rozproszonego przetwarzania bezserwerowego architektury aplikacji.

## <a name="references"></a>Odwołania

- [Informacje o zimnym uruchomieniu bezserwerowym](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Wstępnie grzane wystąpienia Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Tworzenie funkcji w systemie Linux przy użyciu obrazu niestandardowego](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
>[Poprzedni](leverage-containers-orchestrators.md)
>[Następny](combine-containers-serverless-approaches.md)
