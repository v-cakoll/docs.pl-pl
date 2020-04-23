---
title: Architektura narzędzi wiersza polecenia .NET Core
description: Dowiedz się więcej o warstwach narzędziowych .NET Core i o tym, co zmieniło się w najnowszych wersjach.
ms.date: 03/06/2017
ms.openlocfilehash: e1a9fe59225c17d54f6e7213d2b3c3fa70ee58e0
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102882"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Omówienie zmian na wysokim poziomie w narzędziach .NET Core

W tym dokumencie opisano zmiany związane z przejściem z *project.json* do MSBuild i systemu projektu *csproj* z informacjami na temat zmian w nakładaniu warstw narzędzi .NET Core i implementacji poleceń interfejsu wiersza polecenia. Zmiany te wystąpiły wraz z wydaniem .NET Core SDK 1.0 i Visual Studio 2017 w dniu 7 marca 2017 r. (zobacz [anons),](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)ale zostały początkowo zaimplementowane wraz z wydaniem programu .NET Core SDK Preview 3.

## <a name="moving-away-from-projectjson"></a>Odejście od project.json

Największą zmianą w narzędziu dla .NET Core jest z pewnością [odejście od project.json do csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) jako systemu projektu. Najnowsze wersje narzędzi wiersza polecenia nie obsługują plików *project.json.* Oznacza to, że nie można używać do tworzenia, uruchamiania lub publikowania aplikacji i bibliotek opartych na project.json. Aby użyć tej wersji narzędzi, należy przeprowadzić migrację istniejących projektów lub rozpocząć nowe.

W ramach tego ruchu, niestandardowy silnik kompilacji, który został opracowany do tworzenia project.json projektów został zastąpiony dojrzałym i w pełni zdolny silnik kompilacji o nazwie [MSBuild](https://github.com/Microsoft/msbuild). MSBuild jest dobrze znanym aparatem w społeczności .NET. Jest to kluczowa technologia od czasu pierwszego wydania platformy. Ponieważ musi tworzyć aplikacje .NET Core, MSBuild został przeniesiony do platformy .NET Core i może być używany na dowolnej platformie, na którą działa program .NET Core. Jedną z głównych obietnic .NET Core jest stos rozwoju między platformami i upewniliśmy się, że ten ruch nie złamie tej obietnicy.

> [!TIP]
> Jeśli jesteś nowy w MSBuild i chcesz dowiedzieć się więcej na ten temat, można rozpocząć od przeczytania [msbuild pojęcia](/visualstudio/msbuild/msbuild-concepts) artykułu.

## <a name="the-tooling-layers"></a>Warstwy narzędziowe

Wraz ze zmianą w silniku kompilacji i odejściem od istniejącego systemu projektów, oczywiście pojawiają się pewne pytania. Czy któraś z tych zmian zmienia ogólne "warstwowanie" ekosystemu narzędzi .NET Core? Czy są nowe bity i komponenty?

Zacznijmy od szybkiego odświeżania warstw w podglądzie 2, jak pokazano na poniższym rysunku:

![Podgląd 2 narzędzi architektury wysokiego poziomu](media/cli-msbuild-architecture/p2-arch.png)

Nakładanie warstw narzędzi w wersji Preview 2 jest proste. Na dole podstawą jest .NET Core CLI. Wszystkie inne narzędzia wyższego poziomu, takie jak Visual Studio lub Visual Studio Code, zależą i polegają na wierszu polecenia do tworzenia projektów, przywracania zależności i tak dalej. Na przykład jeśli visual studio chciał wykonać operację przywracania, to wywołanie `dotnet restore` polecenia w wierszu polecenia.

Wraz z przejściem do nowego systemu projektu zmienia się poprzedni diagram:

![Architektura wysokiego poziomu .NET Core SDK 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Główną różnicą jest to, że CLI nie jest już warstwą fundamentalną; ta rola jest teraz wypełniona przez "składnik udostępnionego SDK". Ten składnik zestawu SDK udostępnionego jest zestaw obiektów docelowych i skojarzonych zadań, które są odpowiedzialne za kompilacji kodu, publikowania go, pakowania pakietów NuGet i tak dalej. .NET Core SDK jest open-source i jest dostępny na GitHub na [repozytorium SDK](https://github.com/dotnet/sdk).

> [!NOTE]
> "Target" to termin MSBuild, który wskazuje nazwaną operację, którą może wywołać msbuild. Zwykle jest w połączeniu z jednym lub więcej zadań, które wykonują niektóre logiki, które ma zrobić. MSBuild obsługuje wiele gotowych `Copy` celów, takich jak lub `Execute`; umożliwia również użytkownikom pisanie własnych zadań przy użyciu kodu zarządzanego i definiowanie obiektów docelowych do wykonywania tych zadań. Aby uzyskać więcej informacji, zobacz [Zadania MSBuild](/visualstudio/msbuild/msbuild-tasks).

Wszystkie zestawy narzędzi zużywają teraz składnik zestawu SDK udostępnionego i jego obiekty docelowe, w tym interfejsu wiersza polecenia. Na przykład visual studio 2019 nie `dotnet restore` wywołanie polecenia, aby przywrócić zależności dla projektów .NET Core. Zamiast tego używa bezpośrednio obiektu docelowego "Przywróć". Ponieważ są to obiekty docelowe MSBuild, można również użyć nieprzetworzonego MSBuild do ich wykonania za pomocą polecenia [dotnet msbuild.](dotnet-msbuild.md)

### <a name="cli-commands"></a>Polecenia interfejsu wiersza polecenia

Składnik udostępnionego zestawie SDK oznacza, że większość istniejących poleceń interfejsu wiersza polecenia została ponownie zaimplementowana jako zadania i obiekty docelowe MSBuild. Co to oznacza dla poleceń interfejsu wiersza polecenia i użycia zestawu narzędzi?

Z punktu widzenia użycia nie zmienia to sposobu korzystania z interfejsu wiersza polecenia. Interfejs wiersza polecenia nadal ma podstawowe polecenia, które istniały w wersji .NET Core 1.0 Preview 2:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Te polecenia nadal robią to, czego oczekujesz od nich (nowy projekt, zbuduj go, opublikuj, spakowaj i tak dalej). Możesz zapoznać się z ekranem pomocy `dotnet <command> --help`polecenia (za pomocą) lub dokumentacją na tej stronie, aby zapoznać się z ich zachowaniem.

Z punktu widzenia wykonania polecenia interfejsu wiersza polecenia przyjmują swoje parametry i konstruują wywołanie "nieprzetworzonego" MSBuild, który ustawia potrzebne właściwości i uruchamia żądany obiekt docelowy. Aby lepiej to zilustrować, należy wziąć pod uwagę następujące polecenie:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

To polecenie publikuje aplikację `pub` w folderze przy użyciu konfiguracji "Zwolnij". Wewnętrznie to polecenie zostanie przetłumaczone na następujące wywołanie MSBuild:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Godnymi uwagi wyjątkami `new` od `run` tej reguły są polecenia i polecenia. Nie zostały one zaimplementowane jako obiekty docelowe MSBuild.

### <a name="implicit-restore"></a>Niejawne przywracanie

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
