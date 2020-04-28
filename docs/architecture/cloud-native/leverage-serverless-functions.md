---
title: Korzystanie z funkcji bezserwerowych
description: Korzystanie z bezserwerowych i Azure Functions w aplikacjach natywnych w chmurze
ms.date: 04/13/2020
ms.openlocfilehash: 176499e3cd0349cd689b9d13d1c237a6343d13f3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199745"
---
# <a name="leveraging-serverless-functions"></a>Korzystanie z funkcji bezserwerowych

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W spektrum od zarządzania maszynami fizycznymi do korzystania z możliwości chmury, bezserwerowe życie na najwyższym końcu. Jedyną odpowiedzialnością jest Twój kod i płacisz tylko wtedy, gdy kod jest uruchomiony. Azure Functions zapewnia sposób tworzenia możliwości bezserwerowych w aplikacjach natywnych w chmurze.

## <a name="what-is-serverless"></a>Co to jest bezserwerowe?

Bezserwerowy jest stosunkowo nowym modelem usług w chmurze obliczeniowej. Nie oznacza to, że serwery są opcjonalne — kod nadal działa na serwerze. Rozróżnienie polega na tym, że zespół aplikacji nie ma już znaczenia zarządzania infrastrukturą serwera. Zamiast tego dostawca chmury jest odpowiedzialny. Zespół programistyczny zwiększa swoją produktywność, dostarczając rozwiązania biznesowe klientom, a nie w ramach instalacji wodociągowej.

Obliczenia bez użycia serwera wykorzystują bezstanowe kontenery wyzwalające zdarzenia do hostowania usług. Umożliwiają skalowanie w poziomie i w programie w celu spełnienia wymagań w miarę potrzeb. Platformy bezserwerowe, takie jak Azure Functions, mają ścisłą integrację z innymi usługami platformy Azure, takimi jak kolejki, zdarzenia i magazyn.

## <a name="what-challenges-are-solved-by-serverless"></a>Jakie wyzwania są rozwiązywane przez serwer?

Platformy bezserwerowe z wieloma czasochłonnymi i kosztownymi problemami:

- Kupowanie maszyn i licencji na oprogramowanie
- Obudowa, zabezpieczanie, Konfigurowanie i konserwowanie maszyn oraz wymagań dotyczących sieci, mocy i A/C
- Poprawianie i uaktualnianie systemów operacyjnych i oprogramowania
- Konfigurowanie serwerów sieci Web lub usług maszynowych do hostowania oprogramowania aplikacji
- Konfigurowanie oprogramowania aplikacji w ramach jego platformy

Wiele firm przydziela duże budżety do obsługi problemów dotyczących infrastruktury sprzętu. Przejście do chmury może pomóc w zmniejszeniu kosztów. Przesuwanie aplikacji do bezserwerowego może pomóc je wyeliminować.

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>Jaka jest różnica między mikrousługą a funkcją bezserwerową?

Zazwyczaj mikrousługa hermetyzuje możliwość biznesową, taką jak koszyk dla witryny handlu elektronicznego online. Uwidacznia wiele operacji, które umożliwiają użytkownikowi zarządzanie swoimi środowiskami zakupów. Jednakże funkcja jest małym, lekkim blokiem kodu, który wykonuje operację pojedynczego przeznaczenie w odpowiedzi na zdarzenie.
Mikrousługi są zwykle konstruowane do odpowiedzi na żądania, często z interfejsu. Żądania mogą być oparte na protokole HTTP REST lub gRPC. Usługi bezserwerowe reagują na zdarzenia. Oparta na zdarzeniach architektura jest idealnym rozwiązaniem do przetwarzania krótko działających zadań w tle.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Jakie scenariusze są odpowiednie dla bezserwerowego?

Bezserwerowe uwidacznia pojedyncze funkcje, które są wywoływane w odpowiedzi na wyzwalacz. Sprawia to, że są one idealne do przetwarzania zadań w tle.

Aplikacja może wymagać wysłania wiadomości e-mail w ramach przepływu pracy. Zamiast wysyłać powiadomienie w ramach żądania mikrousługi, umieść szczegóły komunikatu w kolejce. Funkcja platformy Azure może usunąć z kolejki komunikat i asynchronicznie wysłać wiadomość e-mail. Wykonanie tej czynności może poprawić wydajność i skalowalność mikrousługi. [Wyrównywanie obciążeń przy użyciu kolejki](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) można zaimplementować, aby uniknąć wąskich gardeł związanych z wysyłaniem wiadomości e-mail. Ponadto ta usługa autonomiczna może zostać ponownie użyta jako narzędzie dla wielu różnych aplikacji.

