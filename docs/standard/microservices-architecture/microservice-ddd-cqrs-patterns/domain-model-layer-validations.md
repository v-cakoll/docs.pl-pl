---
title: Projektowanie reguł weryfikacji w warstwie modelu domeny
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Należy zrozumieć kluczowe pojęcia związane z sprawdzania poprawności modelu domeny.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ae1252f4544f184a5f63ef02ba898da9b4373e17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020000"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Projektowanie reguł weryfikacji w warstwie modelu domeny

W DDD reguł sprawdzania poprawności można traktować jako invariants. Podstawowa odpowiedzialność agregacji jest wymusić invariants na zmiany stanu dla wszystkich jednostek w ramach tej agregacji.

Jednostki domeny powinny być zawsze prawidłowe jednostki. Istnieją pewne invariants dla obiektu, który powinien zawsze być prawdziwe. Na przykład obiekt elementu kolejności zawsze musi mieć ilość, który musi być dodatnią liczbą całkowitą, a także nazwę artykułu i ceny. Dlatego wymuszania invariants odpowiada jednostki domeny (zwłaszcza w zakresie głównego agregacji) i obiektu jednostki nie powinno być możliwe istnieje nie są prawidłowe. Zasad niezmiennej po prostu są wyrażane jako kontraktów i powiadomienia lub wyjątki są zgłaszane w przypadku ich naruszenia.

Uzasadnienie to to, że wiele błędów być fakt, że obiekty są w stanie, które powinny mieć nigdy nie był w. Poniżej przedstawiono dobry opis z Grega Younga w [dyskusji](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):

Zaproponuj Załóżmy że mamy teraz SendUserCreationEmailService, wykorzystującej UserProfile... jak można możemy racjonalizować w tej usłudze, że nazwa nie jest null? Czy możemy sprawdzić go ponownie? Lub bardziej prawdopodobne... po prostu nie zostanie odblokowane można sprawdzić i "najlepszą nadzieję, że" — Mamy nadzieję, że ktoś bothered, aby zweryfikować, czy przed wysłaniem ich do Ciebie. Oczywiście za pomocą TDD pierwszy testy, które firma Microsoft należy pisania, jest to, że jeśli wysyła się klientów z nazwą wartości null, należy je zgłosić błąd. Jednak gdy Rozpoczniemy wielokrotnie pisania tego rodzaju testy Zdajemy sobie sprawę... "oczekiwania, jeśli firma Microsoft nigdy nie mogą nazwę, aby stać się o wartości null nie mamy wszystkich tych testów"

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementowanie walidacji w warstwie modelu domeny

Sprawdzanie poprawności zwykle są implementowane w konstruktorach jednostki domeny lub za pomocą metod, które mogą aktualizować jednostki. Istnieje wiele sposobów implementowania operacji sprawdzania poprawności, takie jak weryfikowanie danych i wywoływanie wyjątków w przypadku niepowodzenia weryfikacji. Istnieją również bardziej zaawansowane wzorców, takich jak przy użyciu wzorca specyfikacji dla sprawdzanie poprawności i wzorzec powiadomień do zwrócenia zbierania błędów zamiast zwracać wyjątek dla każdego sprawdzania poprawności, ponieważ występuje.

### <a name="validate-conditions-and-throw-exceptions"></a>Zweryfikować warunkach i zgłaszanie wyjątków

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
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i Miasto już zostały zmienione. Który może mieć adres nieprawidłowy.

Podejście podobne może służyć w Konstruktorze jednostki, zgłaszania wyjątku, aby upewnić się, że jednostka jest prawidłowa, po jego utworzeniu.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Użyj sprawdzania poprawności atrybutów w modelu na podstawie danych adnotacji

