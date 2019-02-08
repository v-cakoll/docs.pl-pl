---
title: Wybierz między aplikacjami tradycyjnej sieci web i aplikacje jednostronicowe
description: Dowiedz się, jak dokonać wyboru między tradycyjnych aplikacji i internetowych aplikacji jednostronicowej (źródła), podczas tworzenia aplikacji sieci web.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 5b8569f2abd5160fa8a080c06441a963fb455f6b
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825748"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Wybierz między aplikacjami tradycyjnej sieci Web i aplikacje jednostronicowe (źródła)

> "Prawo Atwoodem firmy: Każda aplikacja, która może być napisana w języku JavaScript zostanie ostatecznie zapisany w języku JavaScript."  
> _\- Jeffem Atwoodem_

Dostępne są dwie opcje ogólne do kompilowania nowoczesnych aplikacji sieci web: aplikacje tradycyjnej sieci web, które wykonują większość logiki aplikacji na serwerze i aplikacji jednostronicowej (źródła), które wykonują większość logikę interfejsu użytkownika w przeglądarce sieci web Komunikacja z serwerem sieci web, przede wszystkim za pomocą interfejsów API sieci web. Możliwe jest również podejście hybrydowe, najprostszym trwa hosta jedną lub więcej zaawansowanych przypominającej SPA podrzędnych aplikacji w obrębie większej aplikacji sieci web tradycyjnych.

Skorzystaj z aplikacji sieci web tradycyjnych po:

- Wymagania dotyczące Twojej aplikacji po stronie klienta są proste lub nawet tylko do odczytu.

- Aplikacja musi działać w różnych przeglądarkach bez konieczności obsługi języka JavaScript.

- Twój zespół nie jest zaznajomiony z technik programistycznych języka JavaScript lub TypeScript.

Należy użyć SPA po:

- Aplikacja musi ujawniać zaawansowanego interfejsu użytkownika z wieloma funkcjami.

- Zespół jest znajomość języka JavaScript i/lub TypeScript rozwoju.

- Aplikacja musi już uwidaczniania interfejsu API dla innych klientów (wewnętrznego lub publicznego).

Ponadto wymagają większej struktury SPA architektury i doświadczenia w zakresie zabezpieczeń. One występować większe zmian z powodu częstych aktualizacji i nowych platform niż tradycyjne internetowych. Konfigurowanie zautomatyzowanych procesów kompilacji i wdrożenia, a korzystanie z opcji wdrażania, takich jak kontenery są za pomocą aplikacji SPA trudniejsze niż aplikacji tradycyjnej sieci web.

Ulepszenia środowiska użytkownika staje się możliwy przez SPA model należy porównać te zagadnienia.

## <a name="razor-components"></a>Składniki Razor

