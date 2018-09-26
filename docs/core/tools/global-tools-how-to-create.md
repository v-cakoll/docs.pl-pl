---
title: Jak utworzyć narzędzie globalnej platformy .NET Core
description: Opisuje sposób tworzenia narzędzie globalne. Narzędzie globalnej jest aplikacja konsolowa która instaluje się za pośrednictwem interfejsu wiersza polecenia platformy .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3860aad5e2c13714298d50bb9ac10daec3aadf01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231222"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Utworzyć narzędzie globalnej platformy .NET Core przy użyciu interfejsu wiersza polecenia platformy .NET Core

Ten artykuł nauczy Cię sposobu tworzenia i pakietu Narzędzia globalnej Core środowiska .NET. Interfejs wiersza polecenia platformy .NET Core umożliwia tworzenie aplikacji konsoli jako globalne narzędzia, które inne osoby można łatwo zainstalować i uruchomić. Narzędzia programu .NET core globalne są pakiety NuGet, które są instalowane z interfejsu wiersza polecenia platformy .NET Core. Aby uzyskać więcej informacji na temat narzędzia globalnej zobacz [Omówienie narzędzia globalnej platformy .NET Core][global-tool-info].

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Tworzenie projektu

W tym artykule używa interfejsu wiersza polecenia platformy .NET Core do tworzenia i zarządzania projektem.

Narzędzie naszym przykładzie będzie aplikację konsolową która generuje bot ASCII i drukuje wiadomość. Najpierw utwórz nową aplikację Konsolową .NET Core.

```console
dotnet new console -o botsay
```

Przejdź do `botsay` Katalog utworzony przez poprzednie polecenie.

## <a name="add-the-code"></a>Dodaj kod

Otwórz `Program.cs` plików za pomocą ulubionego edytora tekstu, takie jak `vim` lub [programu Visual Studio Code](https://code.visualstudio.com/).

Dodaj następujący kod `using` dyrektywy do górnej części pliku, pomoże skrócić kod, aby wyświetlić informacje o wersji aplikacji.

```csharp
using System.Reflection;
```

Następnie Przenieś w dół do `Main` metody. Zastąp metodę następujący kod, aby przetworzyć argumenty wiersza polecenia dla aplikacji. Jeśli nie przekazano argumentów, jest wyświetlany komunikat pomocy krótki. W przeciwnym razie tych argumentów są przekształcane na ciąg i drukowania z botami.

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

### <a name="create-the-bot"></a>Utwórz bota

Następnie dodaj nową metodę o nazwie `ShowBot` przyjmującą parametr ciągu. Ta metoda drukuje wiadomość i ASCII bot. W kodzie bot ASCII została pobrana z [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) próbki.

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

### <a name="test-the-tool"></a>Narzędzia testowania

Uruchom projekt i wyświetlić dane wyjściowe. Wypróbuj te zmiany z wiersza polecenia, aby wyświetlić różne wyniki:

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Wszystkie argumenty po `--` ogranicznik są przekazywane do aplikacji.

## <a name="setup-the-global-tool"></a>Ustawienia globalne narzędzia

Przed dodatkiem Service pack i dystrybucji aplikacji jako globalne narzędzie, należy zmodyfikować plik projektu. Otwórz `botsay.csproj` pliku i Dodaj trzy nowe węzły XML do `<Project><PropertyGroup>` węzła:

- `<PackAsTool>`  
[WYMAGANE] Wskazuje, że aplikacja zostanie umieszczony w pakiecie do zainstalowania narzędzia globalnej.

- `<ToolCommandName>`  
[OPCJONALNIE] Alternatywna nazwa narzędzia, w przeciwnym razie nazwa polecenia dla narzędzia będzie identyczna z nazwą pliku projektu. W pakiecie, wybierając unikatową przyjazną nazwą pomaga odróżnić od innych narzędzi, w tym samym pakiecie, może mieć wielu narzędzi.

- `<PackageOutputPath>`  
[OPCJONALNIE] Gdzie będą opracowywane pakietu NuGet. Pakiet NuGet jest narzędzia globalnej interfejsu wiersza polecenia platformy .NET Core używa Aby zainstalować narzędzie.

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

Mimo że `<PackageOutputPath>` jest opcjonalny, użyj go w tym przykładzie. Upewnij się, że jest on ustawiany: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Następnie należy utworzyć pakiet NuGet na potrzeby aplikacji.

```console
dotnet pack
```

`botsay.1.0.0.nupkg` Plik jest tworzony w folderze identyfikowane przez `<PackageOutputPath>` wartość XML z `botsay.csproj` pliku, który w tym przykładzie jest `./nupkg` folderu. Dzięki temu można łatwo zainstalować i przetestować. W przypadku wersji narzędzia publicznie, przekaż go do [ https://www.nuget.org ](https://www.nuget.org).

Teraz, gdy pakiet, należy zainstalować narzędzia z tego pakietu: 

```console
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` Parametru informuje .NET Core interfejs wiersza polecenia i użyj tymczasowo `./nupkg` folder (nasze `<PackageOutputPath>` folder) jako źródło dodatkowych źródło danych dla pakietów NuGet. Aby uzyskać więcej informacji na temat instalowania narzędzi globalnych, zobacz [Omówienie narzędzia globalnej platformy .NET Core][global-tool-info].

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobny do poniższego przykładu:

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Teraz powinno być możliwe do wpisania `botsay` i uzyskać odpowiedzi z narzędzia.

> [!NOTE]
> Jeśli instalacja zakończyła się pomyślnie, ale nie można użyć `botsay` polecenia, może być konieczne otwarcie nowym terminalu, aby odświeżyć ścieżki.

## <a name="remove-the-tool"></a>Usuń narzędzie

Po zakończeniu eksperymentowanie, za pomocą narzędzia, możesz je usunąć za pomocą następujących commnand:

```console
dotnet tool uninstall -g botsay
```

[global-tool-info]: global-tools.md
