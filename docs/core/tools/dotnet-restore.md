---
title: polecenie restore DotNet - .NET Core interfejsu wiersza polecenia
description: "Dowiedz się, jak przywrócić narzędzia specyficzne dla projektu przy użyciu polecenia przywracania dotnet i zależności."
keywords: polecenia interfejsu wiersza polecenia przywracania DotNet, interfejsu wiersza polecenia, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a>Przywracanie DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet restore`-Przywraca zależności i narzędzia do projektu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet restore` Polecenie używa NuGet, aby przywrócić zależności, a także narzędzia specyficzne dla projektu, które są określone w pliku projektu. Domyślnie przywracania zależności oraz narzędzia są wykonywane równolegle.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Aby przywrócić zależności, NuGet musi źródeł danych, w którym znajdują się pakiety. Źródła danych zwykle są udostępniane za pośrednictwem *NuGet.config* pliku konfiguracji. Domyślny plik konfiguracji jest udostępniane po zainstalowaniu narzędzi interfejsu wiersza polecenia. Określ dodatkowe źródła danych, tworząc własne *NuGet.config* pliku w katalogu projektu. Należy także określić dodatkowych źródeł danych dla wywołania w wierszu polecenia.

Dla zależności, należy określić rozmieszczenia przywróconej pakietów podczas przy użyciu operacji przywracania `--packages` argumentu. Jeśli nie jest określony, pamięć podręczną pakietów NuGet domyślnej jest używana, znajdującej się w `.nuget/packages` katalogu w katalogu macierzystego użytkownika we wszystkich systemach operacyjnych (na przykład */home/Użytkownik1* w systemie Linux lub *C:\Users\user1*  w systemie Windows).

Dla narzędzia specyficzne dla projektu `dotnet restore` najpierw przywraca pakietu, w którym narzędzie jest spakowane, a następnie przywrócić zależności narzędzia określone w pliku projektu.

Zachowanie `dotnet restore` polecenia wpływ na niektóre ustawienia w *Nuget.Config* pliku, jeśli jest obecny. Na przykład ustawienie `globalPackagesFolder` w *NuGet.Config* umieszcza przywróconej pakietów NuGet w określonym folderze. Jest to alternatywa do określania `--packages` opcja `dotnet restore` polecenia. Aby uzyskać więcej informacji, zobacz [odwołanie do pliku NuGet.Config](/nuget/schema/nuget-config-file).

## <a name="arguments"></a>Argumenty

`ROOT`

Opcjonalna ścieżka do pliku projektu do przywrócenia.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Plik konfiguracji NuGet (*NuGet.config*) do użycia dla operacji przywracania.

`--disable-parallel`

Wyłącza Przywracanie wielu projektów równolegle.

`--force`

Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie. Jest to równoważne usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--ignore-failed-sources`

Jeśli ma spełnia wymagania wersji pakietów tylko Ostrzegaj o źródła nie powiodło się.

`--no-cache`

Określa, że nie pamięci podręcznej pakietów i żądań HTTP.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.

`--packages <PACKAGES_DIRECTORY>`

Określa katalog dla przywróconych pakietów.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa środowisko uruchomieniowe dla Przywracanie pakietu. Umożliwia przywracanie pakietów dla środowisk uruchomieniowych nie są jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md). Podaj wielu identyfikatorów RID, określając tę opcję wiele razy.

`-s|--source <SOURCE>`

Określa źródło pakietu NuGet do użycia podczas operacji przywracania. Przesłania wszystkie źródła określone w *NuGet.config* plików. Wiele źródeł można podać, określając tę opcję wiele razy.

`--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Plik konfiguracji NuGet (*NuGet.config*) do użycia dla operacji przywracania.

`--disable-parallel`

Wyłącza Przywracanie wielu projektów równolegle.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--ignore-failed-sources`

Jeśli ma spełnia wymagania wersji pakietów tylko Ostrzegaj o źródła nie powiodło się.

`--no-cache`

Określa, że nie pamięci podręcznej pakietów i żądań HTTP.

`--no-dependencies`

Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.

`--packages <PACKAGES_DIRECTORY>`

Określa katalog dla przywróconych pakietów.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa środowisko uruchomieniowe dla Przywracanie pakietu. Umożliwia przywracanie pakietów dla środowisk uruchomieniowych nie są jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md). Podaj wielu identyfikatorów RID, określając tę opcję wiele razy.

`-s|--source <SOURCE>`

Określa źródło pakietu NuGet do użycia podczas operacji przywracania. Przesłania wszystkie źródła określone w *NuGet.config* plików. Wiele źródeł można podać, określając tę opcję wiele razy.

`--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

## <a name="examples"></a>Przykłady

Przywróć zależności i narzędzi dla projektu w bieżącym katalogu:

`dotnet restore`

Przywróć zależności i narzędzia do `app1` znaleziono projektu w podanej ścieżce:

`dotnet restore ~/projects/app1/app1.csproj`

Przywróć zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu ścieżki pliku w źródle:

`dotnet restore -s c:\packages\mypackages`

Przywróć zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu ścieżek plików dostarczana jako źródeł:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Przywróć zależności i narzędzi dla projektu w bieżącym katalogu i pokazuje tylko minimalne dane wyjściowe:

`dotnet restore --verbosity minimal`
