---
title: Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Poznaj kluczowe pojęcia związane z walidacją po stronie klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295996"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)

Nawet wtedy, gdy źródło prawdy jest modelem domeny i ostatecznie należy przeprowadzić weryfikację na poziomie modelu domeny, sprawdzanie poprawności może być nadal obsługiwane zarówno na poziomie modelu domeny (po stronie serwera), jak i w interfejsie użytkownika (po stronie klienta).

Sprawdzanie poprawności po stronie klienta jest doskonałym rozwiązaniem dla użytkowników. Pozwala to zaoszczędzić czas oczekiwania na przekazanie komunikacji z serwerem, który może zwrócić błędy walidacji. W przypadku warunków handlowych nawet kilka części sekund pomnożone przez setki razy każdy dzień dodaje do dużo czasu, wydatków i frustrację. Bezpośrednie i natychmiastowe sprawdzanie poprawności umożliwia użytkownikom wydajniejszą pracę i generowanie lepszych danych wejściowych i wyjściowych.

Podobnie jak model widoku i model domeny różnią się, sprawdzanie poprawności modelu i sprawdzanie poprawności modelu domeny może być podobne, ale w innym celu. Jeśli chodzi o zawartość suchej (Nie powtarzaj się zasady), należy rozważyć, że w tym przypadku ponowne użycie kodu może również oznaczać sprzężenie, a w aplikacjach korporacyjnych ważniejsze jest, aby nie podłączać po stronie klienta strony serwera niż w przypadku wypełniania wysuszonej zasady.

Nawet w przypadku korzystania z walidacji po stronie klienta należy zawsze sprawdzać poprawność poleceń lub danych wejściowych DTO w kodzie serwera, ponieważ interfejsy API serwera są możliwym do zaatakowania. Zwykle najlepszym trafieniem jest to, że jeśli masz aplikację kliencką, z perspektywy środowiska użytkownika najlepiej jest ją uaktywnić i nie zezwalać użytkownikowi na wprowadzanie nieprawidłowych informacji.

W związku z tym w kodzie po stronie klienta zwykle sprawdzane jest modele widoków. Możesz również zweryfikować DTO danych wyjściowych klienta lub polecenia przed wysłaniem ich do usług.

Implementacja weryfikacji po stronie klienta zależy od rodzaju kompilowanej aplikacji klienckiej. Będzie ona różna w przypadku sprawdzania poprawności danych w aplikacji sieci Web MVC w sieci Web z większością kodu w programie .NET, aplikacja sieci Web SPA z tą walidacją jest zakodowana w języku JavaScript lub TypeScript lub w aplikacji mobilnej C#kodowanej przy użyciu platformy Xamarin i.

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="validation-in-xamarin-mobile-apps"></a>Walidacja w usłudze Xamarin Mobile Apps

- **Weryfikuj wprowadzanie tekstu i Wyświetlaj błędy** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-  \ **wywołania zwrotnego walidacji**
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>Walidacja w aplikacjach ASP.NET Core

- **Rick Anderson. Dodawanie \ weryfikacji**
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Walidacja w aplikacjach sieci Web SPA (kątowy 2, TypeScript, JavaScript)

- **KuKic ADO. \ walidacji formularza** z kątem 2
  <https://scotch.io/tutorials/angular-2-form-validation>

-  \ **walidacji formularza**
  <https://angular.io/guide/form-validation>

- **Zatwierdzenia.** Dokumentacja Breeze. \
  <https://breeze.github.io/doc-js/validation.html>

Podsumowując, są to najważniejsze koncepcje dotyczące weryfikacji:

- Jednostki i agregacje powinny wymusić swoją własną spójność i mieć wartość "zawsze prawidłowy". Zagregowane elementy główne są odpowiedzialne za spójność w ramach tej samej agregacji.

- Jeśli uważasz, że jednostka musi wprowadzić nieprawidłowy stan, rozważ użycie innego modelu obiektów — na przykład przy użyciu tymczasowej DTO do momentu utworzenia końcowej jednostki domeny.

- Jeśli musisz utworzyć kilka powiązanych obiektów, takich jak agregowanie, i są one prawidłowe tylko wtedy, gdy wszystkie z nich zostały utworzone, rozważ użycie wzorca fabryki.

- W większości przypadków posiadanie nadmiarowej weryfikacji na stronie klienta jest dobre, ponieważ aplikacja może być aktywna.

>[!div class="step-by-step"]
>[Poprzedni](domain-model-layer-validations.md)
>[Następny](domain-events-design-implementation.md)
