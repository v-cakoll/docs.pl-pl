---
title: Projektowanie reguł weryfikacji w warstwie modelu domeny
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Poznaj kluczowe pojęcia związane z walidacją modelu domeny.
ms.date: 10/08/2018
ms.openlocfilehash: 98ccc5df84c9f6f402ecbee83b077c806d6a76fc
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899666"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Walidacje projektu w warstwie modelu domeny

W DDD reguły walidacji mogą być traktowane jako nieposiadające wariantów. Główną odpowiedzialnością za zagregowaną jest wymuszenie niewariantów między zmianami stanu dla wszystkich jednostek w ramach tej agregacji.

Jednostki domeny powinny być zawsze prawidłowymi jednostkami. Istnieje pewna liczba nieodmian dla obiektu, który powinien mieć zawsze wartość true. Na przykład obiekt elementu Order zawsze musi mieć ilość, która musi być dodatnią liczbą całkowitą oraz nazwę artykułu i cenę. Z tego względu wymuszanie nieistniejące jest odpowiedzialne za jednostki domeny (zwłaszcza w przypadku agregacji głównej), a obiekt jednostki nie powinien być w stanie istnieć. Niezmienne reguły są po prostu wyrażone jako kontrakty, a wyjątki lub powiadomienia są zgłaszane, gdy są naruszane.

Przyczyną tego jest fakt, że występuje wiele usterek, ponieważ obiekty są w stanie, w którym nigdy nie powinny. Poniżej znajduje się dobre wyjaśnienie od Grega młodych w [dyskusji online](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):

Zaproponujemy teraz SendUserCreationEmailService, który zajmuje profil użytkownika... Jak możemy usprawnić działanie tej usługi, która nie ma wartości null? Czy sprawdzimy ją ponownie? Lub najkorzystniej... nie bother do sprawdzenia i "Mam nadzieję, że masz nadzieję, że ktoś bothered go przed wysłaniem do Ciebie. Oczywiście przy użyciu usługi TDD jednym z pierwszych testów, które powinny być napisane, jest to, że jeśli wysyłam klientowi nazwę o wartości null, która powinna zgłosić błąd. Jednak po rozpoczęciu pisania tych rodzajów testów w tym czasie zostanie to zrealizowane... "Zaczekaj, jeśli nigdy nie zezwolisz na przełączenie nazwy do wartości null, nie będziemy mieć wszystkich tych testów"

## <a name="implement-validations-in-the-domain-model-layer"></a>Implementowanie walidacji w warstwie modelu domeny

Walidacje są zwykle implementowane w konstruktorach jednostek domeny lub w metodach, które mogą aktualizować jednostkę. Istnieje wiele sposobów implementacji walidacji, takich jak Weryfikowanie danych i wywoływanie wyjątków, jeśli sprawdzanie poprawności zakończy się niepowodzeniem. Istnieją także bardziej zaawansowane wzorce, takie jak użycie wzorca specyfikacji dla walidacji, oraz wzorzec powiadomienia do zwrócenia kolekcji błędów zamiast zwracać wyjątek dla każdej walidacji w miarę ich występowania.

### <a name="validate-conditions-and-throw-exceptions"></a>Sprawdzanie poprawności warunków i zgłaszanie wyjątków

Poniższy przykład kodu pokazuje najprostszą metodę weryfikacji w jednostce domeny przez podnoszenie wyjątku. W tabeli odwołań na końcu tej sekcji można zobaczyć linki do bardziej zaawansowanych implementacji na podstawie wzorców, które zostały wcześniej omówione.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Lepszy przykład pokazuje konieczność zapewnienia, że stan wewnętrzny nie został zmieniony lub że wszystkie mutacje dla metody wystąpią. Na przykład następująca implementacja pozostawia obiekt w nieprawidłowym stanie:

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

Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i miasto zostały już zmienione. Może to oznaczać, że adres jest nieprawidłowy.

Podobne podejście można użyć w konstruktorze jednostki, wywołując wyjątek, aby upewnić się, że jednostka jest ważna po utworzeniu.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Używanie atrybutów walidacji w modelu na podstawie adnotacji danych

