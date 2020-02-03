---
title: Zależności i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań związanych z zarządzaniem zależnościami NuGet w bibliotekach platformy .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731482"
---
# <a name="dependencies"></a>Zależności

Podstawowym sposobem dodawania zależności do biblioteki .NET jest odwoływanie się do pakietów NuGet. Odwołania do pakietów NuGet umożliwiają szybkie ponowne użycie i wykorzystanie już wykorzystanych funkcji, ale są one typowym źródłem tarcia dla deweloperów platformy .NET. Prawidłowe zarządzanie zależnościami jest ważne, aby zapobiec utracie zmian w innych bibliotekach platformy .NET, a na odwrót.

## <a name="diamond-dependencies"></a>Zależności rombów

Jest to typowa sytuacja, w której projekt .NET ma wiele wersji pakietu w jego drzewie zależności. Na przykład aplikacja zależy od dwóch pakietów NuGet, z których każda jest zależna od różnych wersji tego samego pakietu. Zależność Diamond już istnieje w grafie zależności aplikacji.

![Zależność Diamond](./media/dependencies/diamond-dependency.png "Zależność Diamond")

W czasie kompilacji NuGet analizuje wszystkie pakiety, od których zależy projekt, w tym zależności zależności. W przypadku wykrycia wielu wersji pakietu reguły są oceniane w celu wybrania jednej z nich. Ujednolicenie pakietów jest konieczne, ponieważ uruchomione obok siebie wersje zestawu w tej samej aplikacji są problematyczne w programie .NET.

Większość zależności diamentów jest łatwo rozwiązywana; mogą jednak tworzyć problemy w pewnych okolicznościach:

1. **Sprzeczne odwołania do pakietów NuGet** uniemożliwiają rozpoznanie wersji podczas przywracania pakietu.
2. Istotne **zmiany między wersjami** powodują błędy i wyjątki w czasie wykonywania.
3. **Zestaw pakietu ma silną nazwę**, wersja zestawu została zmieniona, a aplikacja jest uruchomiona na .NET Framework. Przekierowania powiązań zestawu są wymagane.

Nie jest możliwe, aby wiedzieć, które pakiety będą używane razem ze swoimi zadaniami. Dobrym sposobem na zmniejszenie prawdopodobieństwa, że oddzielenie zależności od rombu w bibliotece polega na zminimalizowaniu liczby pakietów, od których zależą.

✔️ PRZEPROWADZIĆ przegląd niepotrzebnych zależności w bibliotece platformy .NET.

## <a name="nuget-dependency-version-ranges"></a>Zakresy wersji zależności NuGet

Odwołanie do pakietu określa zakres prawidłowych pakietów, na które zezwala. Zazwyczaj wersja odwołania do pakietu w pliku projektu jest minimalną wersją i nie ma wartości maksymalnej.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Reguły używane przez NuGet podczas rozpoznawania zależności są [złożone](/nuget/consume-packages/dependency-resolution), ale pakiet NuGet zawsze szuka najniższej stosownej wersji. Pakiet NuGet preferuje najniższą odpowiednią wersję w porównaniu z użyciem najwyższej dostępnej, ponieważ najniższa będzie zawierać najmniej problemów ze zgodnością.

Ze względu na najmniejszą odpowiednią regułę wersji programu NuGet nie trzeba umieszczać w odwołaniach do pakietów górnej wersji ani dokładnego zakresu, aby uniknąć pobierania najnowszej wersji. Pakiet NuGet próbuje już znaleźć najmniejszą, najbardziej zgodną wersję.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Górne ograniczenia wersji spowodują niepowodzenie NuGet w przypadku wystąpienia konfliktu. Na przykład jedna biblioteka akceptuje dokładnie 1,0, a inna biblioteka wymaga 2,0 lub wyższej. W przypadku wprowadzenia zmian w wersji 2,0, ścisła lub górna zależność wersji gwarantuje błąd.

![Konflikt zależności rombu](./media/dependencies/diamond-dependency-conflict.png "Konflikt zależności rombu")

❌ nie mają odwołań do pakietów NuGet bez minimalnej wersji.

❌ UNIKAj odwołań do pakietów NuGet, które wymagają dokładnej wersji.

❌ uniknąć odwołań pakietów NuGet z górnym limitem wersji.

## <a name="nuget-shared-source-packages"></a>Pakiety udostępnione dla narzędzia NuGet

Jednym ze sposobów zredukowania zewnętrznych zależności pakietów NuGet jest odwołanie do udostępnionych pakietów źródłowych. Udostępniony pakiet źródłowy zawiera [pliki kodu źródłowego](/nuget/reference/nuspec#including-content-files) , które są zawarte w projekcie, gdy istnieje odwołanie. Ponieważ właśnie umieszczasz pliki kodu źródłowego, które są kompilowane w pozostałej części projektu, nie istnieje zewnętrzna zależność i szansa konfliktu.

Udostępnione pakiety źródłowe doskonale nadaje się do uwzględnienia małych fragmentów funkcjonalności. Na przykład udostępniony pakiet źródłowy metod pomocników do wykonywania wywołań HTTP.

![Udostępniony pakiet źródłowy](./media/dependencies/shared-source-package.png "Udostępniony pakiet źródłowy")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Udostępniony projekt źródłowy](./media/dependencies/shared-source-project.png "Udostępniony projekt źródłowy")

Udostępnione pakiety źródłowe mają pewne ograniczenia. Można do nich odwoływać się tylko `PackageReference`, więc starsze projekty `packages.config` są wykluczone. Współużytkowane pakiety źródłowe są również używane tylko przez projekty o tym samym typie języka. Ze względu na to, że udostępnione pakiety źródłowe najlepiej wykorzystać do udostępniania funkcjonalności w ramach projektu typu open source.

✔️ ROZWAŻYĆ odwołujące się do udostępnionych pakietów źródłowych dla małych, wewnętrznych fragmentów funkcjonalności.

✔️ Rozważ, aby pakiet był udostępnionym pakietem źródłowym, jeśli udostępnia małe, wewnętrzne elementy funkcjonalności.

✔️ NALEŻY odwoływać się do udostępnionych pakietów źródłowych z `PrivateAssets="All"`.

> To ustawienie informuje program NuGet, że pakiet jest używany tylko w czasie projektowania i nie powinien być ujawniony jako zależność publiczna.

w publicznym interfejsie API ❌ nie mają udostępnionych typów pakietów źródłowych.

> Współużytkowane typy źródeł są kompilowane do zestawu, do którego się odwołuje, i nie mogą być wymieniane między granicami zestawu. Na przykład typ `IRepository` udostępnionego źródła w jednym projekcie jest osobnym typem z tego samego udostępnionego źródła `IRepository` w innym projekcie. Typy we współużytkowanych pakietach źródłowych powinny mieć widoczność `internal`.

❌ nie publikować udostępnionych pakietów źródłowych do NuGet.org.

> Udostępnione pakiety źródłowe zawierają kod źródłowy i mogą być używane tylko przez projekty o tym samym typie języka. Na przykład C# udostępniony pakiet źródłowy nie może być używany przez F# aplikację.
>
> Publikuj udostępnione pakiety źródłowe w [lokalnym kanale informacyjnym lub MyGet](./publish-nuget-package.md) , aby wykorzystać je wewnętrznie w ramach projektu.

>[!div class="step-by-step"]
>[Poprzednie](nuget.md)
>[dalej](sourcelink.md)
