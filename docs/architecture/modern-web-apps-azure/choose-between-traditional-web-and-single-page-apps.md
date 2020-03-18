---
title: Wybieranie między tradycyjnymi aplikacjami internetowymi i aplikacjami jednostronicowymi
description: Dowiedz się, jak wybierać między tradycyjnymi aplikacjami sieci Web a aplikacjami jednostronicowymi (SPA) podczas tworzenia aplikacji sieci Web.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450111"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Wybieranie między tradycyjnymi aplikacjami sieci Web a aplikacjami jednostronicowymi (SPA)

> "Atwood's Law: Każda aplikacja, która może być napisana w JavaScript, w końcu zostanie napisana w JavaScript."  
> _\-Jeff Atwood_

Istnieją dwa ogólne podejścia do tworzenia aplikacji sieci web dzisiaj: tradycyjne aplikacje sieci web, które wykonują większość logiki aplikacji na serwerze i aplikacje jednostronicowe (SpA), które wykonują większość logiki interfejsu użytkownika w przeglądarce sieci web, komunikowanie się z serwerem sieci Web głównie przy użyciu internetowych interfejsów API. Podejście hybrydowe jest również możliwe, najprostszym jest hosta jednej lub więcej bogatych podaplikacji spa jak w większej tradycyjnej aplikacji sieci web.

Korzystaj z tradycyjnych aplikacji internetowych, gdy:

- Wymagania po stronie klienta aplikacji są proste lub nawet tylko do odczytu.

- Aplikacja musi działać w przeglądarkach bez obsługi JavaScript.

- Twój zespół nie zna technik tworzenia języka JavaScript lub TypeScript.

Użyj SPA, gdy:

- Aplikacja musi uwidaczniać bogaty interfejs użytkownika z wielu funkcji.

- Twój zespół jest zaznajomiony z rozwojem języka JavaScript i/lub TypeScript.

- Aplikacja musi już uwidaczniać interfejs API dla innych klientów (wewnętrznych lub publicznych).

Ponadto struktury SPA wymagają większej wiedzy architektonicznej i bezpieczeństwa. Występują one większe churn ze względu na częste aktualizacje i nowe struktury niż tradycyjne aplikacje sieci web. Konfigurowanie zautomatyzowanych procesów kompilacji i wdrażania oraz korzystanie z opcji wdrażania, takich jak kontenery, może być trudniejsze w przypadku aplikacji SPA niż w przypadku tradycyjnych aplikacji sieci Web.

