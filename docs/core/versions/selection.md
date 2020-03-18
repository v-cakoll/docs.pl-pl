---
title: Wybierz wersję programu .NET Core, której ma być używana
description: Dowiedz się, jak program .NET Core automatycznie wyszukuje i wybiera wersje czasu wykonywania programu. Ponadto w tym artykule nauczysz, jak wymusić określoną wersję.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.openlocfilehash: 55f04ce81f63753831fca8fa2e44811c44049733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398826"
---
# <a name="select-the-net-core-version-to-use"></a>Wybierz wersję .NET Core, która ma być używana

W tym artykule wyjaśniono zasady używane przez narzędzia .NET Core, Zestaw SDK i czas wykonywania do wybierania wersji. Te zasady zapewniają równowagę między uruchamianiem aplikacji przy użyciu określonych wersji i umożliwieniem aktualizacji maszyn deweloperskich i użytkowników końcowych. Te zasady wykonują następujące czynności:

- Łatwe i wydajne wdrażanie programu .NET Core, w tym aktualizacje zabezpieczeń i niezawodności.
- Użyj najnowszych narzędzi i poleceń niezależnie od docelowego czasu wykonywania.

Wybór wersji następuje:

- Po uruchomieniu polecenia SDK [zestaw SDK używa najnowszej zainstalowanej wersji](#the-sdk-uses-the-latest-installed-version).
- Podczas tworzenia zestawu, [monikerów platformy docelowej zdefiniować czas kompilacji interfejsów API](#target-framework-monikers-define-build-time-apis).
- Po uruchomieniu aplikacji .NET Core [aplikacje zależne od struktury docelowej przewiń do przodu](#framework-dependent-apps-roll-forward).
- Podczas publikowania niezależnej aplikacji niezależne [wdrożenia obejmują wybrany czas wykonywania](#self-contained-deployments-include-the-selected-runtime).

W pozostałej części tego dokumentu przeanalizowano te cztery scenariusze.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Zestaw SDK korzysta z najnowszej zainstalowanej wersji

Polecenia SDK `dotnet new` obejmują `dotnet run`i . Polecenie CLI programu .NET Core musi wybrać `dotnet` wersję sdk dla każdego polecenia. Domyślnie używa najnowszego sdk zainstalowanego na komputerze, nawet jeśli:

- Projekt jest przeznaczony dla starszej wersji programu runtime .NET Core.
- Najnowsza wersja sdk .NET Core jest wersja zapoznawcza.

Można korzystać z najnowszych funkcji i ulepszeń sdk podczas określania wartości docelowej wcześniejszych wersji programu .NET Core. Można kierować wiele wersji programu .NET Core na różne projekty, przy użyciu tych samych narzędzi SDK dla wszystkich projektów.

W rzadkich przypadkach może być konieczne użycie wcześniejszej wersji sdk. Określ tę wersję w pliku [ *global.json* ](../tools/global-json.md). Zasady "użyj najnowszego" *oznaczają,* że do określenia wersji sdk .NET Core jest używana tylko wersja sdk .NET Core wcześniejsza niż najnowsza zainstalowana wersja.

*global.json* można umieścić w dowolnym miejscu w hierarchii plików. Cli przeszukuje w górę z katalogu projektu dla pierwszego *global.json* znajdzie. Można kontrolować, które projekty danego *global.json* stosuje się do jego miejsca w systemie plików. .NET CLI wyszukuje plik *global.json* iteratively nawigowanie ścieżki w górę od bieżącego katalogu roboczego. Pierwszy znaleziony plik *global.json* określa używaną wersję. Jeśli ta wersja SDK jest zainstalowana, ta wersja jest używana. Jeśli zestaw SDK określony w *global.json* nie zostanie znaleziony, polecenie CLI .NET używa [reguł dopasowywania,](../tools/global-json.md#matching-rules) aby wybrać zgodny zestaw SDK lub nie zostanie znaleziony, jeśli nie zostanie znaleziony.

W poniższym przykładzie przedstawiono składnię *global.json:*

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

Proces wyboru wersji sdk jest:

1. `dotnet`wyszukuje plik *global.json* iteratively odwrotnie nawigując ścieżkę w górę od bieżącego katalogu roboczego.
1. `dotnet`używa sdk określonego w pierwszym *global.json* znaleźć.
1. `dotnet`używa najnowszego zainstalowanego sdk, jeśli nie znaleziono *global.json.*

Więcej informacji na temat wybierania wersji sdk można uzyskać w sekcji [Reguły dopasowywania](../tools/global-json.md#matching-rules) w artykule na *stronie global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Target Framework Monikers zdefiniować czas kompilacji interfejsów API

Tworzenie projektu względem interfejsów API zdefiniowanych w **moniker struktury docelowej** (TFM). Należy określić [platformę docelową](../../standard/frameworks.md) w pliku projektu. Ustaw `TargetFramework` element w pliku projektu, jak pokazano w poniższym przykładzie:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Można utworzyć projekt względem wielu TFM. Ustawienie wielu struktur docelowych jest bardziej powszechne dla bibliotek, ale można to zrobić również za pomocą aplikacji. Należy określić `TargetFrameworks` właściwość (liczba `TargetFramework`mnoga ). Struktury docelowe są rozdzielane średnikami, jak pokazano w poniższym przykładzie:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

A dany zestaw SDK obsługuje stały zestaw struktur, ograniczone do docelowej struktury czasu wykonywania, które jest dostarczany z. Na przykład .NET Core 2.0 SDK zawiera .NET Core 2.0 runtime, który jest implementacją platformy docelowej. `netcoreapp2.0` Zestaw SDK .NET Core `netcoreapp1.0`2.0 `netcoreapp2.0` obsługuje `netcoreapp2.1` , `netcoreapp1.1`ale nie (lub wyższy). Zainstaluj zestaw SDK .NET Core 2.1 do utworzenia dla `netcoreapp2.1`programu .

Platformy docelowe .NET Standard są również ograniczone do docelowej struktury czasu wykonywania, z których jest dostarczany zestaw SDK. Zestaw SDK .NET Core 2.0 jest ograniczony do `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Aplikacje zależne od struktury przewijają się do przodu

Po uruchomieniu aplikacji ze [`dotnet run`](../tools/dotnet-run.md)źródła z , z [**wdrożenia zależnego od struktury**](../deploying/index.md#publish-runtime-dependent) z [`dotnet myapp.dll`](../tools/dotnet.md#description)lub z pliku [**wykonywalnego zależnego od struktury**](../deploying/index.md#publish-runtime-dependent) z `myapp.exe`, `dotnet` plik wykonywalny jest **hostem** dla aplikacji.

Host wybiera najnowszą wersję poprawki zainstalowaną na komputerze. Na przykład jeśli określono `netcoreapp2.0` w pliku projektu `2.0.4` i jest najnowszym zainstalowanym `2.0.4` uruchomieniu .NET, używany jest czas wykonywania.

Jeśli nie `2.0.*` zostanie znaleziona `2.*` akceptowalna wersja, zostanie użyta nowa wersja. Na przykład jeśli określono `netcoreapp2.0` i `2.1.0` jest zainstalowany tylko, `2.1.0` aplikacja jest uruchamiana przy użyciu czasu wykonywania. To zachowanie jest określane jako "wersja pomocnicza roll-forward." Niższe wersje również nie będą brane pod uwagę. Po zainstalowaniu nie jest zainstalowany akceptowalny czas uruchomieniowy, aplikacja nie będzie działać.

Kilka przykładów użycia wykazać zachowanie, jeśli cel 2.0:

- 2.0. 2.0.5 jest najwyższą zainstalowaną wersją poprawek. 2.0.5.
- 2.0. Nie są zainstalowane wersje 2.0.*. 1.1.1 jest najwyższym zainstalowanym czasem pracy. Zostanie wyświetlony komunikat o błędzie.
- 2.0. Nie są zainstalowane wersje 2.0.*. 2.2.2 jest najwyższą zainstalowaną wersją uruchomieniową 2.x. 2.2.2.
- 2.0. Nie zainstalowano wersji 2.x. 3.0.0. Zostanie wyświetlony komunikat o błędzie.

Rzut roll-forward wersji pomocniczej ma jeden efekt uboczny, który może mieć wpływ na użytkowników końcowych. Poniżej przedstawiono przykładowy scenariusz:

1. Aplikacja określa, że wymagany jest 2.0.
2. Po uruchomieniu wersja 2.0.* nie jest zainstalowana, jednak 2.2.2 jest. Zostanie użyta wersja 2.2.2.
3. Później użytkownik instaluje 2.0.5 i uruchamia aplikację ponownie, 2.0.5 będzie teraz używany.

Możliwe, że 2.0.5 i 2.2.2 zachowują się inaczej, szczególnie w scenariuszach takich jak serializacja danych binarnych.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Niezależne wdrożenia obejmują wybrane w czasie wykonywania

Aplikację można opublikować jako [**niezależną dystrybucję.**](../deploying/index.md#publish-self-contained) Takie podejście łączy program runtime i biblioteki .NET Core z aplikacją. Niezależne wdrożenia nie mają zależności od środowisk środowiska uruchomieniowego. Wybór wersji w czasie wykonywania występuje w czasie publikowania, a nie w czasie wykonywania.

Proces publikowania wybiera najnowszą wersję poprawki danej rodziny runtime. Na przykład `dotnet publish` wybierze .NET Core 2.0.4, jeśli jest to najnowsza wersja poprawki z rodziny runtime .NET Core 2.0. Platforma docelowa (w tym najnowsze zainstalowane poprawki zabezpieczeń) jest pakowana z aplikacją.

Jest to błąd, jeśli minimalna wersja określona dla aplikacji nie jest spełniona. `dotnet publish`wiąże się z najnowszą wersją poprawki w czasie wykonywania (w ramach danej rodziny wersji major.minor). `dotnet publish`nie obsługuje semantyki roll-forward `dotnet run`. Aby uzyskać więcej informacji na temat poprawek i wdrożeń zawieranych samodzielnie, zobacz artykuł na [temat wyboru poprawek](../deploying/runtime-patch-selection.md) w czasie wykonywania podczas wdrażania aplikacji .NET Core.

Niezależne wdrożenia mogą wymagać określonej wersji poprawki. W pliku projektu można zastąpić minimalną wersję poprawki w czasie wykonywania (do wyższych lub niższych wersji), jak pokazano w poniższym przykładzie:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

Element `RuntimeFrameworkVersion` zastępuje domyślne zasady wersji. W przypadku wdrożeń `RuntimeFrameworkVersion` samodzielnych określa *dokładną* wersję struktury wykonywania. W przypadku aplikacji zależnych od struktury `RuntimeFrameworkVersion` określa *minimalną* wymaganą wersję struktury wykonywania.
