---
title: Wprowadzenie do platformy .NET Core na macOS
description: Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie .NET Core za pomocą programu Visual Studio Code.
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.openlocfilehash: 5a4b2734137f59b29535f302dd17fb94329d676f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218289"
---
# <a name="getting-started-with-net-core-on-macos"></a>Wprowadzenie do platformy .NET Core na macOS

Ten dokument zawiera kroki i przepływu pracy, aby utworzyć rozwiązanie .NET Core macOS. Informacje o sposobie tworzenia projektów, testy jednostkowe, użyj narzędzi debugowania i dołączyć do nich bibliotek innej firmy za pośrednictwem [NuGet](https://www.nuget.org/).

> [!NOTE]
> W tym artykule wykorzystano [Visual Studio Code](http://code.visualstudio.com) na macOS.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj [.NET Core SDK](https://www.microsoft.com/net/core). .NET Core SDK zawiera najnowszą wersję platformy .NET Core framework i środowiska wykonawczego.

Zainstaluj [kodu programu Visual Studio](http://code.visualstudio.com). W trakcie tego artykułu również zainstalować Visual Studio Code wystąpić rozszerzeń zwiększających programowania .NET Core.

Zainstaluj rozszerzenie programu Visual Studio kodu C# otwierania Visual Studio Code i naciskając klawisz <kbd>F1</kbd> można otworzyć z programu Visual Studio Code palety. Typ **zainstalować ext** Lista rozszerzeń. Wybierz rozszerzenia C#. Ponownie uruchom Visual Studio Code aktywować rozszerzenia. Aby uzyskać więcej informacji, zobacz [dokumentacji programu Visual Studio C# rozszerzeniem kodu](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="getting-started"></a>Wprowadzenie

W tym samouczku, Utwórz trzy projekty: projektu biblioteki testów dla tego projektu biblioteki, a aplikacja konsolowa, która wykorzystuje biblioteki. Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) dla tego tematu w repozytorium dotnet/próbek w witrynie GitHub. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Uruchom kod programu Visual Studio. Naciśnij klawisz <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak znakami odwróconego lub backtick) lub wybierz **Widok > zintegrowane Terminal** z menu, aby otworzyć osadzonych Terminal w programie Visual Studio Code. Nadal można otworzyć zewnętrznego powłoki Eksploratora **Otwórz w wierszu polecenia** polecenia (**Otwórz w terminalu** na Mac lub Linux), jeśli wolisz pracować poza Visual Studio Code.

Rozpocznij od utworzenia pliku rozwiązania, która służy jako kontener dla jednego lub więcej projektów .NET Core. W terminalu, Utwórz *złotego* folder i otwórz folder. Ten folder jest katalogiem głównym rozwiązania. Uruchom [ `dotnet new` ](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *golden.sln*:

```console
dotnet new sln
```

Z *złotego* folderu, uruchom następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*library.csproj* i *Class1.cs*, w *biblioteki* folderu:

```console
dotnet new classlib -o library
```

Wykonanie [ `dotnet sln` ](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzonego *library.csproj* projektu do rozwiązania:

```console
dotnet sln add library/library.csproj
```

*Library.csproj* pliku zawiera następujące informacje:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON. Aby obsługiwać JSON serializacji i deserializacji, Dodaj odwołanie do `Newtonsoft.Json` pakietu NuGet. `dotnet add` Polecenie dodaje nowe elementy do projektu. Aby dodać odwołanie do pakietu NuGet, użyj [ `dotnet add package` ](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:

```console
dotnet add library package Newtonsoft.Json
```

Spowoduje to dodanie `Newtonsoft.Json` i jego zależności do projektu biblioteki. Możesz też ręcznie zmodyfikować *library.csproj* plik i dodać następującego węzła:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Wykonanie [ `dotnet restore` ](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)) która przywraca zależności i tworzy *obj* folder wewnątrz *biblioteki* z trzema pliki w nim, w tym *project.assets.json* pliku:

```console
dotnet restore
```

W *biblioteki* folder, Zmień nazwę pliku *Class1.cs* do *Thing.cs*. Zastąp kod z następujących czynności:

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

`Thing` Klasa zawiera jedną metodę publiczne, `Get`, która zwraca sumę dwóch numery, ale wykonuje konwertowanie Suma na ciąg, a następnie podczas deserializacji do liczby całkowitej. To sprawia, że użycie wiele nowoczesnych C# funkcji, takich jak [ `using static` dyrektywy](../../csharp/language-reference/keywords/using-static.md), [zabudowanych wyrażenia elementów członkowskich](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), i [ciągu interpolacji](../../csharp/language-reference/tokens/interpolated.md).

Tworzenie biblioteki z [ `dotnet build` ](../tools/dotnet-build.md) polecenia. Spowoduje to utworzenie *library.dll* plików w obszarze *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Tworzenie projektu testu

Tworzenie projektu testu w bibliotece. Z *złotego* folderu, Utwórz nowy projekt testu:

```console
dotnet new xunit -o test-library
```

Dodaj projekt testowy do rozwiązania:

```console
dotnet sln add test-library/test-library.csproj
```

Dodaj odwołanie do biblioteki, utworzony w poprzedniej sekcji, aby kompilator można znaleźć i używać projektu biblioteki projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Możesz też ręcznie zmodyfikować *library.csproj testu* plik i dodać następującego węzła:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teraz, zależności zostały poprawnie skonfigurowane, należy utworzyć testów w bibliotece. Otwórz *UnitTest1.cs* i zastąp jego zawartość następującym kodem:

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

Należy zwrócić uwagę assert wartość 42 nie jest równa 19 + 23 (lub 42) po pierwszym utworzeniu testu jednostkowego (`Assert.NotEqual`), który zakończy się niepowodzeniem. Ważnym krokiem podczas tworzenia testów jednostkowych jest tworzenie testu Niepowodzenie po raz pierwszy potwierdzić swojej logiki.

Z *złotego* folder, wykonaj następujące polecenia:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Te polecenia zostaną Znajdź rekursywnie się, że wszystkie projekty, aby przywrócić zależności, je kompilować i aktywować xUnit test runner, aby uruchomić testy. Pojedynczy test zakończy się niepowodzeniem, zgodnie z oczekiwaniami.

Edytuj *UnitTest1.cs* plików i zmień potwierdzenia z `Assert.NotEqual` do `Assert.Equal`. Uruchom następujące polecenie z *złotego* folderu ponowne uruchomienie testu, które przechodzą w tym czasie:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Tworzenie aplikacji konsoli

Aplikacja konsoli tworzonych przez następujące kroki przejmuje zależności projektu biblioteki utworzony wcześniej i wywołuje metodę jego biblioteki, gdy jest uruchamiany. Przy użyciu tego wzorca programowanie, zobaczysz, jak utworzyć wielokrotnego użytku biblioteki dla wielu projektów.

Utwórz nową aplikację konsoli z *złotego* folderu:

```console
dotnet new console -o app
```

Dodaj projekt aplikacji konsoli do rozwiązania:

```console
dotnet sln add app/app.csproj
```

Utwórz zależność biblioteki, uruchamiając `dotnet add reference` polecenia:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do przywrócenia zależności trzy projekty w rozwiązaniu. Otwórz *Program.cs* i Zastąp zawartość `Main` metody o następujący wiersz:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Dodaj dwa `using` dyrektywy na początku *Program.cs* pliku:

```csharp
using static System.Console;
using Library;
```

Wykonaj następujące czynności, `dotnet run` polecenie do uruchomienia pliku wykonywalnego, gdzie `-p` opcji w celu `dotnet run` określa projekt do aplikacji głównej. Aplikacja generuje ciąg "odpowiedź jest 42".

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Debugowanie aplikacji

Ustaw punkt przerwania w `WriteLine` instrukcji w `Main` metody. W tym celu albo naciskając klawisz <kbd>F9</kbd> klucza, gdy kursor znajduje się nad `WriteLine` wiersz lub przez kliknięcie przycisku myszy w lewy margines w wierszu, na którym chcesz ustawić punkt przerwania. Czerwone koło pojawi się na marginesie obok wiersza kodu. Po osiągnięciu punktu przerwania wykonywanie kodu zostanie zatrzymane *przed* wiersza punkt przerwania jest wykonywana.

Otwórz kartę debugera, wybierając ikonę debugowania na pasku narzędzi Visual Studio Code, wybierając **Widok > debugowania** z paska menu lub za pomocą skrótu klawiaturowego <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:

![Visual Studio Code Debugger](./media/using-on-macos/vscodedebugger.png)

Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze. Rozpoczyna wykonanie i uruchamia punkt przerwania, gdzie zatrzymuje aplikacji. Wkrocz `Get` — metoda i upewnij się, że ma przekazano poprawne argumenty. Upewnij się, że odpowiedź jest 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]