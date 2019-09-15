---
title: polecenie dotnet restore
description: Informacje o sposobie przywracania zależności i narzędzi specyficznych dla projektu przy użyciu polecenia dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 1e0e1fbf6ab5f595773a072242440e30865fed16
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969767"
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet restore`— Przywraca zależności i narzędzia projektu.

## <a name="synopsis"></a>Streszczenie

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet restore` Polecenie używa narzędzia NuGet do przywracania zależności oraz narzędzi specyficznych dla projektu, które są określone w pliku projektu. Domyślnie przywracanie zależności i narzędzi jest wykonywane równolegle.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Aby przywrócić zależności, program NuGet potrzebuje kanałów informacyjnych, w których znajdują się pakiety. Kanały informacyjne są zazwyczaj udostępniane za pośrednictwem pliku konfiguracyjnego *NuGet. config* . Domyślny plik konfiguracji jest dostarczany podczas instalacji narzędzi interfejsu wiersza polecenia. Możesz określić dodatkowe źródła danych, tworząc własny plik *NuGet. config* w katalogu projektu. W wierszu polecenia można także określić dodatkowe źródła danych dla każdego wywołania.

W przypadku zależności należy określić miejsce, w którym przywrócone pakiety są umieszczane podczas operacji `--packages` przywracania przy użyciu argumentu. Jeśli nie zostanie określony, zostanie użyta domyślna pamięć podręczna pakietów NuGet, która znajduje `.nuget/packages` się w katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych. Na przykład */home/user1* na system Linux lub *C:\Users\user1* w systemie Windows.

W przypadku narzędzi specyficznych dla projektu `dotnet restore` program najpierw przywraca pakiet, w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w pliku projektu.

### <a name="nugetconfig-differences"></a>różnice NuGet. config

Zachowanie `dotnet restore` polecenia ma wpływ na ustawienia w pliku *NuGet. config* , jeśli jest obecny. Na przykład ustawienie `globalPackagesFolder` w *pliku NuGet. config* powoduje umieszczenie przywróconych pakietów NuGet w określonym folderze. Jest to alternatywa dla określenia `--packages` opcji `dotnet restore` polecenia. Aby uzyskać więcej informacji, zobacz [Dokumentacja NuGet. config](/nuget/schema/nuget-config-file).

Istnieją trzy określone ustawienia, które `dotnet restore` ignorują:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Przekierowania powiązań nie działają z `<PackageReference>` elementami i .NET Core obsługuje `<PackageReference>` tylko elementy dla pakietów NuGet.

- [Narzędzie](/nuget/schema/nuget-config-file#solution-section)

  To ustawienie dotyczy programu Visual Studio i nie ma zastosowania do programu .NET Core. Platforma .NET Core nie używa `packages.config` pliku, a zamiast `<PackageReference>` tego używa elementów dla pakietów NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów przez wiele platform.

## <a name="implicit-dotnet-restore"></a>Konwersja`dotnet restore`

Począwszy od platformy .NET Core 2,0 `dotnet restore` , jest uruchamiany niejawnie, jeśli to konieczne, w przypadku wydawania następujących poleceń:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

W większości przypadków nie trzeba już jawnie używać `dotnet restore` polecenia.

Czasami może być niewygodne uruchamianie `dotnet restore` niejawnie. Na przykład niektóre zautomatyzowane systemy, takie jak systemy kompilacji, muszą jawnie wywołać `dotnet restore` , aby określić, kiedy następuje przywracanie, aby można było kontrolować użycie sieci. Aby zapobiec `dotnet restore` uruchamianiu niejawnie, można `--no-restore` użyć flagi z dowolnym z tych poleceń, aby wyłączyć Przywracanie niejawne.

## <a name="arguments"></a>Argumenty

`ROOT`

Opcjonalna ścieżka do pliku projektu do przywrócenia.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.

`--disable-parallel`

Wyłącza przywracanie równolegle wielu projektów.

`--force`

Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--ignore-failed-sources`

Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.

`--no-cache`

Określa, aby nie buforować pakietów i żądań HTTP.

`--no-dependencies`

W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

`--packages <PACKAGES_DIRECTORY>`

Określa katalog przywróconych pakietów.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa środowisko uruchomieniowe przywracania pakietu. Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są `<RuntimeIdentifiers>` jawnie wymienione w tagu w pliku *. csproj* . Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.

`-s|--source <SOURCE>`

Określa źródło pakietu NuGet do użycia podczas operacji przywracania. To ustawienie zastępuje wszystkie źródła określone w plikach *NuGet. config* . Można podać wiele źródeł, określając tę opcję wiele razy.

`--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

`--interactive`

Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania). Since .NET Core 2.1.400.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.

`--disable-parallel`

Wyłącza przywracanie równolegle wielu projektów.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--ignore-failed-sources`

Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.

`--no-cache`

Określa, aby nie buforować pakietów i żądań HTTP.

`--no-dependencies`

W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.

`--packages <PACKAGES_DIRECTORY>`

Określa katalog przywróconych pakietów.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa środowisko uruchomieniowe przywracania pakietu. Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są `<RuntimeIdentifiers>` jawnie wymienione w tagu w pliku *. csproj* . Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.

`-s|--source <SOURCE>`

Określa źródło pakietu NuGet do użycia podczas operacji przywracania. Zastępuje wszystkie źródła określone w plikach *NuGet. config* , efektywnie odczytując plik *NuGet. config* `<packageSource>` tak, jakby nie było tam elementu. Można podać wiele źródeł, określając tę opcję wiele razy.

`--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

---

## <a name="examples"></a>Przykłady

Przywróć zależności i narzędzia dla projektu w bieżącym katalogu:

`dotnet restore`

Przywróć zależności i narzędzia dla `app1` projektu Znalezione w danej ścieżce:

`dotnet restore ~/projects/app1/app1.csproj`

Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku dostarczonej jako Źródło:

`dotnet restore -s c:\packages\mypackages`

Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Przywróć zależności i narzędzia dla projektu w bieżącym katalogu i Wyświetlaj tylko minimalne dane wyjściowe:

`dotnet restore --verbosity minimal`
