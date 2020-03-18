---
title: Architektura narzędzi wiersza polecenia .NET Core
description: Dowiedz się więcej o warstwach narzędzi .NET Core i o tym, co się zmieniło w najnowszych wersjach.
ms.date: 03/06/2017
ms.openlocfilehash: fde1a0acb6af9dd65aa3466b4ea37473b2eab6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092918"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Ogólne omówienie zmian w narzędziach .NET Core

W tym dokumencie opisano zmiany związane z przejściem z *project.json* do MSBuild i systemu projektu *csproj* z informacjami na temat zmian w warstwach narzędzi .NET Core i implementacji poleceń CLI. Zmiany te wystąpiły wraz z wydaniem .NET Core SDK 1.0 i Visual Studio 2017 w dniu 7 marca 2017 r. (zobacz [ogłoszenie),](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)ale zostały początkowo wdrożone wraz z wydaniem .NET Core SDK Preview 3.

## <a name="moving-away-from-projectjson"></a>Odejście od project.json

Największą zmianą w narzędziach dla .NET Core jest z pewnością [odejście od project.json do csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) jako systemu projektowego. Najnowsze wersje narzędzi wiersza polecenia nie obsługują plików *project.json.* Oznacza to, że nie można go używać do tworzenia, uruchamiania lub publikowania aplikacji i bibliotek opartych na project.json. Aby użyć tej wersji narzędzi, należy przeprowadzić migrację istniejących projektów lub rozpocząć nowe.

W ramach tego ruchu, niestandardowy aparat kompilacji, który został opracowany do tworzenia projektów project.json został zastąpiony dojrzałym i w pełni zdolny aparat kompilacji o nazwie [MSBuild](https://github.com/Microsoft/msbuild). MSBuild jest dobrze znanym aparatem w społeczności .NET. Była to kluczowa technologia od czasu pierwszej premiery platformy. Ponieważ musi on aplikować do aplikacji .NET Core, msbuild został przeniesiony do .NET Core i może być używany na dowolnej platformie, na której działa program .NET Core. Jedną z głównych obietnic .NET Core jest to, że stosu rozwoju między platformami i upewniliśmy się, że ten ruch nie łamie tej obietnicy.

> [!TIP]
> Jeśli jesteś nowym użytkowniku MSBuild i chcesz dowiedzieć się więcej na ten temat, można rozpocząć od przeczytania [MSBuild pojęcia](/visualstudio/msbuild/msbuild-concepts) artykułu.

## <a name="the-tooling-layers"></a>Warstwy narzędziowe

Wraz ze zmianą w silniku kompilacji i odejściem od istniejącego systemu projektowego, niektóre pytania naturalnie następują. Czy którakolwiek z tych zmian zmienić ogólnej "warstw" ekosystemu narzędzi .NET Core? Czy są nowe bity i komponenty?

Zacznijmy od szybkiego odświeżania na podglądzie 2 warstw, jak pokazano na poniższym rysunku:

![Podgląd architektury wysokiego poziomu 2 narzędzi](media/cli-msbuild-architecture/p2-arch.png)

Nakładanie warstw narzędzi w wersji Preview 2 jest proste. U dołu podstawą jest .NET Core CLI. Wszystkie inne narzędzia wyższego poziomu, takie jak Visual Studio lub Visual Studio Code, zależą i polegają na identyfikatorze CLI do tworzenia projektów, przywracania zależności itd. Na przykład jeśli program Visual Studio chciał wykonać operację `dotnet restore` przywracania, będzie wywoływać do[(patrz uwaga)](#dotnet-restore-note)polecenia w wierszu polecenia wiersza polecenia.

Wraz z przejściem do nowego systemu projektu zmienia się poprzedni diagram:

![Architektura wysokiego poziomu .NET Core SDK 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

Główną różnicą jest to, że CLI nie jest już podstawową warstwą; ta rola jest teraz wypełniana przez "składnik udostępnionego sdk". Ten składnik udostępnionego zestawu SDK jest zestawem obiektów docelowych i skojarzonych zadań, które są odpowiedzialne za kompilowanie kodu, publikowanie go, pakowanie pakietów NuGet i tak dalej. Zestaw SDK .NET Core jest open source i jest dostępny w usianej usytuanej usytuanej [usytuanej usytuanej usytuanej usytuanej usytuowanej w usytuowywanie](https://github.com/dotnet/sdk).

> [!NOTE]
> "Target" jest MSBuild termin, który wskazuje na nazwie operacji, które MSBuild można wywołać. Zazwyczaj jest ona sprzężona z jednym lub więcej zadań, które wykonują niektóre logiki, które ma wykonać obiekt docelowy. MSBuild obsługuje wiele gotowych `Copy` celów, takich jak lub `Execute`; umożliwia również użytkownikom pisanie własnych zadań przy użyciu kodu zarządzanego i definiowanie obiektów docelowych do wykonania tych zadań. Aby uzyskać więcej informacji, zobacz [ZADANIA MSBuild](/visualstudio/msbuild/msbuild-tasks).

Wszystkie zestawy narzędzi teraz zużywają składnik udostępnionego zestawu SDK i jego cele, CLI włączone. Na przykład program Visual Studio 2019 `dotnet restore` nie wywoływa ć w[(zobacz uwaga)](#dotnet-restore-note)polecenia, aby przywrócić zależności dla projektów .NET Core. Zamiast tego używa "Restore" cel bezpośrednio. Ponieważ są to obiekty docelowe MSBuild, można również użyć surowego MSBuild do ich wykonania za pomocą polecenia [msbuild dotnet.](dotnet-msbuild.md)

### <a name="cli-commands"></a>Polecenia wiersza polecenia

Składnik udostępnionego zestaw SDK oznacza, że większość istniejących poleceń cli zostały ponownie zaimplementowane jako zadania i obiekty docelowe MSBuild. Co to oznacza dla poleceń wiersza polecenia i użycia zestawu narzędzi?

Z punktu widzenia użycia nie zmienia sposobu korzystania z polecenia CLI. Wiersz wiersza polecenia nadal ma podstawowe polecenia, które istniały w wersji .NET Core 1.0 Preview 2:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Polecenia te nadal robią to, czego oczekujesz (nowy projekt, skompiluj go, opublikuj go, spakowaj itd.). Możesz zapoznać się z ekranem pomocy `dotnet <command> --help`polecenia (za pomocą) lub dokumentacją w tej witrynie, aby zapoznać się z ich zachowaniem.

Z punktu widzenia wykonywania polecenia wiersza polecenia wziąć ich parametry i skonstruować wywołanie "raw" MSBuild, który ustawia potrzebne właściwości i uruchamia żądany obiekt docelowy. Aby lepiej to zilustrować, należy wziąć pod uwagę następujące polecenie:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

To polecenie publikuje aplikację `pub` w folderze przy użyciu konfiguracji "Zwolnij". Wewnętrznie to polecenie jest tłumaczone na następujące wywołanie MSBuild:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Godne uwagi wyjątki od `new` `run` tej reguły są i polecenia. Nie zostały one zaimplementowane jako cele MSBuild.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
