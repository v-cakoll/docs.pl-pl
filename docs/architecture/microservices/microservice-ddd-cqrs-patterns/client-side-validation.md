---
title: Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się z kluczowymi pojęciami sprawdzania poprawności po stronie klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295996"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)

Nawet wtedy, gdy źródłem prawdy jest model domeny i ostatecznie musisz mieć sprawdzanie poprawności na poziomie modelu domeny, sprawdzanie poprawności nadal może być obsługiwane zarówno na poziomie modelu domeny (po stronie serwera), jak i po stronie interfejsu i interfejsu (po stronie klienta).

Weryfikacja po stronie klienta jest dużą wygodą dla użytkowników. Pozwala to zaoszczędzić czas, który w przeciwnym razie spędzają by czekając na podróż w obie strony do serwera, który może zwrócić błędy sprawdzania poprawności. W kategoriach biznesowych nawet kilka ułamków sekund pomnożonych setki razy dziennie daje dużo czasu, kosztów i frustracji. Prosta i natychmiastowa walidacja umożliwia użytkownikom wydajniejszą pracę i zapewnia lepszą jakość danych wejściowych i wyjściowych.

Podobnie jak model widoku i model domeny są różne, sprawdzanie poprawności modelu widoku i sprawdzania poprawności modelu domeny może być podobne, ale służyć innemu celowi. Jeśli obawiasz się o DRY (zasada Nie powtarzaj się), należy wziąć pod uwagę, że w tym przypadku ponowne użycie kodu może również oznaczać sprzężenie, a w aplikacjach korporacyjnych ważniejsze jest, aby nie łączyć strony serwera po stronie klienta niż przestrzegać zasady DRY.

Nawet podczas sprawdzania poprawności po stronie klienta, zawsze należy sprawdzić poprawność poleceń lub danych do danych wejściowych w kodzie serwera, ponieważ interfejsy API serwera są możliwe wektora ataku. Zazwyczaj robienie obu jest najlepszym rozwiązaniem, ponieważ jeśli masz aplikację kliencką, z punktu widzenia UX, najlepiej jest być proaktywnym i nie zezwalać użytkownikowi na wprowadzanie nieprawidłowych informacji.

W związku z tym w kodzie po stronie klienta zazwyczaj sprawdzanie poprawności ViewModels. Można również sprawdzić poprawność danych dko danych wyjściowych klienta lub poleceń przed wysłaniem ich do usług.

Implementacja sprawdzania poprawności po stronie klienta zależy od rodzaju aplikacji klienckiej, którą budujesz. Będzie inaczej, jeśli sprawdzasz sprawdzanie poprawności danych w internetowej aplikacji sieci Web MVC z większością kodu w .NET, aplikacja sieci web SPA z tą weryfikacją kodowana w języku JavaScript lub TypeScript lub aplikacja mobilna kodowana za pomocą platformy Xamarin i C#.

## <a name="additional-resources"></a>Zasoby dodatkowe

### <a name="validation-in-xamarin-mobile-apps"></a>Walidacja w aplikacjach mobilnych Platformy Xamarin

- **Sprawdzanie poprawności wprowadzania tekstu i pokazywanie błędów** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Wywołanie wywołania sprawdzania poprawności** \
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>Sprawdzanie poprawności w aplikacjach ASP.NET Core

- **Rick Anderson. Dodawanie sprawdzania poprawności** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Sprawdzanie poprawności w aplikacjach SIECI WEB SPA (Angular 2, TypeScript, JavaScript)

- **Ado Kukic. Kanciasta 2 Sprawdzanie poprawności formularza** \
  <https://scotch.io/tutorials/angular-2-form-validation>

- **Sprawdzanie poprawności formularza** \
  <https://angular.io/guide/form-validation>

- **Sprawdzania poprawności.** Dokumentacja breeze. \
  <https://breeze.github.io/doc-js/validation.html>

Podsumowując, są to najważniejsze pojęcia dotyczące walidacji:

- Jednostki i agregaty powinny egzekwować własną spójność i być "zawsze ważne". Zagregowane katalogi główne są odpowiedzialne za spójność wielu jednostek w ramach tej samej agregacji.

- Jeśli uważasz, że jednostka musi wprowadzić nieprawidłowy stan, należy rozważyć użycie innego modelu obiektu — na przykład przy użyciu tymczasowego dto do czasu utworzenia jednostki domeny końcowej.

- Jeśli trzeba utworzyć kilka powiązanych obiektów, takich jak agregacji i są one prawidłowe tylko po ich utworzeniu wszystkie z nich, należy rozważyć użycie wzorca fabryki.

- W większości przypadków posiadanie nadmiarowej weryfikacji po stronie klienta jest dobre, ponieważ aplikacja może być proaktywna.

>[!div class="step-by-step"]
>[Poprzedni](domain-model-layer-validations.md)
>[następny](domain-events-design-implementation.md)
