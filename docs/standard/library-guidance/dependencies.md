---
title: Zależności i biblioteki .NET
description: Najlepsze zalecenia dotyczące zarządzania zależnościami NuGet w bibliotekach .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731482"
---
# <a name="dependencies"></a>Zależności

Podstawowym sposobem dodawania zależności do biblioteki .NET jest odwoływanie się do pakietów NuGet. Odwołania do pakietu NuGet umożliwiają szybkie ponowne użycie i wykorzystanie już zapisanych funkcji, ale są one częstym źródłem tarcia dla deweloperów platformy .NET. Poprawne zarządzanie zależnościami jest ważne, aby zapobiec wprowadzaniu zmian w innych bibliotekach .NET przed przerwaniem biblioteki .NET i odwrotnie!

## <a name="diamond-dependencies"></a>Zależności diamentów

Jest to częsta sytuacja dla projektu .NET mieć wiele wersji pakietu w jego drzewa zależności. Na przykład aplikacja zależy od dwóch pakietów NuGet, z których każdy zależy od różnych wersji tego samego pakietu. Zależność od diamentów istnieje teraz na wykresie zależności aplikacji.

![Zależność od diamentów](./media/dependencies/diamond-dependency.png "Zależność od diamentów")

W czasie kompilacji NuGet analizuje wszystkie pakiety, od których zależy projekt, w tym zależności zależności. Po wykryciu wielu wersji pakietu reguły są oceniane, aby wybrać jedną. Ujednolicenie pakietów jest konieczne, ponieważ uruchamianie wersji obok siebie zestawu w tej samej aplikacji jest problematyczne w .NET.

Większość zależności diamentów są łatwo rozwiązane; mogą one jednak powodować problemy w pewnych okolicznościach:

1. **Konflikt odwołania nuget pakiet** zapobiec wersji z rozwiązania podczas przywracania pakietu.
2. **Łamanie zmian między wersjami** powoduje błędy i wyjątki w czasie wykonywania.
3. **Zestaw pakietu jest silny o nazwie,** wersja zestawu zmieniona, a aplikacja jest uruchomiona na .NET Framework. Wymagane są przekierowania wiązania zestawu.

Nie można wiedzieć, jakie pakiety będą używane obok własnych. Dobrym sposobem, aby zmniejszyć prawdopodobieństwo podziału zależności diamentbiblioteki jest zminimalizowanie liczby pakietów, od których zależy.

✔️ do przeglądu biblioteki .NET dla niepotrzebnych zależności.

## <a name="nuget-dependency-version-ranges"></a>Zakresy wersji zależności NuGet

Odwołanie do pakietu określa zakres prawidłowych pakietów, na które zezwala. Zazwyczaj wersja referencyjna pakietu w pliku projektu jest wersją minimalną i nie ma maksymalnej.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Reguły, które NuGet używa podczas rozwiązywania zależności są [złożone,](/nuget/consume-packages/dependency-resolution)ale NuGet zawsze szuka najniższej wersji odpowiednie. NuGet preferuje najniższą odpowiednią wersję niż przy użyciu najwyższej dostępnej, ponieważ najniższy będzie miał najmniej problemów ze zgodnością.

Ze względu na nuget najniższy chorąży reguły wersji, nie jest konieczne umieszczenie górnej wersji lub dokładny zakres na odwołania do pakietu, aby uniknąć uzyskania najnowszej wersji. NuGet już próbuje znaleźć najniższą, najbardziej kompatybilną wersję dla Ciebie.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Górne limity wersji spowoduje NuGet nie powiedzie się, jeśli istnieje konflikt. Na przykład jedna biblioteka akceptuje dokładnie 1.0, podczas gdy inna biblioteka wymaga 2.0 lub wyższej. Podczas wprowadzania zmian w wersji 2.0, ścisła lub górna zależność wersji limitu gwarantuje błąd.

![Konflikt zależności diamentów](./media/dependencies/diamond-dependency-conflict.png "Konflikt zależności diamentów")

❌NIE mają odwołania nuget pakietu bez minimalnej wersji.

❌UNIKAJ nuget odwołań do pakietu, które wymagają dokładnej wersji.

❌UNIKAJ odwołania do pakietu NuGet z górną granicą wersji.

## <a name="nuget-shared-source-packages"></a>NuGet udostępnione pakiety źródłowe

Jednym ze sposobów zmniejszenia zewnętrznych zależności pakietów NuGet jest odwołanie się do udostępnionych pakietów źródłowych. Udostępniony pakiet źródłowy zawiera [pliki kodu źródłowego,](/nuget/reference/nuspec#including-content-files) które są zawarte w projekcie, gdy odwołuje się. Ponieważ po prostu w zestawie plików kodu źródłowego, które są kompilowane z resztą projektu, nie ma żadnych zależności zewnętrznych i prawdopodobieństwo konfliktu.

Udostępnione pakiety źródłowe są idealne do włączenia małych elementów funkcjonalności. Na przykład udostępniony pakiet źródłowy metod pomocnika do wykonywania wywołań HTTP.

![Udostępniony pakiet źródłowy](./media/dependencies/shared-source-package.png "Udostępniony pakiet źródłowy")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Udostępniony projekt źródłowy](./media/dependencies/shared-source-project.png "Udostępniony projekt źródłowy")

Udostępnione pakiety źródłowe mają pewne ograniczenia. Mogą się do których `PackageReference`odwoływać `packages.config` tylko starsze projekty, więc starsze projekty są wykluczone. Również udostępnione pakiety źródłowe są używane tylko przez projekty o tym samym typie języka. Ze względu na te ograniczenia udostępnione pakiety źródłowe najlepiej są używane do udostępniania funkcji w projekcie open source.

✔️ ROZWAŻ odwoływanie się do udostępnionych pakietów źródłowych dla małych, wewnętrznych elementów funkcjonalności.

✔️ ROZWAŻ uczynienie pakietu udostępnionym pakietem źródłowym, jeśli zapewnia on małe, wewnętrzne elementy funkcjonalności.

✔️ do odwoływania `PrivateAssets="All"`się do udostępnionych pakietów źródłowych z .

> To ustawienie informuje NuGet pakiet ma być używany tylko w czasie rozwoju i nie powinny być udostępniane jako zależności publicznej.

❌NIE mają współużytkowanych typów pakietów źródłowych w publicznym interfejsie API.

> Udostępnione typy źródeł są kompilowane do zestawu odwołań i nie mogą być wymieniane przez granice zestawu. Na przykład typu udostępnionego źródła `IRepository` w jednym projekcie jest oddzielnytyp `IRepository` z tego samego źródła udostępnionego w innym projekcie. Typy w udostępnionych pakietach źródłowych `internal` powinny mieć widoczność.

❌NIE publikuj udostępnionych pakietów źródłowych w celu NuGet.org.

> Udostępnione pakiety źródłowe zawierają kod źródłowy i mogą być używane tylko przez projekty o tym samym typie języka. Na przykład pakiet źródłowy współużytkowane C# nie może być używany przez aplikację F#.
>
> Publikowanie udostępnionych pakietów źródłowych w [lokalnym źródle danych lub MyGet,](./publish-nuget-package.md) aby zużywać je wewnętrznie w projekcie.

>[!div class="step-by-step"]
>[Poprzedni](nuget.md)
>[następny](sourcelink.md)
