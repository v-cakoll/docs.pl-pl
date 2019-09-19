---
title: 'Samouczek: Tworzenie rozwiązania .NET Core w macOS przy użyciu Visual Studio Code'
description: Ten dokument zawiera instrukcje i przepływ pracy służące do tworzenia rozwiązania platformy .NET Core przy użyciu Visual Studio Code.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 022afd99c6d36d7a60ac40f3f27ba073c5470bd2
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082813"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Samouczek: Tworzenie rozwiązania .NET Core w macOS przy użyciu Visual Studio Code

Ten dokument zawiera kroki i przepływ pracy służące do tworzenia rozwiązania .NET Core dla macOS. Dowiedz się, jak tworzyć projekty, testy jednostkowe, korzystać z narzędzi debugowania i dołączać biblioteki innych firm za pośrednictwem programu [NuGet](https://www.nuget.org/).

> [!NOTE]
> W tym artykule [Visual Studio Code](https://code.visualstudio.com) w programie macOS.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download). Zestaw .NET Core SDK zawiera najnowszą wersję programu .NET Core Framework i środowiska uruchomieniowego.

Zainstaluj [Visual Studio Code](https://code.visualstudio.com). W trakcie tego artykułu są również instalowane Visual Studio Code rozszerzenia, które zwiększają możliwości programistyczne programu .NET Core.

Zainstaluj rozszerzenie Visual Studio Code C# , otwierając Visual Studio Code i naciskając klawisz <kbd>F1</kbd> , aby otworzyć paletę Visual Studio Code. Wpisz **EXT Install** , aby wyświetlić listę rozszerzeń. Wybierz C# rozszerzenie. Uruchom ponownie Visual Studio Code, aby aktywować rozszerzenie. Aby uzyskać więcej informacji, zobacz [dokumentację C# rozszerzenia Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Wprowadzenie

W tym samouczku utworzysz trzy projekty: projekt biblioteki, testy dla tego projektu biblioteki oraz aplikację konsolową, która używa biblioteki. Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) tego tematu w repozytorium dotnet/Samples w witrynie GitHub. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Rozpocznij Visual Studio Code. Naciśnij klawisz <kbd>Ctrl</kbd> + <kbd>\`</kbd> (znak cudzysłowu lub nadmiaru) lub wybierz opcję **Wyświetl > zintegrowany terminal** z menu, aby otworzyć osadzony terminal w Visual Studio Code. Można nadal otworzyć powłokę zewnętrzną za pomocą Eksploratora **Otwórz w wierszu polecenia** (**Otwórz w terminalu** na komputerach Mac lub Linux), jeśli wolisz pracować poza Visual Studio Code.

Zacznij od utworzenia pliku rozwiązania, który służy jako kontener dla co najmniej jednego projektu .NET Core. W terminalu uruchom [`dotnet new`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *złot. sln* w nowym folderze o nazwie *złota*:

```console
dotnet new sln -o golden
```

Przejdź do nowego folderu *złota* i wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*Library. csproj* i *Class1.cs*, w folderze *Library* :

```console
dotnet new classlib -o library
```

Wykonaj polecenie, aby dodać nowo utworzony projekt *Library. csproj* do rozwiązania: [`dotnet sln`](../tools/dotnet-sln.md)

```console
dotnet sln add library/library.csproj
```

Plik *Library. csproj* zawiera następujące informacje:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON. Aby zapewnić obsługę serializacji i deserializacji JSON, Dodaj odwołanie do `Newtonsoft.Json` pakietu NuGet. `dotnet add` Polecenie dodaje nowe elementy do projektu. Aby dodać odwołanie do pakietu NuGet, użyj [`dotnet add package`](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:

```console
dotnet add library package Newtonsoft.Json
```

Powoduje to `Newtonsoft.Json` dodanie i jego zależności do projektu biblioteki. Alternatywnie możesz ręcznie edytować plik *Library. csproj* i dodać następujący węzeł:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Wykonaj [`dotnet restore`](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)), która przywraca zależności i tworzy folder *obj* w *bibliotece* zawierającej trzy pliki, w tym plik *Project. assets. JSON* :

```console
dotnet restore
```

W folderze *Biblioteka* Zmień nazwę pliku *Class1.cs* na *Thing.cs*. Zastąp kod następującym:

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

Klasa zawiera jedną `Get`metodę publiczną, która zwraca sumę dwóch liczb, ale robi to, konwertując sumę na ciąg, a następnie deserializacji go do liczby całkowitej. `Thing` Dzięki temu można korzystać z wielu C# nowoczesnych funkcji, takich jak [ `using static` dyrektywy](../../csharp/language-reference/keywords/using-static.md), [składowe wyrażeń](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)i [interpolacji ciągów](../../csharp/language-reference/tokens/interpolated.md).

Skompiluj bibliotekę za pomocą [`dotnet build`](../tools/dotnet-build.md) polecenia. Spowoduje to utworzenie pliku *Library. dll* w obszarze *złota/Library/bin/debug/standard 1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Utwórz projekt testu

Kompiluj projekt testowy dla biblioteki. W folderze *złota* Utwórz nowy projekt testowy:

```console
dotnet new xunit -o test-library
```

Dodaj projekt testowy do rozwiązania:

```console
dotnet sln add test-library/test-library.csproj
```

Dodaj odwołanie do projektu biblioteki utworzonej w poprzedniej sekcji, aby kompilator mógł znaleźć i użyć projektu biblioteki. [`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Alternatywnie możesz ręcznie edytować plik *test-library. csproj* i dodać następujący węzeł:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teraz, po poprawnym skonfigurowaniu zależności, należy utworzyć testy dla biblioteki. Otwórz *UnitTest1.cs* i Zastąp jego zawartość następującym kodem:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Należy pamiętać, że wartość 42 nie jest równa 19 + 23 (lub 42) podczas pierwszego utworzenia testu jednostkowego (`Assert.NotEqual`), który zakończy się niepowodzeniem. Ważnym krokiem podczas tworzenia testów jednostkowych jest utworzenie testu, aby zakończyć się niepowodzeniem raz w pierwszej kolejności w celu potwierdzenia jego logiki.

W folderze *złota* wykonaj następujące polecenia:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Te polecenia spowodują cykliczne wyszukiwanie wszystkich projektów w celu przywrócenia zależności, kompilowania ich i aktywowania modułu uruchamiającego testy xUnit w celu uruchomienia testów. Pojedynczy test kończy się niepowodzeniem, zgodnie z oczekiwaniami.

Edytuj plik *UnitTest1.cs* i Zmień potwierdzenie z `Assert.NotEqual` na. `Assert.Equal` Wykonaj następujące polecenie w folderze *złota* , aby ponownie uruchomić test, co przebiega w tym czasie:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Tworzenie aplikacji konsolowej

Aplikacja konsolowa utworzona w ramach następujących kroków przyjmuje zależność od projektu biblioteki utworzonego wcześniej i wywołuje jego metodę biblioteki podczas jej uruchamiania. Korzystając z tego wzorca rozwoju, można zobaczyć, jak utworzyć biblioteki wielokrotnego użytku dla wielu projektów.

Utwórz nową aplikację konsolową z folderu *złota* :

```console
dotnet new console -o app
```

Dodaj projekt aplikacji konsoli do rozwiązania:

```console
dotnet sln add app/app.csproj
```

Utwórz zależność od biblioteki, uruchamiając `dotnet add reference` polecenie:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Uruchom `dotnet restore` ([Zobacz Uwaga](#dotnet-restore-note)), aby przywrócić zależności trzech projektów w rozwiązaniu. Otwórz *program.cs* i Zastąp zawartość `Main` metody następującym wierszem:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Dodaj dwie `using` dyrektywy na początku pliku *program.cs* :

```csharp
using static System.Console;
using Library;
```

Wykonaj następujące `dotnet run` polecenie, aby uruchomić plik wykonywalny, `-p` gdzie opcja `dotnet run` określa projekt głównej aplikacji. Aplikacja tworzy ciąg "odpowiedź to 42".

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Debugowanie aplikacji

Ustaw punkt przerwania `WriteLine` w instrukcji `Main` w metodzie. W tym celu należy nacisnąć klawisz <kbd>F9</kbd> , gdy kursor znajduje się nad `WriteLine` wierszem lub klikając myszą w lewym marginesie w wierszu, w którym ma zostać ustawiony punkt przerwania. Czerwony okrąg zostanie wyświetlony na marginesie obok wiersza kodu. Po osiągnięciu punktu przerwania wykonywanie kodu zostanie zatrzymane *przed* wykonaniem wiersza punktu przerwania.

Otwórz kartę debuger, wybierając ikonę debugowania na pasku narzędzi Visual Studio Code, wybierając pozycję **Wyświetl > Debuguj** z paska menu lub za pomocą skrótu klawiaturowego <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:

![Visual Studio Code Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze. Aplikacja rozpoczyna wykonywanie i uruchamia do punktu przerwania, w którym jest zatrzymana. Przejdź do `Get` metody i upewnij się, że zostały przekazane poprawne argumenty. Upewnij się, że odpowiedź to 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
