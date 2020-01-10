---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania platformy .NET Core, narzędzia z przewodnikiem, które umożliwia kontrolowane czyszczenie zestawów SDK i środowiska uruchomieniowego platformy .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 4944c983cbd02b456c3a09a1b03bc28ba6e458cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714554"
---
# <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie do dezinstalacji programu .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu. Dostępna jest kolekcja opcji, aby określić wersje, które mają zostać odinstalowane.

Narzędzie obsługuje systemy Windows i macOS. System Linux nie jest obecnie obsługiwany.

W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe, które zostały zainstalowane przy użyciu jednego z następujących instalatorów:

- Zestaw .NET Core SDK i Instalator środowiska uruchomieniowego.
- Instalator programu Visual Studio w wersji wcześniejszej niż program Visual Studio 2019 w wersji 16,3.

W systemie macOS narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet* .

Ze względu na te ograniczenia narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i środowisk uruchomieniowych platformy .NET Core na komputerze. Można użyć `dotnet --info` polecenia, aby znaleźć wszystkie zainstalowane zestawy SDK .NET Core i środowiska uruchomieniowe, w tym zestawy SDK i środowiska uruchomieniowe, których to narzędzie nie może usunąć. Polecenie `dotnet-core-uninstall list` wyświetla listę zestawów SDK, które można odinstalować za pomocą narzędzia.

## <a name="install-the-tool"></a>Zainstaluj narzędzie

