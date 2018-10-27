---
title: Projektowanie reguł weryfikacji w warstwie modelu domeny
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Projektowanie reguł weryfikacji w warstwie modelu domeny
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6ff325bb062da2ebff815fc847d2247707a0bf7f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188056"
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Projektowanie reguł weryfikacji w warstwie modelu domeny

W DDD reguł sprawdzania poprawności można traktować jako invariants. Podstawowa odpowiedzialność agregacji jest wymusić invariants na zmiany stanu dla wszystkich jednostek w ramach tej agregacji.

Jednostki domeny powinny być zawsze prawidłowe jednostki. Istnieją pewne invariants dla obiektu, który powinien zawsze być prawdziwe. Na przykład obiekt elementu kolejności zawsze musi mieć ilość, który musi być dodatnią liczbą całkowitą, a także nazwę artykułu i ceny. Dlatego wymuszania invariants odpowiada jednostki domeny (zwłaszcza w zakresie głównego agregacji) i obiektu jednostki nie powinno być możliwe istnieje nie są prawidłowe. Zasad niezmiennej po prostu są wyrażane jako kontraktów i powiadomienia lub wyjątki są zgłaszane w przypadku ich naruszenia.

Uzasadnienie to to, że wiele błędów być fakt, że obiekty są w stanie, które powinny mieć nigdy nie był w. Poniżej przedstawiono dobry opis z Grega Younga w [dyskusji](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Zaproponuj Załóżmy że mamy teraz SendUserCreationEmailService, wykorzystującej UserProfile... jak można możemy racjonalizować w tej usłudze, że nazwa nie jest null? Czy możemy sprawdzić go ponownie? Lub bardziej prawdopodobne... po prostu nie zostanie odblokowane można sprawdzić i "najlepszą nadzieję, że" — Mamy nadzieję, że ktoś bothered, aby zweryfikować, czy przed wysłaniem ich do Ciebie. Oczywiście za pomocą TDD pierwszy testy, które firma Microsoft należy pisania, jest to, że jeśli wysyła się klientów z nazwą wartości null, należy je zgłosić błąd. Jednak gdy Rozpoczniemy wielokrotnie pisania tego rodzaju testy Zdajemy sobie sprawę... "oczekiwania, jeśli firma Microsoft nigdy nie mogą nazwę, aby stać się o wartości null nie mamy wszystkich tych testów"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implementowanie walidacji w warstwie modelu domeny

Sprawdzanie poprawności zwykle są implementowane w konstruktorach jednostki domeny lub za pomocą metod, które mogą aktualizować jednostki. Istnieje wiele sposobów implementowania operacji sprawdzania poprawności, takie jak weryfikowanie danych i wywoływanie wyjątków w przypadku niepowodzenia weryfikacji. Istnieją również bardziej zaawansowane wzorców, takich jak przy użyciu wzorca specyfikacji dla sprawdzanie poprawności i wzorzec powiadomień do zwrócenia zbierania błędów zamiast zwracać wyjątek dla każdego sprawdzania poprawności, ponieważ występuje.

### <a name="validating-conditions-and-throwing-exceptions"></a>Sprawdzanie poprawności warunków i zgłaszanie wyjątków

Poniższy przykład kodu pokazuje najprostsza metoda sprawdzania poprawności w jednostce domeny, podnosząc wyjątek. W tabeli odniesienia na końcu tej sekcji można zobaczyć łącza do bardziej zaawansowanych implementacji na podstawie wzorców, które Omówiliśmy wcześniej.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Przykład lepsze wskazywałoby potrzebę zapewnienia wewnętrzny stan nie został zmieniony lub że wszystkie mutację dla metody wystąpił. Na przykład następującą implementacją spowoduje, że obiekt w nieprawidłowym stanie:

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

Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i Miasto już zostały zmienione. Który może mieć adres nieprawidłowy.

Podejście podobne może służyć w Konstruktorze jednostki, zgłaszania wyjątku, aby upewnić się, że jednostka jest prawidłowa, po jego utworzeniu.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>W modelu, w oparciu o adnotacje danych przy użyciu atrybutów sprawdzania poprawności

Innym podejściem jest używać atrybutów sprawdzania poprawności, w zależności od adnotacji danych. Atrybuty weryfikacji umożliwiają konfigurowanie weryfikacji modelu, które są podobne pod względem koncepcyjnym do sprawdzania poprawności w polach w tabelach bazy danych. Obejmuje to ograniczenia, takie jak przypisywanie typów danych lub wymagane pola. Inne rodzaje weryfikacji obejmują stosowania wzorców do danych w celu wymuszania reguł biznesowych, takich jak numer karty kredytowej lub numer telefonu lub adres e-mail. Atrybuty weryfikacji ułatwiają wymuszanie wymagań dotyczących.

Jednakże jak pokazano w poniższym kodzie, to takie podejście może być zbyt bez wprowadzania niepożądanych w modelu DDD, z powodu zależności na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, który musi wywołać z kontrolerów MVC. Sprawdzanie poprawności modelu występującą przed każdym wywoływana Akcja kontrolera i odpowiada za metody kontrolera sprawdzić wynik wywoływania ModelState.IsValid i odpowiednio reagują. Decyzja z niej korzystać zależy ściśle mają model, który ma być z tej infrastruktury.

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

Jednak z punktu widzenia DDD, model domeny jest najlepiej pozostawić zwarte przy użyciu wyjątków w metodach zachowanie Twojej jednostki lub poprzez implementację wzorców Specyfikacja i powiadomień w celu wymuszania reguł sprawdzania poprawności. Sprawdzanie poprawności środowisk, takich jak adnotacje danych na platformie ASP.NET Core lub innych struktur sprawdzania poprawności podobnie jak FluentValidation wykonać wymagane do wywołania struktury aplikacji. Na przykład podczas wywoływania metody ModelState.IsValid w adnotacjach danych, należy wywołać kontrolerów platformy ASP.NET.

Sensowne może używać adnotacji danych w warstwie aplikacji w klas ViewModel (zamiast domeny podmioty), które akceptują dane wejściowe, aby zezwolić na potrzeby weryfikacji modelu w ramach warstwy interfejsu użytkownika. Jednak to nie należy wykonywać na wyłączenie sprawdzania poprawności w ramach modelu domeny.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Sprawdzanie poprawności jednostek poprzez implementację wzoru specyfikacji i powiadomienia

Na koniec bardziej złożonych podejściem implementowania operacji sprawdzania poprawności w modelu domeny jest implementacja wzorca specyfikacji w połączeniu z wzorcem powiadomień, jak wyjaśniono w niektóre dodatkowe zasoby wymienione w dalszej części.

Warto zauważyć, że umożliwia także tylko jeden z tych wzorców — na przykład, sprawdzanie poprawności ręcznie za pomocą instrukcji sterowania, ale przy użyciu wzorca powiadomień do stosu i powrócić do listy błędów sprawdzania poprawności.

### <a name="using-deferred-validation-in-the-domain"></a>Za pomocą odroczonego sprawdzania poprawności w domenie

Istnieją różne metody radzenia sobie z opóźnieniem walidacji w domenie. W książce [projektowania Implementing Domain-Driven](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon w tym artykule omówiono w sekcji podczas weryfikacji.

### <a name="two-step-validation"></a>Weryfikacja dwuetapowa

Należy również rozważyć weryfikacji dwuetapowej. Użyj weryfikacji na poziomie pola na polecenia obiektów transferu danych (dto) i weryfikacji na poziomie dla domeny wewnątrz jednostek. Można to zrobić, zwracając obiekt wyniku zamiast tego wyjątki ułatwi radzić sobie z błędami sprawdzania poprawności.

Za pomocą weryfikacji pola przy użyciu adnotacji danych, na przykład nie duplikowania definicji sprawdzania poprawności. Wykonanie, jednak może być zarówno po stronie serwera, jak i po stronie klienta w przypadku dto (polecenia i modele widoków, na przykład).

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Rachel Appel. Wprowadzenie do weryfikacji modelu w aplikacji ASP.NET Core MVC**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martina Fowlera. Zastępowanie zgłaszanie wyjątków z powiadomieniem w walidacji**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Specyfikacja i wzorce powiadomień**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lew Gorodinski. Sprawdzanie poprawności w projektowania opartego na domenach (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Gniazdo Colin. Sprawdzanie poprawności modelu domeny**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. Sprawdzanie poprawności w świecie DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Poprzednie](enumeration-classes-over-enum-types.md)
[dalej](client-side-validation.md)
