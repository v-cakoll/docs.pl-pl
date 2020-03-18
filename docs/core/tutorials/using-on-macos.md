---
title: 'Samouczek: Tworzenie rozwiązania .NET Core w systemie macOS przy użyciu kodu programu Visual Studio'
description: Ten dokument zawiera kroki i przepływ pracy, aby utworzyć .NET Core Solution przy użyciu kodu programu Visual Studio.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156598"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Samouczek: Tworzenie rozwiązania .NET Core w systemie macOS przy użyciu kodu programu Visual Studio

Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie .NET Core dla systemu macOS. Dowiedz się, jak tworzyć projekty, testy jednostkowe, używać narzędzi do debugowania i włączać biblioteki innych firm za pośrednictwem [NuGet](https://www.nuget.org/).

> [!NOTE]
> W tym artykule [użyto kodu programu Visual Studio](https://code.visualstudio.com) w systemie macOS.

## <a name="prerequisites"></a>Wymagania wstępne

Zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download). Zestaw SDK .NET Core zawiera najnowszą wersję struktury .NET Core i programu runtime.

Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com). W trakcie tego artykułu można również zainstalować rozszerzenia kodu programu Visual Studio, które poprawiają środowisko programistyczne .NET Core.

Zainstaluj rozszerzenie kodu C# programu Visual Studio, otwierając program Visual Studio Code i naciskając klawisz <kbd>Fn</kbd>+<kbd>F1,</kbd> aby otworzyć paletę Kod programu Visual Studio. Wpisz **instalację ext,** aby wyświetlić listę rozszerzeń. Wybierz rozszerzenie C#. Uruchom ponownie kod programu Visual Studio, aby aktywować rozszerzenie. Aby uzyskać więcej informacji, zobacz [dokumentację rozszerzenia kodu C# programu Visual Studio](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Rozpoczęcie pracy

