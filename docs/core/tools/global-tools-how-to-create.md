---
title: 'Samouczek: Tworzenie narzędzia .NET Core'
description: Dowiedz się, jak utworzyć narzędzie .NET Core. Narzędzie to aplikacja konsoli zainstalowana przy użyciu interfejsu CLI .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156728"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Samouczek: Tworzenie narzędzia .NET Core przy użyciu procesora CLI programu .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

W tym samouczku nauczycię, jak utworzyć i spakować narzędzie .NET Core. Interfejs cli .NET Core umożliwia tworzenie aplikacji konsoli jako narzędzia, które inne osoby mogą instalować i uruchamiać. Narzędzia .NET Core to pakiety NuGet zainstalowane z procesora CLI .NET Core. Aby uzyskać więcej informacji na temat narzędzi, zobacz [omówienie narzędzi programu .NET Core](global-tools.md).

Narzędzie, które utworzysz, to aplikacja konsolowa, która przyjmuje komunikat jako dane wejściowe i wyświetla wiadomość wraz z wierszami tekstu, które tworzą obraz robota.

Jest to pierwszy z serii trzech samouczków. W tym samouczku można utworzyć i spakować narzędzie. W następnych dwóch samouczkach [używasz tego narzędzia jako narzędzia globalnego](global-tools-how-to-use.md) i używasz tego narzędzia jako narzędzia [lokalnego.](local-tools-how-to-use.md)

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) lub nowsza wersja.

  Ten samouczek i poniższy [samouczek dla narzędzi globalnych](global-tools-how-to-use.md) dotyczą .NET Core SDK 2.1 i nowszych wersji, ponieważ narzędzia globalne są dostępne począwszy od tej wersji. Ale ten poradnik zakłada, że masz zainstalowany 3.1 lub nowsze tak, że masz możliwość kontynuowania do [samouczka narzędzi lokalnych](local-tools-how-to-use.md). Lokalne narzędzia są dostępne od .NET Core SDK 3.0. Procedury tworzenia narzędzia są takie same, niezależnie od tego, czy są używane jako narzędzie globalne, czy jako narzędzie lokalne.
  
- Wybrany edytor tekstu lub edytor kodu.

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz wiersz polecenia i utwórz folder o nazwie *repozytorium*.

1. Przejdź do folderu *repozytorium* i wprowadź następujące polecenie:

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   Polecenie tworzy nowy folder o nazwie *microsoft.botsay* w folderze *repozytorium.*

1. Przejdź do folderu *microsoft.botsay.*

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Dodawanie kodu

1. Otwórz `Program.cs` plik za pomocą edytora kodu.

1. Dodaj następującą `using` dyrektywę do górnej części pliku:

   ```csharp
   using System.Reflection;
   ```

1. Zamień metodę na `Main` następujący kod, aby przetworzyć argumenty wiersza polecenia dla aplikacji.

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

   Jeśli nie zostaną przekazane żadne argumenty, zostanie wyświetlony krótki komunikat pomocy. W przeciwnym razie wszystkie argumenty są łączone w jeden ciąg `ShowBot` i drukowane przez wywołanie metody, która jest tworzona w następnym kroku.

1. Dodaj nową metodę `ShowBot` o nazwie, która przyjmuje parametr ciągu. Metoda drukuje wiadomość i obraz robota za pomocą linii tekstu.

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

1. Zapisz zmiany.

## <a name="test-the-application"></a>Testowanie aplikacji

Uruchom projekt i zobacz dane wyjściowe. Wypróbuj te odmiany w wierszu polecenia, aby zobaczyć różne wyniki:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Wszystkie argumenty `--` po ogranicznik są przekazywane do aplikacji.

## <a name="package-the-tool"></a>Zapakować narzędzie

Przed spakowaniem i dystrybucją aplikacji jako narzędzia należy zmodyfikować plik projektu.

1. Otwórz plik *microsoft.botsay.csproj* i dodaj trzy nowe węzły `<PropertyGroup>` XML na końcu węzła:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`jest opcjonalnym elementem, który określa polecenie, które wywoła narzędzie po jego zainstalowaniu. Jeśli ten element nie jest podany, nazwa polecenia narzędzia jest nazwą pliku projektu bez rozszerzenia *csproj.*

   `<PackageOutputPath>`jest opcjonalnym elementem, który określa, gdzie pakiet NuGet zostaną wyprodukowane. Pakiet NuGet jest tym, czego używa cli .NET Core do zainstalowania narzędzia.

   Plik projektu wygląda teraz jak w poniższym przykładzie:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. Utwórz pakiet NuGet, uruchamiając polecenie [dotnet pack:](dotnet-pack.md)

   ```dotnetcli
   dotnet pack
   ```

   Plik *microsoft.botsay.1.0.0.nupkg* jest tworzony w folderze `<PackageOutputPath>` identyfikowanym przez wartość z pliku *microsoft.botsay.csproj,* który w tym przykładzie jest folderem *./nupkg.*
  
   Jeśli chcesz udostępnić narzędzie publicznie, możesz przesłać `https://www.nuget.org`je do programu . Gdy narzędzie jest dostępne na NuGet, deweloperzy mogą zainstalować narzędzie za pomocą polecenia [instalacji narzędzia dotnet.](dotnet-tool-install.md) W tym samouczku można zainstalować pakiet bezpośrednio z lokalnego folderu *nupkg,* więc nie ma potrzeby przekazywania pakietu do NuGet.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli podczas korzystania z samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono aplikację konsoli i spakowałeś ją jako narzędzie. Aby dowiedzieć się, jak korzystać z narzędzia jako narzędzia globalnego, przejdź do następnego samouczka.

> [!div class="nextstepaction"]
> [Instalowanie i używanie narzędzia globalnego](global-tools-how-to-use.md)

Jeśli wolisz, możesz pominąć samouczek narzędzi globalnych i przejść bezpośrednio do samouczka narzędzi lokalnych.

> [!div class="nextstepaction"]
> [Instalowanie i używanie narzędzia lokalnego](local-tools-how-to-use.md)
