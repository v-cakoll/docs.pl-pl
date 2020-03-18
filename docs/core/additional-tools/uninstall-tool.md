---
title: Narzędzie Odinstalowywanie
description: Omówienie narzędzia .NET Core Uninstall Tool, narzędzia z przewodnikiem, które umożliwia kontrolowane oczyszczanie zestawów SDK i runtimes .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847084"
---
# <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umożliwia usunięcie sdk i uruchamiania programu .NET Core z systemu. Dostępna jest kolekcja opcji określających wersje, które mają zostać odinstalowane.

Narzędzie obsługuje systemy Windows i macOS. Linux nie jest obecnie obsługiwany.

W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska uruchomieniowe zainstalowane przy użyciu jednego z następujących instalatorów:

- Zestaw SDK .NET Core i instalator w czasie wykonywania.
- Instalator programu Visual Studio w wersjach wcześniejszych niż Visual Studio 2019 w wersji 16.3.

W systemie macOS narzędzie może odinstalować tylko zestawy SDK i programy uruchomieniowe znajdujące się w folderze */usr/local/share/dotnet.*

Z powodu tych ograniczeń narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK i kręgów .NET Core na komputerze. Za pomocą `dotnet --info` polecenia można znaleźć wszystkie zainstalowane zestawy SDK i programy runi .NET Core, w tym zestawy SDK i programy wykonywania, których nie można usunąć w tym narzędziu. Polecenie `dotnet-core-uninstall list` wyświetla, które zestawy SDK można odinstalować za pomocą narzędzia.

## <a name="install-the-tool"></a>Zainstaluj narzędzie

