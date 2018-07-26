---
title: Wybór wersji platformy .NET core
description: Dowiedz się, jak .NET Core umożliwia znalezienie i wybiera wersje środowiska uruchomieniowego dla Twojego programu.
author: billwagner
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: d1b885ebbade4736d5f592d1dc1d4ba25a321a16
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874473"
---
# <a name="net-core-version-selection"></a>Wybór wersji platformy .NET core

[!INCLUDE [topic-appliesto-net-core-2plus](../../../includes/topic-appliesto-net-core-2plus.md)]

W tym artykule opisano zasady używane przez narzędzia .NET Core, zestaw SDK i środowiska uruchomieniowego do wybierania wersji. Te zasady zapewniają równowagi między uruchamiających aplikacje przy użyciu określonej wersji i włączenie jej obsługi ułatwiają realizację uaktualniania maszyn dla deweloperów i użytkowników końcowych. Te zasady, wykonaj następujące czynności:

- Łatwe wdrażanie platformy .NET Core, w tym aktualizacje zabezpieczeń i niezawodności.
- Użyj najnowsze narzędzia i polecenia niezależnie od docelowego środowiska uruchomieniowego.

Występuje, wybór wersji:

- Po uruchomieniu polecenia zestawu SDK [zestaw sdk używa najnowszej zainstalowanej wersji](#the-sdk-uses-the-latest-installed-version).
- Podczas kompilowania zestawu [target framework monikerów definiują czas kompilacji interfejsów API](#target-framework-monikers-define-build-time-apis).
- Po uruchomieniu aplikacji platformy .NET Core, [aplikacji zależnych target framework uaktualniane](#framework-dependent-apps-roll-forward).
- Gdy opublikujesz aplikację niezależna [niezależna obejmuje wybrane środowisko uruchomieniowe](#self-contained-deployments-include-the-selected-runtime).

Te cztery scenariusze sprawdza, czy pozostałej części tego dokumentu.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Zestaw SDK używa najnowszej zainstalowanej wersji

Następujące polecenia zestawu SDK `dotnet new`, `dotnet build` lub `dotnet run`. `dotnet` Interfejsu wiersza polecenia, musisz wybrać wersję zestawu SDK dla dowolnego polecenia. Najnowszy zestaw SDK domyślnie instalowany na komputerze korzysta z interfejsu wiersza polecenia platformy .NET Core. Użyjesz v2.1.301 zestawu .NET Core SDK po jego zainstalowaniu, nawet wtedy, gdy projekt pracujesz z obiektami docelowymi .NET Core Runtime 2.0. Należy pamiętać, że ta zasada obowiązuje dla wersji zapoznawczych, a także wersje. Korzystać z zalet najnowszych funkcji zestawu SDK i ulepszeń, podczas określania wartości docelowej starszych wersji środowiska uruchomieniowego .NET Core. Można wskazać wiele wersji środowiska uruchomieniowego programu .NET Core w różnych projektach, przy użyciu tych samych narzędzi zestawu SDK dla wszystkich projektów.

W rzadkich przypadkach może być konieczne użycie wcześniejszej wersji zestawu SDK. Należy określić w tej wersji w [ *global.json* pliku](../tools/global-json.md). Zasady "przy użyciu najnowszej" oznacza, że możesz tylko używać *global.json* do wcześniejszych niż jego Najnowsza zainstalowana wersja określanie wersji programu .NET Core SDK.

*Global.JSON* można umieścić w dowolnym miejscu w hierarchii plików. Interfejs wiersza polecenia w górę przeszukuje od katalogu projektu w pierwszym *global.json* znajdzie. Możesz kontrolować, które projekty danego *global.json* dotyczy przez jej miejscu w systemie plików. Interfejs wiersza polecenia platformy .NET, wyszukuje *global.json* pliku iteracyjne przechodząc ścieżkę w górę od bieżącego katalogu roboczego. Pierwszy *global.json* można znaleźć pliku określa wersja użyta. Jeśli ta wersja jest zainstalowana, ta wersja jest używana. Jeśli zestaw SDK określona w *global.json* nie zostanie znaleziony, interfejsu wiersza polecenia platformy .NET przenosi do przodu do zainstalowany najnowszy zestaw SDK. Jest to domyślne zachowanie, gdy nie *global.json* znajduje się plik.

W poniższym przykładzie przedstawiono *global.json* składni:

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

Proces wybierania wersji zestawu SDK jest:

1. `dotnet` wyszukuje *global.json* pliku iteracyjne wstecznego — przechodząc ścieżkę w górę od bieżącego katalogu roboczego.
1. `dotnet` użyto zestawu SDK usługi określonego w pierwszym *global.json* znaleziono.
1. `dotnet` używa najnowszej zainstalowany zestaw SDK, jeśli nie *global.json* zostanie znaleziony.

Dowiedz się więcej o wybranie wersji zestawu SDK w [reguł dopasowania](../tools/global-json.md) części tematu na *global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>TARGET Framework monikerów definiują czas kompilacji interfejsów API

Tworzenie projektu w taki sposób, w odniesieniu do interfejsów API zdefiniowany w **Moniker platformy docelowej** (TFM). Należy określić [platformę docelową](../../standard/frameworks.md) w pliku projektu. Ustaw `TargetFramework` elementu w pliku projektu, jak pokazano w poniższym przykładzie:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Może tworzyć projekty względem wielu krótkich nazw. Ustawianie wielu platform docelowych częściej bibliotek, ale może odbywać się za pomocą aplikacji, jak również. Należy określić `TargetFrameworks` właściwości (liczba mnoga z `TargetFramework`). Platformy docelowe są rozdzielone średnikami jak pokazano w poniższym przykładzie:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Dany zestaw SDK obsługuje stały zestaw struktur, ograniczone do platformy docelowej środowiska uruchomieniowego, które on dostarczany z programem. Na przykład, .NET Core 2.0 SDK zawiera środowisko uruchomieniowe platformy .NET Core 2.0, która jest implementacją elementu `netcoreapp2.0` platformy docelowej. .NET Core 2.0 SDK obsługuje `netcoreapp1.0`, `netcoreapp1.1`, i `netcoreapp2.0` , ale nie `netcoreapp2.1` (lub nowszej). Zainstaluj zestaw .NET Core 2.1 SDK do tworzenia dla `netcoreapp2.1`.

.NET standard platform docelowych również są ograniczone do platformy docelowej środowiska uruchomieniowego, które zestaw SDK, który jest dostarczany z programem. .NET Core 2.0 SDK jest ograniczone do `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Uaktualniane zależny od struktury aplikacji

Uruchamianie aplikacji ze źródła przy użyciu [ `dotnet run` ](../tools/dotnet-run.md). `dotnet run` Tworzy i uruchamia aplikację. `dotnet` Pliku wykonywalnego jest **hosta** dla aplikacji w środowiskach programistycznych.

Host wybiera najnowszą wersję poprawki zainstalowane na komputerze. Na przykład, jeśli określono `netcoreapp2.0` w pliku projektu i `2.0.4` jest zainstalowany, najnowsze środowisko uruchomieniowe .NET `2.0.4` środowiska uruchomieniowego jest używany.

Jeśli nie jest dopuszczalne `2.0.*` wersji zostanie znaleziony, nowy `2.*` wersja jest używana. Na przykład, jeśli określono `netcoreapp2.0` i tylko `2.1.0` jest zainstalowany, jest uruchamiana aplikacja, za pomocą `2.1.0` środowiska uruchomieniowego. To zachowanie jest określany jako "wersja pomocnicza przodu." Niższe wersje również nie były uznawane za. Po zainstalowaniu nie akceptowalnego czasu wykonywania aplikacja nie będzie działać.

Kilka przykładów użycia pokazują to zachowanie:

- 2.0.4 jest wymagana. 2.0.5 jest zainstalowana najnowsza wersja poprawki. 2.0.5 jest używany.
- 2.0.4 jest wymagana. Nie w wersji 2.0. * wersje są zainstalowane. 1.1.1 jest najwyższym zainstalowanego środowiska uruchomieniowego. Wyświetlany jest komunikat o błędzie.
- 2.0.4 jest wymagana. 2.0.0 jest najwyższa wersja zainstalowana. Wyświetlany jest komunikat o błędzie.
- 2.0.4 jest wymagana. Nie w wersji 2.0. * wersje są zainstalowane. 2.2.2 jest najnowsza wersja środowiska uruchomieniowego 2.x zainstalowane. 2.2.2 jest używany.
- 2.0.4 jest wymagana. Brak wersji 2.x są instalowane. 3.0.0 (zainstalowano nie jest obecnie dostępna wersja). Wyświetlany jest komunikat o błędzie.

Wersja pomocnicza przodu ma jeden efekt uboczny, który może mieć wpływ na użytkowników końcowych. Rozważmy następujący scenariusz:

- 2.0.4 jest wymagana. Nie w wersji 2.0. * wersje są zainstalowane. 2.2.2 jest zainstalowany. 2.2.2 jest używany.
- 2.0.5 nowszy jest zainstalowany. 2.0.5 stosowanych w odniesieniu do uruchomienia kolejnych aplikacji, nie 2.2.2. Najnowszą poprawkę wymagana wersja pomocnicza jest preferowane w porównaniu do nowszej wersji pomocniczej.
- Istnieje możliwość, że 2.0.5 i 2.2.2 zachowywać się inaczej, szczególnie w przypadku scenariuszy, takich jak serializacji danych binarnych.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Niezależne wdrożenia obejmują wybrane środowisko uruchomieniowe

Możesz opublikować aplikację jako [ **niezależna dystrybucji**](../deploying/index.md#self-contained-deployments-scd). Ta metoda zawiera również środowisko uruchomieniowe programu .NET Core i biblioteki z aplikacji. Niezależna wdrożeń nie mają zależności środowiska uruchomieniowe. Wybór wersji środowiska uruchomieniowego występuje w momencie, w czasie wykonywania nie publikacji.

Proces publikowania wybiera najnowszą wersję poprawki rodziny danego środowiska uruchomieniowego. Na przykład `dotnet publish` wybierze platformy .NET Core 2.0.4, jeśli jest najnowszą wersję poprawki w rodzinie środowiska uruchomieniowego .NET Core 2.0. Platforma docelowa (w tym najnowsze poprawki zabezpieczeń zainstalowanych) jest dostarczana razem z aplikacją.

Jeśli minimalna wersja określona dla aplikacji nie jest spełniony, występuje błąd. `dotnet publish` tworzy powiązanie z najnowszej wersji środowiska uruchomieniowego dla poprawki (w ramach danej wartości główna.pomocnicza rodzina wersji). `dotnet publish` nie obsługuje semantykę przodu `dotnet run`. Aby uzyskać więcej informacji dotyczących poprawek i niezależna wdrożeń, zobacz artykuł w [wybór poprawki środowiska uruchomieniowego](../deploying/runtime-patch-selection.md) podczas wdrażania aplikacji .NET Core.

Niezależne wdrożenia może wymagać wersja określona poprawka. Minimalna wersja środowiska uruchomieniowego patch (na wersje wyższą lub niższą) w pliku projektu, można zastąpić, jak pokazano w poniższym przykładzie:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` Elementu zastępuje domyślne zasady wersji. W przypadku wdrożeń niezależna `RuntimeFrameworkVersion` Określa *dokładnie* framework w wersji środowiska uruchomieniowego. W przypadku aplikacji zależnych framework `RuntimeFrameworkVersion` Określa *minimalne* framework wymaganego środowiska uruchomieniowego w wersji.