Narzędzie do odinstalowywania platformy .NET Core można pobrać z repozytorium usługi GitHub [/CLI-Lab](https://github.com/dotnet/cli-lab/releases) w ramach programu dotnet.

> [!NOTE]
> Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core. W związku z tym należy ją zainstalować w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* na macOS. Zobacz również [podwyższony poziom dostępu dla poleceń dotnet](../tools/elevated-access.md). Szczegółowe instrukcje dotyczące instalacji są dostępne na [stronie wydań usługi GitHub](https://github.com/dotnet/cli-lab/releases).

## <a name="run-the-tool"></a>Uruchamianie narzędzia

W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:

- [Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Krok 2 — wykonywanie suchego przebiegu](#step-2---do-a-dry-run)
- [Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Krok 1. wyświetlanie zainstalowanych zestawów SDK i środowisk uruchomieniowych platformy .NET Core

`dotnet-core-uninstall list` polecenie wyświetla listę zainstalowanych zestawów SDK .NET Core i środowiska uruchomieniowe, które można usunąć za pomocą tego narzędzia. Niektóre zestawy SDK i środowiska uruchomieniowe mogą być wymagane przez program Visual Studio i są wyświetlane z zawarto adnotacją dlaczego nie zaleca się ich odinstalowywania.

**dotnet-Core — lista dezinstalacji**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Opcje

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Wyświetla wszystkie ASP.NET Core środowiska uruchomieniowe, które można odinstalować za pomocą tego narzędzia.

* **`--hosting-bundle`**

  Wyświetla listę wszystkich pakietów środowiska uruchomieniowego środowiska .NET Core i hostingu, które można odinstalować za pomocą tego narzędzia.

* **`--runtime`**

  Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.

* **`--x64`**

  Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x64 .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--x86`**

  Wyświetla listę wszystkich zestawów SDK i środowisk uruchomieniowych x86 .NET Core, które można odinstalować za pomocą tego narzędzia.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

* **`--runtime`**

  Wyświetla wszystkie środowiska uruchomieniowe platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK platformy .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.
  
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

Polecenia `dotnet-core-uninstall dry-run` i `dotnet-core-uninstall whatif` wyświetlają zestawy .NET Core i środowiska uruchomieniowe, które zostaną usunięte na podstawie opcji dostępnych bez konieczności odinstalowania. Te polecenia są synonimami.

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
  > Są one plikami tekstowymi, zazwyczaj przy użyciu rozszerzenia \*. rsp, a każda wersja jest wymieniona w osobnym wierszu.
  > Aby określić plik odpowiedzi dla argumentu `VERSION`, użyj znaku \@ bezpośrednio po nazwie pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

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

  Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.

* **`--x64`**

  Należy używać z `--sdk`, `--runtime`i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.

* **`--x86`**

  Aby można było usunąć zestawy SDK lub środowiska uruchomieniowe x86, należy użyć programu z `--sdk`, `--runtime`i `--aspnet-runtime`.

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Wymagany jest dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`i `--hosting-bundle`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.
3. Jeśli nie określono `--x64` lub `--x86`, zostaną usunięte oba wersje x64 i x86.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

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

  Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.

Uwagi:

1. Wymagany jest dokładnie jeden z `--sdk` i `--runtime`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie zestawy SDK platformy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK, nie są uwzględniane w danych wyjściowych `dotnet-core-uninstall dry-run`. W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą nie zostać uwzględnione w danych wyjściowych, w zależności od stanu komputera. Aby uwzględnić wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić jako argumenty lub użyć opcji `--force`.

* Suchy przebieg usuwania wszystkich środowisk uruchomieniowych platformy .NET Core, które zostały zastąpione nowszymi poprawkami:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Suche uruchomienie usuwania wszystkich zestawów SDK platformy .NET Core poniżej wersji `2.2.301`:

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Krok 3 — Odinstalowywanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core

`dotnet-core-uninstall remove` Odinstalowuje zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które są określone przez kolekcję opcji. Narzędzia nie można użyć do odinstalowania zestawów SDK i środowiska uruchomieniowego w wersji 5,0 lub nowszej.

Ponieważ to narzędzie ma szkodliwe zachowanie, **zdecydowanie** zaleca się wykonanie suchego uruchomienia przed uruchomieniem polecenia Usuń. W przypadku przebiegu suchego zostanie wyświetlona zawartość zestawów SDK i środowiska uruchomieniowe platformy .NET Core po użyciu polecenia `remove`. Zapoznaj się z tematem [czy należy usunąć wersję?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) , aby dowiedzieć się, które zestawy SDK i środowiska uruchomieniowe są bezpieczne do usunięcia.

> [!CAUTION]
> Należy pamiętać o następujących zastrzeżeniach:
>
>- To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK, które są wymagane przez pliki `global.json` na komputerze. Zestawy SDK platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- To narzędzie umożliwia odinstalowanie wersji środowiska uruchomieniowego programu .NET Core, które są wymagane przez aplikacje zależne od platformy. Środowiska uruchomieniowe platformy .NET Core można ponownie zainstalować ze strony [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- To narzędzie umożliwia odinstalowanie wersji zestaw .NET Core SDK i środowiska uruchomieniowego, na których bazuje program Visual Studio. W przypadku przerwania instalacji programu Visual Studio Uruchom polecenie "Napraw" w Instalatorze programu Visual Studio, aby powrócić do stanu roboczego.

Domyślnie wszystkie polecenia zachowują zestawy .NET Core i środowiska uruchomieniowe, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK. Te zestawy SDK i środowiska uruchomieniowe mogą zostać odinstalowane przez wymienienie ich jawnie jako argumenty lub przy użyciu opcji `--force`.

Narzędzie wymaga podniesienia uprawnień, aby odinstalować zestawy SDK i środowiska uruchomieniowe platformy .NET Core. Uruchom narzędzie w wierszu polecenia administratora w systemie Windows i z `sudo` na macOS. Polecenia `dry-run` i `whatif` nie wymagają podniesienia uprawnień.

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
  > Są one plikami tekstowymi, zazwyczaj przy użyciu rozszerzenia \*. rsp, a każda wersja jest wymieniona w osobnym wierszu.
  > Aby określić plik odpowiedzi dla argumentu `VERSION`, użyj znaku \@ bezpośrednio po nazwie pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

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

  Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.

* **`--x64`**

  Należy używać z `--sdk`, `--runtime`i `--aspnet-runtime` do usuwania zestawów SDK x64 lub środowisk uruchomieniowych.

* **`--x86`**

  Aby można było usunąć zestawy SDK lub środowiska uruchomieniowe x86, należy użyć programu z `--sdk`, `--runtime`i `--aspnet-runtime`.

* **`-y, --yes`** Wykonuje polecenie bez potwierdzenia typu "tak" lub "nie".

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Wymagany jest dokładnie jeden z `--sdk`, `--runtime`, `--aspnet-runtime`i `--hosting-bundle`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.
3. Jeśli nie określono `--x64` lub `--x86`, zostaną usunięte oba wersje x64 i x86.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

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

  Usuwa zestawy .NET Core i środowiska uruchomieniowe zgodne z określoną wersją `major.minor`.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe platformy .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK platformy .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.

* **`-y, --yes`** Wykonuje polecenie bez potwierdzenia Y/N.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub zestawy SDK.

Uwagi:

1. Wymagany jest dokładnie jeden z `--sdk` i `--runtime`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`i `[<VERSION>...]` są na wyłączność.

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie są przechowywane zestawy SDK i środowiska uruchomieniowe platformy .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK. W poniższych przykładach niektóre z określonych zestawów SDK i środowiska uruchomieniowe mogą pozostać w zależności od stanu komputera. Aby usunąć wszystkie zestawy SDK i środowiska uruchomieniowe, należy je jawnie wystawić jako argumenty lub użyć opcji `--force`.

* Usuń wszystkie środowiska uruchomieniowe platformy .NET Core, z wyjątkiem wersji `3.0.0-preview6-27804-01` bez konieczności potwierdzania Y/N:

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

* Usuń wszystkie zestawy SDK platformy .NET Core, które są określone w pliku odpowiedzi `versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Zawartość *wersji. rsp* jest następująca:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Krok 4. Usuwanie folderu rezerwowego NuGet (opcjonalnie)

W niektórych przypadkach nie jest już potrzebne `NuGetFallbackFolder` i może zostać usunięta. Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [usuwanie NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Odinstalowywanie narzędzia

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

1. Otwórz aplet **Dodaj lub usuń programy**.
2. Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.
3. Wybierz pozycję **Odinstaluj**.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

Usuń pobrany plik *dotnet-Core-Uninstall. tar. gz* z katalogu, w którym został zainstalowany. Jeśli zawartość tego pliku została rozpakowany do innego katalogu, pamiętaj, aby usunąć tę zawartość.

---
