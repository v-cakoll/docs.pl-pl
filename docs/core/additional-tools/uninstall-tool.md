---
title: Narzędzie do odinstalowywania
description: Omówienie narzędzia do odinstalowywania rdzenia .NET, narzędzia z przewodnikiem, które umożliwia kontrolowane oczyszczanie zestawów SDK i środowiskach uruchomieniowych .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507324"
---
# <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umożliwia usunięcie zestawów SDK i runtimes .NET Core z systemu. Dostępna jest kolekcja opcji określających, które wersje chcesz odinstalować.

Narzędzie obsługuje systemy Windows i macOS. Linux nie jest obecnie obsługiwany.

W systemie Windows narzędzie może odinstalować tylko zestawy SDK i środowiska wykonawcze zainstalowane przy użyciu jednego z następujących instalatorów:

- Instalator .NET Core SDK i runtime.
- Instalator programu Visual Studio w wersjach wcześniejszych niż Visual Studio 2019 w wersji 16.3.

W systemie macOS narzędzie może odinstalowywać tylko zestawy SDK i środowiska wykonawcze znajdujące się w folderze */usr/local/share/dotnet.*

Z powodu tych ograniczeń narzędzie może nie być w stanie odinstalować wszystkich zestawów SDK core platformy .NET i środowiskach uruchomieniowych na komputerze. Za pomocą `dotnet --info` polecenia można znaleźć wszystkie zestawy SDK rdzenia .NET i zainstalowane środowiska wykonawcze, w tym zestawy SDK i środowiska wykonawcze, których to narzędzie nie może usunąć. Polecenie `dotnet-core-uninstall list` wyświetla, które zestawy SDK można odinstalować za pomocą narzędzia.

## <a name="install-the-tool"></a>Zainstaluj narzędzie

