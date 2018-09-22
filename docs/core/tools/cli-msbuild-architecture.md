---
title: Architektura narzędzi wiersza polecenia programu .NET core
description: Więcej informacji na temat platformy .NET Core, narzędzia warstwy i co zmieniło się w nowszych wersjach.
author: blackdwarf
ms.date: 03/06/2017
ms.openlocfilehash: 85987129421e8ee22f7cf7fe1d44e0768d95a214
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696338"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Ogólne omówienie zmian w narzędziach platformy .NET Core

W tym dokumencie opisano zmiany związane z przenoszeniem z *project.json* do programu MSBuild i *csproj* projektu systemu z informacjami na temat zmian warstw zestaw narzędzi .NET Core i Implementacja poleceń interfejsu wiersza polecenia. Te zmiany podczas wersji platformy .NET Core SDK 1.0 i Visual Studio 2017 z 7 marca 2017 r. (zobacz [ogłoszenie](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/)), ale początkowo zostały wdrożone za pomocą wersji programu .NET Core SDK w wersji zapoznawczej 3.

## <a name="moving-away-from-projectjson"></a>Przejście od pliku project.json
Największe zmiana narzędzi dla platformy .NET Core jest bez obaw [przesuwania kursora od pliku project.json do csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) jako system projektu. Najnowsze wersje narzędzi wiersza polecenia nie obsługują *project.json* plików. Oznacza to, że nie może służyć do tworzenia, uruchamiania lub publikowania aplikacji opartych na pliku project.json i bibliotek. Aby można było używać tej wersji narzędzi, konieczne będzie migracji istniejących projektów lub Rozpocznij nowe. 

W ramach tego przeniesienia, aparat niestandardowej kompilacji, który został opracowany, aby kompilować projekty project.json został zastąpiony z aparatem dojrzałe i pełną obsługę kompilacji o nazwie [MSBuild](https://github.com/Microsoft/msbuild). Program MSBuild jest aparatem dobrze znane w społeczności platformy .NET, ponieważ ma ono kluczowych technologii od pierwszej wersji tej platformy. Oczywiście ponieważ wymagane do kompilowania aplikacji platformy .NET Core, MSBuild wydajnej i .NET Core i może być używany na dowolnej platformie, która platformy .NET Core jest uruchamiany na. Jedną z głównych obietnic programu .NET Core jest to, że stosu wieloplatformowego opracowywania aplikacji, a firma Microsoft ma upewnienie się, że to przeniesienie nie mogą przerwać działania te zobowiązania.

> [!NOTE]
> Jeśli jesteś nowym użytkownikiem programu MSBuild i chcesz dowiedzieć się więcej na ten temat, można zacząć od przeczytania [pojęcia dotyczące programu MSBuild](/visualstudio/msbuild/msbuild-concepts) artykułu. 

## <a name="the-tooling-layers"></a>Narzędzia warstwy
Wraz z przejściem od istniejącego systemu projektów, a także od utworzenia przełączników aparatu pytanie, na które następuje naturalny jest tego typu zmian zmieniaj ogólnej "warstwy" całego ekosystemu narzędzi .NET Core? Czy istnieją nowe usługi bits i składniki?

Zacznijmy od szybkiego przypomnienia informacji na temat wersji zapoznawczej 2 warstw, jak pokazano na poniższej ilustracji:

![Architektura wysokiego poziomu narzędzi w wersji zapoznawczej 2](media/cli-msbuild-architecture/p2-arch.png)

Warstwowe narzędzi jest bardzo proste. W dolnej części mamy narzędzi wiersza polecenia programu .NET Core jako podstawa. Wszystkie inne wyższego poziomu narzędzi takich jak Visual Studio lub Visual Studio Code, zależą od i zależą od interfejsu wiersza polecenia do tworzenia projektów, Przywróć zależności i tak dalej. Oznacza to, że na przykład, jeśli program Visual Studio chciał operacji przywracania, wywołałby do `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia interfejsu wiersza polecenia w pliku. 

Wraz z przejściem do nowego systemu projektu zmienia poprzedniego diagramu: 

![Architektura wysokiego poziomu zestawu SDK platformy .NET core 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Główna różnica polega na, interfejsu wiersza polecenia nie jest podstawowe warstwy już; Ta rola zostanie wypełniony przez "składnik udostępnionego zestawu SDK". Tego składnika współużytkowanego zestawu SDK jest zbiorem obiektów docelowych i skojarzonych zadań, które są odpowiedzialne za kompilowania kodu, publikując je i pakowania pakietów NuGet itp. Zestaw SDK, sama jest typu open source i jest dostępny w witrynie GitHub na [repozytorium zestawu SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> "target" to termin MSBuild wskazującą o nazwie operacji, które może wywołać program MSBuild. Jest ona zwykle połączone z co najmniej jedno zadanie, które są wykonywane logikę i element docelowy powinien zrobić. Program MSBuild obsługuje wiele gotowych elementów docelowych, takie jak `Copy` lub `Execute`; umożliwia również użytkownikom napisać własne zadania przy użyciu kodu zarządzanego i zdefiniuj cele do wykonania tych zadań. Aby uzyskać więcej informacji, zobacz [zadania programu MSBuild](/visualstudio/msbuild/msbuild-tasks). 

Wszystkie zestawy narzędzi teraz korzystać z udostępnionych składników zestawu SDK i interfejsu wiersza polecenia dołączone jego obiekty docelowe. Na przykład następnej wersji programu Visual Studio będzie nie mogą wywoływać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia, aby przywrócić zależności dla projektów .NET Core, zostanie użyty element docelowy "Przywracanie" bezpośrednio. Ponieważ te elementy docelowe programu MSBuild, umożliwia także MSBuild pierwotne można wykonać je za pomocą [dotnet msbuild](dotnet-msbuild.md) polecenia. 

### <a name="cli-commands"></a>Polecenia interfejsu wiersza polecenia
Składnika współużytkowanego zestawu SDK oznacza, że większość istniejących poleceń interfejsu wiersza polecenia zostały ponownie zaimplementowane jako cele i zadania programu MSBuild. Co to oznacza dla poleceń interfejsu wiersza polecenia i użycie zestawu narzędzi programu 

Z perspektywy użycia go nie zmienia sposób użycia interfejsu wiersza polecenia. Interfejs wiersza polecenia nadal ma podstawowe polecenia, które istnieją w wersji 2 (wersja zapoznawcza):

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Te polecenia są nadal odpowiadają Twoim oczekiwaniom (nowy projekt, skompiluj go, opublikuj ją, pakiet go i tak dalej). Większość opcji nie są zmieniane i nadal istnieją i mogą analizować ekrany pomocy poleceń (przy użyciu `dotnet <command> --help`) lub dokumentacji w tej witrynie, aby zapoznać się ze wszystkimi zmianami. 

Z perspektywy wykonywania poleceń interfejsu wiersza polecenia przyjmuje swoich parametrów i konstruowania wywołanie "pierwotne" MSBuild, będzie wymagane właściwości, a następnie uruchom wybraną docelową. Aby lepiej zilustrować to, należy wziąć pod uwagę następujące polecenie: 

   `dotnet publish -o pub -c Release`
    
To polecenie jest publikowanie aplikacji w `pub` folder przy użyciu konfiguracji "Wersja". Wewnętrznie to polecenie pobiera przetłumaczyć następujące wywołania MSBuild: 

   `dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release`

Godne uwagi wyjątkiem od tej reguły są `new` i `run` polecenia, ponieważ nie zostały one wdrożone jako elementy docelowe programu MSBuild.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
