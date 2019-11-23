---
title: Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Poznaj kluczowe pojęcia związane z walidacją po stronie klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295996"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="a018e-103">Weryfikacja po stronie klienta (weryfikacja w warstwach prezentacji)</span><span class="sxs-lookup"><span data-stu-id="a018e-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="a018e-104">Nawet wtedy, gdy źródło prawdy jest modelem domeny i ostatecznie należy przeprowadzić weryfikację na poziomie modelu domeny, sprawdzanie poprawności może być nadal obsługiwane zarówno na poziomie modelu domeny (po stronie serwera), jak i w interfejsie użytkownika (po stronie klienta).</span><span class="sxs-lookup"><span data-stu-id="a018e-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="a018e-105">Sprawdzanie poprawności po stronie klienta jest doskonałym rozwiązaniem dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a018e-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="a018e-106">Pozwala to zaoszczędzić czas oczekiwania na przekazanie komunikacji z serwerem, który może zwrócić błędy walidacji.</span><span class="sxs-lookup"><span data-stu-id="a018e-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="a018e-107">W przypadku warunków handlowych nawet kilka części sekund pomnożone przez setki razy każdy dzień dodaje do dużo czasu, wydatków i frustrację.</span><span class="sxs-lookup"><span data-stu-id="a018e-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="a018e-108">Bezpośrednie i natychmiastowe sprawdzanie poprawności umożliwia użytkownikom wydajniejszą pracę i generowanie lepszych danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a018e-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="a018e-109">Podobnie jak model widoku i model domeny różnią się, sprawdzanie poprawności modelu i sprawdzanie poprawności modelu domeny może być podobne, ale w innym celu.</span><span class="sxs-lookup"><span data-stu-id="a018e-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="a018e-110">Jeśli chodzi o zawartość suchej (Nie powtarzaj się zasady), należy rozważyć, że w tym przypadku ponowne użycie kodu może również oznaczać sprzężenie, a w aplikacjach korporacyjnych ważniejsze jest, aby nie podłączać po stronie klienta strony serwera niż w przypadku wypełniania wysuszonej zasady.</span><span class="sxs-lookup"><span data-stu-id="a018e-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="a018e-111">Nawet w przypadku korzystania z walidacji po stronie klienta należy zawsze sprawdzać poprawność poleceń lub danych wejściowych DTO w kodzie serwera, ponieważ interfejsy API serwera są możliwym do zaatakowania.</span><span class="sxs-lookup"><span data-stu-id="a018e-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="a018e-112">Zwykle najlepszym trafieniem jest to, że jeśli masz aplikację kliencką, z perspektywy środowiska użytkownika najlepiej jest ją uaktywnić i nie zezwalać użytkownikowi na wprowadzanie nieprawidłowych informacji.</span><span class="sxs-lookup"><span data-stu-id="a018e-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="a018e-113">W związku z tym w kodzie po stronie klienta zwykle sprawdzane jest modele widoków.</span><span class="sxs-lookup"><span data-stu-id="a018e-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="a018e-114">Możesz również zweryfikować DTO danych wyjściowych klienta lub polecenia przed wysłaniem ich do usług.</span><span class="sxs-lookup"><span data-stu-id="a018e-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="a018e-115">Implementacja weryfikacji po stronie klienta zależy od rodzaju kompilowanej aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="a018e-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="a018e-116">Będzie ona różna w przypadku sprawdzania poprawności danych w aplikacji sieci Web MVC w sieci Web z większością kodu w programie .NET, aplikacja sieci Web SPA z tą walidacją jest zakodowana w języku JavaScript lub TypeScript lub w aplikacji mobilnej C#kodowanej przy użyciu platformy Xamarin i.</span><span class="sxs-lookup"><span data-stu-id="a018e-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a018e-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="a018e-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="a018e-118">Walidacja w usłudze Xamarin Mobile Apps</span><span class="sxs-lookup"><span data-stu-id="a018e-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="a018e-119">**Weryfikuj wprowadzanie tekstu i Wyświetlaj błędy** </span><span class="sxs-lookup"><span data-stu-id="a018e-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="a018e-120"> \ **wywołania zwrotnego walidacji**</span><span class="sxs-lookup"><span data-stu-id="a018e-120">**Validation Callback** \</span></span>
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="a018e-121">Walidacja w aplikacjach ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a018e-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="a018e-122">**Rick Anderson. Dodawanie \ weryfikacji**</span><span class="sxs-lookup"><span data-stu-id="a018e-122">**Rick Anderson. Adding validation** \</span></span>
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="a018e-123">Walidacja w aplikacjach sieci Web SPA (kątowy 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="a018e-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="a018e-124">**KuKic ADO. \ walidacji formularza** z kątem 2</span><span class="sxs-lookup"><span data-stu-id="a018e-124">**Ado Kukic. Angular 2 Form Validation** \</span></span>
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="a018e-125"> \ **walidacji formularza**</span><span class="sxs-lookup"><span data-stu-id="a018e-125">**Form Validation** \</span></span>
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="a018e-126">**Zatwierdzenia.**</span><span class="sxs-lookup"><span data-stu-id="a018e-126">**Validation.**</span></span> <span data-ttu-id="a018e-127">Dokumentacja Breeze.</span><span class="sxs-lookup"><span data-stu-id="a018e-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="a018e-128">Podsumowując, są to najważniejsze koncepcje dotyczące weryfikacji:</span><span class="sxs-lookup"><span data-stu-id="a018e-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="a018e-129">Jednostki i agregacje powinny wymusić swoją własną spójność i mieć wartość "zawsze prawidłowy".</span><span class="sxs-lookup"><span data-stu-id="a018e-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="a018e-130">Zagregowane elementy główne są odpowiedzialne za spójność w ramach tej samej agregacji.</span><span class="sxs-lookup"><span data-stu-id="a018e-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="a018e-131">Jeśli uważasz, że jednostka musi wprowadzić nieprawidłowy stan, rozważ użycie innego modelu obiektów — na przykład przy użyciu tymczasowej DTO do momentu utworzenia końcowej jednostki domeny.</span><span class="sxs-lookup"><span data-stu-id="a018e-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="a018e-132">Jeśli musisz utworzyć kilka powiązanych obiektów, takich jak agregowanie, i są one prawidłowe tylko wtedy, gdy wszystkie z nich zostały utworzone, rozważ użycie wzorca fabryki.</span><span class="sxs-lookup"><span data-stu-id="a018e-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="a018e-133">W większości przypadków posiadanie nadmiarowej weryfikacji na stronie klienta jest dobre, ponieważ aplikacja może być aktywna.</span><span class="sxs-lookup"><span data-stu-id="a018e-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a018e-134">[Poprzedni](domain-model-layer-validations.md)
>[Następny](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="a018e-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