W tym samouczku utworzysz trzy projekty: projekt biblioteki, testy dla tego projektu biblioteki i aplikację konsoli, która korzysta z biblioteki. Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) tego artykułu w repozytorium dotnet/samples w usylenie GitHub. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Uruchom program Visual Studio Code. Naciśnij <kbd>klawisz Ctrl</kbd> <kbd>\`</kbd> (znak backquote lub backtick) lub wybierz polecenie **Wyświetl** > **terminal** z menu, aby otworzyć osadzony terminal w kodzie programu Visual Studio. Nadal można otworzyć powłokę zewnętrzną za pomocą polecenia Explorer **Open in Command Prompt** **(Otwórz w terminalu** w systemie macOS lub Linux), jeśli wolisz pracować poza kodem programu Visual Studio.

Rozpocznij od utworzenia pliku rozwiązania, który służy jako kontener dla jednego lub więcej projektów programu .NET Core. W terminalu uruchom [`dotnet new`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *golden.sln* wewnątrz nowego folderu o nazwie *złoty:*

```dotnetcli
dotnet new sln -o golden
```

Przejdź do nowego *złotego* folderu i wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*library.csproj* i *Class1.cs*, w folderze *biblioteki:*

```dotnetcli
dotnet new classlib -o library
```

Wykonaj [`dotnet sln`](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzony projekt *library.csproj* do rozwiązania:

```dotnetcli
dotnet sln add library/library.csproj
```

Plik *library.csproj* zawiera następujące informacje:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Nasze metody biblioteki serializują i deserializują obiekty w formacie JSON. Aby obsługiwać serializacji JSON i deserializacji, `Newtonsoft.Json` dodaj odwołanie do pakietu NuGet. Polecenie `dotnet add` dodaje nowe elementy do projektu. Aby dodać odwołanie do pakietu NuGet, użyj [`dotnet add package`](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Spowoduje `Newtonsoft.Json` to dodanie i jego zależności do projektu biblioteki. Alternatywnie ręcznie zrewiduj plik *library.csproj* i dodaj następujący węzeł:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Wykonaj [`dotnet restore`](../tools/dotnet-restore.md),[(patrz uwaga),](#dotnet-restore-note)który przywraca zależności i tworzy folder *obj* wewnątrz *biblioteki* z trzema plikami w nim, w tym plik *project.assets.json:*

```dotnetcli
dotnet restore
```

W folderze *biblioteki* zmień nazwę *pliku Class1.cs* na *Thing.cs*. Zastąp kod następującymi czynnościami:

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

Klasa `Thing` zawiera jedną metodę `Get`publiczną, która zwraca sumę dwóch liczb, ale robi to przez przekonwertowanie sumy na ciąg, a następnie deserializację jej na liczbę całkowitą. Dzięki temu korzysta z wielu nowoczesnych funkcji Języka C#, takich jak [ `using static` dyrektywy,](../../csharp/language-reference/keywords/using-static.md) [elementy członkowskie zabudowane wyrażeniem](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)i [interpolacja ciągów.](../../csharp/language-reference/tokens/interpolated.md)

Zbuduj [`dotnet build`](../tools/dotnet-build.md) bibliotekę za pomocą polecenia. Spowoduje to wygenerowanie pliku *library.dll* pod *golden/library/bin/Debug/netstandard1.4*:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Tworzenie projektu testowego

Tworzenie projektu testowego dla biblioteki. Ze *złotego* folderu utwórz nowy projekt testowy:

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

Alternatywnie ręcznie edytować plik *test-library.csproj* i dodać następujący węzeł:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teraz, gdy zależności zostały poprawnie skonfigurowane, utwórz testy dla biblioteki. Otwórz *UnitTest1.cs* i zastąp jego zawartość następującym kodem:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Należy pamiętać, że wartość 42 nie jest równa 19 +23 (lub 42) podczas pierwszego utworzenia testu jednostkowego (),`Assert.NotEqual`który zakończy się niepowodzeniem. Ważnym krokiem w budowaniu testów jednostkowych jest utworzenie testu, który nie powiedzie się po raz pierwszy, aby potwierdzić jego logikę.

Ze *złotego* folderu wykonaj następujące polecenia:

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Te polecenia będą rekursywnie znaleźć wszystkie projekty, aby przywrócić zależności, skompilować je i aktywować xUnit test runner do uruchomienia testów. Pojedynczy test nie powiedzie się, zgodnie z oczekiwaniami.

Edytowanie *pliku UnitTest1.cs* i zmienianie potwierdzenia z `Assert.NotEqual` na `Assert.Equal`. Wykonaj następujące polecenie ze *złotego* folderu, aby ponownie uruchomić test, który mija tym razem:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Tworzenie aplikacji konsoli

Aplikacja konsoli, którą utworzysz w następujących krokach, ma zależność od projektu biblioteki utworzonego wcześniej i wywołuje jego metodę biblioteki po uruchomieniu. Za pomocą tego wzorca programowania, zobacz, jak utworzyć biblioteki wielokrotnego użytku dla wielu projektów.

Utwórz nową aplikację konsoli ze *złotego* folderu:

```dotnetcli
dotnet new console -o app
```

Dodaj projekt aplikacji konsoli do rozwiązania:

```dotnetcli
dotnet sln add app/app.csproj
```

Utwórz zależność od biblioteki, `dotnet add reference` uruchamiając polecenie:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Uruchom `dotnet restore` ([zobacz notatkę),](#dotnet-restore-note)aby przywrócić zależności trzech projektów w rozwiązaniu. Otwórz *Program.cs* i zastąp zawartość `Main` metody następującym wierszem:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Dodaj `using` dwie dyrektywy do górnej części *pliku Program.cs:*

```csharp
using static System.Console;
using Library;
```

Wykonaj następujące `dotnet run` polecenie, aby uruchomić plik `-p` wykonywalny, gdzie opcja `dotnet run` określa projekt dla aplikacji głównej. Aplikacja tworzy ciąg "Odpowiedź jest 42".

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Debugowanie aplikacji

Ustaw punkt przerwania `WriteLine` w `Main` instrukcji w metodzie. Należy to zrobić, naciskając klawisz <kbd>Fn</kbd>+<kbd>F9,</kbd> `WriteLine` gdy kursor znajduje się nad linią, albo klikając myszą na lewym marginesie w wierszu, w którym chcesz ustawić punkt przerwania. Czerwone kółko pojawi się na marginesie obok wiersza kodu. Po osiągnięciu punktu przerwania wykonanie kodu zostanie zatrzymane *przed* wykonaniem linii punktu przerwania.

Otwórz kartę debugera, wybierając ikonę Debugowania na pasku narzędzi Kodu programu Visual Studio, wybierając **pozycję Wyświetl** > **debugowanie** z paska menu lub używając skrótu klawiaturowego <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D:</kbd>

![Debuger kodu programu Visual Studio](./media/using-on-macos/visual-studio-code-debugger.png)

Naciśnij przycisk Odtwórz, aby uruchomić aplikację w obszarze debugera. Utworzono zarówno projekt testowy, jak i aplikację w tym projekcie. Debuger pyta, który projekt chcesz uruchomić. Wybierz projekt "app". Aplikacja rozpoczyna wykonywanie i działa do punktu przerwania, gdzie zatrzymuje. Krok do `Get` metody i upewnij się, że zostały przekazane w poprawnych argumentów. Upewnij się, że odpowiedź jest 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