Możesz pobrać narzędzie .NET Core Uninstall [Tool stąd](https://aka.ms/dotnet-core-uninstall-tool) i znaleźć kod źródłowy w repozytorium GitHub [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)

> [!NOTE]
> Narzędzie wymaga podniesienia uprawnień do odinstalowywania zestawów SDK core platformy .NET i środowiskach uruchomieniowych. W związku z tym powinien być zainstalowany w katalogu chronionym przed zapisem, takich jak *C:\Program Files* w systemie Windows lub */usr/local/bin* w systemie macOS. Zobacz też [Podwyższony dostęp do poleceń dotnet .](../tools/elevated-access.md) Aby uzyskać więcej informacji, zobacz [szczegółowe instrukcje instalacji](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Uruchamianie narzędzia

W poniższych krokach przedstawiono zalecane podejście do uruchamiania narzędzia do odinstalowywania:

- [Krok 1 - Wyświetlanie zainstalowanych pakietów SDK core .NET i środowiskach uruchomieniowych](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Krok 2 - Wykonaj suchą serię](#step-2---do-a-dry-run)
- [Krok 3 - Odinstalowywanie podstawowych pakietów SDK i runtimes .NET](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Krok 4 - Usuń folder rezerwowy NuGet (opcjonalnie)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Krok 1 - Wyświetlanie zainstalowanych pakietów SDK core .NET i środowiskach uruchomieniowych

Polecenie `dotnet-core-uninstall list` zawiera listę zainstalowanych zestawów SDK rdzenia .NET i środowiskach uruchomieniowych, które można usunąć za pomocą tego narzędzia. Niektóre pakiety SDK i środowiska wykonawcze mogą być wymagane przez program Visual Studio i są wyświetlane z notatką, dlaczego nie jest zalecane, aby je odinstalować.

> [!NOTE]
> Dane wyjściowe `dotnet-core-uninstall list` polecenia nie będą zgodne z listą `dotnet --info` zainstalowanych wersji w danych wyjściowych w większości przypadków. W szczególności to narzędzie nie będzie wyświetlać wersje zainstalowane przez pliki zip lub zarządzane przez program Visual Studio (dowolna wersja zainstalowana z programem Visual Studio 2019 16.3 lub nowszym). Jednym ze sposobów sprawdzenia, czy wersja jest zarządzana `Add or Remove Programs`przez program Visual Studio, jest wyświetlenie jej w programie , gdzie wersje zarządzane programu Visual Studio są oznaczone jako takie w ich nazwach wyświetlanych.

**lista dotnet-core-uninstall**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Wyświetla listę wszystkich ASP.NET core runtimes, które można odinstalować za pomocą tego narzędzia.

* **`--hosting-bundle`**

  Wyświetla listę wszystkich pakietów uruchomieniowych i hostingowych .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--runtime`**

  Wyświetla listę wszystkich przepływów .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `normal`.

* **`--x64`**

  Wyświetla listę wszystkich zestawów SDK rdzenia x64 .NET i środowiskach uruchomieniowych, które można odinstalować za pomocą tego narzędzia.

* **`--x86`**

  Wyświetla listę wszystkich zestawów SDK rdzenia x86 .NET i środowiskach uruchomieniowych, które można odinstalować za pomocą tego narzędzia.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--runtime`**

  Wyświetla listę wszystkich przepływów .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`--sdk`**

  Wyświetla listę wszystkich zestawów SDK .NET Core, które można odinstalować za pomocą tego narzędzia.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `normal`.
  
---

#### <a name="examples"></a>Przykłady

* Wyświetl listę wszystkich zestawów SDK core platformy .NET i środowiskach uruchomieniowych, które można usunąć za pomocą tego narzędzia:

  ```console
  dotnet-core-uninstall list
  ```

* Wyświetl listę wszystkich podstawowych sdk x64 .NET i środowiskach uruchomieniowych:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Wyświetl listę wszystkich podstawowych sdk x86 .NET:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Krok 2 - Wykonaj suchą serię

Polecenia `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` i wyświetlają pakiety SDK rdzenia .NET i środowiska wykonawcze, które zostaną usunięte na podstawie dostępnych opcji bez odinstalowywania. Polecenia te są synonimami.

**dotnet-core-uninstall dry-run i dotnet-core-uninstall whatif**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Określona wersja do odinstalowania. Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami. Obsługiwane są również pliki odpowiedzi.

  > [!TIP]
  > Pliki odpowiedzi są alternatywą dla umieszczania wszystkich wersji w wierszu polecenia.
  > Są to pliki tekstowe, \*zazwyczaj z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.
  > Aby określić plik `VERSION` odpowiedzi dla \@ argumentu, należy użyć znaku natychmiast po nazwie pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.

* **`--all-below <VERSION>`**

  Usuwa tylko .NET Core SDK i runtimes z wersją mniejszą niż określona wersja. Określona wersja pozostaje zainstalowana.

* **`--all-but <VERSIONS>`**

  Usuwa wszystkie.NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.

* **`--all-but-latest`**

  Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--aspnet-runtime`**

  Usuwa tylko ASP.NET podstawowe środowiska wykonawcze.

* **`--hosting-bundle`**

  Usuwa tylko środowisko uruchomieniowe i pakiety hostingu .NET Core.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe .NET Core.

* **`--sdk`**

  Usuwa tylko podstawowe sdk .NET.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `normal`.

* **`--x64`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x64 SDK lub runtimes.

* **`--x86`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x86 SDK lub runtimes.

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Dokładnie jeden `--sdk`z `--runtime` `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.
3. Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.

* **`--all-below <VERSION>`**

  Usuwa .NET Core SDK i środowiska wykonawcze poniżej określonej wersji. Określona wersja pozostanie.

* **`--all-but <VERSIONS>`**

  Usuwa .NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.

* **`--all-but-latest`**

  Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe .NET Core.

* **`--sdk`**

  Usuwa tylko podstawowe sdk .NET.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `normal`.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez visual studio lub SDK.

Uwagi:

1. Dokładnie jeden `--sdk` z `--runtime` i jest wymagany.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie.NET Core SDKs i runtimes, które mogą być wymagane przez visual studio `dotnet-core-uninstall dry-run` lub inne sdk nie są uwzględniane w danych wyjściowych. W poniższych przykładach niektóre z określonych sks i runtimes nie mogą być uwzględnione w danych wyjściowych, w zależności od stanu komputera. Aby uwzględnić wszystkie zestawy SDK i środowiska wykonawcze, `--force` wymień je jawnie jako argumenty lub użyj tej opcji.

* Dry run usuwania wszystkich .NET Core runtimes, które zostały zastąpione przez wyższe poprawki:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Suchy bieg usuwania wszystkich .NET Core SDK poniżej wersji: `2.2.301`

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Krok 3 - Odinstalowywanie podstawowych pakietów SDK i runtimes .NET

`dotnet-core-uninstall remove`odinstalowuje pakiety .NET Core SDK i Runtimes, które są określone przez kolekcję opcji. Narzędzia nie można odinstalować zestawów SDK i Runtimes w wersji 5.0 lub wyższej.

Ponieważ to narzędzie ma destrukcyjne zachowanie, **zaleca** się wykonanie przebiegu na sucho przed uruchomieniem polecenia remove. Dry run pokaże, co .NET Core SDKs i środowiska wykonawcze `remove` zostaną usunięte podczas korzystania z polecenia. Zapoznaj się z [należy usunąć wersję?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)

> [!CAUTION]
> Należy pamiętać o następujących zastrzeżeniach:
>
>- To narzędzie może odinstalować wersje zestawu .NET Core `global.json` SDK, które są wymagane przez pliki na komputerze. Można ponownie zainstalować pliki SDK .NET Core ze strony [Pobierz .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- To narzędzie można odinstalować wersje środowiska uruchomieniowego .NET Core, które są wymagane przez aplikacje zależne od struktury na komputerze. Można ponownie zainstalować środowiska uruchomieniowe .NET Core ze strony [Pobierz .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- To narzędzie może odinstalować wersje zestawu .NET Core SDK i środowiska wykonawczego, na których opiera się program Visual Studio. Jeśli przerwać instalację programu Visual Studio, uruchom "Napraw" w instalatorze programu Visual Studio, aby wrócić do stanu roboczego.

Domyślnie wszystkie polecenia zachowują .NET Core SDKs i runtimes, które mogą być wymagane przez visual studio lub innych SDK. Te zestawy SDK i środowiska wykonawcze można odinstalować, wymieniając `--force` je jawnie jako argumenty lub używając tej opcji.

Narzędzie wymaga podniesienia uprawnień do odinstalowywania zestawów SDK core platformy .NET i środowiskach uruchomieniowych. Uruchom narzędzie w wierszu polecenia Administrator `sudo` w systemie Windows i w systemie macOS. Polecenia `dry-run` `whatif` i polecenia nie wymagają podniesienia uprawnień.

**dotnet-core-uninstall usunąć**

#### <a name="synopsis"></a>Streszczenie

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Określona wersja do odinstalowania. Można wyświetlić kilka wersji jeden po drugim, oddzielone spacjami. Obsługiwane są również pliki odpowiedzi.

  > [!TIP]
  > Pliki odpowiedzi są alternatywą dla umieszczania wszystkich wersji w wierszu polecenia.
  > Są to pliki tekstowe, \*zazwyczaj z rozszerzeniem .rsp, a każda wersja jest wyświetlana w osobnym wierszu.
  > Aby określić plik `VERSION` odpowiedzi dla \@ argumentu, należy użyć znaku natychmiast po nazwie pliku odpowiedzi.

#### <a name="options"></a>Opcje

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.

* **`--all-below <VERSION>`**

  Usuwa tylko .NET Core SDK i runtimes z wersją mniejszą niż określona wersja. Określona wersja pozostaje zainstalowana.

* **`--all-but <VERSIONS>`**

  Usuwa wszystkie.NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.

* **`--all-but-latest`**

  Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--aspnet-runtime`**

  Usuwa tylko ASP.NET podstawowe środowiska wykonawcze.

* **`--hosting-bundle`**

  Usuwa tylko środowisko uruchomieniowe i pakiety hostingu .NET Core.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe .NET Core.

* **`--sdk`**

  Usuwa tylko podstawowe sdk .NET.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `normal`.

* **`--x64`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x64 SDK lub runtimes.

* **`--x86`**

  Musi być `--sdk`używany `--runtime`z `--aspnet-runtime` , i usunąć x86 SDK lub runtimes.

* **`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzenia tak lub nie.

* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez program Visual Studio.

Uwagi:

1. Dokładnie jeden `--sdk`z `--runtime` `--aspnet-runtime`, `--hosting-bundle` , i jest wymagane.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.
3. Jeśli `--x64` `--x86` lub nie są określone, a następnie x64 i x86 zostaną usunięte.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Usuwa wszystkie podstawowe sdk .NET i środowiska wykonawcze.

* **`--all-below <VERSION>`**

  Usuwa .NET Core SDK i środowiska wykonawcze poniżej określonej wersji. Określona wersja pozostanie.

* **`--all-but <VERSIONS>`**

  Usuwa .NET Core SDKs i runtimes, z wyjątkiem tych wersji określonych.

* **`--all-but-latest`**

  Usuwa .NET Core SDK i runtimes, z wyjątkiem jednej najwyższej wersji.

* **`--all-lower-patches`**

  Usuwa .NET Core SDK i runtimes zastąpione przez wyższe poprawki. Ta opcja chroni global.json.

* **`--all-previews`**

  Usuwa .NET Core SDK i środowiska wykonawcze oznaczone jako podglądy.

* **`--all-previews-but-latest`**

  Usuwa .NET Core SDK i runtimes oznaczone jako podglądy z wyjątkiem jednego najwyższego podglądu.

* **`--major-minor <MAJOR_MINOR>`**

  Usuwa .NET Core SDKs i runtimes, które pasują do określonej `major.minor` wersji.

* **`--runtime`**

  Usuwa tylko środowiska uruchomieniowe .NET Core.

* **`--sdk`**

  Usuwa tylko podstawowe sdk .NET.

* **`-v, --verbosity <LEVEL>`**

  Ustawia poziom szczegółowości. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością domyślną jest `normal`.

* **`-y, --yes`** Wykonuje polecenie bez konieczności potwierdzania Y/N.
  
* **`--force`** Wymusza usunięcie wersji, które mogą być używane przez visual studio lub SDK.

Uwagi:

1. Dokładnie jeden `--sdk` z `--runtime` i jest wymagany.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , i są wyłączne.

---

#### <a name="examples"></a>Przykłady

> [!NOTE]
> Domyślnie.NET Core SDKs i runtimes, które mogą być wymagane przez visual studio lub inne SDK są przechowywane. W poniższych przykładach niektóre z określonych sks i środowiska wykonawcze mogą pozostać, w zależności od stanu komputera. Aby usunąć wszystkie zestawy SDK i środowiska wykonawcze, należy `--force` wyświetlić je jawnie jako argumenty lub użyć tej opcji.

* Usuń wszystkie środowiska uruchomieniowe .NET Core z wyjątkiem wersji `3.0.0-preview6-27804-01` bez konieczności potwierdzenia Y/N:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Usuń wszystkie SDK .NET Core 1.1 bez konieczności potwierdzenia Y/n:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Usuń sdk .NET Core 1.1.11 bez wyjścia konsoli:

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

* Usuń wszystkie podstawowe pliki SDK .NET określone w pliku odpowiedzi`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Treść *versions.rsp* jest następująca:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Krok 4 - Usuń folder rezerwowy NuGet (opcjonalnie)

W niektórych przypadkach nie `NuGetFallbackFolder` trzeba już i może chcesz go usunąć. Aby uzyskać więcej informacji na temat usuwania tego [folderu, zobacz Usuwanie pliku NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Odinstaluj narzędzie

## <a name="windows"></a>[Windows](#tab/windows)

1. Otwórz **pozycję Dodaj lub usuń programy**.
2. Wyszukaj `Microsoft .NET Core SDK Uninstall Tool`.
3. Wybierz **pozycję Odinstaluj**.

## <a name="macos"></a>[Macos](#tab/macos)

Usuń pobrany plik *dotnet-core-uninstall.tar.gz* z katalogu, w którym został zainstalowany. Jeśli zawartość tego pliku została rozpakowana do innego katalogu, należy również usunąć tę zawartość.

---
