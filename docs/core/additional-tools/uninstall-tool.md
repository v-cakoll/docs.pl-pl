---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania platformy .NET Core, narzędzia z przewodnikiem, które umożliwia kontrolowane czyszczenie zestawów SDK i środowiska uruchomieniowego platformy .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 45cf0841391d02636770e98666e2897d2598fab4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595718"
---
# <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie do dezinstalacji programu .NET Core](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu. Dostępna jest kolekcja opcji, aby określić wersje, które mają zostać odinstalowane.

Narzędzie obsługuje systemy Windows i macOS. System Linux nie jest obecnie obsługiwany.

W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe, które zostały zainstalowane przy użyciu jednego z następujących instalatorów:

- Zestaw .NET Core SDK i Instalator środowiska uruchomieniowego.
- Instalator programu Visual Studio w wersji wcześniejszej niż program Visual Studio 2019 w wersji 16,3.

W systemie macOS narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet* .

Ze względu na te ograniczenia narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i środowisk uruchomieniowych platformy .NET Core na komputerze. Możesz użyć `dotnet --info` polecenia, aby znaleźć wszystkie zainstalowane zestawy SDK .NET Core i środowiska uruchomieniowe, w tym zestawy SDK i środowiska uruchomieniowe, których to narzędzie nie może usunąć. `dotnet-core-uninstall list` Polecenie wyświetla listę zestawów SDK, które można odinstalować za pomocą narzędzia.

## <a name="install-the-tool"></a>Zainstaluj narzędzie

