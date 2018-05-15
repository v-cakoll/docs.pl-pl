---
title: Weryfikacja po stronie klienta (Sprawdzanie poprawności w warstwy prezentacji)
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Weryfikacja po stronie klienta (Sprawdzanie poprawności w warstwy prezentacji)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2adce39561dd2b97910155ebed595a2df7785c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="4ade9-103">Weryfikacja po stronie klienta (Sprawdzanie poprawności w warstwy prezentacji)</span><span class="sxs-lookup"><span data-stu-id="4ade9-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="4ade9-104">Nawet wtedy, gdy źródłem prawdy jest model domeny, a ostatecznie musi mieć weryfikacji na poziomie modelu domeny, sprawdzania poprawności, nadal mogą być obsługiwane zarówno po stronie klienta, jak i poziom modelu domeny (po stronie serwera).</span><span class="sxs-lookup"><span data-stu-id="4ade9-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="4ade9-105">Weryfikacja po stronie klienta jest doskonałym ułatwienia dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4ade9-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="4ade9-106">Zapisuje w przeciwnym razie poświęcić czas oczekiwania na obiegu do serwera, który może zwrócić błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="4ade9-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="4ade9-107">W terminologii biznesowej nawet kilka części sekundy pomnożone setki razy każdego dnia dodaje do dużo czasu, wydatków i frustracji spowodowanej.</span><span class="sxs-lookup"><span data-stu-id="4ade9-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="4ade9-108">Proste i bezpośrednie weryfikacji umożliwia użytkownikom wydajniejszą pracę i tworzy lepszą jakość danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4ade9-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="4ade9-109">Tak samo, jak model widoku i modelu domeny są różne, sprawdzanie poprawności modelu widoku i weryfikacji modelu domeny może być podobne, ale następnie służą do różnych celów.</span><span class="sxs-lookup"><span data-stu-id="4ade9-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="4ade9-110">Jeśli wiadomo o suchej (nie powtarzaj samodzielnie zasada), należy wziąć pod uwagę w tym przypadku ponowne użycie kodu może to także oznaczać sprzężenia, czy w aplikacjach dla przedsiębiorstw jest ważniejsze nie do sprzęgania po stronie serwera po stronie klienta niż wykonaj suchej zasady.</span><span class="sxs-lookup"><span data-stu-id="4ade9-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="4ade9-111">Nawet przy użyciu weryfikacji po stronie klienta, należy zawsze sprawdzić poleceniach lub wejściowych DTOs w kodzie serwera, ponieważ serwer interfejsy API są zaatakowania.</span><span class="sxs-lookup"><span data-stu-id="4ade9-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="4ade9-112">Zazwyczaj zastosowanie obu jest najlepsze rozwiązanie, ponieważ jeśli masz aplikację klienta z punktu widzenia środowiska użytkownika jest najlepszym rozwiązaniem jest aktywne i nie zezwala użytkownikowi na wprowadzenie nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="4ade9-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="4ade9-113">W związku z tym w kodzie po stronie klienta zazwyczaj sprawdzania poprawności ViewModels.</span><span class="sxs-lookup"><span data-stu-id="4ade9-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="4ade9-114">Można również sprawdzić poprawności klienta dane wyjściowe poleceń lub DTOs przed wysłaniem ich do usług.</span><span class="sxs-lookup"><span data-stu-id="4ade9-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="4ade9-115">Implementacja weryfikacji po stronie klienta zależy od tego, jakiego rodzaju aplikacji klienckiej tworzenia.</span><span class="sxs-lookup"><span data-stu-id="4ade9-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="4ade9-116">Będzie inny są sprawdzanie poprawności danych w sieci web aplikacji sieci web MVC za pomocą większość kodu w aplikacji sieci web SPA przy użyciu tego sprawdzania poprawności jest kodowany w JavaScript i TypeScript, .NET lub aplikacji mobilnej na stałe dzięki platformie Xamarin i C\#.</span><span class="sxs-lookup"><span data-stu-id="4ade9-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4ade9-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="4ade9-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="4ade9-118">Sprawdzanie poprawności w aplikacji mobilnych Xamarin</span><span class="sxs-lookup"><span data-stu-id="4ade9-118">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="4ade9-119">**Sprawdź poprawność wejściowego tekstu i Pokaż komunikaty o błędach**
    [*https://developer.xamarin.com/recipes/ios/standard\_formanty/tekstu\_pola/zweryfikować\_wejściowych /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="4ade9-119">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="4ade9-120">**Wywołanie zwrotne weryfikacji**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="4ade9-120">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="4ade9-121">Sprawdzanie poprawności w aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4ade9-121">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="4ade9-122">**Rick Anderson. Dodawanie walidacji**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="4ade9-122">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="4ade9-123">Sprawdzanie poprawności w SPA Web apps (kątowego 2 TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="4ade9-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="4ade9-124">**Ado Kukic. Dyrektywy angular weryfikacji formularza 2** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="4ade9-124">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="4ade9-125">**Sprawdzanie poprawności formularza**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="4ade9-125">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="4ade9-126">**Sprawdzanie poprawności.**</span><span class="sxs-lookup"><span data-stu-id="4ade9-126">**Validation.**</span></span> <span data-ttu-id="4ade9-127">Błyskawicznie dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="4ade9-127">Breeze documentation.</span></span>
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="4ade9-128">Podsumowując są najważniejsze pojęcia w odniesieniu do sprawdzania poprawności:</span><span class="sxs-lookup"><span data-stu-id="4ade9-128">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="4ade9-129">Jednostki i agreguje powinien wymuszać własnych spójności i ważność "zawsze".</span><span class="sxs-lookup"><span data-stu-id="4ade9-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="4ade9-130">Łączny certyfikaty główne są odpowiedzialne za spójności obejmujące wiele urządzeń w ramach tej samej agregacji.</span><span class="sxs-lookup"><span data-stu-id="4ade9-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="4ade9-131">Jeśli uważasz, że jednostka musi podać nieprawidłowy stan, należy wziąć pod uwagę przy użyciu modelu innego obiektu — na przykład przy użyciu tymczasowego DTO, dopóki nie zostaną utworzone jednostki końcowej domeny.</span><span class="sxs-lookup"><span data-stu-id="4ade9-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="4ade9-132">Należy utworzyć kilka powiązanych obiektów, takich jak agregacji, są one tylko prawidłowe po wszystkich z nich zostały utworzone, należy wziąć pod uwagę przy użyciu wzorca fabryki.</span><span class="sxs-lookup"><span data-stu-id="4ade9-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="4ade9-133">Struktury weryfikacji najlepiej służą w określonych warstw, takich jak warstwy prezentacji lub warstwy aplikacji/usługi, ale zwykle nie warstwy modelu domeny, ponieważ będzie potrzebny do wykonania silne zależności w ramach infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="4ade9-133">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="4ade9-134">W większości przypadków nadmiarowe weryfikacji po stronie klienta jest dobra, ponieważ aplikacji mogą być aktywne.</span><span class="sxs-lookup"><span data-stu-id="4ade9-134">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4ade9-135">[Poprzednie] (domena — model warstwy — validations.md) [dalej] (domena zdarzenia projekt implementation.md)</span><span class="sxs-lookup"><span data-stu-id="4ade9-135">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>
