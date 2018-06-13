---
title: Projektowanie poprawności warstwy modelu domeny
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie poprawności warstwy modelu domeny
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce3cb0c79cbd492224ce1d4ecb25cd02062f11cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578953"
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Projektowanie poprawności warstwy modelu domeny

W DDD można traktować jako invariants reguł sprawdzania poprawności. Podstawowa odpowiedzialność agregacji jest wymuszenie invariants zachowuje zmiany stanu dla wszystkich obiektów w tym agregacji.

Domeny jednostek powinna być zawsze prawidłowe jednostki. Istnieją pewne invariants dla obiekt, który powinien mieć zawsze wartość PRAWDA. Na przykład obiekt elementu kolejności zawsze musi mieć ilość, która musi być dodatnią liczbą całkowitą, a także nazwę artykułu i ceny. W związku z tym wymuszania invariants jest odpowiedzialny za jednostek domeny (szczególnie elementu głównego agregacji) i do obiektu jednostki nie powinien móc istnieje nie są prawidłowe. Niezmienna reguły po prostu są wyrażane jako kontrakty i wyjątków lub powiadomienia są wywoływane, gdy są one naruszone.

To uzasadnienie jest wiele usterek wystąpić, ponieważ obiekt jest w stanie, który powinien być nigdy nie był w. Poniżej przedstawiono dobrej wyjaśnienie z małych Gregowi w [online dyskusji](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Proponować Przyjrzyjmy się, że mamy teraz SendUserCreationEmailService, pobierającej UserProfile... jak można możemy racjonalizacja w tej usługi, nazwa nie jest zerowa? Czy możemy sprawdź go ponownie? Lub bardziej prawdopodobne... właśnie nie zostanie odblokowane można sprawdzić i "nadzieję najlepszą" — Mamy nadzieję, że ktoś bothered do weryfikowania go przed wysłaniem do użytkownika. Oczywiście przy użyciu TDD pierwszy testów, które firma Microsoft powinien zapisu, jest to, że wysyłania się klientów z zerową nazwą czy powinna Zgłoś błąd. Jednak po Rozpoczniemy wielokrotnie pisania tego rodzaju testy Zdajemy sobie sprawę... "oczekiwania, jeśli firma Microsoft nigdy nie mogą nazwę, stając się wartości null nie mamy wszystkie te testy"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implementowanie operacji sprawdzania poprawności w warstwy modelu domeny

Sprawdzanie poprawności zwykle są implementowane w konstruktorów jednostek domeny lub metody aktualizowanych jednostki. Istnieje wiele sposobów, aby zaimplementować metodę sprawdzania, takie jak weryfikowanie danych i wywoływanie wyjątków w przypadku niepowodzenia weryfikacji. Istnieją również bardziej zaawansowanych wzorców, takich jak przy użyciu wzorca specyfikacji dla operacji sprawdzania poprawności i wzorzec powiadomień zwrócić kolekcję błędów zamiast zwracać wyjątek dla każdego weryfikacji występujące.

### <a name="validating-conditions-and-throwing-exceptions"></a>Sprawdzanie poprawności warunki i zgłaszanie wyjątków

Poniższy przykład kodu pokazuje najprostsza metoda weryfikacji w jednostce domeny przez wywołanie wyjątku. Tabela odwołań na końcu tej sekcji przedstawiono łącza do bardziej zaawansowanych implementacje na podstawie wzorców, które wcześniej Omówiliśmy.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Przykład lepsze wskazywałoby konieczność zapewnienia wewnętrzny stan nie został zmieniony lub że wszystkie mutacji metody wystąpił. Na przykład następująca implementacja spowoduje obiektu w nieprawidłowym stanie:

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i Miasto już zostały zmienione. Który może być adres nieprawidłowy.

Podejście podobne można używać w Konstruktorze jednostki, który wywołał wyjątek, aby upewnić się, że obiekt jest prawidłowy, po jego utworzeniu.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>Za pomocą atrybutów sprawdzania poprawności na adnotacje danych na podstawie modelu

Innym rozwiązaniem jest używanie na adnotacje danych na podstawie atrybutów sprawdzania poprawności. Atrybuty weryfikacji umożliwiają konfigurowanie weryfikacji modelu, który jest podobny koncepcyjnie do sprawdzania poprawności dla pól w tabelach bazy danych. W tym ograniczenia, takie jak przypisywanie typów danych lub wymagane pola. Inne typy weryfikacji obejmują stosowania wzorców do danych do wymuszania reguł biznesowych, takich jak numer karty kredytowej lub numer telefonu lub adres e-mail. Atrybuty weryfikacji ułatwiają wymuszanie wymagania.

Jednak jak pokazano w poniższym kodzie, to takie podejście może być zbyt niepożądanych w modelu DDD, ponieważ trwa zależności na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, które należy wywołać z kontrolerów MVC. Sprawdzanie poprawności modelu występuje przed wywoływaną akcję każdego kontrolera i metody kontrolera odpowiedzialność za inspekcji wyników wywołania ModelState.IsValid i odpowiednio zareagować. Zależy decyzji o użyciu go ściśle powiązane ma modelu, który ma być z tej infrastruktury.

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

Jednak z punktu widzenia DDD, model domeny jest najlepiej pozostawić gotowa przy użyciu wyjątków w metodach zachowania użytkownika jednostki lub implementując wzorce specyfikację i powiadomień do wymuszania reguł sprawdzania poprawności. Struktury sprawdzania poprawności podobnie jak adnotacji danych w ASP.NET Core lub innych platform sprawdzania poprawności podobnie jak FluentValidation przenoszenia wymagane do wywołania struktury aplikacji. Na przykład podczas wywoływania metody ModelState.IsValid w adnotacjach danych, należy wywołać kontrolery ASP.NET.

Go wykrywanie używania adnotacji danych w warstwie aplikacji w klasach ViewModel (a nie jednostek domeny), które będzie akceptować dane wejściowe, aby umożliwić sprawdzanie poprawności modelu w ramach warstwy interfejsu użytkownika. Jednak to nie należy przypisywać na wyłączenie sprawdzania poprawności w ramach modelu domeny.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Sprawdzanie poprawności jednostek zaimplementowanie wzoru specyfikacji i powiadomienia

Na koniec bardziej złożonych podejście do wykonania operacji sprawdzania poprawności w modelu domeny jest zaimplementowanie wzorzec specyfikacji w połączeniu z wzorcem powiadomień zgodnie z objaśnieniem w niektórych dodatkowych zasobów wymienionych później.

Warto zauważyć, że umożliwia także tylko w jednej z tych wzorców — na przykład, sprawdzanie poprawności ręcznie z instrukcji sterowania, ale przy użyciu wzorca powiadomień stosu i zwracający listę błędów weryfikacji.

### <a name="using-deferred-validation-in-the-domain"></a>Przy użyciu odroczone sprawdzanie poprawności w domenie

Istnieją różne metody radzenia sobie z odroczone sprawdzanie poprawności w domenie. W jego książce [projekt Implementing Domain-Driven](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon omówiono w sekcji weryfikacji.

### <a name="two-step-validation"></a>Weryfikacja dwuetapowa

Należy również rozważyć weryfikacji dwuetapowej. Użyj weryfikacji na poziomie pola na polecenie obiekty Transfer danych (DTOs) i weryfikacji na poziomie dla domeny wewnątrz jednostki. Można to zrobić, zwracając obiekt wyniku zamiast wyjątków w celu ułatwienia postępowania z błędami sprawdzania poprawności.

Za pomocą pola weryfikacji przy użyciu adnotacji danych, na przykład nie duplikowania definicji sprawdzania poprawności. Wykonywanie, jednak może być zarówno po stronie serwera i po stronie klienta w przypadku DTOs (polecenia i ViewModels, na przykład).

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Rachel Appel. Wprowadzenie do sprawdzania poprawności modelu w programie ASP.NET MVC Core**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Pole Fowler. Zastępowanie zgłaszanie wyjątków z powiadomień w operacji sprawdzania poprawności**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Specyfikacja i wzorce powiadomień**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **LEV Gorodinski. Sprawdzanie poprawności w projekcie oparte na domenie (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Gniazdo Colin. Weryfikacja modelu domeny**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. Sprawdzanie poprawności w świecie DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Poprzednie] (wyliczenie klasy over wyliczenia types.md) [dalej] (po stronie klienta — ruch validation.md)
