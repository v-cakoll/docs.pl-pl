---
title: polecenie restore DotNet
description: Dowiedz się, jak przywrócić zależności i narzędzi specyficznych dla projektu za pomocą polecenia dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 3ddb9f679cfcab972483a4cb53ffe2b075867614
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664808"
---
# <a name="dotnet-restore"></a>DotNet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet restore` -Przywraca zależności i narzędzia do projektu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet restore` Polecenie używa NuGet, aby przywrócić zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu. Domyślnie przywrócenie zależności i narzędzia są wykonywane równolegle.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Aby przywrócić zależności, NuGet wymaga źródła danych, gdzie znajdują się pakiety. Źródła danych zwykle są udostępniane za pośrednictwem *NuGet.config* pliku konfiguracji. Domyślny plik konfiguracji znajduje się po zainstalowaniu narzędzi interfejsu wiersza polecenia. Określ dodatkowe źródła danych, tworząc własne *NuGet.config* pliku w katalogu projektu. Należy również określić dodatkowych źródeł danych dla wywołania w wierszu polecenia.

Dla zależności, należy określić, gdzie przywróconej pakiety są wprowadzane w przy użyciu operacji przywracania `--packages` argumentu. Jeśli nie zostanie określony, domyślny pakiet NuGet z pamięci podręcznej jest używany, który znajduje się w `.nuget/packages` katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych. Na przykład */home/Użytkownik1* w systemie Linux lub *C:\Users\user1* na Windows.

W przypadku narzędzi specyficznych dla projektu `dotnet restore` najpierw przywraca pakietu, w którym narzędzie jest pakowany, a następnie przywrócić narzędzia zależności, jak określono w pliku projektu.

Zachowanie `dotnet restore` polecenia jest zależna od niektórych ustawień w *Nuget.Config* pliku, jeśli jest obecny. Na przykład ustawienie `globalPackagesFolder` w *NuGet.Config* umieszcza przywróconej pakietów NuGet w określonym folderze. Jest to alternatywa do określania `--packages` opcja `dotnet restore` polecenia. Aby uzyskać więcej informacji, zobacz [odwołanie do pliku NuGet.Config](/nuget/schema/nuget-config-file).

## <a name="implicit-dotnet-restore"></a>Niejawne `dotnet restore`

Począwszy od programu .NET Core 2.0, `dotnet restore` zostanie ona uruchomiona niejawnie w razie potrzeby uruchom następujące polecenia:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

W większości przypadków nie trzeba już jawnie użyć `dotnet restore` polecenia.

Czasami może być niewygodne uruchomić `dotnet restore` niejawnie. Na przykład, niektóre zautomatyzowane systemy, takich jak systemy kompilacji, należy wywołać `dotnet restore` jawnie, aby kontrolować, podczas przywracania odbywa się tak, aby kontrolować użycie sieci. Aby zapobiec `dotnet restore` z niejawnie działa, możesz użyć `--no-restore` flagi z dowolnego z tych poleceń, aby wyłączyć niejawne przywracania.

## <a name="arguments"></a>Argumenty

`ROOT`

Opcjonalna ścieżka do pliku projektu do przywrócenia.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Plik konfiguracyjny NuGet (*NuGet.config*) na potrzeby operacji przywracania.

`--disable-parallel`

Wyłącza Przywracanie wielu projektów wykonywane równolegle.

`--force`

Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--ignore-failed-sources`

Tylko Ostrzegaj o źródłach nie powiodło się, jeśli ma pakietów spełniających wymaganie dotyczące wersji.

`--no-cache`

Określa, że nie pamięci podręcznej pakietów oraz żądania HTTP.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.

`--packages <PACKAGES_DIRECTORY>`

Określa katalog dla przywróconej pakietów.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa środowiska wykonawczego Przywracanie pakietu. Jest on używany do przywrócenia pakietów dla środowisk uruchomieniowych nie zostały jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md). Użycie tej opcji wiele razy, aby przekazać wiele identyfikatorów RID.

`-s|--source <SOURCE>`

Określa źródło pakietu NuGet ma być używany podczas operacji przywracania. Ustawienie to zastępuje wszystkie źródła określony w *NuGet.config* plików. Wiele źródeł może być udostępniane przez użycie tej opcji wiele razy.

`--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--interactive`

Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji (na przykład w celu ukończenia uwierzytelniania). Since .NET Core 2.1.400.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Plik konfiguracyjny NuGet (*NuGet.config*) na potrzeby operacji przywracania.

`--disable-parallel`

Wyłącza Przywracanie wielu projektów wykonywane równolegle.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--ignore-failed-sources`

Tylko Ostrzegaj o źródłach nie powiodło się, jeśli ma pakietów spełniających wymaganie dotyczące wersji.

`--no-cache`

Określa, że nie pamięci podręcznej pakietów oraz żądania HTTP.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.

`--packages <PACKAGES_DIRECTORY>`

Określa katalog dla przywróconej pakietów.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa środowiska wykonawczego Przywracanie pakietu. Jest on używany do przywrócenia pakietów dla środowisk uruchomieniowych nie zostały jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md). Użycie tej opcji wiele razy, aby przekazać wiele identyfikatorów RID.

`-s|--source <SOURCE>`

Określa źródło pakietu NuGet ma być używany podczas operacji przywracania. Ustawienie to zastępuje wszystkie źródła określony w *NuGet.config* plików. Wiele źródeł może być udostępniane przez użycie tej opcji wiele razy.

`--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

---

## <a name="examples"></a>Przykłady

Przywróć zależności i narzędzia dla projektów w bieżącym katalogu:

`dotnet restore`

Przywracanie zależności i narzędzia dla `app1` projekt znaleziony w podanej ścieżce:

`dotnet restore ~/projects/app1/app1.csproj`

Przywróć zależności i narzędzia dla projektów w bieżącym katalogu przy użyciu ścieżki pliku w źródle:

`dotnet restore -s c:\packages\mypackages`

Przywróć zależności i narzędzia dla projektów w bieżącym katalogu przy użyciu ścieżki dwóch plików, podana jako źródła:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Przywróć zależności i narzędzia dla projektów w bieżącym katalogu i pokazuje tylko minimalne dane wyjściowe:

`dotnet restore --verbosity minimal`
