---
title: Projektowanie reguł weryfikacji w warstwie modelu domeny
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Poznaj kluczowe pojęcia sprawdzania poprawności modelu domeny.
ms.date: 10/08/2018
ms.openlocfilehash: d2efc5f3b3267c4573409952791c6e883a01aae2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988508"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Sprawdzanie poprawności projektu w warstwie modelu domeny

W DDD reguły sprawdzania poprawności można traktować jako invariants. Główną odpowiedzialnością agregacji jest wymuszanie invariants między zmianami stanu dla wszystkich jednostek w ramach tego agregacji.

Jednostki domeny powinny być zawsze prawidłowymi encjami. Istnieje pewna liczba invariants dla obiektu, który zawsze powinien być prawdziwy. Na przykład obiekt towaru zamówienia zawsze musi mieć ilość, która musi być dodatnią ćwiękową oraz nazwę artykułu i cenę. W związku z tym invariants wymuszania jest odpowiedzialność jednostek domeny (zwłaszcza zagregowanego katalogu głównego) i obiekt jednostki nie powinien istnieć bez ważności. Zasady niezmienne są po prostu wyrażone jako umowy, a wyjątki lub powiadomienia są wywoływane, gdy są naruszane.

Rozumowanie za to jest, że wiele błędów występuje, ponieważ obiekty są w stanie, w jaki nigdy nie powinny być w. Poniżej znajduje się dobre wyjaśnienie z Greg Young w [dyskusji online:](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/)

Zaproponujmy teraz SendUserCreationEmailService, który ma UserProfile ... jak możemy zracjonalizować w tej usłudze, że nazwa nie jest null? Czy sprawdzamy to ponownie? Lub bardziej prawdopodobne ... po prostu nie zawracaj sobie głowy sprawdzaniem i "nadzieją na najlepsze" — masz nadzieję, że komuś przeszkadzało to zweryfikować przed wysłaniem go do Ciebie. Oczywiście, za pomocą TDD jeden z pierwszych testów powinniśmy pisać jest to, że jeśli mogę wysłać klienta z nazwą null, że powinien podnieść błąd. Ale kiedy zaczniemy pisać tego rodzaju testy w kółko zdajemy sobie sprawę ... "Poczekaj, jeśli nigdy nie pozwoliliśmy, aby nazwa stała się null, nie mielibyśmy wszystkich tych testów"

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementowanie weryfikacji w warstwie modelu domeny

Sprawdzanie poprawności są zwykle implementowane w konstruktorach jednostek domeny lub w metodach, które można zaktualizować jednostki. Istnieje wiele sposobów implementacji sprawdzania poprawności, takich jak sprawdzanie danych i wywoływanie wyjątków, jeśli sprawdzanie poprawności nie powiedzie się. Istnieją również bardziej zaawansowane wzorce, takie jak przy użyciu wzorca specyfikacji dla sprawdzania poprawności i wzorzec powiadomień, aby zwrócić kolekcję błędów zamiast zwracać wyjątek dla każdej weryfikacji w miarę jego występowania.

### <a name="validate-conditions-and-throw-exceptions"></a>Sprawdzanie poprawności warunków i zgłaszanie wyjątków

Poniższy przykład kodu pokazuje najprostsze podejście do sprawdzania poprawności w jednostce domeny przez podniesienie wyjątku. W tabeli odwołań na końcu tej sekcji można zobaczyć łącza do bardziej zaawansowanych implementacji na podstawie wzorców, które omówiliśmy wcześniej.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepszy przykład wykazałby potrzebę zapewnienia, że stan wewnętrzny nie zmienił się lub że wystąpiły wszystkie mutacje metody. Na przykład następująca implementacja pozostawi obiekt w nieprawidłowym stanie:

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

Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i miasto zostały już zmienione. To może spowodować, że adres będzie nieprawidłowy.

Podobne podejście może służyć w konstruktorze jednostki, podnosząc wyjątek, aby upewnić się, że jednostka jest prawidłowa po jej utworzeniu.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Używanie atrybutów sprawdzania poprawności w modelu na podstawie adnotacji danych