Asynchroniczna obsługa komunikatów z kolejek i tematów jest typowym wzorcem do wyzwalania funkcji bezserwerowych. Jednak Azure Functions mogą być wyzwalane przez inne zdarzenia, takie jak zmiany w usłudze Azure Blob Storage. Usługa obsługująca przekazywanie obrazów może mieć funkcję platformy Azure odpowiedzialną za optymalizację rozmiaru obrazu. Funkcja może zostać wyzwolona bezpośrednio przez wstawianie do Blob Storage platformy Azure, zachowując złożoność z operacji mikrousług.

Wiele usług ma długotrwałe procesy w ramach przepływów pracy. Często te zadania są wykonywane w ramach interakcji użytkownika z aplikacją. Te zadania mogą wymusić, że użytkownik może czekać, negatywny wpływ na środowisko pracy. Operacje obliczeniowe bez użycia serwera zapewniają doskonały sposób przenoszenia wolniejszych zadań poza pętlę interakcji użytkownika. Te zadania mogą być skalowane na żądanie bez konieczności skalowania całej aplikacji.

## <a name="when-should-you-avoid-serverless"></a>Kiedy należy unikać bezserwerowego?

Rozwiązania bezserwerowe i skalowanie na żądanie. Gdy nowe wystąpienie zostanie wywołane, zimne uruchomienie jest typowym problemem. Zimny start to okres czasu potrzebny na udostępnienie tego wystąpienia. Zwykle to opóźnienie może wynosić kilka sekund, ale może być dłuższe w zależności od różnych czynników. Po zainicjowaniu obsługi pojedyncze wystąpienie będzie utrzymywane pod warunkiem, że otrzymuje okresowe żądania. Jeśli jednak usługa jest wyzwana rzadziej, platforma Azure może usunąć ją z pamięci i wymagać zimnego uruchomienia, gdy zostanie ponownie wywołana. Zimne uruchomienie jest również wymagane, gdy funkcja jest skalowana do nowego wystąpienia.

Rysunek 3-10 pokazuje wzorzec zimnego startu. Należy pamiętać o dodatkowych krokach wymaganych, gdy aplikacja jest zimna.

![Rysunek zimny i](./media/cold-start-warm-start.png)
rozgrzany początek**3-10**. Zimne rozpoczęcie i rozgrzane.

Aby uniknąć całkowitego uruchamiania zimnego, możesz przełączyć się z [planu zużycia do dedykowanego planu](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Możesz również skonfigurować co najmniej jedno [wystąpienie wstępnie rozgrzane](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) z uaktualnieniem planu Premium. W takich przypadkach należy dodać kolejne wystąpienie, które jest już gotowe do użycia. Te opcje mogą pomóc w ograniczeniu problemu zimnego startu związanego z przetwarzaniem nieserwerowym.

Dostawcy usług w chmurze rachunku bezserwerowego na podstawie czasu wykonywania obliczeń i zużytej pamięci. Długotrwałe operacje lub obciążenia zużywające duże ilości pamięci nie zawsze są najlepszymi kandydatami dla bezserwerowych. Funkcje bezserwerowe preferują małe fragmenty pracy, które mogą szybko zakończyć pracę. Większość platform bezserwerowych wymaga, aby poszczególne funkcje zostały wykonane w ciągu kilku minut. Azure Functions wartość domyślna to 5-minutowy czas trwania, który można skonfigurować do 10 minut. Plan Azure Functions Premium umożliwia ograniczenie tego problemu, a także domyślnego limitu czasu do 30 minut z niezwiązanym wyższym limitem, który można skonfigurować. Czas obliczeń nie jest czasem kalendarzowym. Bardziej zaawansowane funkcje wykorzystujące platformę [Azure Durable Functions Framework](https://docs.microsoft.com/azure/azure-functions/durable/durable-functions-overview?tabs=csharp) mogą wstrzymywać wykonywanie w ciągu kilku dni. Rozliczenia opierają się na rzeczywistym czasie wykonywania — gdy funkcja wznawia działanie i wznawia przetwarzanie.

Na koniec korzystanie z Azure Functions dla zadań aplikacji zwiększa złożoność. Warto najpierw przeprowadzić architekta swojej aplikacji przy użyciu modularnie powiązanego projektu. Następnie ustal, czy nie ma żadnych korzyści bezserwerowych, które uzasadniają dodatkową złożoność.

>[!div class="step-by-step"]
>[Poprzedni](leverage-containers-orchestrators.md)
>[Następny](combine-containers-serverless-approaches.md)
