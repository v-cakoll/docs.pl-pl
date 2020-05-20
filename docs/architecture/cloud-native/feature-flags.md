---
title: Flagi funkcji
description: Implementuj flagi funkcji w aplikacjach natywnych w chmurze korzystających z konfiguracji aplikacji platformy Azure
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 607bd14a415a25b382f550e697542cf749a21772
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614074"
---
# <a name="feature-flags"></a><span data-ttu-id="13bd6-103">Flagi funkcji</span><span class="sxs-lookup"><span data-stu-id="13bd6-103">Feature flags</span></span>

<span data-ttu-id="13bd6-104">W rozdziale 1 zagwarantujemy, że chmura w chmurze ma wiele informacji o szybkości i elastyczności.</span><span class="sxs-lookup"><span data-stu-id="13bd6-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="13bd6-105">Użytkownicy oczekują szybkiego reagowania, innowacyjnych funkcji i zerowego przestoju.</span><span class="sxs-lookup"><span data-stu-id="13bd6-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="13bd6-106">`Feature flags`to nowoczesny technik wdrażania, który pomaga zwiększyć elastyczność dla aplikacji natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="13bd6-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="13bd6-107">Umożliwiają one wdrażanie nowych funkcji w środowisku produkcyjnym, ale ogranicza ich dostępność.</span><span class="sxs-lookup"><span data-stu-id="13bd6-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="13bd6-108">Dzięki szybkiemu przejściu przełącznika można aktywować nową funkcję dla określonych użytkowników bez konieczności ponownego uruchamiania aplikacji ani wdrażania nowego kodu.</span><span class="sxs-lookup"><span data-stu-id="13bd6-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="13bd6-109">Oddzielają one wydanie nowych funkcji od ich wdrożenia kodu.</span><span class="sxs-lookup"><span data-stu-id="13bd6-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="13bd6-110">Flagi funkcji są tworzone na podstawie logiki warunkowej kontrolującej widoczność funkcji dla użytkowników w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="13bd6-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="13bd6-111">W nowoczesnych systemach natywnych w chmurze często Wdrażaj nowe funkcje w środowisku produkcyjnym, ale Przetestuj je za pomocą ograniczonej grupy odbiorców.</span><span class="sxs-lookup"><span data-stu-id="13bd6-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="13bd6-112">W miarę wzrostu pewności funkcja może zostać przeprowadzona przyrostowo dla szerszego grona odbiorców.</span><span class="sxs-lookup"><span data-stu-id="13bd6-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="13bd6-113">Inne przypadki użycia dla flag funkcji obejmują:</span><span class="sxs-lookup"><span data-stu-id="13bd6-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="13bd6-114">Ogranicz funkcje premium do określonych grup klientów, które mają być obciążane wyższymi opłatami za subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="13bd6-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="13bd6-115">Stabilizacja systemu przez szybkie dezaktywowanie funkcji problemu, unikając ryzyka wycofania lub natychmiastowej poprawki.</span><span class="sxs-lookup"><span data-stu-id="13bd6-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="13bd6-116">Wyłącz opcjonalną funkcję z wysokim zużyciem zasobów w okresach szczytowego użycia.</span><span class="sxs-lookup"><span data-stu-id="13bd6-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="13bd6-117">Przeprowadzenie `experimental feature releases` do małych segmentów użytkowników w celu sprawdzenia wykonalności i popularności.</span><span class="sxs-lookup"><span data-stu-id="13bd6-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="13bd6-118">Flagi funkcji wspierają także `trunk-based` programowanie.</span><span class="sxs-lookup"><span data-stu-id="13bd6-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="13bd6-119">Jest to model rozgałęzienia kontroli źródła, w którym deweloperzy pracują nad funkcjami w pojedynczej gałęzi.</span><span class="sxs-lookup"><span data-stu-id="13bd6-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="13bd6-120">Podejście minimalizuje ryzyko i złożoność scalania dużej liczby długotrwałych gałęzi funkcji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="13bd6-121">Funkcja jest niedostępna, dopóki nie zostanie aktywowana.</span><span class="sxs-lookup"><span data-stu-id="13bd6-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="13bd6-122">Implementowanie flag funkcji</span><span class="sxs-lookup"><span data-stu-id="13bd6-122">Implementing feature flags</span></span>