Adnotacje danych, takie jak wymagane lub Atrybuty MaxLength, mogą służyć do konfigurowania właściwości pola bazy danych EF Core, jak wyjaśniono szczegółowo w sekcji [mapowanie tabeli,](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) ale [nie działają już dla sprawdzania poprawności jednostki w EF Core](https://github.com/dotnet/efcore/issues/3680) (nie ma <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> metody), jak to miało miejsce od EF 4.x w .NET Framework.

Adnotacje danych <xref:System.ComponentModel.DataAnnotations.IValidatableObject> i interfejs może nadal służyć do sprawdzania poprawności modelu podczas wiązania modelu, przed wywołania akcji kontrolera jak zwykle, ale ten model ma być ViewModel lub DTO i to jest MVC lub interfejsu API dotyczą nie problem modelu domeny.

Po dokonaniu różnicy koncepcyjnej jasne, nadal `IValidatableObject` można użyć adnotacji danych i w klasie jednostki do sprawdzania poprawności, jeśli akcje otrzymują parametr obiektu klasy jednostki, który nie jest zalecane. W takim przypadku sprawdzanie poprawności nastąpi na powiązanie modelu, tuż przed wywołaniem akcji i można sprawdzić właściwości ModelState.IsValid kontrolera, aby sprawdzić wynik, ale potem ponownie, dzieje się w kontrolerze, nie przed utrwalanie obiektu jednostki w DbContext, jak to miało miejsce od EF 4.x.

Nadal można zaimplementować niestandardowe sprawdzanie poprawności `IValidatableObject.Validate` w klasie jednostki przy użyciu adnotacji danych i metody, zastępując DbContext SaveChanges metody.

W tym komentarzu na `IValidatableObject` [gitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539)można wyświetlić przykładową implementację sprawdzania poprawności jednostek. W tym przykładzie nie wykonuje sprawdzania poprawności opartych na atrybutach, ale powinny być łatwe do zaimplementowania przy użyciu odbicia w tym samym zastąpienia.

Jednak z punktu widzenia DDD modelu domeny najlepiej zachować chudego przy użyciu wyjątków w metody zachowania jednostki lub implementując wzorce specyfikacji i powiadomień w celu wymuszenia reguł sprawdzania poprawności.

Warto użyć adnotacji danych w warstwie aplikacji w viewmodel klas (zamiast jednostek domeny), które będą akceptować dane wejściowe, aby umożliwić sprawdzanie poprawności modelu w warstwie interfejsu użytkownika. Jednak nie należy tego robić z wyłączeniem sprawdzania poprawności w modelu domeny.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Sprawdzanie poprawności jednostek przez implementowanie wzorca specyfikacji i wzorca powiadomień

Na koniec bardziej skomplikowane podejście do implementowania sprawdzania poprawności w modelu domeny jest przez implementowanie wzorzec specyfikacji w połączeniu ze wzorcem powiadomień, jak wyjaśniono w niektórych dodatkowych zasobów wymienionych później.

Warto wspomnieć, że można również użyć tylko jednego z tych wzorców — na przykład sprawdzania poprawności ręcznie za pomocą instrukcji sterujących, ale przy użyciu wzorca powiadomień do stosu i zwracania listy błędów sprawdzania poprawności.

### <a name="use-deferred-validation-in-the-domain"></a>Użyj odroczonej weryfikacji w domenie

Istnieją różne podejścia do czynienia z odroczonych sprawdzania poprawności w domenie. W swojej książce [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon omawia je w sekcji na temat walidacji.

### <a name="two-step-validation"></a>Sprawdzanie poprawności dwuetapowej

Należy również wziąć pod uwagę dwuetapowe sprawdzanie poprawności. Użyj sprawdzania poprawności na poziomie pola w poleceniu Obiekty transferu danych (DTO) i sprawdzanie poprawności na poziomie domeny wewnątrz encji. Można to zrobić, zwracając obiekt wynik zamiast wyjątków w celu ułatwienia radzenia sobie z błędami sprawdzania poprawności.

Na przykład za pomocą sprawdzania poprawności pola z adnotacjami danych nie należy powielać definicji sprawdzania poprawności. Wykonanie może jednak być zarówno po stronie serwera, jak i po stronie klienta w przypadku DTO (polecenia i ViewModels, na przykład).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Rachel Appel. Wprowadzenie do sprawdzania poprawności modelu w ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Dodawanie sprawdzania poprawności** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler. Zastępowanie zgłaszania wyjątków powiadomieniem w weryfikacjach** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Wzorce specyfikacji i powiadomień** \
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
