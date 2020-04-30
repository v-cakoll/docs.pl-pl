---
title: Wybierz używaną wersję platformy .NET Core
description: Dowiedz się, jak platforma .NET Core automatycznie wyszukuje i wybiera wersje środowiska uruchomieniowego dla programu. Ponadto w tym artykule opisano, jak wymusić określoną wersję.
author: thraka
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: 3c3d9b4ec5a68c88bdd0a45acfb49191f22abda4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595731"
---
# <a name="select-the-net-core-version-to-use"></a>Wybierz wersję platformy .NET Core do użycia

W tym artykule wyjaśniono zasady używane przez narzędzia, zestaw SDK i środowisko uruchomieniowe programu .NET Core do wybierania wersji. Te zasady zapewniają równowagę między uruchomionymi aplikacjami korzystającymi z określonych wersji i umożliwiającą łatwe uaktualnienie maszyn deweloperskich i użytkowników końcowych. Te zasady wykonują następujące czynności:

- Łatwe i wydajne wdrażanie programu .NET Core, w tym aktualizacje zabezpieczeń i niezawodności.
- Użyj najnowszych narzędzi i poleceń niezależnie od docelowego środowiska uruchomieniowego.

Wybór wersji:

- Po uruchomieniu polecenia zestawu SDK [zestaw SDK używa najnowszej zainstalowanej wersji](#the-sdk-uses-the-latest-installed-version).
- Podczas kompilowania zestawu [monikery struktury docelowej definiują interfejsy API czasu kompilacji](#target-framework-monikers-define-build-time-apis).
- Po uruchomieniu aplikacji platformy .NET Core [aplikacje zależne od platformy docelowej są przenoszone do przodu](#framework-dependent-apps-roll-forward).
- Po opublikowaniu aplikacji samodzielne [wdrożenia obejmują wybrane środowisko uruchomieniowe](#self-contained-deployments-include-the-selected-runtime).

Pozostała część tego dokumentu bada te cztery scenariusze.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Zestaw SDK używa najnowszej zainstalowanej wersji

Polecenia zestawu SDK `dotnet new` obejmują `dotnet run`i. Interfejs wiersza polecenia platformy .NET Core musi wybrać wersję zestawu SDK dla każdego `dotnet` polecenia. Domyślnie używa najnowszego zestawu SDK zainstalowanego na komputerze, nawet jeśli:

- Projekt jest przeznaczony dla starszej wersji środowiska uruchomieniowego .NET Core.
- Najnowsza wersja zestaw .NET Core SDK jest wersją zapoznawczą.

W przypadku wcześniejszych wersji środowiska uruchomieniowego platformy .NET Core można korzystać z najnowszych funkcji i ulepszeń zestawu SDK. Można kierować wiele wersji środowiska uruchomieniowego platformy .NET Core w różnych projektach przy użyciu tych samych narzędzi zestawu SDK dla wszystkich projektów.

W rzadkich przypadkach może być konieczne użycie wcześniejszej wersji zestawu SDK. Należy określić tę wersję w pliku [ *Global. JSON* ](../tools/global-json.md). Zasady "Użyj najnowszych" oznacza, że do określenia wersji zestaw .NET Core SDKj starszej niż Najnowsza wersja jest używany plik *Global. JSON* .

plik *Global. JSON* można umieścić w dowolnym miejscu w hierarchii plików. Interfejs wiersza polecenia przeszukuje w górę w katalogu projektu pierwszy znaleziony plik *Global. JSON* . Można kontrolować, które projekty, do których odnosi się plik *Global. JSON* w systemie plików. Interfejs wiersza polecenia platformy .NET wyszukuje plik *Global. JSON* , co umożliwia iteracyjne nawigowanie po ścieżce z bieżącego katalogu roboczego. Pierwszy znaleziony plik *Global. JSON* Określa używaną wersję. W przypadku zainstalowania tej wersji zestawu SDK ta wersja jest używana. Jeśli zestaw SDK określony w pliku *Global. JSON* nie zostanie znaleziony, interfejs wiersza polecenia platformy .NET używa [reguł dopasowania](../tools/global-json.md#matching-rules) do wybrania zgodnego zestawu SDK lub kończy się niepowodzeniem, jeśli nie zostanie znaleziony.

W poniższym przykładzie przedstawiono składnię *Global. JSON* :

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

Proces wybierania wersji zestawu SDK to:

1. `dotnet`wyszukuje cyklicznie Odwróć plik *Global. JSON* , przechodząc do lokalizacji z bieżącego katalogu roboczego.
1. `dotnet`używa zestawu SDK określonego w pierwszym pliku *Global. JSON* .
1. `dotnet`program używa najnowszego zainstalowanego zestawu SDK, jeśli nie zostanie znaleziony plik *Global. JSON* .

Więcej informacji na temat wybierania wersji zestawu SDK można znaleźć w sekcji [reguł dopasowania](../tools/global-json.md#matching-rules) w artykule w pliku *Global. JSON*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Monikery struktury docelowej definiują interfejsy API czasu kompilacji

Projekt można skompilować pod kątem interfejsów API zdefiniowanych w **monikerze platformy docelowej** (TFM). Należy określić [platformę docelową](../../standard/frameworks.md) w pliku projektu. Ustaw `TargetFramework` element w pliku projektu, jak pokazano w następującym przykładzie:

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Możesz skompilować projekt na wiele TFMs. Ustawienie wielu struktur docelowych jest bardziej popularne dla bibliotek, ale można je również wykonywać przy użyciu aplikacji. Należy określić `TargetFrameworks` Właściwość (plural of `TargetFramework`). Struktury docelowe są rozdzielane średnikami, jak pokazano w następującym przykładzie:

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

Dany zestaw SDK obsługuje ustalony zestaw struktur, ograniczone do docelowej struktury środowiska uruchomieniowego, z którym jest dostarczany. Na przykład zestaw SDK programu .NET Core 3,0 zawiera środowisko uruchomieniowe programu .NET Core 3,0, które jest implementacją `netcoreapp3.0` platformy docelowej. Zestaw SDK platformy .NET Core 3,0 `netcoreapp2.1`obsługuje `netcoreapp2.2`, `netcoreapp3.0`,, ale `netcoreapp3.1` nie (lub nowsze). Zainstaluj zestaw SDK platformy .NET Core 3,1 do kompilowania `netcoreapp3.1`.

Platformy docelowe .NET Standard są również ograniczone do docelowej struktury środowiska uruchomieniowego, które jest dostarczane z zestawem SDK. Zestaw SDK platformy .NET Core 3,1 jest ograniczone do `netstandard2.1`. Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).

## <a name="framework-dependent-apps-roll-forward"></a>Aplikacje zależne od platformy przekazują

Gdy uruchamiasz aplikację ze [`dotnet run`](../tools/dotnet-run.md)źródła z, z [**wdrożenia zależnego od platformy**](../deploying/index.md#publish-runtime-dependent) z [`dotnet myapp.dll`](../tools/dotnet.md#description), lub z [**pliku wykonywalnego zależnego od platformy**](../deploying/index.md#publish-runtime-dependent) z `myapp.exe`, `dotnet` plik wykonywalny jest **hostem** aplikacji.

Na hoście wybierana jest Najnowsza wersja poprawki zainstalowana na maszynie. Na przykład, jeśli określono `netcoreapp3.0` w pliku projektu i `3.0.4` jest Najnowsza wersja środowiska uruchomieniowego platformy .NET, jest używane `3.0.4` środowisko uruchomieniowe.

Jeśli nie zostanie `3.0.*` znaleziona akceptowalna wersja, `3.*` zostanie użyta Nowa wersja. Jeśli na przykład zostanie określona `netcoreapp3.0` i zostanie zainstalowana `3.1.0` tylko, aplikacja zostanie uruchomiona przy użyciu `3.1.0` środowiska uruchomieniowego. Takie zachowanie jest określane jako "wersja pomocnicza do przełączenia do przodu". Małe wersje nie będą również brane pod uwagę. Gdy nie zainstalowano akceptowalnego środowiska uruchomieniowego, aplikacja nie zostanie uruchomiona.

Kilka przykładów użycia przedstawia zachowanie, jeśli celem jest 3,0:

- określono ✔️ 3,0. 3.0.5 to najwyższa zainstalowana wersja poprawki. 3.0.5.
- ❌3,0 został określony. Nie zainstalowano żadnych wersji 3,0. *. 2.1.1 to najwyższy zainstalowany środowisko uruchomieniowe. Zostanie wyświetlony komunikat o błędzie.
- określono ✔️ 3,0. Nie zainstalowano żadnych wersji 3,0. *. 3.1.0 to najwyższa zainstalowana wersja środowiska uruchomieniowego. 3.1.0.
- ❌2,0 został określony. Nie ma zainstalowanych wersji 2. x. 3.0.0 to najwyższe zainstalowane środowisko uruchomieniowe. Zostanie wyświetlony komunikat o błędzie.

Wersja pomocnicza — do przodu ma jeden efekt uboczny, który może mieć wpływ na użytkowników końcowych. Poniżej przedstawiono przykładowy scenariusz:

1. Aplikacja określa, że 3,0 jest wymagana.
2. Gdy jest uruchomiona, wersja 3,0. * nie jest zainstalowana, jednak 3.1.0 jest. Zostanie użyta wersja 3.1.0.
3. Później użytkownik zainstaluje 3.0.5 i uruchomi aplikację ponownie, 3.0.5 będzie teraz używany.

Możliwe jest, że 3.0.5 i 3.1.0 działają inaczej, szczególnie w przypadku scenariuszy, takich jak Serializowanie danych binarnych.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Wdrożenia z własnym uwzględnieniem obejmują wybrane środowisko uruchomieniowe

Aplikację można opublikować jako samodzielną [**dystrybucję**](../deploying/index.md#publish-self-contained). To podejście służy do łączenia środowiska uruchomieniowego i bibliotek platformy .NET Core z aplikacją. Wdrożenia samodzielne nie mają zależności w środowiskach środowiska uruchomieniowego. Wybór wersji środowiska uruchomieniowego występuje w czasie publikowania, a nie w czasie wykonywania.

Proces publikowania wybiera najnowszą wersję poprawki danej rodziny środowiska uruchomieniowego. Na przykład wybierz `dotnet publish` pozycję .NET Core 3.0.4, jeśli jest to Najnowsza wersja poprawki w rodzinie środowiska uruchomieniowego programu .net Core 3,0. Platforma docelowa (łącznie z najnowszymi zainstalowanymi poprawkami zabezpieczeń) jest spakowana z aplikacją.

Jeśli minimalna wersja określona dla aplikacji nie jest spełniona, występuje błąd. `dotnet publish`tworzy powiązanie z najnowszą wersją poprawki środowiska uruchomieniowego (w ramach danej głównej rodziny wersji). `dotnet publish`nie obsługuje semantyki z przekazaniem do `dotnet run`przodu. Aby uzyskać więcej informacji na temat poprawek i wdrożeń samodzielnych, zapoznaj się z artykułem dotyczącym [wyboru poprawek w środowisku uruchomieniowym](../deploying/runtime-patch-selection.md) w temacie Wdrażanie aplikacji .NET Core.

Wdrożenia samodzielne mogą wymagać określonej wersji poprawki. Można zastąpić minimalną wersję poprawki środowiska uruchomieniowego (do nowszej lub niższej wersji) w pliku projektu, jak pokazano w następującym przykładzie:

``` xml
<RuntimeFrameworkVersion>3.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` Element zastępuje domyślne zasady wersji. W przypadku wdrożeń samodzielnych `RuntimeFrameworkVersion` określa *dokładną* wersję struktury środowiska uruchomieniowego. W `RuntimeFrameworkVersion` przypadku aplikacji zależnych od platformy określa *minimalną* wymaganą wersję środowiska uruchomieniowego.

## <a name="see-also"></a>Zobacz także

- [Pobierz i zainstaluj program .NET Core](../install/index.md).
- [Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK](../install/remove-runtime-sdk-versions.md).
