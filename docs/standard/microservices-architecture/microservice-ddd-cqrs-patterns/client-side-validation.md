---
title: Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Zapoznaj się z kluczowymi założeniami programu weryfikacji po stronie klienta.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ddf53456f9356817d28cd0bfa75df3296fb5d722
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020065"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="9bead-103">Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)</span><span class="sxs-lookup"><span data-stu-id="9bead-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="9bead-104">Nawet wtedy, gdy źródło prawdziwych danych jest modelem domeny i ostatecznie konieczne jest posiadanie weryfikacji na poziomie modelu domeny, sprawdzania poprawności, nadal mogą być obsługiwane na poziomie modelu domeny (po stronie serwera) i interfejsu użytkownika (po stronie klienta).</span><span class="sxs-lookup"><span data-stu-id="9bead-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="9bead-105">Weryfikacja po stronie klienta jest doskonałym wygodę dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9bead-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="9bead-106">Zaoszczędzić czas, który one byłby przeznaczany na oczekiwanie na komunikację dwustronną do serwera, który może zwrócić błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="9bead-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="9bead-107">W terminologii biznesowej nawet kilka użycie ułamkowych części sekundy pomnożone setki razy każdego dnia dodaje do mnóstwo czasu i pieniędzy oraz Rozczarowanie.</span><span class="sxs-lookup"><span data-stu-id="9bead-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="9bead-108">Proste i natychmiastowe sprawdzanie poprawności umożliwia użytkownikom bardziej wydajną pracę i wygenerować lepszą jakość danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9bead-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="9bead-109">Tak, jak model widoku i modelu domeny są różne, sprawdzanie poprawności modelu widoku i sprawdzanie poprawności modelu domeny mogą być podobne, ale następnie spełniać różne zadania.</span><span class="sxs-lookup"><span data-stu-id="9bead-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="9bead-110">Jeśli dane o PRÓBNEGO (nie należy powtórzyć samodzielnie zasada), należy wziąć pod uwagę, w tym przypadku ponowne wykorzystanie kodu może również oznaczać sprzężenia i w aplikacjach dla przedsiębiorstw jest niezwykle ważne nie połączenie po stronie serwera na komputerach klienckich, niż się postępuj zgodnie z zasadą susz.</span><span class="sxs-lookup"><span data-stu-id="9bead-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="9bead-111">Nawet korzystając z weryfikacji po stronie klienta, należy zawsze sprawdzić poleceń lub wejściowych dto w kodzie serwera, ponieważ serwer interfejsy API są zaatakowania.</span><span class="sxs-lookup"><span data-stu-id="9bead-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="9bead-112">Zwykle zastosowanie obu podejść jest najlepsze rozwiązanie, ponieważ w przypadku aplikacji klienckiej, z punktu widzenia UX najlepiej stosować proaktywne podejście i uniemożliwia użytkownikowi wprowadzanie nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="9bead-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="9bead-113">W związku z tym w kodzie po stronie klienta zazwyczaj zweryfikowanie modele widoków.</span><span class="sxs-lookup"><span data-stu-id="9bead-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="9bead-114">Można również sprawdzić poprawności klienta przed wysłaniem ich do usługi danych wyjściowych dto ani nowych poleceń.</span><span class="sxs-lookup"><span data-stu-id="9bead-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="9bead-115">Implementacja weryfikacji po stronie klienta zależy od tego, jakiego rodzaju aplikacji klienckiej, którą tworzysz.</span><span class="sxs-lookup"><span data-stu-id="9bead-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="9bead-116">Będzie on być inny, Jeśli zatwierdzasz danych w sieci web aplikacji sieci web MVC za pomocą większość kodu na platformie .NET, SPA aplikacji sieci web z tego są kodowane w języku JavaScript, TypeScript, czy lub aplikacji mobilnej są kodowane za pomocą platformy Xamarin i C#.</span><span class="sxs-lookup"><span data-stu-id="9bead-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9bead-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9bead-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="9bead-118">Sprawdzanie poprawności w aplikacjach mobilnych platformy Xamarin</span><span class="sxs-lookup"><span data-stu-id="9bead-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="9bead-119">**Sprawdź poprawność tekst wejściowy i Pokaż błędy** \\</span><span class="sxs-lookup"><span data-stu-id="9bead-119">**Validate Text Input and Show Errors** \\</span></span>
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="9bead-120">**Wywołanie zwrotne weryfikacji** \\</span><span class="sxs-lookup"><span data-stu-id="9bead-120">**Validation Callback** \\</span></span>
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="9bead-121">Sprawdzanie poprawności w aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9bead-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="9bead-122">**Rick Anderson. Dodawanie walidacji** \\</span><span class="sxs-lookup"><span data-stu-id="9bead-122">**Rick Anderson. Adding validation** \\</span></span>
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="9bead-123">Sprawdzanie poprawności w SPA, Web apps (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="9bead-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="9bead-124">**Ado Kukic. Platformy angular 2 formularz weryfikacji** \\</span><span class="sxs-lookup"><span data-stu-id="9bead-124">**Ado Kukic. Angular 2 Form Validation** \\</span></span>
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="9bead-125">**Weryfikacji formularza** \\</span><span class="sxs-lookup"><span data-stu-id="9bead-125">**Form Validation** \\</span></span>
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="9bead-126">**Sprawdzanie poprawności.**</span><span class="sxs-lookup"><span data-stu-id="9bead-126">**Validation.**</span></span> <span data-ttu-id="9bead-127">Szybka i bezproblemowa dokumentację.</span><span class="sxs-lookup"><span data-stu-id="9bead-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="9bead-128">Podsumowując poniżej przedstawiono najważniejsze pojęcia związane z weryfikacją:</span><span class="sxs-lookup"><span data-stu-id="9bead-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="9bead-129">Jednostki i agregacji należy wymusić spójność własne i ważność "zawsze".</span><span class="sxs-lookup"><span data-stu-id="9bead-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="9bead-130">Katalogi główne agregacji są odpowiedzialne za spójność wielu jednostek w ramach tej samej agregacji.</span><span class="sxs-lookup"><span data-stu-id="9bead-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="9bead-131">Jeśli uważasz, że jednostka musi podać nieprawidłowy stan, należy wziąć pod uwagę przy użyciu modelu innego obiektu — na przykład za pomocą tymczasowy obiekt DTO, dopóki nie utworzysz jednostki końcowej domeny.</span><span class="sxs-lookup"><span data-stu-id="9bead-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="9bead-132">Jeśli musisz utworzyć kilka powiązanych obiektów, takich jak agregacji, i są tylko prawidłowe gdy wszystkie z nich zostały utworzone, należy wziąć pod uwagę przy użyciu wzorca fabryki.</span><span class="sxs-lookup"><span data-stu-id="9bead-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="9bead-133">W większości przypadków nadmiarowe weryfikacji po stronie klienta jest dobre rozwiązanie, ponieważ aplikacja może być aktywne.</span><span class="sxs-lookup"><span data-stu-id="9bead-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9bead-134">[Poprzednie](domain-model-layer-validations.md)
>[dalej](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="9bead-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
