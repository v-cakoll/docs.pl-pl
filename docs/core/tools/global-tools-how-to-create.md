---
title: Jak utworzyć narzędzie globalne platformy .NET Core
description: Opisuje sposób tworzenia narzędzia globalnego. Narzędzie globalne jest aplikacją konsolową, która jest instalowana za pomocą interfejs wiersza polecenia platformy .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 1daecf7234f02a5fe0dcf25cf7edbb0af327b8c1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343522"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Tworzenie globalnego narzędzia platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core

W tym artykule przedstawiono sposób tworzenia i pakowania globalnego narzędzia platformy .NET Core. Interfejs wiersza polecenia platformy .NET Core pozwala utworzyć aplikację konsolową jako narzędzie globalne, którą mogą łatwo instalować i uruchamiać inne osoby. Narzędzia globalne platformy .NET Core są pakietami NuGet, które są instalowane z interfejs wiersza polecenia platformy .NET Core. Aby uzyskać więcej informacji na temat narzędzi globalnych, zobacz [Omówienie narzędzi globalnych platformy .NET Core](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Tworzenie projektu

W tym artykule interfejs wiersza polecenia platformy .NET Core tworzenia projektu i zarządzania nim.

Nasze przykładowe narzędzie będzie aplikacją konsolową, która generuje bot ASCII i drukuje komunikat. Najpierw utwórz nową aplikację konsolową platformy .NET Core.

```dotnetcli
dotnet new console -o botsay
```

Przejdź do katalogu `botsay` utworzonego przez poprzednie polecenie.

## <a name="add-the-code"></a>Dodawanie kodu

Otwórz plik `Program.cs` za pomocą ulubionego edytora tekstu, takiego jak `vim` lub [Visual Studio Code](https://code.visualstudio.com/).

Dodaj następującą `using` dyrektywę na początku pliku, co pomaga skrócić kod w celu wyświetlenia informacji o wersji aplikacji.

```csharp
using System.Reflection;
```

Następnie przejdź w dół do metody `Main`. Zastąp metodę poniższym kodem, aby przetworzyć argumenty wiersza polecenia dla aplikacji. Jeśli nie przekazano żadnych argumentów, zostanie wyświetlony krótki komunikat pomocy. W przeciwnym razie wszystkie te argumenty są przekształcane w ciąg i drukowane przy użyciu bot.

```csharp
static void Main(string[] args)
{
    if (args.Length == 0)
    {
        var versionString = Assembly.GetEntryAssembly()
                                .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                .InformationalVersion
                                .ToString();

        Console.WriteLine($"botsay v{versionString}");
        Console.WriteLine("-------------");
        Console.WriteLine("\nUsage:");
        Console.WriteLine("  botsay <message>");
        return;
    }

    ShowBot(string.Join(' ', args));
}
```

### <a name="create-the-bot"></a>Tworzenie bot

Następnie Dodaj nową metodę o nazwie `ShowBot`, która przyjmuje parametr ciągu. Ta metoda drukuje komunikat i bot ASCII. Kod bot ASCII został pobrany z przykładu [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) .

```csharp
static void ShowBot(string message)
{
    string bot = $"\n        {message}";
    bot += @"
    __________________
                      \
                       \
                          ....
                          ....'
                           ....
                        ..........
                    .............'..'..
                 ................'..'.....
               .......'..........'..'..'....
              ........'..........'..'..'.....
             .'....'..'..........'..'.......'.
             .'..................'...   ......
             .  ......'.........         .....
             .    _            __        ......
            ..    #            ##        ......
           ....       .                 .......
           ......  .......          ............
            ................  ......................
            ........................'................
           ......................'..'......    .......
        .........................'..'.....       .......
     ........    ..'.............'..'....      ..........
   ..'..'...      ...............'.......      ..........
  ...'......     ...... ..........  ......         .......
 ...........   .......              ........        ......
.......        '...'.'.              '.'.'.'         ....
.......       .....'..               ..'.....
   ..       ..........               ..'........
          ............               ..............
         .............               '..............
        ...........'..              .'.'............
       ...............              .'.'.............
      .............'..               ..'..'...........
      ...............                 .'..............
       .........                        ..............
        .....
";
    Console.WriteLine(bot);
}
```

### <a name="test-the-tool"></a>Testowanie narzędzia

Uruchom projekt i zobacz dane wyjściowe. Wypróbuj te Wariacje w wierszu polecenia, aby zobaczyć różne wyniki:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Wszystkie argumenty po przekroczeniu ogranicznika `--` są przesyłane do aplikacji.

## <a name="set-up-the-global-tool"></a>Konfigurowanie narzędzia globalnego

Przed spakowaniem i dystrybucją aplikacji jako narzędzia globalnego należy zmodyfikować plik projektu. Otwórz plik `botsay.csproj` i Dodaj trzy nowe węzły XML do węzła `<Project><PropertyGroup>`:

- `<PackAsTool>`\
POTRZEB Wskazuje, że aplikacja zostanie spakowana do zainstalowania jako narzędzie globalne.

- `<ToolCommandName>`\
OBOWIĄZKOWE Alternatywna nazwa narzędzia, w przeciwnym razie nazwa polecenia dla narzędzia będzie nazywana po pliku projektu. W pakiecie można korzystać z wielu narzędzi, ale wybór unikatowej i przyjaznej nazwy ułatwia odróżnienie od innych narzędzi w tym samym pakiecie.

- `<PackageOutputPath>`\
OBOWIĄZKOWE Miejsce, w którym zostanie utworzony pakiet NuGet. Pakiet NuGet jest używany przez narzędzia globalne interfejs wiersza polecenia platformy .NET Core do instalowania narzędzia.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

Mimo że `<PackageOutputPath>` jest opcjonalne, użyj go w tym przykładzie. Upewnij się, że została ustawiona: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Następnie Utwórz pakiet NuGet dla swojej aplikacji.

```dotnetcli
dotnet pack
```

Plik `botsay.1.0.0.nupkg` jest tworzony w folderze identyfikowanym przez `<PackageOutputPath>` wartość XML z pliku `botsay.csproj`, który w tym przykładzie jest folderem `./nupkg`. Ułatwia to Instalowanie i testowanie. Jeśli chcesz publicznie wydać narzędzie, przekaż je do <https://www.nuget.org>. Po udostępnieniu narzędzia w narzędziu NuGet deweloperzy mogą wykonać instalację narzędzia przy użyciu opcji `--global` narzędzia [dotnet](dotnet-tool-install.md) .

Teraz, gdy masz pakiet, zainstaluj narzędzie z tego pakietu:

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` parametr informuje interfejs wiersza polecenia platformy .NET Core o tymczasowym użyciu folderu `./nupkg` (nasz folder `<PackageOutputPath>`) jako dodatkowego źródła strumieniowego dla pakietów NuGet. Aby uzyskać więcej informacji na temat instalowania narzędzi globalnych, zobacz [Omówienie narzędzi globalnych platformy .NET Core](global-tools.md).

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Teraz powinno być możliwe wpisanie `botsay` i uzyskanie odpowiedzi z narzędzia.

> [!NOTE]
> Jeśli instalacja zakończyła się pomyślnie, ale nie można użyć `botsay` polecenia, może być konieczne otwarcie nowego terminalu w celu odświeżenia ścieżki.

## <a name="remove-the-tool"></a>Usuń narzędzie

Po zakończeniu eksperymentowania z narzędziem można je usunąć za pomocą następującego polecenia:

```dotnetcli
dotnet tool uninstall -g botsay
```
