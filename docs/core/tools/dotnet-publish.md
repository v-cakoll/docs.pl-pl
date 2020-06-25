---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt .NET Core lub rozwiązanie w katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: 61cfcf06586f3ac66526de69a17b8aef3cf0c795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365586"
---
# <a name="dotnet-publish"></a>dotnet publish

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet publish`-Publikuje aplikację i jej zależności do folderu wdrożenia w systemie hostingu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a>Opis

`dotnet publish`kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu. Dane wyjściowe obejmują następujące zasoby:

- Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .
- *.deps.jsw* pliku, który zawiera wszystkie zależności projektu.
- *.runtimeconfig.jsw* pliku, który określa udostępnione środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).
- Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.

`dotnet publish`Dane wyjściowe polecenia są gotowe do wdrożenia w systemie hostingu (na przykład na serwerze, komputerze, Mac, laptopie) do wykonania. Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia. W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core. Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).

### <a name="implicit-restore"></a>Przywracanie niejawne

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a>MSBuild

`dotnet publish`Polecenie wywołuje program MSBuild, który wywołuje `Publish` element docelowy. Wszystkie parametry przesłane do `dotnet publish` są przesyłane do programu MSBuild. `-c`Parametry i są `-o` mapowane odpowiednio do programu MSBuild `Configuration` i `PublishDir` właściwości.

`dotnet publish`Polecenie akceptuje Opcje programu MSBuild, takie jak `-p` Ustawienia właściwości i `-l` definiowania rejestratora. Na przykład można ustawić właściwość programu MSBuild przy użyciu formatu: `-p:<NAME>=<VALUE>` . Można również ustawić właściwości związane z publikowaniem, odwołując się do pliku *. pubxml* , na przykład:

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

Więcej informacji zawierają następujące zasoby:

- [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Profile publikacji programu Visual Studio (. pubxml) dla wdrożenia aplikacji ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Argumenty

- **`PROJECT|SOLUTION`**

  Projekt lub rozwiązanie do opublikowania.
  
  * `PROJECT`jest ścieżką i nazwą pliku projektu [c#](csproj.md), f # lub Visual Basic lub ścieżką do katalogu, który zawiera plik projektu C#, f # lub Visual Basic. Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem.

  * `SOLUTION`jest ścieżką i nazwą pliku rozwiązania (rozszerzeniem*sln* ) lub ścieżką do katalogu zawierającego plik rozwiązania. Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem. Dostępne od wersji .NET Core 3,0 SDK.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartością domyślną dla większości projektów jest `Debug` , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md). Należy określić platformę docelową w pliku projektu.

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie *project.assets.jsw* pliku.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji. Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md). Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu.

- **`--no-build`**

  Nie kompiluje projektu przed opublikowaniem. Również niejawnie ustawia `--no-restore` flagę.

- **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

- **`--nologo`**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. Dostępne od wersji .NET Core 3,0 SDK.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę do katalogu wyjściowego.
  
  Jeśli nie zostanie określony, domyślna wartość to *[project_file_folder]./bin/[Konfiguracja]/[Framework]/Publish/* dla plików binarnych zależnych od środowiska uruchomieniowego i dla wielu platform. Wartość domyślna to *[project_file_folder]/bin/[Konfiguracja]/[Framework]/[Runtime]/Publish/* dla samodzielnego pliku wykonywalnego.

  W projekcie sieci Web, jeśli folder wyjściowy znajduje się w folderze projektu, kolejne `dotnet publish` polecenia powodują zagnieżdżone foldery wyjściowe. Na przykład, jeśli folder projektu jest typu moje *projekty*, a folder danych wyjściowych publikowanie jest w *projekcie/publikacji*i uruchamiasz `dotnet publish` dwa razy, drugi przebieg umieszcza pliki zawartości, takie jak pliki *config* i *JSON* w programie *WebProject/Publish/Publish*. Aby uniknąć zagnieżdżania folderów publikowania, określ folder publikowania, który nie znajduje się **bezpośrednio** w folderze projektu, lub wyklucz folder publikacji z projektu. Aby wykluczyć folder publikacji o nazwie *publishoutput*, Dodaj następujący element do `PropertyGroup` elementu w pliku *. csproj* :

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET Core 3. x SDK i nowsze
  
    Jeśli ścieżka względna jest określona podczas publikowania projektu, wygenerowany katalog wyjściowy jest względem bieżącego katalogu roboczego, a nie lokalizacji pliku projektu.

    Jeśli ścieżka względna zostanie określona podczas publikowania rozwiązania, wszystkie dane wyjściowe dla wszystkich projektów przechodzą do określonego folderu względem bieżącego katalogu roboczego. Aby opublikować dane wyjściowe, przejdź do oddzielnych folderów dla każdego projektu, określ ścieżkę względną przy użyciu `PublishDir` właściwości MSBuild zamiast `--output` opcji. Na przykład program `dotnet publish -p:PublishDir=.\publish` wysyła dane wyjściowe publikowania dla każdego projektu do `publish` folderu znajdującego się w folderze, który zawiera plik projektu.

  - Zestaw SDK platformy .NET Core 2. x
  
    Jeśli ścieżka względna jest określona podczas publikowania projektu, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.

    Jeśli ścieżka względna zostanie określona podczas publikowania rozwiązania, dane wyjściowe każdego projektu są umieszczane w oddzielnym folderze względem lokalizacji pliku projektu. Jeśli ścieżka bezwzględna zostanie określona podczas publikowania rozwiązania, wszystkie dane wyjściowe publikowania dla wszystkich projektów przechodzą do określonego folderu.

- **`-p:PublishReadyToRun=true`**

  Kompiluje zestawy aplikacji jako format ReadyToRun (R2R). R2R to forma kompilacji z wyprzedzeniem (AOT). Aby uzyskać więcej informacji, zobacz [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images). Dostępne od wersji .NET Core 3,0 SDK.

  Zalecamy określenie tej opcji w profilu publikowania, a nie w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [MSBuild](#msbuild).

- **`-p:PublishSingleFile=true`**

  Pakuje aplikację do pliku wykonywalnego określonego dla konkretnej platformy. Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji. Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji. Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie. Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że jest używana nowa wersja. Dostępne od wersji .NET Core 3,0 SDK.

  Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

  Zalecamy określenie tej opcji w profilu publikowania, a nie w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [MSBuild](#msbuild).

- **`-p:PublishTrimmed=true`**

  Przycina nieużywane biblioteki, aby zmniejszyć rozmiar wdrożenia aplikacji podczas publikowania samodzielnego pliku wykonywalnego. Aby uzyskać więcej informacji, zobacz sekcję [przycinanie wdrożeń samodzielnych i plików wykonywalnych](../deploying/trim-self-contained.md). Dostępne od wersji .NET Core 3,0 SDK.

  Zalecamy określenie tej opcji w profilu publikowania, a nie w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [MSBuild](#msbuild).

- **`--self-contained [true|false]`**

  Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym. Wartość domyślna to `true` Jeśli określono identyfikator środowiska uruchomieniowego, a projekt jest projektem wykonywalnym (a nie projektem biblioteki). Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).

  Jeśli ta opcja jest używana bez określenia `true` lub `false` , wartość domyślna to `true` . W takim przypadku nie należy umieszczać rozwiązania ani argumentu projektu bezpośrednio po `--self-contained` , ponieważ `true` lub `false` jest oczekiwany w tym miejscu.

- **`--no-self-contained`**

  Odpowiednik `--self-contained false` . Dostępne od wersji .NET Core 3,0 SDK.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikację dla danego środowiska uruchomieniowego. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md). Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` . Wartość domyślna to `minimal` .

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje sufiks wersji, aby zastąpić gwiazdkę ( `*` ) w polu wersja pliku projektu.

## <a name="examples"></a>Przykłady

- Utwórz [Międzyplatformowy plik binarny zależny od środowiska uruchomieniowego](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet publish
  ```

  Począwszy od zestawu SDK platformy .NET Core 3,0, w tym przykładzie tworzony jest również [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.

- Utwórz [własny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego środowiska uruchomieniowego:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Identyfikator RID musi znajdować się w pliku projektu.

- Utwórz [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Identyfikator RID musi znajdować się w pliku projektu. Ten przykład dotyczy zestawu .NET Core 3,0 SDK i nowszych wersji.

- Opublikuj projekt w bieżącym katalogu dla określonego środowiska uruchomieniowego i platformy docelowej:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publikuj określony plik projektu:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Zobacz też

- [Omówienie publikowania aplikacji .NET Core](../deploying/index.md)
- [Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md)
- [Platformy docelowe](../../standard/frameworks.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md)
- [Praca z macOS Catalina Notarization](../install/macos-notarization-issues.md)
- [Struktura katalogów opublikowanej aplikacji](/aspnet/core/hosting/directory-structure)
- [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Profile publikacji programu Visual Studio (. pubxml) dla wdrożenia aplikacji ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk. Tasks](https://aka.ms/dotnet-illink)
