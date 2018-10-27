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
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="7d264-103">Projektowanie reguł weryfikacji w warstwie modelu domeny</span><span class="sxs-lookup"><span data-stu-id="7d264-103">Designing validations in the domain model layer</span></span>

<span data-ttu-id="7d264-104">W DDD reguł sprawdzania poprawności można traktować jako invariants.</span><span class="sxs-lookup"><span data-stu-id="7d264-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="7d264-105">Podstawowa odpowiedzialność agregacji jest wymusić invariants na zmiany stanu dla wszystkich jednostek w ramach tej agregacji.</span><span class="sxs-lookup"><span data-stu-id="7d264-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="7d264-106">Jednostki domeny powinny być zawsze prawidłowe jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d264-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="7d264-107">Istnieją pewne invariants dla obiektu, który powinien zawsze być prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="7d264-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="7d264-108">Na przykład obiekt elementu kolejności zawsze musi mieć ilość, który musi być dodatnią liczbą całkowitą, a także nazwę artykułu i ceny.</span><span class="sxs-lookup"><span data-stu-id="7d264-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="7d264-109">Dlatego wymuszania invariants odpowiada jednostki domeny (zwłaszcza w zakresie głównego agregacji) i obiektu jednostki nie powinno być możliwe istnieje nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="7d264-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="7d264-110">Zasad niezmiennej po prostu są wyrażane jako kontraktów i powiadomienia lub wyjątki są zgłaszane w przypadku ich naruszenia.</span><span class="sxs-lookup"><span data-stu-id="7d264-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="7d264-111">Uzasadnienie to to, że wiele błędów być fakt, że obiekty są w stanie, które powinny mieć nigdy nie był w.</span><span class="sxs-lookup"><span data-stu-id="7d264-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="7d264-112">Poniżej przedstawiono dobry opis z Grega Younga w [dyskusji](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="7d264-112">The following is a good explanation from Greg Young in an [online discussion](https://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="7d264-113">Zaproponuj Załóżmy że mamy teraz SendUserCreationEmailService, wykorzystującej UserProfile... jak można możemy racjonalizować w tej usłudze, że nazwa nie jest null?</span><span class="sxs-lookup"><span data-stu-id="7d264-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="7d264-114">Czy możemy sprawdzić go ponownie?</span><span class="sxs-lookup"><span data-stu-id="7d264-114">Do we check it again?</span></span> <span data-ttu-id="7d264-115">Lub bardziej prawdopodobne... po prostu nie zostanie odblokowane można sprawdzić i "najlepszą nadzieję, że" — Mamy nadzieję, że ktoś bothered, aby zweryfikować, czy przed wysłaniem ich do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="7d264-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="7d264-116">Oczywiście za pomocą TDD pierwszy testy, które firma Microsoft należy pisania, jest to, że jeśli wysyła się klientów z nazwą wartości null, należy je zgłosić błąd.</span><span class="sxs-lookup"><span data-stu-id="7d264-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="7d264-117">Jednak gdy Rozpoczniemy wielokrotnie pisania tego rodzaju testy Zdajemy sobie sprawę... "oczekiwania, jeśli firma Microsoft nigdy nie mogą nazwę, aby stać się o wartości null nie mamy wszystkich tych testów"</span><span class="sxs-lookup"><span data-stu-id="7d264-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="7d264-118">Implementowanie walidacji w warstwie modelu domeny</span><span class="sxs-lookup"><span data-stu-id="7d264-118">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="7d264-119">Sprawdzanie poprawności zwykle są implementowane w konstruktorach jednostki domeny lub za pomocą metod, które mogą aktualizować jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d264-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="7d264-120">Istnieje wiele sposobów implementowania operacji sprawdzania poprawności, takie jak weryfikowanie danych i wywoływanie wyjątków w przypadku niepowodzenia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="7d264-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="7d264-121">Istnieją również bardziej zaawansowane wzorców, takich jak przy użyciu wzorca specyfikacji dla sprawdzanie poprawności i wzorzec powiadomień do zwrócenia zbierania błędów zamiast zwracać wyjątek dla każdego sprawdzania poprawności, ponieważ występuje.</span><span class="sxs-lookup"><span data-stu-id="7d264-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="7d264-122">Sprawdzanie poprawności warunków i zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="7d264-122">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="7d264-123">Poniższy przykład kodu pokazuje najprostsza metoda sprawdzania poprawności w jednostce domeny, podnosząc wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7d264-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="7d264-124">W tabeli odniesienia na końcu tej sekcji można zobaczyć łącza do bardziej zaawansowanych implementacji na podstawie wzorców, które Omówiliśmy wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7d264-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="7d264-125">Przykład lepsze wskazywałoby potrzebę zapewnienia wewnętrzny stan nie został zmieniony lub że wszystkie mutację dla metody wystąpił.</span><span class="sxs-lookup"><span data-stu-id="7d264-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="7d264-126">Na przykład następującą implementacją spowoduje, że obiekt w nieprawidłowym stanie:</span><span class="sxs-lookup"><span data-stu-id="7d264-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="7d264-127">Jeśli wartość stanu jest nieprawidłowa, pierwszy wiersz adresu i Miasto już zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="7d264-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="7d264-128">Który może mieć adres nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7d264-128">That might make the address invalid.</span></span>