Platforma ASP.NET Core 3.0 wprowadzono nowy model do tworzenia bogatych i interaktywnych i konfigurowalna interfejsu użytkownika o nazwie składniki Razor. Składniki razor umożliwić deweloperom tworzenie interfejsu użytkownika ze składnią Razor na serwerze, a dla tego kodu, które mają zostać dostarczone do przeglądarki i wykonywane przy użyciu biblioteki JavaScript o nazwie format WebAssembly klienta. Platforma ASP.NET Core 3.0 jest nadal w fazie projektowania, ale należy się spodziewać zobaczyć więcej informacji na temat tej technologii w wersji 3.0 aktualizacji tę książkę elektroniczną. Aby uzyskać więcej informacji na temat składników Razor (o nazwie Blazor kod), zobacz [wprowadzenie Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Kiedy należy wybrać aplikacje tradycyjnej sieci web

Oto bardziej szczegółowy opis wcześniej podane przyczyny pobrania aplikacji tradycyjnej sieci web.

**Twoja aplikacja ma wymagania prosty, prawdopodobnie tylko do odczytu, po stronie klienta**

Wiele aplikacji sieci web są głównie używane w sposób umożliwiający tylko do odczytu przez większość użytkowników. Tylko do odczytu (lub przeczytaj najczęściej) aplikacji zwykle jest znacznie prostsze niż te, które utrzymują i manipulowania dużym stopniem stanu. Na przykład aparatu wyszukiwania może składać się z pojedynczego punktu wejścia przy użyciu pola tekstowego i drugiej stronie do wyświetlania wyników wyszukiwania. Anonimowi użytkownicy mogą łatwo wysyłać żądania, a istnieje potrzeba nieco logiki po stronie klienta. Podobnie blogu lub zawartości systemem zarządzania firmy publicznie dostępnych aplikacji zwykle składa się głównie z zawartości przy użyciu nieco zachowania po stronie klienta. Takie aplikacje łatwo są tworzone w aplikacji tradycyjnych oparte na serwerze sieci web, które wykonywania logiki na serwerze sieci web i renderowania elementów HTML mają być wyświetlane w przeglądarce. Fakt, że każdy unikatową stronę witryny ma swój własny adres URL, który może być zakładek i indeksowany przez wyszukiwarki (domyślnie, bez konieczności dodawania to jako osobna funkcja aplikacji) jest również wyczyść korzyści w takich scenariuszach.

**Aplikacja musi działać w różnych przeglądarkach bez konieczności obsługi języka JavaScript**

Aplikacje sieci Web, które muszą działać w przeglądarkach z ograniczonym lub brak obsługi języka JavaScript powinna być zapisana przy użyciu przepływów pracy aplikacji w tradycyjnej sieci web (lub co najmniej można przełączyć się na takie zachowanie). Aplikacji jednostronicowych wymagają języka JavaScript po stronie klienta, aby funkcjonować; Jeśli nie jest dostępna, aplikacji jednostronicowych nie są dobrym wyborem.

**Twój zespół nie jest zaznajomiony z technik programistycznych języka JavaScript lub TypeScript**

Jeśli Twój zespół nie jest zaznajomiony z języka JavaScript lub TypeScript jest jednak zapoznać się z programowania aplikacji sieci web po stronie serwera, prawdopodobnie będzie mogła dostarczać aplikacji sieci web tradycyjnych znacznie szybciej niż SPA. Chyba, że celem jest learning, aby program aplikacji jednostronicowych lub komfortu zapewnianej przez SPA jest wymagany, aplikacje sieci web tradycyjnych są bardziej produktywne wybór dla zespołów, którzy znają już tworzenia ich.

## <a name="when-to-choose-spas"></a>Kiedy należy wybrać aplikacji jednostronicowych

Oto bardziej szczegółowe wyjaśnienie, kiedy należy wybrać aplikacje jednostronicowe stylu programowania dla aplikacji sieci web.

**Aplikacja musi udostępniać zaawansowanego interfejsu użytkownika z wieloma funkcjami**

Aplikacji jednostronicowych może obsługiwać zaawansowane funkcje po stronie klienta, która nie wymaga ponownie załadować stronę, gdy użytkownicy akcje lub przechodzenie między obszarami aplikacji. Aplikacji jednostronicowych mogą ładować szybsze pobieranie danych w tle, i akcji użytkownika są zwiększyć szybkość reakcji, ponieważ cała strona ładuje ponownie są rzadkie. Aplikacji jednostronicowych może obsługiwać aktualizacje przyrostowe zapisywanie częściowo wypełnione formularze lub dokumenty bez użytkownika, po kliknięciu przycisku, które można przesłać formularza. Aplikacji jednostronicowych może obsługiwać znacznie łatwiej niż tradycyjne aplikacje rozbudowane zachowania po stronie klienta, takich jak przeciągania i upuszczania. Źródła można zaprojektować do działania w trybie rozłączonym wprowadzania aktualizacji w modelu po stronie klienta, który ostatecznie są synchronizowane na serwerze, po ponownym nawiązaniu połączenia. Należy wybrać aplikację w języku SPA, jeśli wymagania dotyczące Twojej aplikacji zawiera zaawansowane funkcje, które wykraczają poza oferują typowy formularzy HTML.

Należy zauważyć, że często aplikacji jednostronicowych implementuje funkcje, które są wbudowane w platformę aplikacji tradycyjnej sieci web, takich jak wyświetlanie opisowy adres URL na adres pasku odzwierciedlający bieżącej operacji (i umożliwiając użytkownikom do zakładki lub link bezpośredni do tego adresu URL, aby powrócić do niego). Aplikacji jednostronicowych powinien również zezwolić użytkownikom korzystanie z wyników, które nie będą zaskakującymi je w przeglądarce przycisków Wstecz i dalej.

**Zespół jest znane, za pomocą języka JavaScript i/lub TypeScript**

Pisanie aplikacji jednostronicowych wymaga znajomości języka JavaScript i/lub TypeScript i techniki programowania po stronie klienta i bibliotek. Zespół powinien być właściwa w pisaniu nowoczesnego języka JavaScript przy użyciu SPA framework, takich jak Angular.

> ### <a name="references--spa-frameworks"></a>Odwołania — struktury SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Porównanie platformy JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Aplikacja musi już uwidaczniania interfejsu API dla innych klientów (wewnętrznego lub publicznego)**

Jeśli masz już obsługi interfejsu API sieci web używane przez innych klientów, może wymagać mniejszym nakładzie pracy do utworzenia implementacji SPA, który korzysta z tych interfejsów API, a nie odtwarzanie logiki w formularzu po stronie serwera. Aplikacji jednostronicowych upewnij zwiększone użycie interfejsów API sieci web do wykonywania zapytań i aktualizacji danych, zgodnie z użytkownikom interakcję z aplikacją.

## <a name="decision-table--traditional-web-or-spa"></a>Tabela decyzji — tradycyjnej sieci Web lub SPA

W poniższej tabeli decyzji zawiera podsumowanie podstawowych czynników, które należy wziąć pod uwagę przy wyborze między aplikacją internetową tradycyjnych i SPA.

| **współczynnik**                                           | **Aplikacja sieci Web tradycyjny** | **Aplikacja jednostronicowa** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| Wymagane zespołu znajomość języka JavaScript/TypeScript | **Minimalny**             | **Wymagane**                |
| Obsługa przeglądarki bez obsługi skryptów                   | **Obsługiwane**           | **Nie jest obsługiwany**           |
| Zachowanie minimalnego aplikacji po stronie klienta             | **Well-Suited**         | **Obszerne**                |
| Wymagania dotyczące interfejsu użytkownika zaawansowane, złożone            | **Ograniczone**             | **Well-Suited**             |

>[!div class="step-by-step"]
>[Poprzednie](modern-web-applications-characteristics.md)
>[dalej](architectural-principles.md)
