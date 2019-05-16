---
title: Zależności i bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań do zarządzania zależności NuGet w bibliotekach .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0cd00ff36ad52bc46769ca1793b9efd02db14da1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644275"
---
# <a name="dependencies"></a>Zależności

Podstawowym sposobem dodawania zależności do biblioteki .NET odwołuje się do pakietów NuGet. Odwołania do pakietu NuGet pozwalają na szybkie ponowne użycie i korzystać z funkcji już napisane, ale są one wspólne źródło zajmowania się dla deweloperów platformy .NET. Poprawnie Zarządzanie zależnościami ważne jest, aby zapobiegać zmianom w innych bibliotekach .NET przed przerwaniem działania biblioteki .NET i na odwrót!

## <a name="diamond-dependencies"></a>Zależności romb

To sytuacja wspólne dla projektu .NET wiele wersji pakietu w jego drzewie zależności. Na przykład aplikacja jest zależna od dwóch pakietów NuGet, z których każdy jest zależna od różne wersje tego samego pakietu. Obecnie istnieje zależność romb w wykres zależności aplikacji.

![Romboidalny zależności](./media/dependencies/diamond-dependency.png "romboidalna zależności")

W czasie kompilacji NuGet analizuje wszystkie pakiety, które projekt zależy, wraz z zależnościami zależności. Po wykryciu wiele wersji pakietu do pobrania jednego oceniania reguł. Pakiety, ujednolicając naukę jest konieczne w przypadku, ponieważ wersjami side-by-side zestawu w tej samej aplikacji jest problematyczne na platformie .NET.

Większość zależności romb łatwo są rozwiązywane; jednak ich może prowadzić do problemów w pewnych okolicznościach:

1. **Odwołania do pakietu NuGet powodujące konflikt** uniemożliwić wersji rozwiązania podczas przywracania pakietów.
2. **Fundamentalne zmiany między wersjami** powodować błędy i wyjątki w czasie wykonywania.
3. **Zestaw pakietów ma silną nazwę**, zmianie wersji zestawu, a aplikacja jest uruchomiona w środowisku .NET Framework. Przekierowania powiązań zestawu są wymagane.

Nie jest możliwe, należy wiedzieć, jakie pakiety będą używać razem z własnych. Dobrym sposobem zmniejszenia prawdopodobieństwa zależność romb istotne biblioteki jest zminimalizowanie liczby pakietów, które zależą od.

**CZY ✔️** Przejrzyj biblioteki .NET niepotrzebne zależności.

## <a name="nuget-dependency-version-ranges"></a>Zakresów wersji zależności NuGet

Odwołanie do pakietu określa zakres prawidłowy pakietów, które będzie ona zezwalała. Zazwyczaj wersja odwołanie do pakietu w pliku projektu jest minimalną wersją, a jest brak maksimum.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Dostępne są następujące reguły, których NuGet używa podczas rozpoznawania zależności [złożonych](/nuget/consume-packages/dependency-resolution), ale NuGet zawsze szuka najniższą odpowiedniej wersji. NuGet preferuje najniższy odpowiednią wersję przy użyciu najwyższej dostępności, ponieważ najniższa będzie miał co najmniej problemy ze zgodnością.

Ze względu na najniższym reguły odpowiedniej wersji NuGet nie jest niezbędna do umieszczenia w wersji górny lub dokładny zakres na odwołania do pakietu, aby uniknąć pobierania najnowszej wersji. NuGet już próbuje znaleźć najniższej i najbardziej zgodnej wersji.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Limity górny wersji spowoduje, że rozszerzenie NuGet, aby zakończyć się niepowodzeniem, jeśli występuje konflikt. Na przykład jedna biblioteka przyjmuje dokładnie 1.0 innej biblioteki wymaga 2.0 lub nowszej. Gdy przełomowe zmiany mogły zostać wprowadzone w wersji 2.0, zależność wersji strict lub górny limit gwarantuje błąd.

![Romboidalna konfliktów zależności](./media/dependencies/diamond-dependency-conflict.png "romboidalna konfliktów zależności")

**❌ NIE** ma odwołania do pakietu NuGet bez ograniczeń minimalnej wersji.

**Należy UNIKAĆ ❌** odwołania do pakietu NuGet, wymagających dokładna wersja.

**Należy UNIKAĆ ❌** odwołania do pakietu NuGet za pomocą wersji z górnego limitu.

## <a name="nuget-shared-source-packages"></a>NuGet udostępnione źródła pakietów

Jest jednym ze sposobów, aby zmniejszyć zewnętrznych zależności pakietów NuGet do odwołania się do udostępnionego źródła pakietów. Pakiet źródłowy udostępniony zawiera [pliki kodów źródłowych](/nuget/reference/nuspec#including-content-files) uwzględnianych w przypadku odwołania do projektu. Ponieważ one po prostu łącznie z plików kodu źródłowego, które są kompilowane z pozostałą częścią projektu, jest nie zależności zewnętrznych oraz prawdopodobieństwo konfliktu.

Udostępnione źródło, które pakiety są doskonale sprawdza się w tym małe fragmenty funkcji. Na przykład pakiet źródłowy udostępniony metody pomocnika do nawiązywania połączeń HTTP.

![Pakiet "source" Shared](./media/dependencies/shared-source-package.png "udostępnione źródła pakietu")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Projekt źródłowy współużytkowanego](./media/dependencies/shared-source-project.png "projekt źródłowy współużytkowanego")

Źródłowy udostępniony pakiety mają pewne ograniczenia. One mogą być przywoływane tylko przez `PackageReference`, więc starsze `packages.config` projekty są wyłączone. Pakiety źródłowy udostępniony tylko są również może być używany przez projektów za pomocą tego samego typu języka. Ze względu na ograniczenia te pakiety źródłowy udostępniony najlepiej sprawdzają się udostępniania funkcji w ramach projektu open source.

**ROZWAŻ ✔️** odwołuje się do udostępnionego źródła pakietów dla małych, wewnętrzne elementy funkcjonalności.

**ROZWAŻ ✔️** co pakiet źródłowy udostępniony pakiet zapewnia małe, wewnętrzne elementy funkcjonalności.

**CZY ✔️** odwołania się do udostępnionego źródła pakietów przy użyciu `PrivateAssets="All"`.

> To ustawienie określa pakiet NuGet tylko ma być używany w czasie tworzenia i nie powinien być udostępniany jako publicznego zależności.

**❌ NIE** udostępnionego źródła typów pakietów w publicznego interfejsu API.

> Udostępnione źródło typy są kompilowane do zestawu odwołującego się i nie można wymienić poza granicami zestawu. Na przykład udostępniane source `IRepository` typ w jednym projekcie to oddzielne z tego samego udostępnionego źródła `IRepository` w innym projekcie. Typy w pakietach źródłowy udostępniony powinny mieć `internal` widoczności.

**❌ NIE** Publikowanie pakietów źródłowy udostępniony na stronie NuGet.org.

> Udostępnione źródło pakiety zawierają kod źródłowy i mogą być używane tylko przez projektów za pomocą tego samego typu języka. Na przykład C# udostępnionego źródła pakietu nie może używać F# aplikacji.
>
> Publikowanie pakietów źródłowy udostępniony na [lokalne źródła danych lub MyGet](./publish-nuget-package.md) do korzystania z nich wewnętrznie w obrębie projektu.

>[!div class="step-by-step"]
>[Poprzednie](nuget.md)
>[dalej](sourcelink.md)
