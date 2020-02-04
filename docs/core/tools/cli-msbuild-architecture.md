---
title: Architektura narzędzi wiersza polecenia platformy .NET Core
description: Dowiedz się więcej o warstwach narzędzi programu .NET Core i zmianach w ostatnich wersjach.
ms.date: 03/06/2017
ms.openlocfilehash: 0064e7354f073be618bcf6a79962ab495927fadd
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980213"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Ogólne omówienie zmian w narzędziach .NET Core

W tym dokumencie opisano zmiany związane z przechodzeniem z pliku *Project. JSON* do programu MSBuild i system projektu *csproj* z informacjami o zmianach w warstwach narzędzi platformy .NET Core i implementacji poleceń interfejsu wiersza polecenia. Te zmiany wystąpiły z wydaniem zestaw .NET Core SDK 1,0 i Visual Studio 2017 w dniu 7 marca 2017 (zobacz [anons](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), ale początkowo zostały wdrożone w wersji zapoznawczej zestaw .NET Core SDK 3.

## <a name="moving-away-from-projectjson"></a>Przejście z pliku Project. JSON

Największą zmianą w narzędziach dla platformy .NET Core jest odmowa [od pliku Project. JSON do csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) jako system projektu. Najnowsze wersje narzędzi wiersza polecenia nie obsługują plików *Project. JSON* . Oznacza to, że nie można jej użyć do kompilowania, uruchamiania lub publikowania aplikacji i bibliotek opartych na pliku Project. JSON. Aby użyć tej wersji narzędzi, Migruj istniejące projekty lub Rozpocznij nowe.

W ramach tego przenoszenia niestandardowy aparat kompilacji, który został opracowany do kompilowania projektów Project. JSON, został zastąpiony przez kompletny i w pełni obsługujący aparat kompilacji o nazwie [MSBuild](https://github.com/Microsoft/msbuild). Program MSBuild jest dobrze znanym aparatem w społeczności programu .NET. Jest to kluczowa technologia od momentu pierwszej wersji platformy. Ponieważ musi on kompilować aplikacje platformy .NET Core, program MSBuild został portem do programu .NET Core i może być używany na dowolnej platformie, na której działa .NET Core. Jednym z głównych niesie obietnice zwiększenia .NET Core jest to, że wieloplatformowy stos programistyczny, a my upewnimy się, że to przeniesienie nie przerywa tego obietnicy.

> [!TIP]
> Jeśli jesteś nowym narzędziem MSBuild i chcesz dowiedzieć się więcej na jego temat, możesz zacząć od odczytywania artykułu [koncepcji programu MSBuild](/visualstudio/msbuild/msbuild-concepts) .

## <a name="the-tooling-layers"></a>Warstwy narzędzi

Po przejściu z istniejącego systemu projektu, a także w przypadku tworzenia przełączników aparatu, pytanie, które w sposób naturalny następuje, zmieni ogólny "warstwowy" w całym ekosystemie narzędzi platformy .NET Core? Czy istnieją nowe bity i składniki?

Zacznijmy od szybkiego odświeżacza w wersji zapoznawczej 2, jak pokazano na poniższej ilustracji:

![Wersja zapoznawcza 2 — architektura wysokiego poziomu](media/cli-msbuild-architecture/p2-arch.png)

Warstwa narzędzi jest bardzo prosta. Na dole podstawą jest interfejs wiersza polecenia platformy .NET Core. Wszystkie inne narzędzia wyższego poziomu, takie jak Visual Studio lub Visual Studio Code, są zależne i polegają na interfejsie wiersza polecenia do kompilowania projektów, przywracania zależności i tak dalej. Na przykład jeśli program Visual Studio chciał wykonać operację przywracania, wywoła on polecenie `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w interfejsie wiersza polecenia.

Po przejściu do nowego systemu projektu, poprzedni diagram zmienia się:

![Architektura wysokiego poziomu zestaw .NET Core SDK 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Główną różnicą jest to, że interfejs wiersza polecenia nie jest już podstawą. Ta rola jest teraz wypełniana przez "współużytkowany składnik zestawu SDK". Ten współużytkowany składnik zestawu SDK to zbiór elementów docelowych i skojarzonych zadań, które są odpowiedzialne za kompilowanie kodu, publikowanie go, pakowanie pakietów NuGet itd. Zestaw .NET Core SDK jest otwartym źródłem i jest dostępny w witrynie GitHub w [repozytorium zestawu SDK](https://github.com/dotnet/sdk).

> [!NOTE]
> "Target" jest terminem MSBuild, który wskazuje nazwę operacji, którą MSBuild może wywołać. Zwykle jest to powiązane z jednym lub kilkoma zadaniami, które wykonują pewną logikę, którą powinien wykonać element docelowy. Program MSBuild obsługuje wiele gotowych obiektów docelowych, takich jak `Copy` lub `Execute`; umożliwia również użytkownikom pisanie własnych zadań przy użyciu kodu zarządzanego i definiowanie celów do wykonania tych zadań. Aby uzyskać więcej informacji, zobacz [zadania programu MSBuild](/visualstudio/msbuild/msbuild-tasks).

Wszystkie zestawy narzędzi wykorzystują teraz współużytkowany składnik zestawu SDK i jego obiekty docelowe, dołączone do interfejsu wiersza polecenia. Na przykład program Visual Studio 2019 nie wywołuje polecenia `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), aby przywrócić zależności dla projektów .NET Core. Zamiast tego używa elementu docelowego "Restore" bezpośrednio. Ponieważ są to obiekty docelowe programu MSBuild, można także użyć pierwotnego programu MSBuild do wykonywania ich przy użyciu polecenia programu [dotnet MSBuild](dotnet-msbuild.md) .

### <a name="cli-commands"></a>Poleceń interfejsu wiersza polecenia

Współużytkowany składnik zestawu SDK oznacza, że większość istniejących poleceń interfejsu wiersza polecenia została zaimplementowana jako zadania i elementy docelowe programu MSBuild. Co to znaczy dla poleceń interfejsu wiersza polecenia i użycia zestawu narzędzi?

Z punktu widzenia użycia nie zmienia on sposobu korzystania z interfejsu wiersza polecenia. Interfejs wiersza polecenia ma nadal dostępne podstawowe polecenie, które istniały w wersji .NET Core 1,0 Preview 2:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Te polecenia nadal wykonują czynności, które należy wykonać (nowy projekt, kompilacja, publikowanie, pakowanie i tak dalej). Aby zapoznać się z zachowaniem, możesz zapoznać się z ekranem pomocy polecenia (za pomocą `dotnet <command> --help`) lub dokumentacją w tej witrynie.

Z perspektywy wykonywania polecenie interfejsu wiersza polecenia przyjmuje parametry i konstruuje wywołanie "RAW" MSBuild, który ustawia wymagane właściwości i uruchamia żądany element docelowy. Aby lepiej zilustrować ten sposób, weź pod uwagę następujące polecenie:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

To polecenie publikuje aplikację w folderze `pub` przy użyciu konfiguracji "Release". Wewnętrznie to polecenie jest tłumaczone na następujące wywołanie MSBuild:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Istotne wyjątki od tej reguły to `new` i `run` polecenia. Nie zostały one zaimplementowane jako cele programu MSBuild.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
