---
title: polecenie przywracania dotnet
description: Dowiedz się, jak przywrócić zależności i narzędzia specyficzne dla projektu za pomocą polecenia przywracania dotnet.
ms.date: 02/27/2020
ms.openlocfilehash: e74027ba70ddf6905a12f9691caeb0a406428ad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157027"
---
# <a name="dotnet-restore"></a>dotnet restore

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet restore`- Przywraca zależności i narzędzia projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet restore` używa NuGet do przywracania zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu. Domyślnie przywracanie zależności i narzędzi są wykonywane równolegle.

Aby przywrócić zależności, NuGet potrzebuje źródeł danych, w których znajdują się pakiety. Kanały informacyjne są zwykle dostarczane za pośrednictwem pliku konfiguracyjnego *nuget.config.* Domyślny plik konfiguracyjny jest dostarczany po zainstalowaniu sdk .NET Core. Dodatkowe źródła danych można określić, tworząc własny plik *nuget.config* w katalogu projektu. Można zastąpić kanały *nuget.config* opcją `-s` - - można zastąpić.

W przypadku zależności należy określić, gdzie przywrócone pakiety są `--packages` umieszczane podczas operacji przywracania przy użyciu argumentu. Jeśli nie zostanie określony, używana jest domyślna pamięć podręczna pakietu NuGet, która znajduje się w `.nuget/packages` katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych. Na przykład */home/user1* w systemie Linux lub *C:\Users\user1* w systemie Windows.

W przypadku narzędzi specyficznych dla projektu najpierw przywraca pakiet, `dotnet restore` w którym narzędzie jest zapakowane, a następnie przechodzi do przywrócenia zależności narzędzia, jak określono w jego pliku projektu.

### <a name="nugetconfig-differences"></a>różnice nuget.config

Na zachowanie `dotnet restore` polecenia mają wpływ ustawienia pliku *nuget.config,* jeśli są obecne. Na przykład ustawienie `globalPackagesFolder` in *nuget.config* umieszcza przywrócone pakiety NuGet w określonym folderze. Jest to alternatywa dla `--packages` określenia `dotnet restore` opcji w poleceniu. Aby uzyskać więcej informacji, zobacz [odwołanie nuget.config](/nuget/schema/nuget-config-file).

Istnieją trzy specyficzne `dotnet restore` ustawienia, które ignorują:

- [bindingRedirects (Redirects)](/nuget/schema/nuget-config-file#bindingredirects-section)

  Powiązanie przekierowania nie działają `<PackageReference>` z elementami i `<PackageReference>` .NET Core obsługuje tylko elementy dla pakietów NuGet.

- [Rozwiązanie](/nuget/schema/nuget-config-file#solution-section)

  To ustawienie jest specyficzne dla programu Visual Studio i nie ma zastosowania do programu .NET Core. .NET Core nie używa `packages.config` pliku i `<PackageReference>` zamiast tego używa elementów dla pakietów NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów na wielu platformach.

## <a name="implicit-restore"></a>Przywracanie niejawne

W `dotnet restore` razie potrzeby po uruchomieniu następującepolecenia jest uruchamiane niejawnie:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.

Czasami może być niewygodne `dotnet restore` do uruchomienia niejawnie. Na przykład niektóre zautomatyzowane systemy, takie jak `dotnet restore` systemy kompilacji, muszą jawnie wywołać, aby kontrolować, gdy nastąpi przywracanie, aby mogły kontrolować użycie sieci. Aby `dotnet restore` zapobiec uruchamianiu niejawnie, można użyć `--no-restore` flagi z dowolnym z tych poleceń, aby wyłączyć przywracanie niejawne.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Opcjonalna ścieżka do pliku projektu do przywrócenia.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracyjny NuGet (*nuget.config*) do użycia w operacji przywracania.

- **`--disable-parallel`**

  Wyłącza przywracanie wielu projektów równolegle.

- **`--force`**

  Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--ignore-failed-sources`**

  Ostrzegaj tylko o źródłach, które nie powiodło się, jeśli istnieją pakiety spełniające wymagania wersji.

- **`--no-cache`**

  Określa, aby nie buforować pakietów i żądań HTTP.

- **`--no-dependencies`**

  Podczas przywracania projektu z odwołaniami do projektu (P2P) przywraca projekt główny, a nie odwołania.

- **`--packages <PACKAGES_DIRECTORY>`**

  Określa katalog przywróconych pakietów.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa czas wykonywania przywracania pakietu. Służy do przywracania pakietów dla krzepków `<RuntimeIdentifiers>` niejawnie wymienionych w tagu w pliku *csproj.* Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md). Podaj wiele identyfikatorów NIK, określając tę opcję wiele razy.

- **`-s|--source <SOURCE>`**

  Określa źródło pakietu NuGet do użycia podczas operacji przywracania. To ustawienie zastępuje wszystkie źródła określone w plikach *nuget.config.* Można podać wiele źródeł, określając tę opcję wiele razy.

- **`--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartością `minimal`domyślną jest .

- **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie). Od .NET Core 2.1.400.

## <a name="examples"></a>Przykłady

- Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet restore
  ```

- Przywracanie zależności i `app1` narzędzi dla projektu znalezionych w danej ścieżce:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, używając ścieżki pliku dostarczonej jako źródło:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, używając dwóch ścieżek plików podanych jako źródła:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu z szczegółowymi wynikami:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
