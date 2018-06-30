---
title: Projektowanie poprawności warstwy modelu domeny
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie poprawności warstwy modelu domeny
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c071d269977ccecea9a7d4d79da78d7967bb1618
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105738"
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="8ead8-103">Projektowanie poprawności warstwy modelu domeny</span><span class="sxs-lookup"><span data-stu-id="8ead8-103">Designing validations in the domain model layer</span></span>

<span data-ttu-id="8ead8-104">W DDD można traktować jako invariants reguł sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8ead8-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="8ead8-105">Podstawowa odpowiedzialność agregacji jest wymuszenie invariants zachowuje zmiany stanu dla wszystkich obiektów w tym agregacji.</span><span class="sxs-lookup"><span data-stu-id="8ead8-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="8ead8-106">Domeny jednostek powinna być zawsze prawidłowe jednostki.</span><span class="sxs-lookup"><span data-stu-id="8ead8-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="8ead8-107">Istnieją pewne invariants dla obiekt, który powinien mieć zawsze wartość PRAWDA.</span><span class="sxs-lookup"><span data-stu-id="8ead8-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="8ead8-108">Na przykład obiekt elementu kolejności zawsze musi mieć ilość, która musi być dodatnią liczbą całkowitą, a także nazwę artykułu i ceny.</span><span class="sxs-lookup"><span data-stu-id="8ead8-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="8ead8-109">W związku z tym wymuszania invariants jest odpowiedzialny za jednostek domeny (szczególnie elementu głównego agregacji) i do obiektu jednostki nie powinien móc istnieje nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8ead8-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="8ead8-110">Niezmienna reguły po prostu są wyrażane jako kontrakty i wyjątków lub powiadomienia są wywoływane, gdy są one naruszone.</span><span class="sxs-lookup"><span data-stu-id="8ead8-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="8ead8-111">To uzasadnienie jest wiele usterek wystąpić, ponieważ obiekt jest w stanie, który powinien być nigdy nie był w.</span><span class="sxs-lookup"><span data-stu-id="8ead8-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="8ead8-112">Poniżej przedstawiono dobrej wyjaśnienie z małych Gregowi w [online dyskusji](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="8ead8-112">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="8ead8-113">Proponować Przyjrzyjmy się, że mamy teraz SendUserCreationEmailService, pobierającej UserProfile... jak można możemy racjonalizacja w tej usługi, nazwa nie jest zerowa?</span><span class="sxs-lookup"><span data-stu-id="8ead8-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="8ead8-114">Czy możemy sprawdź go ponownie?</span><span class="sxs-lookup"><span data-stu-id="8ead8-114">Do we check it again?</span></span> <span data-ttu-id="8ead8-115">Lub bardziej prawdopodobne... właśnie nie zostanie odblokowane można sprawdzić i "nadzieję najlepszą" — Mamy nadzieję, że ktoś bothered do weryfikowania go przed wysłaniem do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ead8-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="8ead8-116">Oczywiście przy użyciu TDD pierwszy testów, które firma Microsoft powinien zapisu, jest to, że wysyłania się klientów z zerową nazwą czy powinna Zgłoś błąd.</span><span class="sxs-lookup"><span data-stu-id="8ead8-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="8ead8-117">Jednak po Rozpoczniemy wielokrotnie pisania tego rodzaju testy Zdajemy sobie sprawę... "oczekiwania, jeśli firma Microsoft nigdy nie mogą nazwę, stając się wartości null nie mamy wszystkie te testy"</span><span class="sxs-lookup"><span data-stu-id="8ead8-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="8ead8-118">Implementowanie operacji sprawdzania poprawności w warstwy modelu domeny</span><span class="sxs-lookup"><span data-stu-id="8ead8-118">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="8ead8-119">Sprawdzanie poprawności zwykle są implementowane w konstruktorów jednostek domeny lub metody aktualizowanych jednostki.</span><span class="sxs-lookup"><span data-stu-id="8ead8-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="8ead8-120">Istnieje wiele sposobów, aby zaimplementować metodę sprawdzania, takie jak weryfikowanie danych i wywoływanie wyjątków w przypadku niepowodzenia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="8ead8-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="8ead8-121">Istnieją również bardziej zaawansowanych wzorców, takich jak przy użyciu wzorca specyfikacji dla operacji sprawdzania poprawności i wzorzec powiadomień zwrócić kolekcję błędów zamiast zwracać wyjątek dla każdego weryfikacji występujące.</span><span class="sxs-lookup"><span data-stu-id="8ead8-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="8ead8-122">Sprawdzanie poprawności warunki i zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="8ead8-122">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="8ead8-123">Poniższy przykład kodu pokazuje najprostsza metoda weryfikacji w jednostce domeny przez wywołanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8ead8-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="8ead8-124">Tabela odwołań na końcu tej sekcji przedstawiono łącza do bardziej zaawansowanych implementacje na podstawie wzorców, które wcześniej Omówiliśmy.</span><span class="sxs-lookup"><span data-stu-id="8ead8-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="8ead8-125">Przykład lepsze wskazywałoby konieczność zapewnienia wewnętrzny stan nie został zmieniony lub że wszystkie mutacji metody wystąpił.</span><span class="sxs-lookup"><span data-stu-id="8ead8-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="8ead8-126">Na przykład następująca implementacja spowoduje obiektu w nieprawidłowym stanie:</span><span class="sxs-lookup"><span data-stu-id="8ead8-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="8ead8-127">Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i Miasto już zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="8ead8-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="8ead8-128">Który może być adres nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8ead8-128">That might make the address invalid.</span></span>

<span data-ttu-id="8ead8-129">Podejście podobne można używać w Konstruktorze jednostki, który wywołał wyjątek, aby upewnić się, że obiekt jest prawidłowy, po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="8ead8-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="8ead8-130">Za pomocą atrybutów sprawdzania poprawności na adnotacje danych na podstawie modelu</span><span class="sxs-lookup"><span data-stu-id="8ead8-130">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="8ead8-131">Innym rozwiązaniem jest używanie na adnotacje danych na podstawie atrybutów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8ead8-131">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="8ead8-132">Atrybuty weryfikacji umożliwiają konfigurowanie weryfikacji modelu, który jest podobny koncepcyjnie do sprawdzania poprawności dla pól w tabelach bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8ead8-132">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="8ead8-133">W tym ograniczenia, takie jak przypisywanie typów danych lub wymagane pola.</span><span class="sxs-lookup"><span data-stu-id="8ead8-133">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="8ead8-134">Inne typy weryfikacji obejmują stosowania wzorców do danych do wymuszania reguł biznesowych, takich jak numer karty kredytowej lub numer telefonu lub adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="8ead8-134">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="8ead8-135">Atrybuty weryfikacji ułatwiają wymuszanie wymagania.</span><span class="sxs-lookup"><span data-stu-id="8ead8-135">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="8ead8-136">Jednak jak pokazano w poniższym kodzie, to takie podejście może być zbyt niepożądanych w modelu DDD, ponieważ trwa zależności na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, które należy wywołać z kontrolerów MVC.</span><span class="sxs-lookup"><span data-stu-id="8ead8-136">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="8ead8-137">Sprawdzanie poprawności modelu występuje przed wywoływaną akcję każdego kontrolera i metody kontrolera odpowiedzialność za inspekcji wyników wywołania ModelState.IsValid i odpowiednio zareagować.</span><span class="sxs-lookup"><span data-stu-id="8ead8-137">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="8ead8-138">Zależy decyzji o użyciu go ściśle powiązane ma modelu, który ma być z tej infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="8ead8-138">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="8ead8-139">Jednak z punktu widzenia DDD, model domeny jest najlepiej pozostawić gotowa przy użyciu wyjątków w metodach zachowania użytkownika jednostki lub implementując wzorce specyfikację i powiadomień do wymuszania reguł sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8ead8-139">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="8ead8-140">Struktury sprawdzania poprawności podobnie jak adnotacji danych w ASP.NET Core lub innych platform sprawdzania poprawności podobnie jak FluentValidation przenoszenia wymagane do wywołania struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ead8-140">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="8ead8-141">Na przykład podczas wywoływania metody ModelState.IsValid w adnotacjach danych, należy wywołać kontrolery ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8ead8-141">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="8ead8-142">Go wykrywanie używania adnotacji danych w warstwie aplikacji w klasach ViewModel (a nie jednostek domeny), które będzie akceptować dane wejściowe, aby umożliwić sprawdzanie poprawności modelu w ramach warstwy interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ead8-142">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="8ead8-143">Jednak to nie należy przypisywać na wyłączenie sprawdzania poprawności w ramach modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="8ead8-143">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="8ead8-144">Sprawdzanie poprawności jednostek zaimplementowanie wzoru specyfikacji i powiadomienia</span><span class="sxs-lookup"><span data-stu-id="8ead8-144">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="8ead8-145">Na koniec bardziej złożonych podejście do wykonania operacji sprawdzania poprawności w modelu domeny jest zaimplementowanie wzorzec specyfikacji w połączeniu z wzorcem powiadomień zgodnie z objaśnieniem w niektórych dodatkowych zasobów wymienionych później.</span><span class="sxs-lookup"><span data-stu-id="8ead8-145">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="8ead8-146">Warto zauważyć, że umożliwia także tylko w jednej z tych wzorców — na przykład, sprawdzanie poprawności ręcznie z instrukcji sterowania, ale przy użyciu wzorca powiadomień stosu i zwracający listę błędów weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="8ead8-146">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="8ead8-147">Przy użyciu odroczone sprawdzanie poprawności w domenie</span><span class="sxs-lookup"><span data-stu-id="8ead8-147">Using deferred validation in the domain</span></span>

<span data-ttu-id="8ead8-148">Istnieją różne metody radzenia sobie z odroczone sprawdzanie poprawności w domenie.</span><span class="sxs-lookup"><span data-stu-id="8ead8-148">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="8ead8-149">W jego książce [projekt Implementing Domain-Driven](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon omówiono w sekcji weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="8ead8-149">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="8ead8-150">Weryfikacja dwuetapowa</span><span class="sxs-lookup"><span data-stu-id="8ead8-150">Two-step validation</span></span>

<span data-ttu-id="8ead8-151">Należy również rozważyć weryfikacji dwuetapowej.</span><span class="sxs-lookup"><span data-stu-id="8ead8-151">Also consider two-step validation.</span></span> <span data-ttu-id="8ead8-152">Użyj weryfikacji na poziomie pola na polecenie obiekty Transfer danych (DTOs) i weryfikacji na poziomie dla domeny wewnątrz jednostki.</span><span class="sxs-lookup"><span data-stu-id="8ead8-152">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="8ead8-153">Można to zrobić, zwracając obiekt wyniku zamiast wyjątków w celu ułatwienia postępowania z błędami sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8ead8-153">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="8ead8-154">Za pomocą pola weryfikacji przy użyciu adnotacji danych, na przykład nie duplikowania definicji sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="8ead8-154">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="8ead8-155">Wykonywanie, jednak może być zarówno po stronie serwera i po stronie klienta w przypadku DTOs (polecenia i ViewModels, na przykład).</span><span class="sxs-lookup"><span data-stu-id="8ead8-155">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8ead8-156">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="8ead8-156">Additional resources</span></span>

-   <span data-ttu-id="8ead8-157">**Rachel Appel. Wprowadzenie do sprawdzania poprawności modelu w programie ASP.NET MVC Core**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="8ead8-157">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="8ead8-158">**Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="8ead8-158">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="8ead8-159">**Pole Fowler. Zastępowanie zgłaszanie wyjątków z powiadomień w operacji sprawdzania poprawności**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="8ead8-159">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="8ead8-160">**Specyfikacja i wzorce powiadomień**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="8ead8-160">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="8ead8-161">**LEV Gorodinski. Sprawdzanie poprawności w projekcie oparte na domenie (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="8ead8-161">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="8ead8-162">**Gniazdo Colin. Weryfikacja modelu domeny**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="8ead8-162">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="8ead8-163">**Jimmy Bogard. Sprawdzanie poprawności w świecie DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="8ead8-163">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8ead8-164">[Poprzednie](enumeration-classes-over-enum-types.md)
[dalej](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="8ead8-164">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