Adnotacje danych, takich jak wymagane lub atrybutów MaxLength, mogą być używane do konfigurowania właściwości pola bazy danych programu EF Core, jak wyjaśniono szczegółowo w [Mapowanie tabeli](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) sekcji, ale [przestanie działać, jednostki Sprawdzanie poprawności w programie EF Core](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (żadna z nich nie jest <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metoda), jak miało to miejsce od EF 4.x w programie .NET Framework.

Adnotacje danych i <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interfejsu, nadal mogą służyć do sprawdzania poprawności modelu podczas powiązań modelu, przed wywołanie akcji kontrolera w zwykły sposób, ale model jest przeznaczony do ViewModel lub obiekt DTO, która jest kwestią MVC lub interfejsu API nie modelu domeny zastrzeżenia.

Po dokonaniu koncepcyjny różnica, wyczyść, można nadal używać adnotacji danych i `IValidatableObject` w klasie jednostki do sprawdzania poprawności, jeśli parametr obiektu klasy jednostki, co nie jest zalecane akcje. W takiej sytuacji nastąpi sprawdzanie poprawności podczas wiązania modelu, tuż przed wywoływania akcji można sprawdzić właściwość ModelState.IsValid kontrolera Aby sprawdzić wynik, ale następnie ponownie go odbywa się w kontrolerze, nie wcześniej niż przechowywanie obiektu jednostki w Kontekst DbContext, ponieważ przeprowadzono od EF 4.x.

Nadal można zaimplementować niestandardowego sprawdzania poprawności w klasie jednostki przy użyciu adnotacji danych i `IValidatableObject.Validate` metoda poprzez zastąpienie metody SaveChanges DbContext.

Możesz zobaczyć przykład implementacji weryfikowania `IValidatableObject` jednostek w [ten komentarz w serwisie GitHub](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539). Ten przykład nie opartych na atrybutach operacji sprawdzania poprawności, ale powinny one być łatwe do wdrożenia przy użyciu odbicia w tej samej zastąpienie.

Jednak z punktu widzenia DDD, model domeny jest najlepiej pozostawić zwarte przy użyciu wyjątków w metodach zachowanie Twojej jednostki lub poprzez implementację wzorców Specyfikacja i powiadomień w celu wymuszania reguł sprawdzania poprawności.

Sensowne może używać adnotacji danych w warstwie aplikacji w klas ViewModel (zamiast domeny podmioty), które akceptują dane wejściowe, aby zezwolić na potrzeby weryfikacji modelu w ramach warstwy interfejsu użytkownika. Jednak to nie należy wykonywać na wyłączenie sprawdzania poprawności w ramach modelu domeny.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Sprawdź poprawność jednostek poprzez implementację wzoru specyfikacji i powiadomienia

Na koniec bardziej złożonych podejściem implementowania operacji sprawdzania poprawności w modelu domeny jest implementacja wzorca specyfikacji w połączeniu z wzorcem powiadomień, jak wyjaśniono w niektóre dodatkowe zasoby wymienione w dalszej części.

Warto zauważyć, że umożliwia także tylko jeden z tych wzorców — na przykład, sprawdzanie poprawności ręcznie za pomocą instrukcji sterowania, ale przy użyciu wzorca powiadomień do stosu i powrócić do listy błędów sprawdzania poprawności.

### <a name="use-deferred-validation-in-the-domain"></a>Użyj odroczonego sprawdzania poprawności w domenie

Istnieją różne metody radzenia sobie z opóźnieniem walidacji w domenie. W książce [projektowania Implementing Domain-Driven](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon w tym artykule omówiono w sekcji podczas weryfikacji.

### <a name="two-step-validation"></a>Weryfikacja dwuetapowa

Należy również rozważyć weryfikacji dwuetapowej. Użyj weryfikacji na poziomie pola na polecenia obiektów transferu danych (dto) i weryfikacji na poziomie dla domeny wewnątrz jednostek. Można to zrobić, zwracając obiekt wyniku zamiast tego wyjątki ułatwi radzić sobie z błędami sprawdzania poprawności.

Za pomocą weryfikacji pola przy użyciu adnotacji danych, na przykład nie duplikowania definicji sprawdzania poprawności. Wykonanie, jednak może być zarówno po stronie serwera, jak i po stronie klienta w przypadku dto (polecenia i modele widoków, na przykład).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Rachel Appel. Wprowadzenie do weryfikacji modelu w aplikacji ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Dodawanie walidacji** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler. Zastępowanie zgłaszanie wyjątków z powiadomieniem w walidacji** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Specyfikacja i wzorce powiadomień** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski. Sprawdzanie poprawności w projektowania opartego na domenach (DDD)** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Gniazdo Colin. Sprawdzanie poprawności modelu domeny** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard. Sprawdzanie poprawności w świecie DDD** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Poprzednie](enumeration-classes-over-enum-types.md)
> [dalej](client-side-validation.md)