Ulepszenia w środowisku użytkownika możliwe dzięki podejściu SPA muszą być ważone w stosunku do tych zagadnień.

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 wprowadza nowy model budowania bogatego, interaktywnego i komposable interfejsu o nazwie Blazor. Blazor po stronie serwera pozwala deweloperom na tworzenie interfejsu użytkownika z Razor na serwerze i dla tego kodu, które mają być dostarczone do przeglądarki i wykonywane po stronie klienta za pomocą [WebAssembly](https://webassembly.org/). Strona serwera Blazor jest już dostępna z ASP.NET Core 3.0 lub nowszym. Blazor po stronie klienta powinien być dostępny w 2020 roku.

Blazor udostępnia nową, trzecią opcję do rozważenia przy ocenie, czy utworzyć czysto renderowane przez serwer aplikację sieci web, czy SPA. Można tworzyć bogate, spa-jak zachowanie po stronie klienta przy użyciu Blazor, bez konieczności znaczącego rozwoju JavaScript. Aplikacje Blazor aplikacje mogą wywoływać interfejsy API do żądania danych lub wykonywania operacji po stronie serwera.

Rozważ zbudowanie aplikacji internetowej z Blazorem, gdy:

- Aplikacja musi uwidaczniać bogaty interfejs użytkownika

- Twój zespół jest bardziej komfortowo z rozwojem .NET niż javascript lub program TypeScript

Aby uzyskać więcej informacji o Blazor, zobacz [Wprowadzenie do Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Kiedy wybrać tradycyjne aplikacje internetowe

Poniżej znajduje się bardziej szczegółowe wyjaśnienie wcześniej poddanych powodów wybierania tradycyjnych aplikacji internetowych.

**Aplikacja ma proste, ewentualnie tylko do odczytu, wymagania po stronie klienta**

Wiele aplikacji internetowych są używane głównie w sposób tylko do odczytu przez zdecydowaną większość swoich użytkowników. Tylko do odczytu (lub odczytu głównie) aplikacje wydają się być znacznie prostsze niż te, które utrzymują i manipulować dużo stanu. Na przykład wyszukiwarka może składać się z pojedynczego punktu wejścia z polem tekstowym i drugiej strony do wyświetlania wyników wyszukiwania. Anonimowi użytkownicy mogą łatwo wysyłać żądania i nie ma potrzeby logiki po stronie klienta. Podobnie aplikacja publiczna bloga lub systemu zarządzania treścią zwykle składa się głównie z zawartości o niewielkim zachowaniu po stronie klienta. Takie aplikacje są łatwo zbudowane jako tradycyjne aplikacje internetowe oparte na serwerze, które wykonują logikę na serwerze www i renderują kod HTML, który ma być wyświetlany w przeglądarce. Fakt, że każda unikatowa strona witryny ma swój własny adres URL, który może być zakładkowy i indeksowany przez wyszukiwarki (domyślnie bez konieczności dodawania tego jako oddzielnej funkcji aplikacji) jest również wyraźną korzyścią w takich scenariuszach.

**Aplikacja musi działać w przeglądarkach bez obsługi JavaScript**

Aplikacje sieci Web, które muszą działać w przeglądarkach z ograniczoną obsługą języka JavaScript lub bez obsługi javascript, powinny być zapisywane przy użyciu tradycyjnych przepływów pracy aplikacji sieci Web (lub przynajmniej być w stanie powrócić do takiego zachowania). Dodatki SPA wymagają obsługi JavaScript po stronie klienta, aby funkcjonować; jeśli nie jest dostępna, spa nie są dobrym wyborem.

**Twój zespół nie zna technik tworzenia języka JavaScript lub TypeScript**

Jeśli twój zespół nie jest zaznajomiony z JavaScript lub TypeScript, ale jest zaznajomiony z tworzeniem aplikacji sieci web po stronie serwera, prawdopodobnie będzie w stanie dostarczyć tradycyjną aplikację internetową szybciej niż SPA. O ile nauka programowania dodatków SPA nie jest celem lub wymagane jest środowisko użytkownika zapewniane przez SPA, tradycyjne aplikacje sieci web są bardziej produktywnym wyborem dla zespołów, które już znają je.

## <a name="when-to-choose-spas"></a>Kiedy wybrać spa

Poniżej przedstawiono bardziej szczegółowe wyjaśnienie, kiedy wybrać styl tworzenia aplikacji jednostronicowych dla aplikacji sieci web.

**Aplikacja musi udostępniać bogaty interfejs użytkownika z wieloma funkcjami**

Dodatki SPA mogą obsługiwać rozbudowane funkcje po stronie klienta, które nie wymagają ponownego ładowania strony, gdy użytkownicy podejmują akcje lub nawigują między obszarami aplikacji. Dodatki SPA można ładować szybciej, pobieranie danych w tle i poszczególnych działań użytkownika są bardziej elastyczne, ponieważ pełne jeńców stronicowych są rzadkie. Dodatki SPA mogą obsługiwać aktualizacje przyrostowe, zapisując częściowo wypełnione formularze lub dokumenty bez konieczności klikania przycisku w celu przesłania formularza przez użytkownika. Dodatki SPA mogą obsługiwać zaawansowane zachowania po stronie klienta, takie jak przeciąganie i upuszczanie, znacznie łatwiej niż tradycyjne aplikacje. Dodatki SPA mogą być przeznaczone do uruchamiania w trybie rozłączonym, co aktualizacje modelu po stronie klienta, które są ostatecznie synchronizowane z powrotem do serwera po ponownym nawiązaniu połączenia. Wybierz aplikację w stylu SPA, jeśli wymagania aplikacji obejmują rozbudowane funkcje, które wykraczają poza typowe formularze HTML.

Często dodatki SPA muszą implementować funkcje wbudowane w tradycyjne aplikacje sieci web, takie jak wyświetlanie znaczącego adresu URL na pasku adresu odzwierciedlającego bieżącą operację (i umożliwienie użytkownikom zakładki lub głębokiego łącza do tego adresu URL, aby do niego powrócić). Dodatki SPA powinny również umożliwiać użytkownikom korzystanie z przycisków wstecz i do przodu przeglądarki z wynikami, które ich nie zaskoczą.

**Twój zespół jest zaznajomiony z rozwojem języka JavaScript i/lub TypeScript**

Pisanie dodatków SPA wymaga znajomości technik i bibliotek programowania po stronie klienta oraz technik programowania po stronie klienta. Twój zespół powinien być kompetentny w pisaniu nowoczesnego JavaScript przy użyciu struktury SPA, takiej jak Angular.

> ### <a name="references--spa-frameworks"></a>Referencje – struktury SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Reagować**
>   <https://reactjs.org/>
> - **Porównanie struktur JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Aplikacja musi już uwidaczniać interfejs API dla innych (wewnętrznych lub publicznych) klientów**

Jeśli już obsługujesz interfejs API sieci Web do użytku przez innych klientów, może wymagać mniej wysiłku, aby utworzyć implementację SPA, która wykorzystuje te interfejsy API, a nie odtwarzanie logiki w formie po stronie serwera. Dodatki SPA intensywnie korzystają z internetowych interfejsów API do wykonywania zapytań i aktualizacji danych w miarę interakcji użytkowników z aplikacją.

## <a name="when-to-choose-blazor"></a>Kiedy wybrać Blazor

Poniżej znajduje się bardziej szczegółowe wyjaśnienie, kiedy wybrać Blazor dla aplikacji internetowej.

**Aplikacja musi uwidaczniać bogaty interfejs użytkownika**

Podobnie jak aSP oparte na języku JavaScript, aplikacje Blazor mogą obsługiwać rozbudowane zachowanie klienta bez ponownego ładowania strony. Te aplikacje są bardziej elastyczne dla użytkowników, pobierając tylko dane (lub HTML) wymagane do odpowiedzi na daną interakcję z użytkownikiem. Zaprojektowane prawidłowo, aplikacje Blazor po stronie serwera można skonfigurować do uruchamiania jako aplikacje Blazor po stronie klienta przy minimalnych zmianach po obsłudze tej funkcji.

**Twój zespół jest bardziej komfortowo z rozwojem .NET niż javascript lub program TypeScript**

Wielu programistów jest bardziej produktywnych dzięki .NET i Razor niż w językach po stronie klienta, takich jak JavaScript lub TypeScript. Ponieważ strona serwera aplikacji jest już opracowywana z .NET, przy użyciu Blazor zapewnia każdy deweloper .NET w zespole można zrozumieć i potencjalnie utworzyć zachowanie frontonu aplikacji.

## <a name="decision-table"></a>Tabela decyzji

W poniższej tabeli decyzji podsumowano niektóre z podstawowych czynników, które należy wziąć pod uwagę przy wyborze między tradycyjną aplikacją internetową, SPA lub aplikacją Blazor.

| **Czynnikiem**                                           | **Tradycyjna aplikacja sieci Web** | **Aplikacja jednostronicowa** | **Aplikacja Blazor**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| Wymagana znajomość zespołu z językiem JavaScript/TypeScript | **Minimalny**             | **Wymagane**                | **Minimalny**     |
| Obsługa przeglądarek bez skryptów                   | **Obsługiwane**           | **Nie obsługiwane**           | **Obsługiwane**   |
| Minimalne zachowanie aplikacji po stronie klienta             | **Dobrze dopasowane**         | **Overkill**                | **Opłacalne**      |
| Rozbudowane, złożone wymagania dotyczące interfejsu użytkownika            | **Ograniczone**             | **Dobrze dopasowane**             | **Dobrze dopasowane** |

>[!div class="step-by-step"]
>[Poprzedni](modern-web-applications-characteristics.md)
>[następny](architectural-principles.md)