<span data-ttu-id="7d264-129">Podejście podobne może służyć w Konstruktorze jednostki, zgłaszania wyjątku, aby upewnić się, że jednostka jest prawidłowa, po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="7d264-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="7d264-130">W modelu, w oparciu o adnotacje danych przy użyciu atrybutów sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="7d264-130">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="7d264-131">Innym podejściem jest używać atrybutów sprawdzania poprawności, w zależności od adnotacji danych.</span><span class="sxs-lookup"><span data-stu-id="7d264-131">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="7d264-132">Atrybuty weryfikacji umożliwiają konfigurowanie weryfikacji modelu, które są podobne pod względem koncepcyjnym do sprawdzania poprawności w polach w tabelach bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7d264-132">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="7d264-133">Obejmuje to ograniczenia, takie jak przypisywanie typów danych lub wymagane pola.</span><span class="sxs-lookup"><span data-stu-id="7d264-133">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="7d264-134">Inne rodzaje weryfikacji obejmują stosowania wzorców do danych w celu wymuszania reguł biznesowych, takich jak numer karty kredytowej lub numer telefonu lub adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="7d264-134">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="7d264-135">Atrybuty weryfikacji ułatwiają wymuszanie wymagań dotyczących.</span><span class="sxs-lookup"><span data-stu-id="7d264-135">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="7d264-136">Jednakże jak pokazano w poniższym kodzie, to takie podejście może być zbyt bez wprowadzania niepożądanych w modelu DDD, z powodu zależności na ModelState.IsValid z Microsoft.AspNetCore.Mvc.ModelState, który musi wywołać z kontrolerów MVC.</span><span class="sxs-lookup"><span data-stu-id="7d264-136">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="7d264-137">Sprawdzanie poprawności modelu występującą przed każdym wywoływana Akcja kontrolera i odpowiada za metody kontrolera sprawdzić wynik wywoływania ModelState.IsValid i odpowiednio reagują.</span><span class="sxs-lookup"><span data-stu-id="7d264-137">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="7d264-138">Decyzja z niej korzystać zależy ściśle mają model, który ma być z tej infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="7d264-138">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="7d264-139">Jednak z punktu widzenia DDD, model domeny jest najlepiej pozostawić zwarte przy użyciu wyjątków w metodach zachowanie Twojej jednostki lub poprzez implementację wzorców Specyfikacja i powiadomień w celu wymuszania reguł sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7d264-139">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="7d264-140">Sprawdzanie poprawności środowisk, takich jak adnotacje danych na platformie ASP.NET Core lub innych struktur sprawdzania poprawności podobnie jak FluentValidation wykonać wymagane do wywołania struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d264-140">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="7d264-141">Na przykład podczas wywoływania metody ModelState.IsValid w adnotacjach danych, należy wywołać kontrolerów platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7d264-141">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="7d264-142">Sensowne może używać adnotacji danych w warstwie aplikacji w klas ViewModel (zamiast domeny podmioty), które akceptują dane wejściowe, aby zezwolić na potrzeby weryfikacji modelu w ramach warstwy interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d264-142">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="7d264-143">Jednak to nie należy wykonywać na wyłączenie sprawdzania poprawności w ramach modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="7d264-143">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="7d264-144">Sprawdzanie poprawności jednostek poprzez implementację wzoru specyfikacji i powiadomienia</span><span class="sxs-lookup"><span data-stu-id="7d264-144">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="7d264-145">Na koniec bardziej złożonych podejściem implementowania operacji sprawdzania poprawności w modelu domeny jest implementacja wzorca specyfikacji w połączeniu z wzorcem powiadomień, jak wyjaśniono w niektóre dodatkowe zasoby wymienione w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="7d264-145">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="7d264-146">Warto zauważyć, że umożliwia także tylko jeden z tych wzorców — na przykład, sprawdzanie poprawności ręcznie za pomocą instrukcji sterowania, ale przy użyciu wzorca powiadomień do stosu i powrócić do listy błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7d264-146">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="7d264-147">Za pomocą odroczonego sprawdzania poprawności w domenie</span><span class="sxs-lookup"><span data-stu-id="7d264-147">Using deferred validation in the domain</span></span>