Adnotacje danych, takie jak atrybuty wymagane lub MaxLength, mogą służyć do konfigurowania właściwości pola EF Core bazy danych, jak wyjaśniono szczegółowo w sekcji [Mapowanie tabeli](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) , ale [nie będą już działać do sprawdzania poprawności jednostek w EF Core](https://github.com/dotnet/efcore/issues/3680) (żadna z metod <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType>), ponieważ zostały one wykonane od Ef 4. x w .NET Framework.

Adnotacje danych i interfejs <xref:System.ComponentModel.DataAnnotations.IValidatableObject> nadal mogą być używane do walidacji modelu podczas powiązania modelu, przed wywołaniem akcji kontrolera w zwykły sposób, ale ten model ma być ViewModel lub DTO, a to nie jest problemem z modelem MVC lub INTERFEJSem domeny.

Po wyczyszczeniu różnicy pojęciowej można nadal używać adnotacji danych i `IValidatableObject` w klasie jednostek do walidacji, jeśli akcje odbierają parametr obiektu klasy jednostki, co nie jest zalecane. W takim przypadku Walidacja zostanie wykonana po powiązaniu modelu przed wywołaniem akcji i można sprawdzić Właściwość ModelState. IsValid kontrolera, aby sprawdzić wynik, ale następnie ponownie, dzieje się w kontrolerze, a nie przed utrwalaniem obiektu Entity w DbContext, jak zrobiono od EF 4. x.

Nadal można zaimplementować niestandardowe sprawdzanie poprawności w klasie Entity przy użyciu adnotacji danych i metody `IValidatableObject.Validate`, zastępując metodę metody SaveChanges DbContext.

Możesz zobaczyć przykładową implementację sprawdzania poprawności jednostek `IValidatableObject` w [tym komentarzu w serwisie GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539). Ten przykład nie wykonuje walidacji opartych na atrybutach, ale powinien być łatwy do wdrożenia przy użyciu odbicia w tym samym przesłonięciu.

Jednak z punktu widzenia, model domeny najlepiej utrzymuje się oszczędne przy użyciu wyjątków w metodach zachowań jednostki lub implementując wzorce specyfikacji i powiadomień w celu wymuszenia reguł walidacji.

Warto mieć sens, aby użyć adnotacji danych w warstwie aplikacji w klasach ViewModel (zamiast jednostek domeny), które będą akceptować dane wejściowe, aby umożliwić weryfikację modelu w warstwie interfejsu użytkownika. Jednak nie należy tego robić podczas wykluczania walidacji w modelu domeny.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Weryfikuj jednostki przez implementację wzorca specyfikacji i wzorzec powiadomienia

Na koniec bardziej rozbudowane podejście do implementowania walidacji w modelu domeny jest przez implementację wzorca specyfikacji w połączeniu ze wzorcem powiadomienia, jak wyjaśniono w niektórych dodatkowych zasobach wymienionych w dalszej części.

Warto zauważyć, że można również użyć tylko jednego z tych wzorców — na przykład walidacji ręcznie przy użyciu instrukcji kontroli, ale przy użyciu wzorca powiadomienia, aby układać i zwracać listę błędów walidacji.

### <a name="use-deferred-validation-in-the-domain"></a>Korzystanie z odroczonego sprawdzania poprawności w domenie

Istnieją różne podejścia do postępowania z odroczonymi walidacjami w domenie. W swojej książce [implementującej Projektowanie oparte na domenie](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)Vaughn Vernon omawia te w sekcji dotyczącej weryfikacji.

### <a name="two-step-validation"></a>Weryfikacja dwuetapowa

Należy również rozważyć weryfikację dwuetapową. Przy użyciu walidacji na poziomie pola Transfer danych obiektów (DTO) i walidacji na poziomie domeny wewnątrz jednostek. Można to zrobić, zwracając obiekt wyniku zamiast wyjątków, aby ułatwić rozproszenie z błędami walidacji.

Używanie weryfikacji pola z adnotacjami danych, na przykład, nie duplikuje definicji walidacji. Wykonanie, chociaż, może być zarówno po stronie serwera, jak i po stronie klienta w przypadku DTO (polecenia i modele widoków, na przykład).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Rachel Appel. Wprowadzenie do walidacji modelu w ASP.NET Core MVC** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Dodawanie \ weryfikacji**
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Fowlera Martin. Zastępowanie zgłaszania wyjątków przy użyciu powiadomień w ramach walidacji** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Wzorce specyfikacji i powiadomień** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lew Gorodinski. Walidacja w projekcie opartym na domenie (DDD)**  \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Wtyczka Colin. Weryfikacja modelu domeny** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard. Weryfikacja w \ DDD**
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Poprzedni](enumeration-classes-over-enum-types.md)
> [Następny](client-side-validation.md)
