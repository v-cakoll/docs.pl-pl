---
title: Projektowanie reguł weryfikacji w warstwie modelu domeny
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się z kluczowymi pojęciami sprawdzania poprawności modelu domeny.
ms.date: 10/08/2018
ms.openlocfilehash: 98ccc5df84c9f6f402ecbee83b077c806d6a76fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899666"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Sprawdzanie poprawności projektu w warstwie modelu domeny

W DDD reguły sprawdzania poprawności można traktować jako niezmienne. Główną odpowiedzialnością za agregat jest wymuszanie niezmiennych zmian stanu dla wszystkich jednostek w ramach tego agregatu.

Jednostki domeny powinny być zawsze prawidłowe jednostki. Istnieje pewna liczba invariants dla obiektu, który zawsze powinien być true. Na przykład obiekt zapasu zamówienia zawsze musi mieć ilość, która musi być dodatnią liczbą całkowitą, plus nazwa artykułu i cena. W związku z tym wymuszanie invariants jest obowiązkiem jednostek domeny (zwłaszcza zagregowanego katalogu głównego) i obiekt jednostki nie powinien istnieć bez ważności. Niezmienne reguły są po prostu wyrażone jako kontrakty, a wyjątki lub powiadomienia są wywoływane, gdy są naruszane.

Rozumowanie za to jest, że wiele błędów występują, ponieważ obiekty są w stanie, w jaki nigdy nie powinny być w. Oto dobre wyjaśnienie greg young w [dyskusji online:](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/)

Zaproponujmy teraz sendusercreationemailservice, który ma UserProfile ... jak możemy zracjonalizować w tej usłudze, że nazwa nie jest null? Czy sprawdzamy to jeszcze raz? Lub bardziej prawdopodobne ... po prostu nie zawracaj sobie głowy, aby sprawdzić i "nadzieję na najlepsze" - masz nadzieję, że ktoś zadał sobie trud, aby potwierdzić go przed wysłaniem go do Ciebie. Oczywiście, za pomocą TDD jednym z pierwszych testów powinniśmy pisać jest to, że jeśli wysłać klienta o nazwie null, że powinien zgłosić błąd. Ale kiedy zaczniemy pisać tego rodzaju testy w kółko, zdajemy sobie sprawę ... "poczekaj, jeśli nigdy nie pozwoliliśmy nazwę stać się null nie mielibyśmy wszystkie te testy"

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementowanie sprawdzania poprawności w warstwie modelu domeny

Sprawdzanie poprawności są zwykle implementowane w konstruktorów jednostek domeny lub w metodach, które można zaktualizować jednostki. Istnieje wiele sposobów implementowania sprawdzania poprawności, takich jak weryfikowanie danych i zgłaszanie wyjątków w przypadku niepowodzenia sprawdzania poprawności. Istnieją również bardziej zaawansowane wzorce, takie jak przy użyciu wzorca specyfikacji dla sprawdzania poprawności i wzorzec powiadomień, aby zwrócić kolekcję błędów zamiast zwracać wyjątek dla każdego sprawdzania poprawności, jak to się dzieje.

### <a name="validate-conditions-and-throw-exceptions"></a>Sprawdzanie poprawności warunków i zgłaszanie wyjątków

W poniższym przykładzie kodu przedstawiono najprostsze podejście do sprawdzania poprawności w jednostce domeny, zgłaszając wyjątek. W tabeli odwołań na końcu tej sekcji można zobaczyć łącza do bardziej zaawansowanych implementacji na podstawie wzorców, które omówiliśmy wcześniej.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepszym przykładem może być wykazanie potrzeby zapewnienia, że stan wewnętrzny nie zmienił się lub że wystąpiły wszystkie mutacje dla metody. Na przykład następująca implementacja pozostawi obiekt w nieprawidłowym stanie:

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

Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i miasto zostały już zmienione. To może sprawić, że adres jest nieprawidłowy.

Podobne podejście może służyć w konstruktorze jednostki, podnosząc wyjątek, aby upewnić się, że jednostka jest prawidłowa po utworzeniu.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Używanie atrybutów sprawdzania poprawności w modelu na podstawie adnotacji danych

