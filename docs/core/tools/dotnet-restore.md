---
title: polecenie dotnet restore
description: Informacje o sposobie przywracania zależności i narzędzi specyficznych dla projektu przy użyciu polecenia dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: c221e8a34e844d0ad0482d2bb4aa6e1c795555ca
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626063"
---
# <a name="dotnet-restore"></a>dotnet restore

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet restore` — przywraca zależności i narzędzia projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet restore` używa narzędzia NuGet do przywracania zależności oraz narzędzi specyficznych dla projektu, które są określone w pliku projektu. Domyślnie przywracanie zależności i narzędzi jest wykonywane równolegle.

Aby przywrócić zależności, program NuGet potrzebuje kanałów informacyjnych, w których znajdują się pakiety. Kanały informacyjne są zazwyczaj udostępniane za pośrednictwem pliku konfiguracyjnego *NuGet. config* . Domyślny plik konfiguracji jest dostarczany, gdy zainstalowano zestaw .NET Core SDK. Możesz określić dodatkowe źródła danych, tworząc własny plik *NuGet. config* w katalogu projektu. Można zastąpić źródła danych *NuGet. config* opcją-`-s`.

W przypadku zależności należy określić miejsce, w którym przywrócone pakiety są umieszczane podczas operacji przywracania przy użyciu argumentu `--packages`. Jeśli nie zostanie określony, zostanie użyta domyślna pamięć podręczna pakietów NuGet, która znajduje się w katalogu `.nuget/packages` w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych. Na przykład */home/user1* na system Linux lub *C:\Users\user1* w systemie Windows.

W przypadku narzędzi specyficznych dla projektu `dotnet restore` najpierw przywraca pakiet, w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w pliku projektu.

### <a name="nugetconfig-differences"></a>różnice NuGet. config

Na zachowanie polecenia `dotnet restore` są zależne od ustawień w pliku *NuGet. config* (jeśli istnieją). Na przykład ustawienie `globalPackagesFolder` w *pliku NuGet. config* powoduje umieszczenie przywróconych pakietów NuGet w określonym folderze. Jest to alternatywa dla określenia opcji `--packages` na `dotnet restore` polecenie. Aby uzyskać więcej informacji, zobacz [Dokumentacja NuGet. config](/nuget/schema/nuget-config-file).

Istnieją trzy określone ustawienia, które `dotnet restore` ignoruje:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Przekierowania powiązań nie współpracują z `<PackageReference>` elementami, a platforma .NET Core obsługuje tylko `<PackageReference>` elementów dla pakietów NuGet.

- [Narzędzie](/nuget/schema/nuget-config-file#solution-section)

  To ustawienie dotyczy programu Visual Studio i nie ma zastosowania do programu .NET Core. Platforma .NET Core nie używa pliku `packages.config` i zamiast tego używa elementów `<PackageReference>` dla pakietów NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów przez wiele platform.

## <a name="implicit-restore"></a>Przywracanie niejawne

Polecenie `dotnet restore` jest uruchamiane niejawnie w razie potrzeby po uruchomieniu następujących poleceń:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.

Czasami może być niewygodne uruchamianie `dotnet restore` niejawnie. Na przykład niektóre zautomatyzowane systemy, takie jak systemy kompilacji, muszą wywoływać `dotnet restore` jawnie, aby określić, kiedy następuje przywracanie, aby umożliwić im sterowanie użyciem sieci. Aby zapobiec niejawnemu uruchamianiu `dotnet restore`, można użyć flagi `--no-restore` z dowolnym z tych poleceń, aby wyłączyć Przywracanie niejawne.

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

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--ignore-failed-sources`**

  Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.

- **`--no-cache`**

  Określa, aby nie buforować pakietów i żądań HTTP.

- **`--no-dependencies`**

  W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

- **`--packages <PACKAGES_DIRECTORY>`**

  Określa katalog przywróconych pakietów.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa środowisko uruchomieniowe przywracania pakietu. Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w tagu `<RuntimeIdentifiers>` w pliku *csproj* . Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.

- **`-s|--source <SOURCE>`**

  Określa źródło pakietu NuGet do użycia podczas operacji przywracania. To ustawienie zastępuje wszystkie źródła określone w plikach *NuGet. config* . Można podać wiele źródeł, określając tę opcję wiele razy.

- **`--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `minimal`.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania). Since .NET Core 2.1.400.

## <a name="examples"></a>Przykłady

- Przywróć zależności i narzędzia dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet restore
  ```

- Przywróć zależności i narzędzia dla projektu `app1` Znalezione w danej ścieżce:

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
