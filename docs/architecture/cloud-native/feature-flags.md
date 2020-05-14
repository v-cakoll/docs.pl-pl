---
title: Flagi funkcji
description: Implementuj flagi funkcji w aplikacjach natywnych w chmurze korzystających z konfiguracji aplikacji platformy Azure
ms.date: 05/03/2020
ms.openlocfilehash: 72e1bfe777854a74fcac926811caf97e59986146
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83398310"
---
# <a name="feature-flags"></a>Flagi funkcji

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W rozdziale 1 zagwarantujemy, że chmura w chmurze ma wiele informacji o szybkości i elastyczności. Użytkownicy oczekują szybkiego reagowania, innowacyjnych funkcji i zerowego przestoju. `Feature flags`to nowoczesny technik wdrażania, który pomaga zwiększyć elastyczność dla aplikacji natywnych w chmurze. Umożliwiają one wdrażanie nowych funkcji w środowisku produkcyjnym, ale ogranicza ich dostępność. Dzięki szybkiemu przejściu przełącznika można aktywować nową funkcję dla określonych użytkowników bez konieczności ponownego uruchamiania aplikacji ani wdrażania nowego kodu. Oddzielają one wydanie nowych funkcji od ich wdrożenia kodu.

Flagi funkcji są tworzone na podstawie logiki warunkowej kontrolującej widoczność funkcji dla użytkowników w środowisku uruchomieniowym. W nowoczesnych systemach natywnych w chmurze często Wdrażaj nowe funkcje w środowisku produkcyjnym, ale Przetestuj je za pomocą ograniczonej grupy odbiorców. W miarę wzrostu pewności funkcja może zostać przeprowadzona przyrostowo dla szerszego grona odbiorców.

Inne przypadki użycia dla flag funkcji obejmują:

- Ogranicz funkcje premium do określonych grup klientów, które mają być obciążane wyższymi opłatami za subskrypcję.
- Stabilizacja systemu przez szybkie dezaktywowanie funkcji problemu, unikając ryzyka wycofania lub natychmiastowej poprawki.
- Wyłącz opcjonalną funkcję z wysokim zużyciem zasobów w okresach szczytowego użycia.
- Przeprowadzenie `experimental feature releases` do małych segmentów użytkowników w celu sprawdzenia wykonalności i popularności.

Flagi funkcji wspierają także `trunk-based` programowanie. Jest to model rozgałęzienia kontroli źródła, w którym deweloperzy pracują nad funkcjami w pojedynczej gałęzi. Podejście minimalizuje ryzyko i złożoność scalania dużej liczby długotrwałych gałęzi funkcji. Funkcja jest niedostępna, dopóki nie zostanie aktywowana.

## <a name="implementing-feature-flags"></a>Implementowanie flag funkcji

W jego rdzeńu flaga funkcji jest odwołaniem do prostej `decision object` . Zwraca wartość logiczną `on` lub `off` . Flaga zwykle otacza blok kodu, który hermetyzuje funkcję funkcji. Stan flagi określa, czy ten blok kodu jest wykonywany dla danego użytkownika. Na rysunku 10-11 przedstawiono implementację.

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

**Rysunek 10-11** . implementacja flagi prostej funkcji.

Należy zauważyć, jak to podejście oddziela logikę decyzyjną od kodu funkcji.

W rozdziale 1 omawiamy `Twelve-Factor App` . Wskazówki dotyczące przechowywania ustawień konfiguracji zewnętrznych z kodu wykonywalnego aplikacji. W razie konieczności ustawienia mogą być odczytywane ze źródła zewnętrznego. Wartości konfiguracji flagi funkcji powinny być również niezależne od ich bazy kodu. Zgodnie z konfiguracją flagi eksternalizacji w oddzielnym repozytorium można zmienić stan flagi bez modyfikowania i ponownego wdrażania aplikacji.

[Konfiguracja aplikacji platformy Azure](https://docs.microsoft.com/azure/azure-app-configuration/overview) zapewnia scentralizowane repozytorium dla flag funkcji. Dzięki niej można definiować różne rodzaje flag funkcji i manipulować ich Stanami szybko i bezpiecznie. Aby włączyć funkcję flagi funkcji, należy dodać biblioteki klienta konfiguracji aplikacji do aplikacji. Obsługiwane są różne struktury języka programowania.

Flagi funkcji można łatwo zaimplementować w [usłudze ASP.NET Core](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core). Zainstalowanie bibliotek zarządzania funkcją .NET i dostawcy konfiguracji aplikacji umożliwia deklaratywne Dodawanie flag funkcji do kodu. Umożliwiają one włączenie `FeatureGate` atrybutów w taki sposób, aby nie trzeba było ręcznie pisać instrukcji if w bazie kodu.

Po skonfigurowaniu w klasie startowej można dodać funkcję flagi funkcji na poziomie kontrolera, akcji lub oprogramowania pośredniczącego. Rysunek 10-12 przedstawia implementację kontrolera i akcji:

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

**Rysunek 10-12** — implementacja flagi funkcji w kontrolerze i akcji.

Jeśli flaga funkcji jest wyłączona, użytkownik otrzyma kod stanu 404 (nie znaleziono) bez treści odpowiedzi.

Flagi funkcji można również dodawać bezpośrednio do klas języka C#. Rysunek 10-13 pokazuje iniekcję flagi funkcji:

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

**Rysunek 10-13** — iniekcja flagi funkcji do klasy.

Biblioteki zarządzania funkcjami zarządzają cyklem życia flagi funkcji w tle. Aby na przykład zminimalizować dużą liczbę wywołań do magazynu konfiguracji, biblioteki buforują Stany flag dla określonego czasu trwania. Mogą zagwarantować niezmienności Stanów flag podczas wywoływania żądania. Oferują one również `Point-in-time snapshot` . Można odtworzyć historię dowolnej wartości klucza i w dowolnym momencie podać jej wartość przeszłą w ciągu ostatnich siedmiu dni.

>[!div class="step-by-step"]
>[Poprzedni](devops.md) 
> [Dalej](infrastructure-as-code.md)
