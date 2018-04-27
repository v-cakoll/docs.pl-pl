---
title: Wybierz między aplikacjami sieci web tradycyjnych i aplikacje jednej strony
description: Architektów nowoczesnych aplikacji sieci web platformy ASP.NET Core i Microsoft Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b1472f8107d57eff8faca1b4c7de7ba43f4271c0
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Wybierz między aplikacjami sieci Web tradycyjnych i aplikacje jednej strony (źródła)

> "Prawa w Atwood: dowolnej aplikacji, które mogą być zapisywane w języku JavaScript, po pewnym czasie zostaną zapisane w języku JavaScript."  
> _\- Jan Atwood_

## <a name="summary"></a>Podsumowanie

Istnieją dwie metody ogólne do tworzenia aplikacji sieci web dzisiaj: aplikacje sieci web tradycyjnych, które wykonują większość logiki aplikacji na serwerze i aplikacji jednej strony (źródła), które wykonują większość logikę interfejsu użytkownika w przeglądarce sieci web podczas komunikacji z serwerem sieci web, przede wszystkim za pomocą interfejsów API sieci web. Możliwe jest również rozwiązanie hybrydowe, jest najprostsza hosta jedną lub więcej sformatowanego SPA przypominającej podrzędnych aplikacji w aplikacji sieci web tradycyjnych większy.

Należy użyć aplikacji sieci web tradycyjnych po:

-   Wymagania po stronie klienta aplikacji są proste lub nawet tylko do odczytu.

-   Aplikacja musi działać w przeglądarkach bez obsługi języka JavaScript.

-   Zespół nie może rozpoznać metody JavaScript i TypeScript.

Należy używać SPA po:

-   Aplikacja musi ujawniać interfejs użytkownika sformatowanego z wielu funkcji.

-   Zespół jest znajomość języka JavaScript i/lub TypeScript programowanie.

-   Aplikacja już musi ujawniać interfejsu API dla innych klientów (wewnętrzny lub publiczny).

Ponadto wymagają większej struktury SPA architektury i doświadczenia zabezpieczeń. Większa ilość danych churn z powodu częstych aktualizacji i nowych struktur niż aplikacji sieci web tradycyjnych wystąpieniu. Konfigurowanie zautomatyzowanych procesów kompilacji i wdrożenia i przy użyciu opcji wdrażania, takie jak kontenery są trudniejsze z aplikacjami SPA niż aplikacje sieci web tradycyjnych.

Ulepszenia środowiska użytkownika możliwe dzięki SPA modelu należy porównać te zagadnienia.

## <a name="when-to-choose-traditional-web-apps"></a>Kiedy należy wybrać aplikacje sieci web tradycyjny

Poniżej znajduje się bardziej szczegółowy opis pobrania aplikacji sieci web tradycyjnych przyczyny podane wcześniej.

**Aplikacja ma wymagania prosty, prawdopodobnie tylko do odczytu, po stronie klienta**

Wiele aplikacji sieci web są głównie używane w sposób tylko do odczytu przez większość użytkowników. Tylko do odczytu (lub odczytu głównie) aplikacji zwykle można znacznie prostsze niż te, które utrzymują i manipulowania dużą stanu. Na przykład wyszukiwarki może obejmować jeden punkt wejścia z pola tekstowego, a druga strona do wyświetlania wyników wyszukiwania. Użytkownicy anonimowi łatwo mogą wysyłać żądania, a pojawia się potrzeba logiki po stronie klienta. Podobnie blogu lub zawartości systemu zarządzania publicznych aplikacji zwykle składa się głównie z zawartości z małego zachowanie po stronie klienta. Takie aplikacje są wbudowane łatwo jako aplikacje tradycyjnych na serwerze sieci web, których wykonywanie logiki na serwerze sieci web i renderowania kodu HTML, który będzie wyświetlany w przeglądarce. Fakt, że każdy unikatowy strony witryny ma własny adres URL, który może być zakładki i indeksowany przez wyszukiwarki (domyślnie bez konieczności Dodaj ją jako osobna funkcja aplikacji) jest również wyczyść korzyści w takich scenariuszach.

**Aplikacja musi działać w przeglądarkach bez obsługi języka JavaScript**

Aplikacje sieci Web, które muszą działać w przeglądarkach z ograniczoną liczbą lub brak obsługi języka JavaScript powinna być zapisana przy użyciu przepływów pracy aplikacji sieci web tradycyjnych lub co najmniej można przełączyć się na takie zachowanie. Źródła wymagają JavaScript po stronie klienta do funkcji; Jeśli nie jest dostępna, źródła nie są dobrym rozwiązaniem.

**Zespół nie może rozpoznać metody JavaScript i TypeScript**