Możesz pobrać narzędzie .NET Core Uninstall Tool [z tego miejsca](https://aka.ms/dotnet-core-uninstall-tool) i znaleźć kod źródłowy w repozytorium Github [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)

> [!NOTE]
> Narzędzie wymaga podniesienia uprawnień, aby odinstalować sdk .NET Core i kręgowych. W związku z tym powinien być zainstalowany w katalogu chronionym przed zapisem, takim jak *C:\Program Files* w systemie Windows lub */usr/local/bin* w systemie macOS. Zobacz też [Podwyższony dostęp do poleceń dotnet](../tools/elevated-access.md). Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje instalacji](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Uruchamianie narzędzia

W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:

- [Krok 1 — Wyświetlanie zainstalowanych zestawów SDK i runi .NET Core](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Krok 2 - Wykonaj suchy bieg](#step-2---do-a-dry-run)
- [Krok 3 — odinstalowywanie zestawów SDK i runi programu .NET Core](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Krok 4 - Usuwanie folderu rezerwowego NuGet (opcjonalnie)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Krok 1 — Wyświetlanie zainstalowanych zestawów SDK i runi .NET Core

Polecenie `dotnet-core-uninstall list` zawiera listę zainstalowanych zestawów SDK i uruchomień .NET Core, które można usunąć za pomocą tego narzędzia. Niektóre zestawy SDK i krępy mogą być wymagane przez program Visual Studio i są wyświetlane z notatką, dlaczego nie zaleca się ich odinstalowywania.

**lista dotnet-core-deinstall**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Wyświetla listę wszystkich ASP.NET podstawowych uruchomień, które można odinstalować za pomocą tego narzędzia.

* **`--hosting-bundle`**

  Wyświetla listę wszystkich pakietów runowych i hostingowych .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--runtime`**

  Wyświetla listę wszystkich uruchomień programu .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `normal`.

* **`--x64`**

  Wyświetla listę wszystkich zestawów SDK i zestawów RUN x64 .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--x86`**

  Wyświetla listę wszystkich zestawów SDK i zestawów RUN x86 .NET Core, które można odinstalować za pomocą tego narzędzia.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--runtime`**

  Wyświetla listę wszystkich uruchomień programu .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `normal`.
  
---

#### <a name="examples"></a>Przykłady

* Lista wszystkich zestawów SDK i runi .NET Core, które można usunąć za pomocą tego narzędzia:

  ```console
  dotnet-core-uninstall list
  ```

* Lista wszystkich zestawów SDK i uruchomień x64 .NET Core:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Lista wszystkich zestawów SDK x86 .NET Core:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Krok 2 - Wykonaj suchy bieg

Polecenia `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` i wyświetlają zestawy SDK .NET Core i programy uruchomieniowe, które zostaną usunięte na podstawie dostępnych opcji bez odinstalowywania. Polecenia te są synonimami.

**dotnet-core-odinstalować suche uruchamianie i dotnet-core-odinstalować whatif**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Określona wersja do odinstalowania. Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami. Pliki odpowiedzi są również obsługiwane.

  > [!TIP]
  > Pliki odpowiedzi są alternatywą dla umieszczenia wszystkich wersji w wierszu polecenia.
  > Są to pliki tekstowe, zazwyczaj \*z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.
  > Aby określić plik odpowiedzi `VERSION` dla argumentu, użyj \@ znaku, po którym natychmiast następuje nazwa pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.

* **`--all-below <VERSION>`**

  Usuwa tylko zestawy SDK i programy wykonywania .NET Core z wersją mniejszą niż określona wersja. Określona wersja pozostaje zainstalowana.

* **`--all-but <VERSIONS>`**

  Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--aspnet-runtime`**

  Usuwa tylko ASP.NET core.Removes ASP.NET Core runtimes only.

* **`--hosting-bundle`**

  Usuwa tylko pakiety uruchomieniowe programu .NET Core i hosting.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.

* **`--runtime`**

  Usuwa tylko uruchamianie programu .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `normal`.

* **`--x64`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x64 SDK sdk lub kręgów.

* **`--x86`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x86 SDK sdk lub kręgów.

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Dokładnie jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.
3. Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.

* **`--all-below <VERSION>`**

  Usuwa zestawy SDK i programy wykonywania .NET Core poniżej określonej wersji. Określona wersja pozostanie.

* **`--all-but <VERSIONS>`**

  Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.

* **`--runtime`**

  Usuwa tylko uruchamianie programu .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `normal`.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub SDK.

Uwagi:

1. Dokładnie jeden `--sdk` `--runtime` z i jest wymagany.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie zestawy SDK .NET Core i uruchamianie, które mogą być wymagane przez `dotnet-core-uninstall dry-run` program Visual Studio lub inne zestawy SDK, nie są uwzględniane w danych wyjściowych. W poniższych przykładach niektóre z określonych zestawów SDK i runtimes nie mogą być uwzględnione w danych wyjściowych, w zależności od stanu komputera. Aby uwzględnić wszystkie zestawy SDK i czas wykonywania, `--force` należy wyświetlić je jawnie jako argumenty lub użyć tej opcji.

* Suchy przebieg usuwania wszystkich środowiska uruchomieniowego .NET Core, które zostały zastąpione przez wyższe poprawki:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Suchy przebieg usuwania wszystkich zestawów SDK .NET Core poniżej wersji: `2.2.301`

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Krok 3 — odinstalowywanie zestawów SDK i runi programu .NET Core

`dotnet-core-uninstall remove`odinstalowuje zestawy SDK .NET Core i runtimes, które są określone przez zbiór opcji. Nie można użyć narzędzia do odinstalowywania zestawów SDK i uruchomień w wersji 5.0 lub wyższej.

Ponieważ to narzędzie ma destrukcyjne zachowanie, **zdecydowanie** zaleca się wykonanie biegu na sucho przed uruchomieniem polecenia usuwania. Uruchamianie na sucho pokaże, jakie zestawy SDK i środowiska `remove` uruchomieniowe .NET Core zostaną usunięte podczas korzystania z polecenia. Odnoszą się do [Czy należy usunąć wersję?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)

> [!CAUTION]
> Należy pamiętać o następujących zastrzeżeniach:
>
>- To narzędzie może odinstalować wersje zestawu SDK `global.json` .NET Core, które są wymagane przez pliki na komputerze. Zestawy SDK programu .NET Core można ponownie zainstalować na stronie [Pobierz program .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- To narzędzie można odinstalować wersje programu .NET Core, które są wymagane przez aplikacje zależne od struktury na komputerze. Czas wykonywania programu .NET Core można ponownie zainstalować na stronie [Pobieranie programu .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- To narzędzie można odinstalować wersje zestawu SDK .NET Core i w czasie wykonywania, na których opiera się program Visual Studio. Jeśli przerwiesz instalację programu Visual Studio, uruchom "Naprawę" w instalatorze programu Visual Studio, aby powrócić do stanu roboczego.

Domyślnie wszystkie polecenia zachowują zestawy SDK i kręgowych .NET Core, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK. Te zestawy SDK i krępy można odinstalować, `--force` wymieniając je jawnie jako argumenty lub za pomocą tej opcji.

Narzędzie wymaga podniesienia uprawnień, aby odinstalować sdk .NET Core i kręgowych. Uruchom narzędzie w wierszu polecenia Administrator `sudo` w systemie Windows i w systemie macOS. Polecenia `dry-run` `whatif` i nie wymagają podniesienia wysokości.

**usuwanie dotnet-core-deinstall**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Określona wersja do odinstalowania. Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami. Pliki odpowiedzi są również obsługiwane.

  > [!TIP]
  > Pliki odpowiedzi są alternatywą dla umieszczenia wszystkich wersji w wierszu polecenia.
  > Są to pliki tekstowe, zazwyczaj \*z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.
  > Aby określić plik odpowiedzi `VERSION` dla argumentu, użyj \@ znaku, po którym natychmiast następuje nazwa pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.

* **`--all-below <VERSION>`**

  Usuwa tylko zestawy SDK i programy wykonywania .NET Core z wersją mniejszą niż określona wersja. Określona wersja pozostaje zainstalowana.

* **`--all-but <VERSIONS>`**

  Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--aspnet-runtime`**

  Usuwa tylko ASP.NET core.Removes ASP.NET Core runtimes only.

* **`--hosting-bundle`**

  Usuwa tylko pakiety uruchomieniowe programu .NET Core i hosting.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.

* **`--runtime`**

  Usuwa tylko uruchamianie programu .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `normal`.

* **`--x64`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x64 SDK sdk lub kręgów.

* **`--x86`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , , i usunąć x86 SDK sdk lub kręgów.

* **`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzenia tak lub nie.

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Dokładnie jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.
3. Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Usuwa wszystkie zestawy SDK i programy wykonywania programu .NET Core.

* **`--all-below <VERSION>`**

  Usuwa zestawy SDK i programy wykonywania .NET Core poniżej określonej wersji. Określona wersja pozostanie.

* **`--all-but <VERSIONS>`**

  Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem określonych wersji.

* **`--all-but-latest`**

  Usuwa zestawy SDK i programy wykonywania .NET Core, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa zestawy SDK .NET Core i uruchamiane przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa zestawy SDK .NET Core i uruchamiane jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa zestawy SDK .NET Core i uruchamiane, które są zgodne z określoną `major.minor` wersją.

* **`--runtime`**

  Usuwa tylko uruchamianie programu .NET Core.

* **`--sdk`**

  Usuwa tylko zestawy SDK .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością domyślną jest `normal`.

* **`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzenia Y/N.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio lub SDK.

Uwagi:

1. Dokładnie jeden `--sdk` `--runtime` z i jest wymagany.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , i są wyłączne.

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie zestawy SDK .NET Core i uruchamianie, które mogą być wymagane przez program Visual Studio lub inne zestawy SDK są przechowywane. W poniższych przykładach niektóre z określonych zestawów SDK i runtimes może pozostać, w zależności od stanu komputera. Aby usunąć wszystkie zestawy SDK i czas wykonywania, `--force` należy wyświetlić je jawnie jako argumenty lub użyć tej opcji.

* Usuń wszystkie uruchomienia programu .NET `3.0.0-preview6-27804-01` Core z wyjątkiem wersji bez konieczności potwierdzenia przez Wartość Y/N:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Usuń wszystkie zestawy SDK .NET Core 1.1 bez konieczności potwierdzenia przez wartość Y/n:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Usuń zestaw SDK .NET Core 1.1.11 bez wyjścia konsoli:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Usuń wszystkie zestawy SDK .NET Core, które można bezpiecznie usunąć za pomocą tego narzędzia:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Usuń wszystkie zestawy SDK .NET Core, które mogą zostać usunięte przez to narzędzie, w tym zestawy SDK, które mogą być wymagane przez program Visual Studio (nie zalecane):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Usuwanie wszystkich zestawów SDK programu .NET Core określonych w pliku odpowiedzi`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Zawartość *versions.rsp* jest następująca:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Krok 4 - Usuwanie folderu rezerwowego NuGet (opcjonalnie)

W niektórych przypadkach nie potrzebujesz `NuGetFallbackFolder` już i możesz chcieć go usunąć. Aby uzyskać więcej informacji na temat usuwania tego folderu, zobacz [Usuwanie NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Odinstaluj narzędzie

## <a name="windows"></a>[Windows](#tab/windows)

1. Otwórz **pozycję Dodaj lub usuń programy**.
2. Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.
3. Wybierz **pozycję Odinstaluj**.

## <a name="macos"></a>[Macos](#tab/macos)

Usuń pobrany plik *dotnet-core-uninstall.tar.gz* z katalogu, w którym został zainstalowany. Jeśli zawartość tego pliku zostanie rozpakowana do innego katalogu, należy również usunąć tę zawartość.

---