W [tym miejscu](https://aka.ms/dotnet-core-uninstall-tool) możesz pobrać narzędzie do odinstalowywania platformy .NET Core i znaleźć kod źródłowy w repozytorium GitHub [/CLI-Lab](https://github.com/dotnet/cli-lab) .

> [!NOTE]
> Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core. W związku z tym należy ją zainstalować w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* na macOS. Zobacz również [podwyższony poziom dostępu dla poleceń dotnet](../tools/elevated-access.md). Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje dotyczące instalacji](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Uruchamianie narzędzia

W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:

- [Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Krok 2 — wykonywanie suchego przebiegu](#step-2---do-a-dry-run)
- [Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core

`dotnet-core-uninstall list` Polecenie wyświetla listę zainstalowanych zestawów SDK .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia. Niektóre zestawy SDK i środowiska uruchomieniowe mogą być wymagane przez program Visual Studio i są wyświetlane z zawarto adnotacją dlaczego nie zaleca się ich odinstalowywania.

> [!NOTE]
> Dane wyjściowe `dotnet-core-uninstall list` polecenia nie będą zgodne z listą zainstalowanych wersji w danych wyjściowych `dotnet --info` w większości przypadków. W przypadku tego narzędzia nie będą wyświetlane wersje zainstalowane przez pliki zip ani zarządzane przez program Visual Studio (dowolna wersja zainstalowana z programem Visual Studio 2019 16,3 lub nowszym). Jednym ze sposobów sprawdzenia, czy wersja jest zarządzana przez program Visual Studio, jest wyświetlenie jej w programie `Add or Remove Programs`, gdzie wersje zarządzane programu Visual Studio są oznaczone jako takie w nazwach wyświetlanych.

**dotnet-Core — lista dezinstalacji**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Wyświetla wszystkie ASP.NET Core środowiska uruchomieniowe, które można odinstalować za pomocą tego narzędzia.

* **`--hosting-bundle`**

  Wyświetla listę wszystkich pakietów środowiska uruchomieniowego środowiska .NET Core i hostingu, które można odinstalować za pomocą tego narzędzia.

* **`--runtime`**

  Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `normal`.

* **`--x64`**

  Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--x86`**

  Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x86 .NET Core, które można odinstalować za pomocą tego narzędzia.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `normal`.
  
---

#### <a name="examples"></a>Przykłady

* Wyświetl listę wszystkich zestawów SDK platformy .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia:

  ```console
  dotnet-core-uninstall list
  ```

* Wyświetl listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Wyświetl listę wszystkich zestawów SDK dla platformy .NET Core:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Krok 2 — wykonywanie suchego przebiegu

Polecenia `dotnet-core-uninstall dry-run` i `dotnet-core-uninstall whatif` wyświetlają .NET Core zestawy SDK i środowiska uruchomieniowe, które zostaną usunięte na podstawie opcji dostępnych bez konieczności odinstalowania. Te polecenia są synonimami.

**dotnet-Core — Odinstalowywanie suchego i dotnet-Core-Uninstall whatIf**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Określona wersja do odinstalowania. Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami. Pliki odpowiedzi są również obsługiwane.

  > [!TIP]
  > Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.
  > Są one plikami tekstowymi, zazwyczaj z \*rozszerzeniem. rsp, a każda wersja jest wymieniona w osobnym wierszu.
  > Aby określić plik odpowiedzi dla `VERSION` argumentu, użyj \@ znaku bezpośrednio po nazwie pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.

* **`--all-below <VERSION>`**

  Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja. Określona wersja jest zainstalowana.

* **`--all-but <VERSIONS>`**

  Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami. Ta opcja chroni plik Global. JSON.

* **`--all-previews`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.

* **`--aspnet-runtime`**

  Usuwa tylko ASP.NET Core środowiska uruchomieniowe.

* **`--hosting-bundle`**

  Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `normal`.

* **`--x64`**

  Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.

* **`--x86`**

  Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x86 lub środowisk uruchomieniowych.

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`, i `--hosting-bundle` jest wymagany.
2. `--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`
3. Jeśli `--x64` lub `--x86` nie zostanie określony, zostaną usunięte oba wersje x64 i x86.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.

* **`--all-below <VERSION>`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji. Określona wersja pozostanie.

* **`--all-but <VERSIONS>`**

  Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami. Ta opcja chroni plik Global. JSON.

* **`--all-previews`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `normal`.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.

Uwagi:

1. Dokładnie jeden z `--sdk` i `--runtime` jest wymagany.
2. `--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK `dotnet-core-uninstall dry-run` , nie są uwzględniane w danych wyjściowych. W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą nie zostać uwzględnione w danych wyjściowych, w zależności od stanu komputera. Aby uwzględnić wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić `--force` jako argumenty lub użyć opcji.

* Suchy przebieg usuwania wszystkich środowisk uruchomieniowych platformy .NET Core, które zostały zastąpione nowszymi poprawkami:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Suchy przebieg usuwania wszystkich zestawów .NET Core SDK poniżej wersji `2.2.301`:

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core

`dotnet-core-uninstall remove`Odinstalowuje zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które są określone przez kolekcję opcji. Narzędzia nie można użyć do odinstalowania zestawów SDK i środowiska uruchomieniowego w wersji 5,0 lub nowszej.

Ponieważ to narzędzie ma szkodliwe zachowanie, **zdecydowanie** zaleca się wykonanie suchego uruchomienia przed uruchomieniem polecenia Usuń. W przypadku uruchamiania w trybie suchym zostanie wyświetlone, które zestawy SDK i środowiska uruchomieniowe platformy .NET Core `remove` zostaną usunięte przy użyciu polecenia. Zapoznaj się z tematem [czy należy usunąć wersję?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) , aby dowiedzieć się, które zestawy SDK i środowiska uruchomieniowe są bezpieczne do usunięcia.

> [!CAUTION]
> Należy pamiętać o następujących zastrzeżeniach:
>
>- To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK, które są wymagane przez `global.json` pliki na komputerze. Zestawy SDK platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- To narzędzie umożliwia odinstalowanie wersji środowiska uruchomieniowego programu .NET Core, które są wymagane przez aplikacje zależne od platformy. Środowiska uruchomieniowe platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK i środowiska uruchomieniowego, na których bazuje program Visual Studio. W przypadku przerwania instalacji programu Visual Studio Uruchom polecenie "Napraw" w Instalatorze programu Visual Studio, aby powrócić do stanu roboczego.

Domyślnie wszystkie polecenia zachowują zestawy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK. Te zestawy SDK i środowiska uruchomieniowe mogą zostać odinstalowane przez wymienienie ich jawnie jako `--force` argumenty lub przy użyciu opcji.

Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core. Uruchom narzędzie w wierszu polecenia administratora w systemie Windows i `sudo` w systemie macOS. Polecenia `dry-run` i `whatif` nie wymagają podniesienia uprawnień.

**dotnet-Core — usuwanie odinstalowania**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Określona wersja do odinstalowania. Można wyświetlić kilka kolejnych wersji, rozdzielonych spacjami. Pliki odpowiedzi są również obsługiwane.

  > [!TIP]
  > Pliki odpowiedzi są alternatywą do umieszczania wszystkich wersji w wierszu polecenia.
  > Są one plikami tekstowymi, zazwyczaj z \*rozszerzeniem. rsp, a każda wersja jest wymieniona w osobnym wierszu.
  > Aby określić plik odpowiedzi dla `VERSION` argumentu, użyj \@ znaku bezpośrednio po nazwie pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.

* **`--all-below <VERSION>`**

  Usuwa tylko zestawy SDK i środowiska uruchomieniowe platformy .NET Core z wersją mniejszą niż określona wersja. Określona wersja jest zainstalowana.

* **`--all-but <VERSIONS>`**

  Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami. Ta opcja chroni plik Global. JSON.

* **`--all-previews`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.

* **`--aspnet-runtime`**

  Usuwa tylko ASP.NET Core środowiska uruchomieniowe.

* **`--hosting-bundle`**

  Usuwa środowisko uruchomieniowe programu .NET Core i tylko pakiety hostingu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `normal`.

* **`--x64`**

  Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.

* **`--x86`**

  Musi być używana z `--sdk`, `--runtime`, i `--aspnet-runtime` do usuwania zestawów SDK x86 lub środowisk uruchomieniowych.

* **`-y, --yes`** Wykonuje polecenie bez potwierdzenia typu "tak" lub "nie".

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`, i `--hosting-bundle` jest wymagany.
2. `--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`
3. Jeśli `--x64` lub `--x86` nie zostanie określony, zostaną usunięte oba wersje x64 i x86.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Usuwa wszystkie zestawy SDK i środowiska uruchomieniowe platformy .NET Core.

* **`--all-below <VERSION>`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core poniżej określonej wersji. Określona wersja pozostanie.

* **`--all-but <VERSIONS>`**

  Usuwa zestawy .NET Core i środowiska uruchomieniowe, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe zastąpione nowszymi poprawkami. Ta opcja chroni plik Global. JSON.

* **`--all-previews`**

  Usuwa zestawy SDK i środowiska uruchomieniowe platformy .NET Core oznaczone jako wersje zapoznawcze.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK platformy .NET Core i środowiska uruchomieniowe oznaczone jako wersje zapoznawcze z wyjątkiem tego, który jest najwyższego poziomu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy .NET Core i środowiska uruchomieniowe, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartością domyślną jest `normal`.

* **`-y, --yes`** Wykonuje polecenie bez potwierdzenia Y/N.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.

Uwagi:

1. Dokładnie jeden z `--sdk` i `--runtime` jest wymagany.
2. `--all`, `--all-below`, `--all-but` `--major-minor` `[<VERSION>...]` ,,,,, i są wyłączne. `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest`

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie są przechowywane zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK. W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą pozostać w zależności od stanu komputera. Aby usunąć wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić `--force` jako argumenty lub użyć opcji.

* Usuń wszystkie środowiska uruchomieniowe platformy .NET Core z `3.0.0-preview6-27804-01` wyjątkiem wersji, która nie wymaga potwierdzenia Y/N:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Usuń wszystkie zestawy SDK platformy .NET Core 1,1 bez konieczności potwierdzania Y/n:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Usuń zestaw .NET Core 1.1.11 SDK bez danych wyjściowych konsoli:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Usuń wszystkie zestawy SDK platformy .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Usuń wszystkie zestawy SDK platformy .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (niezalecane):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Usuń wszystkie zestawy SDK platformy .NET Core, które są określone w pliku odpowiedzi`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Zawartość *wersji. rsp* jest następująca:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)

W niektórych przypadkach nie jest już potrzebna `NuGetFallbackFolder` i może chcieć ją usunąć. Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [usuwanie NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Odinstalowywanie narzędzia

## <a name="windows"></a>[Windows](#tab/windows)

1. Otwórz aplet **Dodaj lub usuń programy**.
2. Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.
3. Wybierz pozycję **Odinstaluj**.

## <a name="macos"></a>[macOS](#tab/macos)

Usuń pobrany plik *dotnet-Core-Uninstall. tar. gz* z katalogu, w którym został zainstalowany. Jeśli zawartość tego pliku została rozpakowany do innego katalogu, pamiętaj, aby usunąć tę zawartość.

---
