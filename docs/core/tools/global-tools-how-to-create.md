---
title: 'Samouczek: Tworzenie narzędzia platformy .NET Core'
description: Dowiedz się, jak utworzyć narzędzie .NET Core. Narzędzie jest aplikacją konsolową, która jest instalowana przy użyciu interfejs wiersza polecenia platformy .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543407"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Samouczek: Tworzenie narzędzia platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

W tym samouczku przedstawiono sposób tworzenia i pakowania narzędzia platformy .NET Core. Interfejs wiersza polecenia platformy .NET Core pozwala utworzyć aplikację konsolową jako narzędzie, którą mogą instalować i uruchamiać inne osoby. Narzędzia .NET Core są pakietami NuGet, które są instalowane z interfejs wiersza polecenia platformy .NET Core. Aby uzyskać więcej informacji na temat narzędzi, zobacz [Narzędzia .NET Core Tools — Omówienie](global-tools.md).

Tworzone narzędzie jest aplikacją konsolową, która przyjmuje komunikat jako dane wejściowe i wyświetla komunikat wraz z wierszami tekstu, które tworzą obraz robota.

Jest to pierwsza z serii trzech samouczków. Ten samouczek obejmuje tworzenie i pakowanie narzędzi. W następnych dwóch samouczkach [użyjesz narzędzia jako narzędzia globalnego](global-tools-how-to-use.md) i [Użyj tego narzędzia jako narzędzia lokalnego](local-tools-how-to-use.md).

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core SDK 3,1](https://dotnet.microsoft.com/download) lub nowsza wersja.

  Ten samouczek i Poniższy samouczek dotyczący [narzędzi globalnych](global-tools-how-to-use.md) mają zastosowanie do zestaw .NET Core SDK 2,1 i nowszych wersji, ponieważ narzędzia globalne są dostępne w tej wersji. Jednak w tym samouczku założono, że zainstalowano program 3,1 lub nowszy, aby można było kontynuować korzystanie z [samouczka narzędzi lokalnych](local-tools-how-to-use.md). Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0. Procedury tworzenia narzędzia są takie same, niezależnie od tego, czy są używane jako narzędzie globalne, czy jako narzędzie lokalne.
  
- Wybrany edytor tekstu lub edytor kodu.

## <a name="create-a-project"></a>Tworzenie projektu

1. Otwórz wiersz polecenia i Utwórz folder o nazwie *Repository*.

1. Przejdź do folderu *repozytorium* i wprowadź następujące polecenie, zastępując `<name>` unikatową wartością, aby nazwa projektu była unikatowa. 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   Można na przykład uruchomić następujące polecenie:

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   Polecenie tworzy nowy folder o nazwie *botsay-\<name >* w folderze *repozytorium* .

1. Przejdź do folderu *botsay\<name >* .

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a>Dodawanie kodu

1. Otwórz plik `Program.cs` z edytorem kodu.

1. Dodaj następującą `using` dyrektywę na początku pliku:

   ```csharp
   using System.Reflection;
   ```

1. Zastąp metodę `Main` poniższym kodem, aby przetworzyć argumenty wiersza polecenia dla aplikacji.

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

   Jeśli nie przechodzą żadnych argumentów, zostanie wyświetlony krótki komunikat pomocy. W przeciwnym razie wszystkie argumenty są łączone w jeden ciąg i drukowane przez wywołanie metody `ShowBot` utworzonej w następnym kroku.

1. Dodaj nową metodę o nazwie `ShowBot`, która przyjmuje parametr ciągu. Metoda drukuje komunikat i obraz robota przy użyciu wierszy tekstu.

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

Uruchom projekt i zobacz dane wyjściowe. Wypróbuj te Wariacje w wierszu polecenia, aby zobaczyć różne wyniki:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Wszystkie argumenty po przekroczeniu ogranicznika `--` są przesyłane do aplikacji.

## <a name="package-the-tool"></a>Pakowanie narzędzia

Przed spakowaniem i dystrybucją aplikacji jako narzędzia należy zmodyfikować plik projektu. 

1. Otwórz plik *botsay\<>. csproj* i Dodaj trzy nowe węzły XML na końcu węzła `<PropertyGroup>`:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` to opcjonalny element określający polecenie, które spowoduje wywołanie narzędzia po jego zainstalowaniu. Jeśli ten element nie zostanie podany, nazwa polecenia dla narzędzia jest nazwą pliku projektu bez rozszerzenia *. csproj* .

   `<PackageOutputPath>` to opcjonalny element określający, gdzie zostanie utworzony pakiet NuGet. Pakiet NuGet jest używany przez interfejs wiersza polecenia platformy .NET Core do instalowania narzędzia.

   Plik projektu wygląda teraz tak, jak w poniższym przykładzie:

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

1. Utwórz pakiet NuGet, uruchamiając polecenie [dotnet Pack](dotnet-pack.md) :

   ```dotnetcli
   dotnet pack
   ```

   *Nazwa botsay\<>. 1.0.0. nupkg* zostanie utworzona w folderze identyfikowanym przez `<PackageOutputPath>` wartość z pliku *botsay-\<nazwa >. csproj* , który w tym przykładzie jest folderem *./nupkg* .
  
   Aby publicznie wydać narzędzie, można przekazać je do `https://www.nuget.org`. Po udostępnieniu narzędzia w narzędziu NuGet deweloperzy mogą zainstalować narzędzie za pomocą polecenia [Install narzędzia dotnet](dotnet-tool-install.md) . Na potrzeby tego samouczka zainstalujesz pakiet bezpośrednio z lokalnego folderu *NUPKG* , więc nie ma potrzeby przekazywania pakietu do narzędzia NuGet.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli podczas wykonywania samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzysz aplikację konsolową i spakowano ją jako narzędzie. Aby dowiedzieć się, jak używać narzędzia jako narzędzia globalnego, przejdź do następnego samouczka.

> [!div class="nextstepaction"]
> [Instalowanie i używanie narzędzia globalnego](global-tools-how-to-use.md)

Jeśli wolisz, możesz pominąć samouczek dotyczący narzędzi globalnych i przejść bezpośrednio do samouczka dotyczącego narzędzi lokalnych.

> [!div class="nextstepaction"]
> [Instalowanie i używanie narzędzia lokalnego](local-tools-how-to-use.md)
