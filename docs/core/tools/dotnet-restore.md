---
title: polecenie przywracanie dotnet
description: Dowiedz się, jak przywrócić zależności i narzędzia specyficzne dla projektu za pomocą polecenia przywracania dotnet.
ms.date: 02/27/2020
ms.openlocfilehash: c5cc9adf1d77b0ab03a61cc315d42c2f38362ad9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021776"
---
# <a name="dotnet-restore"></a>dotnet restore

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet restore`- Przywraca zależności i narzędzia projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet restore` używa NuGet do przywracania zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu. Domyślnie przywracanie zależności i narzędzia są wykonywane równolegle.

Aby przywrócić zależności, NuGet potrzebuje źródeł danych, w których znajdują się pakiety. Kanały informacyjne są zwykle dostarczane za pośrednictwem pliku konfiguracyjnego *nuget.config.* Domyślny plik konfiguracyjny jest dostarczany po zainstalowaniu narzędzia .NET Core SDK. Dodatkowe źródła danych można określić, tworząc własny plik *nuget.config* w katalogu projektu. Można zastąpić *nuget.config* kanałów z - `-s` opcja.

Dla zależności należy określić, gdzie przywrócone pakiety są `--packages` umieszczane podczas operacji przywracania przy użyciu argumentu. Jeśli nie zostanie określony, używana jest domyślna pamięć `.nuget/packages` podręczna pakietów NuGet, która znajduje się w katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych. Na przykład */home/user1* w systemie Linux lub *C:\Users\user1* w systemie Windows.

W przypadku narzędzi specyficznych dla projektu najpierw przywraca pakiet, `dotnet restore` w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w jego pliku projektu.

### <a name="nugetconfig-differences"></a>różnice nuget.config

Na zachowanie `dotnet restore` polecenia mają wpływ ustawienia w pliku *nuget.config,* jeśli jest obecny. Na przykład ustawienie `globalPackagesFolder` w *nuget.config* umieszcza przywrócone pakiety NuGet w określonym folderze. Jest to alternatywa dla `--packages` określenia `dotnet restore` opcji w poleceniu. Aby uzyskać więcej informacji, zobacz [nuget.config reference](/nuget/schema/nuget-config-file).

Istnieją trzy określone `dotnet restore` ustawienia, które ignorują:

- [bindingRedirects (przekierowanie)](/nuget/schema/nuget-config-file#bindingredirects-section)

  Przekierowania powiązania nie działają `<PackageReference>` z elementami, `<PackageReference>` a program .NET Core obsługuje tylko elementy dla pakietów NuGet.

- [Rozwiązanie](/nuget/schema/nuget-config-file#solution-section)

  To ustawienie jest specyficzne dla programu Visual Studio i nie dotyczy programu .NET Core. .NET Core nie używa `packages.config` pliku i zamiast `<PackageReference>` tego używa elementów dla pakietów NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji zaufanych](https://github.com/NuGet/Home/issues/7939) pakietów na różnych platformach.

## <a name="implicit-restore"></a>Niejawne przywracanie

Polecenie `dotnet restore` jest uruchamiane niejawnie, jeśli to konieczne po uruchomieniu następujących poleceń:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.

Czasami może być niewygodne do uruchomienia `dotnet restore` niejawnie. Na przykład niektóre zautomatyzowane systemy, takie jak `dotnet restore` systemy kompilacji, muszą jawnie wywoływać, aby kontrolować, kiedy nastąpi przywracanie, aby mogły kontrolować użycie sieci. Aby `dotnet restore` zapobiec niejawnie, można `--no-restore` użyć flagi z dowolnym z tych poleceń, aby wyłączyć niejawne przywracanie.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Opcjonalna ścieżka do pliku projektu do przywrócenia.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracyjny NuGet (*nuget.config*) do użycia w operacji przywracania.

- **`--disable-parallel`**

  Wyłącza przywracanie wielu projektów równolegle.

- **`--force`**

  Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`--force-evaluate`**

  Wymusza przywracanie, aby ponownie ocenić wszystkie zależności, nawet jeśli plik blokady już istnieje.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--ignore-failed-sources`**

  O nieudanych źródłach należy tylko ostrzec, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania). Od .NET Core 2.1.400.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Lokalizacja wyjściowa, w której zapisywany jest plik blokady projektu. Domyślnie jest to *PROJECT_ROOT\packages.lock.json*.

- **`--locked-mode`**

  Nie zezwalaj na aktualizowanie pliku blokady projektu.

- **`--no-cache`**

  Określa, że nie buforuje żądań HTTP.

- **`--no-dependencies`**

  Podczas przywracania projektu z odwołaniami do projektu do projektu (P2P), przywraca projekt główny, a nie odwołania.

- **`--packages <PACKAGES_DIRECTORY>`**

  Określa katalog przywróconych pakietów.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa środowisko uruchomieniowe przywracania pakietu. Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w tagu `<RuntimeIdentifiers>` w pliku *csproj.* Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md). Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.

- **`-s|--source <SOURCE>`**

  Określa źródło pakietu NuGet do użycia podczas operacji przywracania. To ustawienie zastępuje wszystkie źródła określone w plikach *nuget.config.* Wiele źródeł można podać, określając tę opcję wiele razy.

- **`--use-lockfile`**

  Umożliwia generowanie i używane go z przywracania pliku blokady projektu.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartością `minimal`domyślną jest .

## <a name="examples"></a>Przykłady

- Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet restore
  ```

- Przywróć zależności `app1` i narzędzia dla projektu znajdującego się w danej ścieżce:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku podanej jako źródło:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przedstawiającym szczegółowe dane wyjściowe:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