<span data-ttu-id="13bd6-123">W jego rdzeńu flaga funkcji jest odwołaniem do prostej `decision object` .</span><span class="sxs-lookup"><span data-stu-id="13bd6-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="13bd6-124">Zwraca wartość logiczną `on` lub `off` .</span><span class="sxs-lookup"><span data-stu-id="13bd6-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="13bd6-125">Flaga zwykle otacza blok kodu, który hermetyzuje funkcję funkcji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="13bd6-126">Stan flagi określa, czy ten blok kodu jest wykonywany dla danego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="13bd6-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="13bd6-127">Na rysunku 10-11 przedstawiono implementację.</span><span class="sxs-lookup"><span data-stu-id="13bd6-127">Figure 10-11 shows the implementation.</span></span>

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="13bd6-128">**Rysunek 10-11** . implementacja flagi prostej funkcji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="13bd6-129">Należy zauważyć, jak to podejście oddziela logikę decyzyjną od kodu funkcji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="13bd6-130">W rozdziale 1 omawiamy `Twelve-Factor App` .</span><span class="sxs-lookup"><span data-stu-id="13bd6-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="13bd6-131">Wskazówki dotyczące przechowywania ustawień konfiguracji zewnętrznych z kodu wykonywalnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="13bd6-132">W razie konieczności ustawienia mogą być odczytywane ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="13bd6-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="13bd6-133">Wartości konfiguracji flagi funkcji powinny być również niezależne od ich bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="13bd6-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="13bd6-134">Zgodnie z konfiguracją flagi eksternalizacji w oddzielnym repozytorium można zmienić stan flagi bez modyfikowania i ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="13bd6-135">[Konfiguracja aplikacji platformy Azure](https://docs.microsoft.com/azure/azure-app-configuration/overview) zapewnia scentralizowane repozytorium dla flag funkcji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-135">[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="13bd6-136">Dzięki niej można definiować różne rodzaje flag funkcji i manipulować ich Stanami szybko i bezpiecznie.</span><span class="sxs-lookup"><span data-stu-id="13bd6-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="13bd6-137">Aby włączyć funkcję flagi funkcji, należy dodać biblioteki klienta konfiguracji aplikacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="13bd6-138">Obsługiwane są różne struktury języka programowania.</span><span class="sxs-lookup"><span data-stu-id="13bd6-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="13bd6-139">Flagi funkcji można łatwo zaimplementować w [usłudze ASP.NET Core](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="13bd6-139">Feature flags can be easily implemented in an [ASP.NET Core service](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="13bd6-140">Zainstalowanie bibliotek zarządzania funkcją .NET i dostawcy konfiguracji aplikacji umożliwia deklaratywne Dodawanie flag funkcji do kodu.</span><span class="sxs-lookup"><span data-stu-id="13bd6-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="13bd6-141">Umożliwiają one włączenie `FeatureGate` atrybutów w taki sposób, aby nie trzeba było ręcznie pisać instrukcji if w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="13bd6-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="13bd6-142">Po skonfigurowaniu w klasie startowej można dodać funkcję flagi funkcji na poziomie kontrolera, akcji lub oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="13bd6-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="13bd6-143">Rysunek 10-12 przedstawia implementację kontrolera i akcji:</span><span class="sxs-lookup"><span data-stu-id="13bd6-143">Figure 10-12 presents controller and action implementation:</span></span>

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="13bd6-144">**Rysunek 10-12** — implementacja flagi funkcji w kontrolerze i akcji.</span><span class="sxs-lookup"><span data-stu-id="13bd6-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="13bd6-145">Jeśli flaga funkcji jest wyłączona, użytkownik otrzyma kod stanu 404 (nie znaleziono) bez treści odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="13bd6-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="13bd6-146">Flagi funkcji można również dodawać bezpośrednio do klas języka C#.</span><span class="sxs-lookup"><span data-stu-id="13bd6-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="13bd6-147">Rysunek 10-13 pokazuje iniekcję flagi funkcji:</span><span class="sxs-lookup"><span data-stu-id="13bd6-147">Figure 10-13 shows feature flag injection:</span></span>

```c#
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="13bd6-148">**Rysunek 10-13** — iniekcja flagi funkcji do klasy.</span><span class="sxs-lookup"><span data-stu-id="13bd6-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="13bd6-149">Biblioteki zarządzania funkcjami zarządzają cyklem życia flagi funkcji w tle.</span><span class="sxs-lookup"><span data-stu-id="13bd6-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="13bd6-150">Aby na przykład zminimalizować dużą liczbę wywołań do magazynu konfiguracji, biblioteki buforują Stany flag dla określonego czasu trwania.</span><span class="sxs-lookup"><span data-stu-id="13bd6-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="13bd6-151">Mogą zagwarantować niezmienności Stanów flag podczas wywoływania żądania.</span><span class="sxs-lookup"><span data-stu-id="13bd6-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="13bd6-152">Oferują one również `Point-in-time snapshot` .</span><span class="sxs-lookup"><span data-stu-id="13bd6-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="13bd6-153">Można odtworzyć historię dowolnej wartości klucza i w dowolnym momencie podać jej wartość przeszłą w ciągu ostatnich siedmiu dni.</span><span class="sxs-lookup"><span data-stu-id="13bd6-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="13bd6-154">[Poprzedni](devops.md) 
> [Dalej](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="13bd6-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>
