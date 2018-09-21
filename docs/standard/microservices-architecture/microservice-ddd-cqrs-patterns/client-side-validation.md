---
title: Weryfikacja po stronie klienta (Weryfikacja w warstwach prezentacji)
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Weryfikacja po stronie klienta (Weryfikacja w warstwach prezentacji)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 70a1f716797e03acdcbf1c58d4b0302449d98fa9
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519292"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Weryfikacja po stronie klienta (Weryfikacja w warstwach prezentacji)

Nawet wtedy, gdy źródło prawdziwych danych jest modelem domeny i ostatecznie konieczne jest posiadanie weryfikacji na poziomie modelu domeny, sprawdzania poprawności, nadal mogą być obsługiwane na poziomie modelu domeny (po stronie serwera) i po stronie klienta.

Weryfikacja po stronie klienta jest doskonałym wygodę dla użytkowników. Zaoszczędzić czas, który one byłby przeznaczany na oczekiwanie na komunikację dwustronną do serwera, który może zwrócić błędy sprawdzania poprawności. W terminologii biznesowej nawet kilka użycie ułamkowych części sekundy pomnożone setki razy każdego dnia dodaje do mnóstwo czasu i pieniędzy oraz Rozczarowanie. Proste i natychmiastowe sprawdzanie poprawności umożliwia użytkownikom bardziej wydajną pracę i wygenerować lepszą jakość danych wejściowych i wyjściowych.

Tak, jak model widoku i modelu domeny są różne, sprawdzanie poprawności modelu widoku i sprawdzanie poprawności modelu domeny mogą być podobne, ale następnie spełniać różne zadania. Jeśli dane o PRÓBNEGO (nie należy powtórzyć samodzielnie zasada), należy wziąć pod uwagę, w tym przypadku ponowne wykorzystanie kodu może również oznaczać sprzężenia i w aplikacjach dla przedsiębiorstw jest niezwykle ważne nie połączenie po stronie serwera na komputerach klienckich, niż się postępuj zgodnie z zasadą susz.

Nawet korzystając z weryfikacji po stronie klienta, należy zawsze sprawdzić poleceń lub wejściowych dto w kodzie serwera, ponieważ serwer interfejsy API są zaatakowania. Zwykle zastosowanie obu podejść jest najlepsze rozwiązanie, ponieważ w przypadku aplikacji klienckiej, z punktu widzenia UX najlepiej stosować proaktywne podejście i uniemożliwia użytkownikowi wprowadzanie nieprawidłowe informacje.

W związku z tym w kodzie po stronie klienta zazwyczaj zweryfikowanie modele widoków. Można również sprawdzić poprawności klienta przed wysłaniem ich do usługi danych wyjściowych dto ani nowych poleceń.

Implementacja weryfikacji po stronie klienta zależy od tego, jakiego rodzaju aplikacji klienckiej, którą tworzysz. Będzie on być inny, Jeśli zatwierdzasz danych w sieci web aplikacji sieci web MVC za pomocą większość kodu na platformie .NET, SPA aplikacji sieci web za pomocą tego sprawdzania poprawności są kodowane w języku JavaScript, TypeScript, czy lub aplikacji mobilnej kodowanego z rozwiązaniami Xamarin i C#.

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="validation-in-xamarin-mobile-apps"></a>Sprawdzanie poprawności w aplikacjach mobilnych platformy Xamarin

-   **Sprawdź poprawność tekst wejściowy i Pokaż błędy**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Wywołanie zwrotne weryfikacji**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Sprawdzanie poprawności w aplikacji platformy ASP.NET Core

-   **Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Sprawdzanie poprawności w SPA, Web apps (Angular 2, TypeScript, JavaScript)

-   **Ado Kukic. Platformy angular 2 formularz weryfikacji**
    [*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **Weryfikacji formularza**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Sprawdzanie poprawności.** Szybka i bezproblemowa dokumentację.
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

Podsumowując poniżej przedstawiono najważniejsze pojęcia związane z weryfikacją:

- Jednostki i agregacji należy wymusić spójność własne i ważność "zawsze". Katalogi główne agregacji są odpowiedzialne za spójność wielu jednostek w ramach tej samej agregacji.

- Jeśli uważasz, że jednostka musi podać nieprawidłowy stan, należy wziąć pod uwagę przy użyciu modelu innego obiektu — na przykład za pomocą tymczasowy obiekt DTO, dopóki nie utworzysz jednostki końcowej domeny.

- Jeśli musisz utworzyć kilka powiązanych obiektów, takich jak agregacji, i są tylko prawidłowe gdy wszystkie z nich zostały utworzone, należy wziąć pod uwagę przy użyciu wzorca fabryki.

- Struktury sprawdzania poprawności najlepiej sprawdzają w określonych warstw, np. Warstwa prezentacji lub warstwie aplikacji/usługi, ale zwykle nie w warstwie modelu domeny, ponieważ należy skorzystać z silną zależności w ramach infrastruktury.

- W większości przypadków nadmiarowe weryfikacji po stronie klienta jest dobre rozwiązanie, ponieważ aplikacja może być aktywne.

>[!div class="step-by-step"]
[Poprzednie](domain-model-layer-validations.md)
[dalej](domain-events-design-implementation.md)