Jeśli zespół nie może rozpoznać JavaScript i TypeScript, ale są zaznajomieni z tworzenia aplikacji sieci web po stronie serwera, prawdopodobnie będzie mogła dostarczać szybciej niż JEDNOSTRONICOWEJ aplikacji sieci web tradycyjnych. Chyba, że celem jest uczenia źródła programu lub zapewnianej przez SPA środowisko użytkownika jest wymagana, aplikacje sieci web tradycyjnych są bardziej wydajnej pracy wybór dla zespołów, które znają ich tworzenia.

## <a name="when-to-choose-spas"></a>Kiedy należy wybrać źródła

Poniżej znajduje się bardziej szczegółowy opis kiedy wybierz styl aplikacje jednostronicowe rozwoju aplikacji sieci web.

**Aplikacja musi ujawniać interfejs użytkownika sformatowanego z wielu funkcji**

Źródła może obsługiwać rozbudowane funkcje po stronie klienta, które nie wymagają ponownego ładowania strony, gdy użytkownicy podjęcia działań lub przechodzenie między obszarami aplikacji. Źródła może załadować szybciej, pobieranie danych w tle, a akcje użytkownika są bardziej elastyczny, ponieważ przeładowania całej stronie występują rzadko. Źródła może obsługiwać aktualizacje przyrostowe zapisywanie częściowo ukończone formularze lub dokumenty bez użytkownikowi konieczności kliknij przycisk przesyłania formularza. Źródła można znacznie łatwiej niż tradycyjne aplikacje obsługują sformatowanego zachowania po stronie klienta, takich jak przeciągania i upuszczania. Źródła mogą służyć do uruchamiania w trybie rozłączonym wprowadzanie aktualizacji do modelu po stronie klienta, które są synchronizowane ostatecznie do serwera, po ponownym nawiązaniu połączenia. Należy wybrać aplikację stylów SPA, gdy wymagania dotyczące aplikacji obejmują zaawansowane funkcje, które wykracza poza oferują typowe formularzy HTML.

Należy zauważyć, że często źródła implementuje funkcje, które są wbudowane w aplikacji sieci web tradycyjne, takie jak wyświetlanie łatwy do rozpoznania adresu URL na adres pasku odzwierciedlające bieżącej operacji (i umożliwienie użytkownikom do zakładki i link bezpośredni do tego adresu URL powrócić do niego). Źródła powinny również zezwala użytkownikom na używanie przeglądarki przycisków Wstecz i dalej z wynikami, które nie będą niespodzianek je.

**Zespół jest znajomość języka JavaScript i/lub TypeScript programowanie**

Zapisywanie źródła wymaga znajomości języka JavaScript i/lub TypeScript i technik programowania po stronie klienta i bibliotek. Zespół powinien być właściwe w pisaniu nowoczesnych JavaScript przy użyciu platformy SPA jak kątową.

> ### <a name="references--spa-frameworks"></a>Odwołania — SPA struktur
> - **AngularJS**  
> <https://angularjs.org/>
> - **Porównanie 4 JavaScript popularnych struktur**  
> <https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks>

**Aplikacja już musi ujawniać interfejsu API dla innych klientów (wewnętrzny lub publiczny)**

Jeśli interfejs API sieci web jest już obsługiwane dla innych klientów, może wymagać mniej działań zmierzających do utworzenia implementacji SPA, który korzysta z poniższych interfejsów API, zamiast odtwarzanie logikę w postaci po stronie serwera. Źródła wprowadzić zwiększone użycie interfejsów API sieci web do wykonywania zapytań i aktualizacji danych, jak użytkownicy korzystają z aplikacji.

## <a name="decision-table--traditional-web-or-spa"></a>Tabela decyzji — tradycyjnych sieci Web lub SPA

W poniższej tabeli decyzji przedstawiono niektóre podstawowe czynniki, które należy wziąć pod uwagę podczas wybierania między aplikacją sieci web tradycyjnych i SPA.

  | **Współczynnik** | **Aplikacja sieci Web tradycyjny** | **Aplikacja jednostronicowa** |
  |---|---|---|
  | Wymagane zespołu znajomość JavaScript/TypeScript | **Minimalny** | **Wymagane** |
  | Obsługa przeglądarki bez obsługi skryptów | **Obsługiwane** | **Nieobsługiwane** |
  | Zachowanie minimalnego aplikacji po stronie klienta | **Well-Suited** | **Zbyt obszerne** |
  | Wymagania interfejsu użytkownika zaawansowane, złożone | **Ograniczone** | **Well-Suited** |

>[!div class="step-by-step"]
[Poprzednie] (modern-web aplikacje characteristics.md) [dalej](architectural-principles.md)
