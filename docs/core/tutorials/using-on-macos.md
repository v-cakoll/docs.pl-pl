---
title: 'Samouczek: Tworzenie rozwiązania .NET Core w macOS przy użyciu Visual Studio Code'
description: Ten dokument zawiera instrukcje i przepływ pracy służące do tworzenia rozwiązania platformy .NET Core przy użyciu Visual Studio Code.
ms.date: 12/19/2019
ms.openlocfilehash: 4dc44a0aa155dca3c106a7da68cf100ef644b58b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715306"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Samouczek: Tworzenie rozwiązania .NET Core w macOS przy użyciu Visual Studio Code

Ten dokument zawiera kroki i przepływ pracy służące do tworzenia rozwiązania .NET Core dla macOS. Dowiedz się, jak tworzyć projekty, testy jednostkowe, korzystać z narzędzi debugowania i dołączać biblioteki innych firm za pośrednictwem programu [NuGet](https://www.nuget.org/).

> [!NOTE]
> W tym artykule [Visual Studio Code](https://code.visualstudio.com) w programie macOS.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download). Zestaw .NET Core SDK zawiera najnowszą wersję programu .NET Core Framework i środowiska uruchomieniowego.

Zainstalowanie programu [Visual Studio Code](https://code.visualstudio.com). W trakcie tego artykułu są również instalowane Visual Studio Code rozszerzenia, które zwiększają możliwości programistyczne programu .NET Core.

Zainstaluj rozszerzenie Visual Studio Code C# , otwierając Visual Studio Code i naciskając klawisz <kbd>Fn</kbd>+<kbd>F1</kbd> , aby otworzyć paletę Visual Studio Code. Wpisz **EXT Install** , aby wyświetlić listę rozszerzeń. Wybierz C# rozszerzenie. Uruchom ponownie Visual Studio Code, aby aktywować rozszerzenie. Aby uzyskać więcej informacji, zobacz [dokumentację C# rozszerzenia Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Wprowadzenie

W tym samouczku utworzysz trzy projekty: projekt biblioteki, testy dla tego projektu biblioteki oraz aplikację konsolową, która używa biblioteki. Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) tego artykułu w repozytorium dotnet/Samples w witrynie GitHub. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Uruchom program Visual Studio Code. Naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>\`</kbd> (znak cudzysłowu lub znaku nadmiarowy) lub wybierz pozycję **Wyświetl Terminal >** z menu, aby otworzyć osadzony terminal w Visual Studio Code. Można nadal otworzyć powłokę zewnętrzną za pomocą Eksploratora **Otwórz w wierszu polecenia** (**Otwórz w terminalu** na komputerach Mac lub Linux), jeśli wolisz pracować poza Visual Studio Code.

Zacznij od utworzenia pliku rozwiązania, który służy jako kontener dla co najmniej jednego projektu .NET Core. W terminalu uruchom polecenie [`dotnet new`](../tools/dotnet-new.md) , aby utworzyć nowe rozwiązanie *złot. sln* w nowym folderze o nazwie *złota*:

```dotnetcli
dotnet new sln -o golden
```

Przejdź do nowego folderu *złota* i wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*Library. csproj* i *Class1.cs*, w folderze *Library* :

```dotnetcli
dotnet new classlib -o library
```

Wykonaj [`dotnet sln`](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzony projekt *Library. csproj* do rozwiązania:

```dotnetcli
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

Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON. Aby zapewnić obsługę serializacji i deserializacji JSON, Dodaj odwołanie do pakietu NuGet `Newtonsoft.Json`. Polecenie `dotnet add` dodaje nowe elementy do projektu. Aby dodać odwołanie do pakietu NuGet, użyj polecenia [`dotnet add package`](../tools/dotnet-add-package.md) i określ nazwę pakietu:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Spowoduje to dodanie `Newtonsoft.Json` i jego zależności do projektu biblioteki. Alternatywnie możesz ręcznie edytować plik *Library. csproj* i dodać następujący węzeł:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Wykonaj [`dotnet restore`](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)), która przywraca zależności i tworzy folder *obj* wewnątrz *biblioteki* zawierającej trzy pliki, w tym plik *Project. assets. JSON* :

```dotnetcli
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

Klasa `Thing` zawiera jedną metodę publiczną, `Get`, która zwraca sumę dwóch liczb, ale robi to, konwertując sumę na ciąg, a następnie deserializacji ją na liczbę całkowitą. Dzięki temu można korzystać z wielu C# nowoczesnych funkcji, takich jak [dyrektywy`using static`](../../csharp/language-reference/keywords/using-static.md), [składowe wyrażeń](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)i [interpolacji ciągów](../../csharp/language-reference/tokens/interpolated.md).

Skompiluj bibliotekę za pomocą polecenia [`dotnet build`](../tools/dotnet-build.md) . Spowoduje to utworzenie pliku *Library. dll* w obszarze *złota/Library/bin/debug/standard 1.4*:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Utwórz projekt testu

Kompiluj projekt testowy dla biblioteki. W folderze *złota* Utwórz nowy projekt testowy:

```dotnetcli
dotnet new xunit -o test-library
```

Dodaj projekt testowy do rozwiązania:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Dodaj odwołanie do projektu biblioteki utworzonej w poprzedniej sekcji, aby kompilator mógł znaleźć i użyć projektu biblioteki. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
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

Należy pamiętać, że wartość 42 nie jest równa 19 + 23 (lub 42) podczas pierwszego utworzenia testu jednostkowego (`Assert.NotEqual`), co zakończy się niepowodzeniem. Ważnym krokiem podczas tworzenia testów jednostkowych jest utworzenie testu, aby zakończyć się niepowodzeniem raz w pierwszej kolejności w celu potwierdzenia jego logiki.

W folderze *złota* wykonaj następujące polecenia:

```dotnetcli
dotnet restore 
dotnet test test-library/test-library.csproj
```

Te polecenia spowodują cykliczne wyszukiwanie wszystkich projektów w celu przywrócenia zależności, kompilowania ich i aktywowania modułu uruchamiającego testy xUnit w celu uruchomienia testów. Pojedynczy test kończy się niepowodzeniem, zgodnie z oczekiwaniami.

Edytuj plik *UnitTest1.cs* i Zmień potwierdzenie z `Assert.NotEqual` na `Assert.Equal`. Wykonaj następujące polecenie w folderze *złota* , aby ponownie uruchomić test, co przebiega w tym czasie:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Tworzenie aplikacji konsolowej

Aplikacja konsolowa utworzona w ramach następujących kroków przyjmuje zależność od projektu biblioteki utworzonego wcześniej i wywołuje jego metodę biblioteki podczas jej uruchamiania. Korzystając z tego wzorca rozwoju, można zobaczyć, jak utworzyć biblioteki wielokrotnego użytku dla wielu projektów.

Utwórz nową aplikację konsolową z folderu *złota* :

```dotnetcli
dotnet new console -o app
```

Dodaj projekt aplikacji konsoli do rozwiązania:

```dotnetcli
dotnet sln add app/app.csproj
```

Utwórz zależność od biblioteki, uruchamiając `dotnet add reference` polecenie:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Uruchom `dotnet restore` ([Zobacz Uwaga](#dotnet-restore-note)), aby przywrócić zależności trzech projektów w rozwiązaniu. Otwórz *program.cs* i Zastąp zawartość metody `Main` następującym wierszem:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Dodaj dwie dyrektywy `using` na początku pliku *program.cs* :

```csharp
using static System.Console;
using Library;
```

Wykonaj następujące `dotnet run` polecenie, aby uruchomić plik wykonywalny, gdzie opcja `-p` `dotnet run` określa projekt głównej aplikacji. Aplikacja tworzy ciąg "odpowiedź to 42".

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Debugowanie aplikacji

Ustaw punkt przerwania w instrukcji `WriteLine` w metodzie `Main`. W tym celu należy nacisnąć klawisz <kbd>Fn</kbd>+<kbd>F9</kbd> , gdy kursor znajduje się nad linią `WriteLine` lub klikając myszą w lewym marginesie w wierszu, w którym ma zostać ustawiony punkt przerwania. Czerwony okrąg zostanie wyświetlony na marginesie obok wiersza kodu. Po osiągnięciu punktu przerwania wykonywanie kodu zostanie zatrzymane *przed* wykonaniem wiersza punktu przerwania.

Otwórz kartę debuger, wybierając ikonę debugowania na pasku narzędzi Visual Studio Code, wybierając pozycję **wyświetl > Debuguj** z paska menu lub przy użyciu <kbd>polecenia</kbd> skrótu klawiaturowego+<kbd>SHIFT</kbd>+<kbd>D</kbd>:

![Visual Studio Code Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze. Utworzono projekt testowy i aplikację w tym projekcie. Debuger monituje o projekt, który chcesz uruchomić. Wybierz projekt "aplikacja". Aplikacja rozpoczyna wykonywanie i uruchamia do punktu przerwania, w którym jest zatrzymana. Przejdź do metody `Get` i upewnij się, że zostały przekazane poprawne argumenty. Upewnij się, że odpowiedź to 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