<span data-ttu-id="7d264-148">Istnieją różne metody radzenia sobie z opóźnieniem walidacji w domenie.</span><span class="sxs-lookup"><span data-stu-id="7d264-148">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="7d264-149">W książce [projektowania Implementing Domain-Driven](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon w tym artykule omówiono w sekcji podczas weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="7d264-149">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="7d264-150">Weryfikacja dwuetapowa</span><span class="sxs-lookup"><span data-stu-id="7d264-150">Two-step validation</span></span>

<span data-ttu-id="7d264-151">Należy również rozważyć weryfikacji dwuetapowej.</span><span class="sxs-lookup"><span data-stu-id="7d264-151">Also consider two-step validation.</span></span> <span data-ttu-id="7d264-152">Użyj weryfikacji na poziomie pola na polecenia obiektów transferu danych (dto) i weryfikacji na poziomie dla domeny wewnątrz jednostek.</span><span class="sxs-lookup"><span data-stu-id="7d264-152">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="7d264-153">Można to zrobić, zwracając obiekt wyniku zamiast tego wyjątki ułatwi radzić sobie z błędami sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7d264-153">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="7d264-154">Za pomocą weryfikacji pola przy użyciu adnotacji danych, na przykład nie duplikowania definicji sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7d264-154">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="7d264-155">Wykonanie, jednak może być zarówno po stronie serwera, jak i po stronie klienta w przypadku dto (polecenia i modele widoków, na przykład).</span><span class="sxs-lookup"><span data-stu-id="7d264-155">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7d264-156">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7d264-156">Additional resources</span></span>

-   <span data-ttu-id="7d264-157">**Rachel Appel. Wprowadzenie do weryfikacji modelu w aplikacji ASP.NET Core MVC**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="7d264-157">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="7d264-158">**Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="7d264-158">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="7d264-159">**Martina Fowlera. Zastępowanie zgłaszanie wyjątków z powiadomieniem w walidacji**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="7d264-159">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="7d264-160">**Specyfikacja i wzorce powiadomień**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="7d264-160">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="7d264-161">**Lew Gorodinski. Sprawdzanie poprawności w projektowania opartego na domenach (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="7d264-161">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="7d264-162">**Gniazdo Colin. Sprawdzanie poprawności modelu domeny**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="7d264-162">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="7d264-163">**Jimmy Bogard. Sprawdzanie poprawności w świecie DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="7d264-163">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7d264-164">[Poprzednie](enumeration-classes-over-enum-types.md)
[dalej](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="7d264-164">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
