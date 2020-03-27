---
title: Wybierz wersję .NET Core, której chcesz użyć
description: Dowiedz się, jak program .NET Core automatycznie wyszukuje i wybiera wersje środowiska wykonawczego dla programu. Ponadto w tym artykule uczy się, jak wymusić określoną wersję.
author: thraka
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: 26aecdf2bf3ebd033e80eec26159eb9fa3cd54dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345158"
---
# <a name="select-the-net-core-version-to-use"></a>Wybierz wersję .NET Core, której chcesz użyć

W tym artykule opisano zasady używane przez narzędzia .NET Core, zestaw SDK i środowisko uruchomieniowe do wybierania wersji. Te zasady zapewniają równowagę między uruchamianiem aplikacji przy użyciu określonych wersji i ułatwienie uaktualniania maszyn deweloperów i użytkowników końcowych. Te zasady wykonują następujące akcje:

- Łatwe i wydajne wdrażanie programu .NET Core, w tym aktualizacje zabezpieczeń i niezawodności.
- Użyj najnowszych narzędzi i poleceń niezależnie od docelowego środowiska uruchomieniowego.

Wybór wersji występuje:

- Po uruchomieniu polecenia SDK, [SDK używa najnowszej zainstalowanej wersji](#the-sdk-uses-the-latest-installed-version).
- Podczas tworzenia zestawu, [monikerów struktury docelowej zdefiniować interfejsy API czasu kompilacji](#target-framework-monikers-define-build-time-apis).
- Po uruchomieniu aplikacji .NET Core [aplikacje zależne od struktury docelowej są przesuwające się do przodu](#framework-dependent-apps-roll-forward).
- Podczas publikowania aplikacji niezależnej, [samodzielne wdrożenia obejmują wybrane środowisko uruchomieniowe](#self-contained-deployments-include-the-selected-runtime).

W pozostałej części tego dokumentu przeanalizowano te cztery scenariusze.

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK korzysta z najnowszej zainstalowanej wersji

Polecenia SDK `dotnet new` obejmują `dotnet run`i . Wierszka polecenia .NET Core musi wybrać `dotnet` wersję SDK dla każdego polecenia. Domyślnie używa najnowszego SDK zainstalowanego na komputerze, nawet jeśli:

- Projekt jest przeznaczony dla wcześniejszej wersji środowiska uruchomieniowego .NET Core.
- Najnowsza wersja .NET Core SDK jest wersją zapoznawczą.

Możesz korzystać z najnowszych funkcji i ulepszeń SDK podczas kierowania na wcześniejsze wersje środowiska uruchomieniowego .NET Core. Można kierować wiele wersji środowiska uruchomieniowego .NET Core na różnych projektach, przy użyciu tych samych narzędzi zestawu SDK dla wszystkich projektów.

W rzadkich przypadkach może być konieczne użycie wcześniejszej wersji sdk. Można określić tę wersję w pliku [ *global.json* ](../tools/global-json.md). Zasady "użyj najnowszych" oznaczają, że używasz tylko *global.json,* aby określić wersję .NET Core SDK wcześniej niż najnowsza zainstalowana wersja.

*global.json* można umieścić w dowolnym miejscu w hierarchii plików. Cli przeszukuje w górę z katalogu projektu dla pierwszego *global.json* znajdzie. Użytkownik kontroluje, które projekty danego *global.json* ma zastosowanie do jego miejsca w systemie plików. Plik .NET CLI wyszukuje plik *global.json* iterująco nawigując ścieżkę w górę od bieżącego katalogu roboczego. Pierwszy znaleziony plik *global.json* określa używaną wersję. Jeśli ta wersja SDK jest zainstalowana, ta wersja jest używana. Jeśli nie znaleziono pliku SDK określonego w *pliku global.json,* plik .NET CLI używa [reguł dopasowania](../tools/global-json.md#matching-rules) do wybierania zgodnego sdk lub nie powiedzie się, jeśli nie zostanie znaleziony.

W poniższym przykładzie przedstawiono składnię *global.json:*

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

Proces wyboru wersji SDK jest:

1. `dotnet`wyszukuje plik *global.json* iteracyjne odwrotnej nawigacji ścieżki w górę od bieżącego katalogu roboczego.
1. `dotnet`używa SDK określonego w pierwszym znalezionym *pliku global.json.*
1. `dotnet`używa najnowszego zainstalowanego SDK, jeśli nie zostanie znaleziony *plik global.json.*

Więcej informacji na temat wybierania wersji SDK można dowiedzieć się w sekcji [Reguły dopasowania](../tools/global-json.md#matching-rules) w artykule *global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Monikery struktury docelowej definiują interfejsy API czasu kompilacji

Tworzenie projektu względem interfejsów API zdefiniowanych w **monikeru platformy docelowej** (TFM). Określić [platformę docelową](../../standard/frameworks.md) w pliku projektu. Ustaw `TargetFramework` element w pliku projektu, jak pokazano w poniższym przykładzie:

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Możesz utworzyć projekt na wielu TFM. Ustawienie wielu struktur docelowych jest bardziej powszechne w przypadku bibliotek, ale można to zrobić również za pomocą aplikacji. Należy określić `TargetFrameworks` właściwość `TargetFramework`(liczba mnoga ). Struktury docelowe są rozdzielane średnikami, jak pokazano w poniższym przykładzie:

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

Dany zestaw SDK obsługuje stały zestaw struktur, ograniczona do struktury docelowej środowiska wykonawczego, z jakim jest dostarczany. Na przykład zestaw SDK .NET Core 3.0 zawiera środowisko uruchomieniowe .NET Core `netcoreapp3.0` 3.0, które jest implementacją struktury docelowej. Zestaw SDK .NET Core 3.0 obsługuje `netcoreapp2.1`, `netcoreapp2.2`, `netcoreapp3.0`ale nie `netcoreapp3.1` (lub wyższy). Instalujesz sdk .NET Core 3.1, aby utworzyć dla `netcoreapp3.1`.

.NET Standardowe struktury docelowe są również ograniczone do struktury docelowej środowiska wykonawczego sdk ships z. SDK .NET Core 3.1 jest `netstandard2.1`ograniczony do . Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).

## <a name="framework-dependent-apps-roll-forward"></a>Aplikacje zależne od struktury są przewijane do przodu

Po uruchomieniu aplikacji ze [`dotnet run`](../tools/dotnet-run.md)źródła z , z [**wdrożenia zależnego od struktury**](../deploying/index.md#publish-runtime-dependent) z `myapp.exe` `dotnet` [`dotnet myapp.dll`](../tools/dotnet.md#description), lub z pliku [**wykonywalnego zależnego od struktury**](../deploying/index.md#publish-runtime-dependent) z , plik wykonywalny jest **hostem** aplikacji.

Host wybiera najnowszą wersję poprawki zainstalowaną na komputerze. Na przykład jeśli `netcoreapp3.0` określono w pliku `3.0.4` projektu i jest zainstalowany najnowszy `3.0.4` czas wykonywania .NET, środowisko wykonawcze jest używany.

Jeśli nie `3.0.*` zostanie znaleziona `3.*` żadna dopuszczalna wersja, używana jest nowa wersja. Na przykład jeśli `netcoreapp3.0` określono `3.1.0` i tylko jest zainstalowany, `3.1.0` aplikacja jest uruchamiana przy użyciu środowiska wykonawczego. To zachowanie jest określane jako "wersja pomocnicza roll-forward." Niższe wersje również nie będą brane pod uwagę. Gdy nie jest zainstalowany nie dopuszczalne środowisko uruchomieniowe, aplikacja nie zostanie uruchomiony.

Kilka przykładów użycia demonstruje zachowanie, jeśli kierowane 3.0:

- ✔️ określono 3.0. 3.0.5 jest najwyższą zainstalowaną wersją poprawki. 3.0.5.
- ❌3.0. Nie są zainstalowane wersje 3.0.*. 2.1.1 jest najwyższym zainstalowanym czasem wykonywania. Zostanie wyświetlony komunikat o błędzie.
- ✔️ określono 3.0. Nie są zainstalowane wersje 3.0.*. 3.1.0 jest najwyższą zainstalowaną wersją środowiska wykonawczego. 3.1.0.
- ❌2.0. Nie są zainstalowane wersje 2.x. 3.0.0 jest najwyższym zainstalowanym czasem wykonywania. Zostanie wyświetlony komunikat o błędzie.

Wersja pomocnicza do przodu ma jeden efekt uboczny, który może mieć wpływ na użytkowników końcowych. Poniżej przedstawiono przykładowy scenariusz:

1. Aplikacja określa, że wymagane jest 3.0.
2. Po uruchomieniu wersja 3.0.* nie jest zainstalowana, jednak jest 3.1.0. Zostanie użyta wersja 3.1.0.
3. Później użytkownik instaluje 3.0.5 i uruchamia aplikację ponownie, 3.0.5 będzie teraz używany.

Jest możliwe, że 3.0.5 i 3.1.0 zachowują się inaczej, szczególnie w scenariuszach, takich jak serializacji danych binarnych.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Samodzielne wdrożenia obejmują wybrany czas pracy

Aplikację można opublikować jako [**samodzielną dystrybucję.**](../deploying/index.md#publish-self-contained) Takie podejście łączy środowisko uruchomieniowe .NET Core i biblioteki z aplikacją. Samodzielne wdrożenia nie mają zależności od środowisk uruchomieniowych. Wybór wersji środowiska uruchomieniowego występuje w czasie publikowania, a nie w czasie wykonywania.

Proces publikowania wybiera najnowszą wersję poprawki danej rodziny wykonawczej. Na przykład `dotnet publish` wybierze .NET Core 3.0.4, jeśli jest to najnowsza wersja poprawki w rodzinie środowiska uruchomieniowego .NET Core 3.0. Struktura docelowa (w tym najnowsze zainstalowane poprawki zabezpieczeń) jest pakowana z aplikacją.

Jest to błąd, jeśli minimalna wersja określona dla aplikacji nie jest spełniona. `dotnet publish`wiąże się z najnowszą wersją poprawki środowiska uruchomieniowego (w ramach danej rodziny wersji major.minor). `dotnet publish`nie obsługuje semantyki roll-forward `dotnet run`. Aby uzyskać więcej informacji na temat poprawek i samodzielnych wdrożeń, zobacz artykuł dotyczący [wyboru poprawek środowiska wykonawczego](../deploying/runtime-patch-selection.md) podczas wdrażania aplikacji .NET Core.

Samodzielne wdrożenia mogą wymagać określonej wersji poprawki. Można zastąpić minimalną wersję poprawki środowiska uruchomieniowego (do wersji wyższej lub niższej) w pliku projektu, jak pokazano w poniższym przykładzie:

``` xml
<RuntimeFrameworkVersion>3.0.4</RuntimeFrameworkVersion>
```

Element `RuntimeFrameworkVersion` zastępuje domyślne zasady wersji. W przypadku wdrożeń `RuntimeFrameworkVersion` samodzielnych określa *dokładną* wersję struktury środowiska wykonawczego. W przypadku aplikacji zależnych od struktury `RuntimeFrameworkVersion` określa *minimalną* wymaganą wersję struktury środowiska wykonawczego.

## <a name="see-also"></a>Zobacz też

- [Pobierz i zainstaluj program .NET Core](../install/index.md).
- [Jak usunąć środowisko uruchomieniowe .NET Core i SDK](remove-runtime-sdk-versions.md).
