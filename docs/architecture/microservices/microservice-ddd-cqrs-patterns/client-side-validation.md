---
title: Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się z kluczowymi pojęciami sprawdzania poprawności po stronie klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 44c1e9fa280b19fcee87d4d1cdfcaa2ab9462f27
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988704"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="408b8-103">Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)</span><span class="sxs-lookup"><span data-stu-id="408b8-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="408b8-104">Nawet wtedy, gdy źródłem prawdy jest model domeny i ostatecznie musi mieć sprawdzania poprawności na poziomie modelu domeny, sprawdzanie poprawności nadal mogą być obsługiwane zarówno na poziomie modelu domeny (po stronie serwera) i interfejsu użytkownika (po stronie klienta).</span><span class="sxs-lookup"><span data-stu-id="408b8-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="408b8-105">Walidacja po stronie klienta to duże udogodnienie dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="408b8-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="408b8-106">Oszczędza czas, który w przeciwnym razie spędzają czekając na podróż w obie strony do serwera, który może zwracać błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="408b8-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="408b8-107">W kategoriach biznesowych, nawet kilka ułamków sekund pomnożone setki razy dziennie dodaje się do dużo czasu, wydatków i frustracji.</span><span class="sxs-lookup"><span data-stu-id="408b8-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="408b8-108">Prosta i natychmiastowa walidacja umożliwia użytkownikom wydajniejszą pracę i uzyskanie lepszej jakości danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="408b8-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="408b8-109">Podobnie jak model widoku i model domeny są różne, sprawdzanie poprawności modelu widoku i sprawdzania poprawności modelu domeny może być podobne, ale służyć innemu celowi.</span><span class="sxs-lookup"><span data-stu-id="408b8-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="408b8-110">Jeśli obawiasz się dry (zasada Nie powtarzaj siebie), należy wziąć pod uwagę, że w tym przypadku ponowne użycie kodu może również oznaczać sprzężenie, a w aplikacjach korporacyjnych ważniejsze jest, aby nie łączyć strony serwera po stronie klienta niż przestrzegać zasady DRY.</span><span class="sxs-lookup"><span data-stu-id="408b8-110">If you are concerned about DRY (the Don't Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="408b8-111">Nawet podczas korzystania z sprawdzania poprawności po stronie klienta, należy zawsze sprawdzić poprawność poleceń lub wejściowych DTO w kodzie serwera, ponieważ interfejsy API serwera są możliwe wektor ataku.</span><span class="sxs-lookup"><span data-stu-id="408b8-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="408b8-112">Zazwyczaj robienie obu jest najlepszym rozwiązaniem, ponieważ jeśli masz aplikację kliencką, z punktu widzenia środowiska użytkownika, najlepiej jest być proaktywnym i nie zezwalać użytkownikowi na wprowadzanie nieprawidłowych informacji.</span><span class="sxs-lookup"><span data-stu-id="408b8-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="408b8-113">W związku z tym w kodzie po stronie klienta zazwyczaj sprawdź poprawność ViewModels.</span><span class="sxs-lookup"><span data-stu-id="408b8-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="408b8-114">Można również sprawdzić poprawność danych DTO danych wyjściowych klienta lub poleceń przed wysłaniem ich do usług.</span><span class="sxs-lookup"><span data-stu-id="408b8-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="408b8-115">Implementacja sprawdzania poprawności po stronie klienta zależy od tego, jakiego rodzaju aplikacji klienckiej, którą budujesz.</span><span class="sxs-lookup"><span data-stu-id="408b8-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="408b8-116">Będzie inaczej, jeśli sprawdzasz dane w internetowej aplikacji sieci web MVC z większością kodu w .NET, aplikacji sieci web SPA z tą weryfikacją kodowane w javascript lub TypeScript lub aplikacji mobilnej zakodowanej za pomocą platformy Xamarin i C#.</span><span class="sxs-lookup"><span data-stu-id="408b8-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="408b8-117">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="408b8-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="408b8-118">Sprawdzanie poprawności w aplikacjach mobilnych platformy Xamarin</span><span class="sxs-lookup"><span data-stu-id="408b8-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="408b8-119">**Sprawdzanie poprawności wprowadzania tekstu i pokazywalanie błędów** </span><span class="sxs-lookup"><span data-stu-id="408b8-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="408b8-120">**Wywołanie zwrotne w weryfikacji** </span><span class="sxs-lookup"><span data-stu-id="408b8-120">**Validation Callback** </span></span>\
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="408b8-121">Sprawdzanie poprawności w aplikacjach ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="408b8-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="408b8-122">**Rick Anderson. Dodawanie sprawdzania poprawności** </span><span class="sxs-lookup"><span data-stu-id="408b8-122">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="408b8-123">Sprawdzanie poprawności w aplikacjach SIECI Web SPA (kątowe 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="408b8-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="408b8-124">**Ado Kukic. Sprawdzanie poprawności formularza kątowego 2** </span><span class="sxs-lookup"><span data-stu-id="408b8-124">**Ado Kukic. Angular 2 Form Validation** </span></span>\
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="408b8-125">**Sprawdzanie poprawności formularza** </span><span class="sxs-lookup"><span data-stu-id="408b8-125">**Form Validation** </span></span>\
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="408b8-126">**Sprawdzania poprawności.**</span><span class="sxs-lookup"><span data-stu-id="408b8-126">**Validation.**</span></span> <span data-ttu-id="408b8-127">Dokumentacja breeze.</span><span class="sxs-lookup"><span data-stu-id="408b8-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="408b8-128">Podsumowując, są to najważniejsze pojęcia dotyczące walidacji:</span><span class="sxs-lookup"><span data-stu-id="408b8-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="408b8-129">Jednostki i agregaty powinny wymuszać własną spójność i być "zawsze ważne".</span><span class="sxs-lookup"><span data-stu-id="408b8-129">Entities and aggregates should enforce their own consistency and be "always valid".</span></span> <span data-ttu-id="408b8-130">Zagregowane katalogi główne są odpowiedzialne za spójność wielu jednostek w ramach tego samego agregacji.</span><span class="sxs-lookup"><span data-stu-id="408b8-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="408b8-131">Jeśli uważasz, że jednostka musi wprowadzić nieprawidłowy stan, należy rozważyć użycie innego modelu obiektu — na przykład przy użyciu tymczasowego celu duchcę, dopóki nie utworzysz ostatecznej jednostki domeny.</span><span class="sxs-lookup"><span data-stu-id="408b8-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="408b8-132">Jeśli trzeba utworzyć kilka powiązanych obiektów, takich jak agregacja i są one prawidłowe tylko po utworzeniu wszystkich z nich, należy rozważyć użycie wzorzec Factory.</span><span class="sxs-lookup"><span data-stu-id="408b8-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="408b8-133">W większości przypadków o nadmiarowe sprawdzania poprawności po stronie klienta jest dobry, ponieważ aplikacja może być aktywne.</span><span class="sxs-lookup"><span data-stu-id="408b8-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="408b8-134">[Poprzedni](domain-model-layer-validations.md)
>[następny](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="408b8-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
