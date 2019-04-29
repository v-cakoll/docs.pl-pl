---
title: Rozpoczynanie pracy z platformą .NET Core w systemie macOS
description: Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie podstawowych platformy .NET przy użyciu programu Visual Studio Code.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e5ac6fa04a2a5001146936de56acafeec7dd895d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647014"
---
# <a name="get-started-with-net-core-on-macos"></a>Rozpoczynanie pracy z platformą .NET Core w systemie macOS

Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie platformy .NET Core dla systemu macOS. Dowiedz się, jak tworzyć projekty, testy jednostkowe, użyj narzędzi debugowania i zestawowi bibliotek innych firm za pomocą [NuGet](https://www.nuget.org/).

> [!NOTE]
> W tym artykule wykorzystano [programu Visual Studio Code](https://code.visualstudio.com) w systemie macOS.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj [platformy .NET Core SDK](https://www.microsoft.com/net/core). .NET Core SDK zawiera najnowszą wersję platformy .NET Core framework i środowiska uruchomieniowego.

Zainstaluj [programu Visual Studio Code](https://code.visualstudio.com). W trakcie tego artykułu także zainstalować rozszerzenia, które zwiększają programowania .NET Core środowisko Visual Studio Code.

Zainstaluj rozszerzenie programu Visual Studio kodu C#, otwierając program Visual Studio Code i naciskając klawisz <kbd>F1</kbd> aby otworzyć paletę programu Visual Studio Code. Typ **zainstalować ext** Aby wyświetlić listę rozszerzeń. Wybierz rozszerzenie języka C#. Uruchom ponownie Visual Studio Code, aby aktywować rozszerzenia. Aby uzyskać więcej informacji, zobacz [dokumentację kodu C# rozszerzenie programu Visual Studio](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Wprowadzenie

W tym samouczku utworzysz trzy projekty: projektu biblioteki testów dla tego projektu biblioteki i aplikacji konsoli korzystającej z biblioteki. Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) dla tego tematu w repozytorium dotnet/samples w witrynie GitHub. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Start Visual Studio Code. Naciśnij klawisz <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak znakami odwróconego lub początkowych) lub wybierz **Widok > zintegrowany Terminal** z menu aby otworzyć osadzonych w terminalu w programie Visual Studio Code. Możesz nadal otworzyć powłokę zewnętrznych za pomocą Eksploratora usługi **Otwórz w wierszu polecenia** polecenia (**Otwórz w terminalu** na komputerze Mac lub Linux), jeśli wolisz pracować poza programem Visual Studio Code.

Rozpocznij od utworzenia pliku rozwiązania, który służy jako kontener dla jednego lub więcej projektów .NET Core. W terminalu Utwórz *złoty* folder i otwórz folder. Ten folder jest katalogiem głównym rozwiązania. Uruchom [ `dotnet new` ](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *golden.sln*:

```console
dotnet new sln
```

Z *złoty* folder, wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*library.csproj* i *Class1.cs*, w *biblioteki* folderu:

```console
dotnet new classlib -o library
```

Wykonaj [ `dotnet sln` ](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzonego *library.csproj* projektu do rozwiązania:

```console
dotnet sln add library/library.csproj
```

*Library.csproj* plik zawiera następujące informacje:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON. Aby zapewnić obsługę JSON serializacji i deserializacji, Dodaj odwołanie do `Newtonsoft.Json` pakietu NuGet. `dotnet add` Polecenie dodaje nowe elementy do projektu. Aby dodać odwołanie do pakietu NuGet, użyj [ `dotnet add package` ](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:

```console
dotnet add library package Newtonsoft.Json
```

Spowoduje to dodanie `Newtonsoft.Json` i jego zależności do projektu biblioteki. Ręcznie Edytuj *library.csproj* pliku i Dodaj następujący węzeł:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Wykonaj [ `dotnet restore` ](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)) który przywraca zależności i tworzy *obj* folder wewnątrz *biblioteki* z trzema pliki w nim, w tym *project.assets.json* pliku:

```console
dotnet restore
```

W *biblioteki* folderu, Zmień nazwę pliku *Class1.cs* do *Thing.cs*. Zastąp kod z następujących czynności:

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

`Thing` Klasa zawiera jedną metodę publicznych, `Get`, która zwraca sumę dwóch liczby, ale wykonuje konwertowanie sumy w ciąg, a następnie deserializacji na liczbę całkowitą. To korzysta z liczbą nowoczesne funkcje języka C#, takie jak [ `using static` dyrektywy](../../csharp/language-reference/keywords/using-static.md), [elementy członkowskie z wyrażeniem](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), i [Interpolacja ciągów](../../csharp/language-reference/tokens/interpolated.md).

Tworzenie biblioteki za pomocą [ `dotnet build` ](../tools/dotnet-build.md) polecenia. Pozwala to na utworzenie *library.dll* plik *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Utwórz projekt testu

Tworzenie projektu testu dla biblioteki. Z *złoty* folderu, Utwórz nowy projekt testu:

```console
dotnet new xunit -o test-library
```

Dodaj projekt testu do rozwiązania:

```console
dotnet sln add test-library/test-library.csproj
```

Dodaj odwołanie do projektu biblioteki, utworzonego w poprzedniej sekcji, aby kompilator znajdować i używać projektu biblioteki. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Ręcznie Edytuj *library.csproj testu* pliku i Dodaj następujący węzeł:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teraz, gdy zostały poprawnie skonfigurowane zależności, należy utworzyć testy dla biblioteki. Otwórz *UnitTest1.cs* i zastąp jego zawartość następującym kodem:

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

Należy pamiętać, asercja wartość 42 nie jest równa 19 + 23 (lub 42) po utworzeniu testu jednostkowego (`Assert.NotEqual`), który zakończy się niepowodzeniem. Ważnym krokiem w tworzeniu testów jednostkowych jest utworzyć test się niepowodzeniem po raz pierwszy potwierdzić swojej logiki.

Z *złoty* folder, wykonaj następujące polecenia:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Te polecenia zostaną Znajdź rekursywnie wszystkie projekty, aby przywrócić zależności, możesz tworzyć aplikacje i aktywować xUnit uruchamiający testy do uruchomienia testów. Jeden test kończy się niepowodzeniem, zgodnie z oczekiwaniami.

Edytuj *UnitTest1.cs* pliku, a następnie zmień potwierdzenia z `Assert.NotEqual` do `Assert.Equal`. Wykonaj następujące polecenie z *złoty* folder, aby ponownie uruchomić test, który przekazuje teraz:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Tworzenie aplikacji konsoli

Aplikacja konsoli, tworzonych przez następujące kroki przejmuje zależności projektu biblioteki utworzony wcześniej i wywołuje swoją metodę biblioteki, po jego uruchomieniu. Korzystając z tego wzorca, rozwoju, zobaczysz, jak utworzyć biblioteki do ponownego wykorzystania dla wielu projektów.

Utwórz nową aplikację konsoli z *złoty* folderu:

```console
dotnet new console -o app
```

Dodaj projekt aplikacji konsoli w rozwiązaniu:

```console
dotnet sln add app/app.csproj
```

Tworzenie zależności w bibliotece, uruchamiając `dotnet add reference` polecenia:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do przywrócenia zależności trzy projekty w rozwiązaniu. Otwórz *Program.cs* i Zastąp zawartość `Main` metoda o następujący wiersz:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Dodaj dwie `using` dyrektywy do góry *Program.cs* pliku:

```csharp
using static System.Console;
using Library;
```

Wykonaj następujące czynności, `dotnet run` polecenie do uruchomienia pliku wykonywalnego, gdzie `-p` opcję `dotnet run` określa projekt dla głównej aplikacji. Aplikacja tworzy ciąg "odpowiedź brzmi 42".

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Debugowanie aplikacji

Ustaw punkt przerwania w `WriteLine` instrukcji w `Main` metody. W tym celu albo naciskając <kbd>F9</kbd> klucza, gdy kursor znajduje się nad `WriteLine` wiersz lub przez kliknięcie przycisku myszy w lewy margines w wierszu, na którym chcesz ustawić punkt przerwania. Na marginesie obok wiersza kodu pojawi się czerwone kółko. Po osiągnięciu punktu przerwania, wykonanie kodu spowoduje zatrzymanie *przed* zostanie wykonany wiersz punktu przerwania.

Otwórz kartę debuger, wybierając ikonę debugowania na pasku narzędzi programu Visual Studio Code, wybierając **Widok > debugowanie** z paska menu lub za pomocą skrótu klawiaturowego <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:

![Visual Studio Code Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze. Aplikacja rozpoczyna wykonywanie i uruchamia punkt przerwania, gdzie zatrzymuje. Wejdź do `Get` metody i upewnij się, że przeszły w poprawne argumenty. Upewnij się, że odpowiedź zawiera się 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]