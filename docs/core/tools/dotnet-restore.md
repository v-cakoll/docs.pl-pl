---
title: polecenie dotnet restore
description: Informacje o sposobie przywracania zależności i narzędzi specyficznych dla projektu przy użyciu polecenia dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: 276fad896a6a8a647ed05a9de8c582d463d9ab8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005323"
---
# <a name="dotnet-restore"></a>dotnet restore

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet restore`— Przywraca zależności i narzędzia projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>Opis

`dotnet restore`Polecenie używa narzędzia NuGet do przywracania zależności oraz narzędzi specyficznych dla projektu, które są określone w pliku projektu.  W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia, ponieważ przywracanie NuGet jest uruchamiane niejawnie w razie potrzeby podczas uruchamiania następujących poleceń:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Czasami może być niewygodne uruchamianie niejawnego przywracania NuGet przy użyciu tych poleceń. Na przykład niektóre zautomatyzowane systemy, takie jak systemy kompilacji, muszą jawnie wywołać, `dotnet restore` Aby określić, kiedy następuje przywracanie, aby można było kontrolować użycie sieci. Aby zapobiec niejawnemu przywracaniu NuGet, można użyć `--no-restore` flagi z dowolnym z tych poleceń, aby wyłączyć Przywracanie niejawne.

### <a name="specify-feeds"></a>Określ źródła danych

Aby przywrócić zależności, program NuGet potrzebuje kanałów informacyjnych, w których znajdują się pakiety. Kanały informacyjne są zazwyczaj udostępniane za pośrednictwem pliku konfiguracyjnego *NuGet. config* . Domyślny plik konfiguracji jest dostarczany, gdy zainstalowano zestaw .NET Core SDK. Aby określić dodatkowe źródła danych, wykonaj jedną z następujących czynności:

- Utwórz własny plik *NuGet. config* w katalogu projektu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](/nuget/consume-packages/configuring-nuget-behavior) i [NuGet. config różnice](#nugetconfig-differences) w dalszej części tego artykułu.
- Użyj `dotnet nuget` poleceń, takich jak [`dotnet nuget add source`](dotnet-nuget-add-source.md) .

Można zastąpić źródła danych *NuGet. config* `-s` opcją.

Informacje o sposobach korzystania z uwierzytelnionych źródeł danych znajdują się w temacie Używanie [pakietów z uwierzytelnionych kanałów informacyjnych](/nuget/consume-packages/consuming-packages-authenticated-feeds).

### <a name="global-packages-folder"></a>Folder pakietów globalnych

W przypadku zależności można określić miejsce, w którym przywrócone pakiety są umieszczane podczas operacji przywracania przy użyciu `--packages` argumentu. Jeśli nie zostanie określony, zostanie użyta domyślna pamięć podręczna pakietów NuGet, która znajduje się w katalogu `.nuget/packages` w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych. Na przykład */home/user1* na system Linux lub *C:\Users\user1* w systemie Windows.

### <a name="project-specific-tooling"></a>Narzędzia specyficzne dla projektu

W przypadku narzędzi specyficznych dla projektu program `dotnet restore` najpierw przywraca pakiet, w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w pliku projektu.

### <a name="nugetconfig-differences"></a>różnice NuGet. config

Zachowanie `dotnet restore` polecenia ma wpływ na ustawienia w pliku *NuGet. config* , jeśli jest obecny. Na przykład ustawienie `globalPackagesFolder` w *pliku NuGet. config* powoduje umieszczenie przywróconych pakietów NuGet w określonym folderze. Jest to alternatywa dla określenia `--packages` opcji `dotnet restore` polecenia. Aby uzyskać więcej informacji, zobacz [Dokumentacja NuGet. config](/nuget/schema/nuget-config-file).

Istnieją trzy określone ustawienia, które `dotnet restore` ignorują:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Przekierowania powiązań nie działają z `<PackageReference>` elementami i .NET Core obsługuje tylko `<PackageReference>` elementy dla pakietów NuGet.

- [Narzędzie](/nuget/schema/nuget-config-file#solution-section)

  To ustawienie dotyczy programu Visual Studio i nie ma zastosowania do programu .NET Core. Platforma .NET Core nie używa `packages.config` pliku, a zamiast tego używa `<PackageReference>` elementów dla pakietów NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów przez wiele platform.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Opcjonalna ścieżka do pliku projektu do przywrócenia.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.

- **`--disable-parallel`**

  Wyłącza przywracanie równolegle wielu projektów.

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

- **`--force-evaluate`**

  Wymusza przywrócenie przez Przywracanie wszystkich zależności, nawet jeśli plik blokady już istnieje.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--ignore-failed-sources`**

  Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania). Od programu .NET Core 2.1.400.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Lokalizacja wyjściowa, w której jest zapisywana plik blokady projektu. Domyślnie jest to *PROJECT_ROOT \packages.Lock.JSON*.

- **`--locked-mode`**

  Nie Zezwalaj na aktualizowanie pliku blokady projektu.

- **`--no-cache`**

  Określa, że nie mają być buforowane żądania HTTP.

- **`--no-dependencies`**

  W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

- **`--packages <PACKAGES_DIRECTORY>`**

  Określa katalog przywróconych pakietów.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa środowisko uruchomieniowe przywracania pakietu. Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w `<RuntimeIdentifiers>` tagu w pliku *. csproj* . Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.

- **`-s|--source <SOURCE>`**

  Określa identyfikator URI źródła pakietu NuGet do użycia podczas operacji przywracania. To ustawienie zastępuje wszystkie źródła określone w plikach *NuGet. config* . Można podać wiele źródeł, określając tę opcję wiele razy.

- **`--use-lock-file`**

  Umożliwia generowanie i używanie pliku blokady projektu z przywracaniem.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` . Wartość domyślna to `minimal` .

## <a name="examples"></a>Przykłady

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet restore
  ```

- Przywróć zależności i narzędzia dla `app1` projektu Znalezione w danej ścieżce:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku dostarczonej jako Źródło:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przedstawiające szczegółowe dane wyjściowe:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
