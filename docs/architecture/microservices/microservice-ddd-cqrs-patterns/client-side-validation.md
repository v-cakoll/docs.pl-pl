---
title: Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się z kluczowymi pojęciami sprawdzania poprawności po stronie klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 44c1e9fa280b19fcee87d4d1cdfcaa2ab9462f27
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988704"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)

Nawet wtedy, gdy źródłem prawdy jest model domeny i ostatecznie musi mieć sprawdzania poprawności na poziomie modelu domeny, sprawdzanie poprawności nadal mogą być obsługiwane zarówno na poziomie modelu domeny (po stronie serwera) i interfejsu użytkownika (po stronie klienta).

Walidacja po stronie klienta to duże udogodnienie dla użytkowników. Oszczędza czas, który w przeciwnym razie spędzają czekając na podróż w obie strony do serwera, który może zwracać błędy sprawdzania poprawności. W kategoriach biznesowych, nawet kilka ułamków sekund pomnożone setki razy dziennie dodaje się do dużo czasu, wydatków i frustracji. Prosta i natychmiastowa walidacja umożliwia użytkownikom wydajniejszą pracę i uzyskanie lepszej jakości danych wejściowych i wyjściowych.

Podobnie jak model widoku i model domeny są różne, sprawdzanie poprawności modelu widoku i sprawdzania poprawności modelu domeny może być podobne, ale służyć innemu celowi. Jeśli obawiasz się dry (zasada Nie powtarzaj siebie), należy wziąć pod uwagę, że w tym przypadku ponowne użycie kodu może również oznaczać sprzężenie, a w aplikacjach korporacyjnych ważniejsze jest, aby nie łączyć strony serwera po stronie klienta niż przestrzegać zasady DRY.

Nawet podczas korzystania z sprawdzania poprawności po stronie klienta, należy zawsze sprawdzić poprawność poleceń lub wejściowych DTO w kodzie serwera, ponieważ interfejsy API serwera są możliwe wektor ataku. Zazwyczaj robienie obu jest najlepszym rozwiązaniem, ponieważ jeśli masz aplikację kliencką, z punktu widzenia środowiska użytkownika, najlepiej jest być proaktywnym i nie zezwalać użytkownikowi na wprowadzanie nieprawidłowych informacji.

W związku z tym w kodzie po stronie klienta zazwyczaj sprawdź poprawność ViewModels. Można również sprawdzić poprawność danych DTO danych wyjściowych klienta lub poleceń przed wysłaniem ich do usług.

Implementacja sprawdzania poprawności po stronie klienta zależy od tego, jakiego rodzaju aplikacji klienckiej, którą budujesz. Będzie inaczej, jeśli sprawdzasz dane w internetowej aplikacji sieci web MVC z większością kodu w .NET, aplikacji sieci web SPA z tą weryfikacją kodowane w javascript lub TypeScript lub aplikacji mobilnej zakodowanej za pomocą platformy Xamarin i C#.

## <a name="additional-resources"></a>Zasoby dodatkowe

### <a name="validation-in-xamarin-mobile-apps"></a>Sprawdzanie poprawności w aplikacjach mobilnych platformy Xamarin

- **Sprawdzanie poprawności wprowadzania tekstu i pokazywalanie błędów** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Wywołanie zwrotne w weryfikacji** \
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>Sprawdzanie poprawności w aplikacjach ASP.NET Core

- **Rick Anderson. Dodawanie sprawdzania poprawności** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Sprawdzanie poprawności w aplikacjach SIECI Web SPA (kątowe 2, TypeScript, JavaScript)

- **Ado Kukic. Sprawdzanie poprawności formularza kątowego 2** \
  <https://scotch.io/tutorials/angular-2-form-validation>

- **Sprawdzanie poprawności formularza** \
  <https://angular.io/guide/form-validation>

- **Sprawdzania poprawności.** Dokumentacja breeze. \
  <https://breeze.github.io/doc-js/validation.html>

Podsumowując, są to najważniejsze pojęcia dotyczące walidacji:

- Jednostki i agregaty powinny wymuszać własną spójność i być "zawsze ważne". Zagregowane katalogi główne są odpowiedzialne za spójność wielu jednostek w ramach tego samego agregacji.

- Jeśli uważasz, że jednostka musi wprowadzić nieprawidłowy stan, należy rozważyć użycie innego modelu obiektu — na przykład przy użyciu tymczasowego celu duchcę, dopóki nie utworzysz ostatecznej jednostki domeny.

- Jeśli trzeba utworzyć kilka powiązanych obiektów, takich jak agregacja i są one prawidłowe tylko po utworzeniu wszystkich z nich, należy rozważyć użycie wzorzec Factory.

- W większości przypadków o nadmiarowe sprawdzania poprawności po stronie klienta jest dobry, ponieważ aplikacja może być aktywne.

>[!div class="step-by-step"]
>[Poprzedni](domain-model-layer-validations.md)
>[następny](domain-events-design-implementation.md)
