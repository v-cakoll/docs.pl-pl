---
title: Weryfikacja po stronie klienta (Sprawdzanie poprawności w warstwy prezentacji)
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Weryfikacja po stronie klienta (Sprawdzanie poprawności w warstwy prezentacji)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c61a08566492a59090b19f99aaf97b5f6082c1fb
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104572"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Weryfikacja po stronie klienta (Sprawdzanie poprawności w warstwy prezentacji)

Nawet wtedy, gdy źródłem prawdy jest model domeny, a ostatecznie musi mieć weryfikacji na poziomie modelu domeny, sprawdzania poprawności, nadal mogą być obsługiwane zarówno po stronie klienta, jak i poziom modelu domeny (po stronie serwera).

Weryfikacja po stronie klienta jest doskonałym ułatwienia dla użytkowników. Zapisuje w przeciwnym razie poświęcić czas oczekiwania na obiegu do serwera, który może zwrócić błędy sprawdzania poprawności. W terminologii biznesowej nawet kilka części sekundy pomnożone setki razy każdego dnia dodaje do dużo czasu, wydatków i frustracji spowodowanej. Proste i bezpośrednie weryfikacji umożliwia użytkownikom wydajniejszą pracę i tworzy lepszą jakość danych wejściowych i wyjściowych.

Tak samo, jak model widoku i modelu domeny są różne, sprawdzanie poprawności modelu widoku i weryfikacji modelu domeny może być podobne, ale następnie służą do różnych celów. Jeśli wiadomo o suchej (nie powtarzaj samodzielnie zasada), należy wziąć pod uwagę w tym przypadku ponowne użycie kodu może to także oznaczać sprzężenia, czy w aplikacjach dla przedsiębiorstw jest ważniejsze nie do sprzęgania po stronie serwera po stronie klienta niż wykonaj suchej zasady.

Nawet przy użyciu weryfikacji po stronie klienta, należy zawsze sprawdzić poleceniach lub wejściowych DTOs w kodzie serwera, ponieważ serwer interfejsy API są zaatakowania. Zazwyczaj zastosowanie obu jest najlepsze rozwiązanie, ponieważ jeśli masz aplikację klienta z punktu widzenia środowiska użytkownika jest najlepszym rozwiązaniem jest aktywne i nie zezwala użytkownikowi na wprowadzenie nieprawidłowe informacje.

W związku z tym w kodzie po stronie klienta zazwyczaj sprawdzania poprawności ViewModels. Można również sprawdzić poprawności klienta dane wyjściowe poleceń lub DTOs przed wysłaniem ich do usług.

Implementacja weryfikacji po stronie klienta zależy od tego, jakiego rodzaju aplikacji klienckiej tworzenia. Będzie inny są sprawdzanie poprawności danych w sieci web aplikacji sieci web MVC za pomocą większość kodu w aplikacji sieci web SPA przy użyciu tego sprawdzania poprawności jest kodowany w JavaScript i TypeScript, .NET lub aplikacji mobilnej na stałe dzięki platformie Xamarin i C\#.

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="validation-in-xamarin-mobile-apps"></a>Sprawdzanie poprawności w aplikacji mobilnych Xamarin

-   **Sprawdź poprawność tekst wejściowy i argument Pokaż błędy**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Wywołanie zwrotne weryfikacji**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Sprawdzanie poprawności w aplikacji platformy ASP.NET Core

-   **Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Sprawdzanie poprawności w SPA Web apps (kątowego 2 TypeScript, JavaScript)

-   **Ado Kukic. Dyrektywy angular weryfikacji formularza 2** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **Sprawdzanie poprawności formularza**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Sprawdzanie poprawności.** Błyskawicznie dokumentacji.
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

Podsumowując są najważniejsze pojęcia w odniesieniu do sprawdzania poprawności:

-   Jednostki i agreguje powinien wymuszać własnych spójności i ważność "zawsze". Łączny certyfikaty główne są odpowiedzialne za spójności obejmujące wiele urządzeń w ramach tej samej agregacji.

-   Jeśli uważasz, że jednostka musi podać nieprawidłowy stan, należy wziąć pod uwagę przy użyciu modelu innego obiektu — na przykład przy użyciu tymczasowego DTO, dopóki nie zostaną utworzone jednostki końcowej domeny.

-   Należy utworzyć kilka powiązanych obiektów, takich jak agregacji, są one tylko prawidłowe po wszystkich z nich zostały utworzone, należy wziąć pod uwagę przy użyciu wzorca fabryki.

-   Struktury weryfikacji najlepiej służą w określonych warstw, takich jak warstwy prezentacji lub warstwy aplikacji/usługi, ale zwykle nie warstwy modelu domeny, ponieważ będzie potrzebny do wykonania silne zależności w ramach infrastruktury.

-   W większości przypadków nadmiarowe weryfikacji po stronie klienta jest dobra, ponieważ aplikacji mogą być aktywne.


>[!div class="step-by-step"]
[Poprzednie](domain-model-layer-validations.md)
[dalej](domain-events-design-implementation.md)
