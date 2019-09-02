---
title: Jak utworzyć narzędzie globalne platformy .NET Core
description: Opisuje sposób tworzenia narzędzia globalnego. Narzędzie globalne jest aplikacją konsolową, która jest instalowana za pomocą interfejs wiersza polecenia platformy .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: f60e26d14e89b6b7c34b32bf9a114fe4ad691981
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202767"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Tworzenie globalnego narzędzia platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core

W tym artykule przedstawiono sposób tworzenia i pakowania globalnego narzędzia platformy .NET Core. Interfejs wiersza polecenia platformy .NET Core pozwala utworzyć aplikację konsolową jako narzędzie globalne, którą mogą łatwo instalować i uruchamiać inne osoby. Narzędzia globalne platformy .NET Core są pakietami NuGet, które są instalowane z interfejs wiersza polecenia platformy .NET Core. Aby uzyskać więcej informacji na temat narzędzi globalnych, zobacz [Omówienie narzędzi globalnych platformy .NET Core](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Tworzenie projektu

W tym artykule interfejs wiersza polecenia platformy .NET Core tworzenia projektu i zarządzania nim.

Nasze przykładowe narzędzie będzie aplikacją konsolową, która generuje bot ASCII i drukuje komunikat. Najpierw utwórz nową aplikację konsolową platformy .NET Core.

```console
dotnet new console -o botsay
```

Przejdź do `botsay` katalogu utworzonego przez poprzednie polecenie.

## <a name="add-the-code"></a>Dodaj kod

Otwórz plik za pomocą ulubionego edytora tekstu, takiego jak `vim` lub [Visual Studio Code.](https://code.visualstudio.com/) `Program.cs`

Dodaj następującą `using` dyrektywę na początku pliku, aby skrócić kod w celu wyświetlenia informacji o wersji aplikacji.

```csharp
using System.Reflection;
```

Następnie przejdź do `Main` metody. Zastąp metodę poniższym kodem, aby przetworzyć argumenty wiersza polecenia dla aplikacji. Jeśli nie przekazano żadnych argumentów, zostanie wyświetlony krótki komunikat pomocy. W przeciwnym razie wszystkie te argumenty są przekształcane w ciąg i drukowane przy użyciu bot.

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

Następnie Dodaj nową metodę o nazwie `ShowBot` , która przyjmuje parametr ciągu. Ta metoda drukuje komunikat i bot ASCII. Kod bot ASCII został pobrany z przykładu [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) .

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

Uruchom projekt i zobacz dane wyjściowe. Wypróbuj te zmiany w wierszu polecenia, aby zobaczyć różne wyniki:

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Wszystkie argumenty po `--` ograniczniku są przesyłane do aplikacji.

## <a name="setup-the-global-tool"></a>Skonfiguruj narzędzie globalne

Przed spakowaniem i dystrybucją aplikacji jako narzędzia globalnego należy zmodyfikować plik projektu. Otwórz plik i Dodaj trzy nowe węzły XML `<Project><PropertyGroup>` do węzła: `botsay.csproj`

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

Mimo że `<PackageOutputPath>` jest to opcjonalne, użyj go w tym przykładzie. Upewnij się, że: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Następnie Utwórz pakiet NuGet dla swojej aplikacji.

```console
dotnet pack
```

Plik jest tworzony w folderze identyfikowanym `<PackageOutputPath>` przez wartość XML z `botsay.csproj` `./nupkg` pliku, który w tym przykładzie jest folderem. `botsay.1.0.0.nupkg` Ułatwia to Instalowanie i testowanie. Jeśli chcesz publicznie wydać narzędzie, przekaż je do programu <https://www.nuget.org>. Po udostępnieniu narzędzia w programie NuGet deweloperzy mogą wykonać instalację narzędzia dla całego użytkownika, korzystając `--global` z opcji polecenia [Zainstaluj narzędzie dotnet](dotnet-tool-install.md) .

Teraz, gdy masz pakiet, zainstaluj narzędzie z tego pakietu:

```console
dotnet tool install --global --add-source ./nupkg botsay
```

Parametr nakazuje interfejs wiersza polecenia platformy .NET Core tymczasowego `./nupkg` używania folderu (nasz `<PackageOutputPath>` folder) jako dodatkowego źródła strumieniowego dla pakietów NuGet. `--add-source` Aby uzyskać więcej informacji na temat instalowania narzędzi globalnych, zobacz [Omówienie narzędzi globalnych platformy .NET Core](global-tools.md).

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Teraz powinno być możliwe wpisywanie `botsay` i pobieranie odpowiedzi z narzędzia.

> [!NOTE]
> Jeśli instalacja zakończyła się pomyślnie, ale nie można `botsay` użyć polecenia, może być konieczne otwarcie nowego terminalu w celu odświeżenia ścieżki.

## <a name="remove-the-tool"></a>Usuń narzędzie

Po zakończeniu eksperymentowania z narzędziem można je usunąć za pomocą następującego polecenia:

```console
dotnet tool uninstall -g botsay
```
