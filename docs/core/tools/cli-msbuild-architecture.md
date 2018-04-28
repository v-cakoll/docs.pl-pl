---
title: Architektura narzędzi wiersza polecenia programu .NET core
description: Więcej informacji na temat platformy .NET Core narzędzi warstwy i co się zmieniło w nowszych wersjach.
author: blackdwarf
ms.date: 03/06/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 909e3ba088a3eabededf008fa07a51ac7d677fa2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Ogólne omówienie zmian w narzędziach .NET Core

W tym dokumencie opisano zmiany skojarzone z przenoszenie z *project.json* dla programu MSBuild i *csproj* projektu systemu informacji o zmiany kolejności nakładania się narzędzi platformy .NET Core i wykonanie polecenia interfejsu wiersza polecenia. Te zmiany na 7 marca 2017 wystąpił w wersji 1.0 zestawu SDK programu .NET Core i Visual Studio 2017 (zobacz [anonsu](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/)), ale początkowo zostały wprowadzone w wersji programu .NET Core SDK w wersji zapoznawczej 3.

## <a name="moving-away-from-projectjson"></a>Przenoszenie od pliku project.json
Największych zmiana narzędzi dla platformy .NET Core jest oczywiście [przenieść poza project.json csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) jako system projektu. Najnowsze wersje narzędzia wiersza polecenia nie obsługują *project.json* plików. Oznacza to, że nie może służyć do kompilacji, uruchomić lub publikowania aplikacji na podstawie pliku project.json i bibliotek. Aby można było używać tej wersji narzędzi, należy przeprowadzić migrację istniejących projektów lub Rozpocznij nowe. 

W ramach tego przeniesienia, aparat niestandardowej kompilacji, który został opracowany do kompilacji projektów project.json został zastąpiony aparatem dojrzałe i w pełni współpracować kompilacji o nazwie [MSBuild](https://github.com/Microsoft/msbuild). MSBuild jest dobrze znanego aparatu w społeczności .NET, ponieważ był to kluczowa technologia od pierwszej wersji platformy. Oczywiście ponieważ należy do tworzenia aplikacji platformy .NET Core, MSBuild systemie .NET Core i można używać na dowolnej platformie .NET Core uruchamianego na. Jedną z głównych zapowiedzi .NET Core jest to, że stosu wiele platform i wprowadzono się, że to przeniesienie przerwał tego promise.

> [!NOTE]
> Jeśli dopiero zaczynasz korzystać z programu MSBuild i chcesz dowiedzieć się więcej informacji na ten temat, możesz uruchomić odczytywania [pojęcia dotyczące programu MSBuild](/visualstudio/msbuild/msbuild-concepts) artykułu. 

## <a name="the-tooling-layers"></a>Warstwy narzędzi
Wraz z przejściem od istniejącego systemu projektów, a także budowania aparat przełączników pytanie naturalnie jest zmian zmienić ogólnej "warstwy" cały ekosystem narzędzi platformy .NET Core? Istnieją nowe usługi bits i składniki?

Zacznijmy od szybkie odświeżacz na tworzenie warstw Preview 2 jak pokazano na poniższej ilustracji:

![Architektura wysokiego poziomu narzędzi Preview 2](media/cli-msbuild-architecture/p2-arch.png)

Tworzenie warstw narzędzi jest bardzo proste. W dolnej części jako podstawę zostały narzędzia wiersza polecenia programu .NET Core. Wszystkie inne, wyższego poziomu narzędzi takich jak Visual Studio lub Visual Studio Code, są zależne i zależne od interfejsu wiersza polecenia do kompilacji projektów, Przywróć zależności i tak dalej. Oznacza to, że na przykład, jeśli program Visual Studio do wykonania operacji przywracania, jego spowodowałoby wywołanie do `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w interfejsu wiersza polecenia. 

Wraz z przejściem do nowego systemu projektu poprzedni diagram zmiany: 

![Architektura wysokiego poziomu zestawu SDK programu .NET core 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Główną różnicą jest to, że interfejsu wiersza polecenia nie jest podstawowym warstwy już; Ta rola zostanie wypełniony przez "składnika współużytkowanego zestawu SDK". Ten składnik udostępnionego zestawu SDK jest zestaw elementów docelowych i skojarzone zadania, które są odpowiedzialne za kompilowanie kodu, publikowania, pakowanie pakietów NuGet itp. Sam zestaw SDK open source i jest dostępny w witrynie GitHub na [repozytorium SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> "Miejsce docelowe" to termin MSBuild wskazuje nazwanego operacji, które może wywołać program MSBuild. Jest on zwykle połączone z jednego lub więcej zadań, które wykonać niektóre logiki element docelowy powinien wykonać. MSBuild obsługuje wiele gotowych elementów docelowych, takich jak `Copy` lub `Execute`; umożliwia także użytkownikom pisać własne zadania przy użyciu kodu zarządzanego i zdefiniuj cele do wykonania tych zadań. Aby uzyskać więcej informacji, zobacz [zadania programu MSBuild](/visualstudio/msbuild/msbuild-tasks). 

Wszystkie procesami teraz korzystać z udostępnionego składnika zestawu SDK i jego elementów docelowych, interfejsu wiersza polecenia uwzględnione. Na przykład na następną wersję programu Visual Studio nie zostanie wywołany `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia do przywrócenia zależności dla platformy .NET Core projektów, zostanie użyty element docelowy "Przywracanie" bezpośrednio. Ponieważ są one docelowych elementów MSBuild, umożliwia także raw MSBuild można wykonać je za pomocą [dotnet msbuild](dotnet-msbuild.md) polecenia. 

### <a name="cli-commands"></a>Polecenia interfejsu wiersza polecenia
Składnik zestawu SDK udostępnionego oznacza, że większość istniejących poleceń interfejsu wiersza polecenia zostały ponownie zaimplementowane jako zadania programu MSBuild i obiektów docelowych. Co to znaczy polecenia interfejsu wiersza polecenia i użycie zestawu narzędzi 

Z perspektywy użycia nie zmienia sposób użycia interfejsu wiersza polecenia. Interfejsu wiersza polecenia nadal ma podstawowe polecenia, które istnieją w wersji Preview 2:

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Te polecenia są nadal oczekiwaniami (nowy projekt, skompiluj go, przed opublikowaniem, pakiet go i tak dalej). Większość opcji nie są zmieniane i nadal występują i można znaleźć ekrany pomocy poleceń (przy użyciu `dotnet <command> --help`) lub dokumentacji w tej lokacji, aby zapoznać się z wszelkie zmiany. 

Z perspektywy wykonanie polecenia interfejsu wiersza polecenia otrzymuje ich parametrów i utworzyć wywołanie "nieprzetworzonej" MSBuild, który będzie wymagane właściwości, a następnie uruchom wybrany element docelowy. Aby lepiej zilustrować ten, należy wziąć pod uwagę następujące polecenie: 

   `dotnet publish -o pub -c Release`
    
To polecenie jest publikowanie aplikacji w `pub` folderu za pomocą konfiguracji "Wersja". Wewnętrznie to polecenie pobiera przetłumaczyć następujące wywołanie MSBuild: 

   `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

Godne wyjątkiem od tej reguły są `new` i `run` polecenia, ponieważ nie zostały one wdrożone jako docelowych elementów MSBuild.

<a name="dotnet-restore-note"></a> [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]