Adnotacje danych, takie jak required lub MaxLength atrybuty, może służyć do konfigurowania właściwości pola bazy danych EF Core, jak wyjaśniono szczegółowo w sekcji [mapowania tabeli,](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) ale [nie działają już dla sprawdzania poprawności jednostki w EF Core](https://github.com/dotnet/efcore/issues/3680) (nie ma <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metody), jak to miało miejsce od EF 4.x w .NET Framework.

Adnotacje danych <xref:System.ComponentModel.DataAnnotations.IValidatableObject> i interfejs nadal mogą być używane do sprawdzania poprawności modelu podczas wiązania modelu, przed wywołaniem akcji kontrolera, jak zwykle, ale ten model ma być ViewModel lub DTO i to jest MVC lub API dotyczą nie dotyczy problemu modelu domeny.

Po dokonaniu różnica koncepcyjne jasne, nadal można użyć `IValidatableObject` adnotacji danych i w klasie jednostki do sprawdzania poprawności, jeśli akcje odbierają parametr obiektu klasy jednostki, który nie jest zalecane. W takim przypadku sprawdzania poprawności nastąpi na powiązanie modelu, tuż przed wywołaniem akcji i można sprawdzić modelstate kontrolera.IsValid właściwości, aby sprawdzić wynik, ale potem znowu, dzieje się w kontrolerze, nie przed utrwalenia obiektu jednostki w DbContext, jak to miało miejsce od EF 4.x.

Nadal można zaimplementować niestandardowe sprawdzanie poprawności w klasie `IValidatableObject.Validate` jednostki przy użyciu adnotacji danych i metody, zastępując Metodę SaveChanges DbContext.

Możesz zobaczyć przykładową implementację `IValidatableObject` sprawdzania poprawności jednostek w [tym komentarzu w uspolu GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539). Ten przykład nie wykonuje sprawdzania poprawności opartych na atrybutach, ale powinny być łatwe do zaimplementowania przy użyciu odbicia w tym samym zastąpić.

Jednak z punktu widzenia DDD model domeny jest najlepiej utrzymywany jako lean przy użyciu wyjątków w metodach zachowania jednostki lub przez wdrożenie wzorców specyfikacji i powiadomień w celu wymuszenia reguł sprawdzania poprawności.

Warto użyć adnotacji danych w warstwie aplikacji w klasach ViewModel (zamiast jednostek domeny), które będą akceptować dane wejściowe, aby umożliwić sprawdzanie poprawności modelu w warstwie interfejsu użytkownika. Jednak nie należy tego robić z wyłączeniem sprawdzania poprawności w modelu domeny.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Sprawdzanie poprawności jednostek przez wdrożenie wzorca specyfikacji i wzorca powiadomień

Na koniec bardziej rozbudowane podejście do implementowania sprawdzania poprawności w modelu domeny jest poprzez implementowanie wzorca specyfikacji w połączeniu ze wzorcem powiadomień, jak wyjaśniono w niektórych dodatkowych zasobów wymienionych później.

Warto wspomnieć, że można również użyć tylko jednego z tych wzorców — na przykład ręcznego sprawdzania poprawności za pomocą instrukcji sterujących, ale przy użyciu wzorca powiadomień do stosu i zwrócenia listy błędów sprawdzania poprawności.

### <a name="use-deferred-validation-in-the-domain"></a>Używanie odroczonego sprawdzania poprawności w domenie

Istnieją różne podejścia do radzenia sobie z odroczonego sprawdzania poprawności w domenie. W swojej książce [Implementing Domain-Driven Design,](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)Vaughn Vernon omawia te w sekcji na walidacji.

### <a name="two-step-validation"></a>Walidacja dwuetapowa

Należy również wziąć pod uwagę weryfikacji dwuetapowej. Użyj sprawdzania poprawności na poziomie pola w pole obiekty transferu danych (DTO) i sprawdzania poprawności na poziomie domeny wewnątrz jednostek. Można to zrobić, zwracając obiekt wynik zamiast wyjątków, aby ułatwić radzenie sobie z błędami sprawdzania poprawności.

Na przykład za pomocą sprawdzania poprawności pola z adnotacjami danych nie można powielać definicji sprawdzania poprawności. Wykonanie, choć może być zarówno po stronie serwera, jak i po stronie klienta w przypadku DCO (polecenia i ViewModels, na przykład).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Rachel Appel. Wprowadzenie do sprawdzania poprawności modelu w ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Dodawanie sprawdzania poprawności** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler. Zastępowanie zgłaszających wyjątków powiadomieniem w modułach sprawdzania poprawności** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Specyfikacja i wzorce powiadomień** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lew Gorodinski. Sprawdzanie poprawności w projekcie opartym na domenie (DDD)** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Colin Jack. Sprawdzanie poprawności modelu domeny** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard. Walidacja w świecie DDD** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Poprzedni](enumeration-classes-over-enum-types.md)
> [następny](client-side-validation.md)
