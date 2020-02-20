---
title: Utwórz szablon projektu dla nowego dotnet
description: Dowiedz się, jak utworzyć szablon projektu dla nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503537"
---
# <a name="tutorial-create-a-project-template"></a>Samouczek: Tworzenie szablonu projektu

Za pomocą platformy .NET Core można tworzyć i wdrażać szablony generujące projekty, pliki, nawet zasoby. Ten samouczek jest drugą częścią serii, która zawiera informacje na temat tworzenia, instalowania i odinstalowywania szablonów do użycia z poleceniem `dotnet new`.

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
>
> * Tworzenie zasobów szablonu projektu
> * Tworzenie folderu i pliku konfiguracji szablonu
> * Instalowanie szablonu ze ścieżki pliku
> * Testowanie szablonu elementu
> * Odinstaluj szablon elementu

## <a name="prerequisites"></a>Wymagania wstępne

* Ukończ [część 1](cli-templates-create-item-template.md) tej serii samouczków.
* Otwórz Terminal i przejdź do folderu _working\templates_ .

## <a name="create-a-project-template"></a>Utwórz szablon projektu

Szablony projektów tworzą gotowe do uruchomienia projekty, które ułatwiają użytkownikom rozpoczęcie pracy z zestawem roboczym kodu. Platforma .NET Core zawiera kilka szablonów projektu, takich jak Aplikacja konsolowa lub Biblioteka klas. W tym przykładzie utworzysz nowy projekt konsoli, który umożliwia C# 8,0 i generuje punkt wejścia `async main`.

W terminalu przejdź do folderu _working\templates_ i Utwórz nowy podfolder o nazwie _consoleasync_. Wprowadź podfolder i uruchom `dotnet new console` w celu wygenerowania standardowej aplikacji konsolowej. Będziesz edytować pliki utworzone przez ten szablon w celu utworzenia nowego szablonu.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Modyfikuj Program.cs

Otwórz plik _program.cs_ . Projekt konsoli nie używa asynchronicznego punktu wejścia, więc Dodajmy ten element. Zmień kod na następujący i Zapisz plik.

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>Modyfikuj consoleasync. csproj

Zaktualizujmy wersję C# językową używaną przez ten projekt do wersji 8,0. Edytuj plik _consoleasync. csproj_ i Dodaj `<LangVersion>` ustawienia do węzła `<PropertyGroup>`.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Kompilowanie projektu

Przed ukończeniem szablonu projektu należy go przetestować, aby upewnić się, że kompiluje i działa poprawnie.

W terminalu uruchom następujące polecenie.

```dotnetcli
dotnet run
```

Otrzymujesz następujące dane wyjściowe.

```console
Hello World with C# 8.0!
```

Można usunąć foldery _obj_ i _bin_ utworzone przy użyciu `dotnet run`. Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki powiązane z szablonem, a nie wszystkie pliki, które powodują akcję kompilacji.

Teraz, gdy masz już utworzoną zawartość szablonu, musisz utworzyć konfigurację szablonu w folderze głównym szablonu.

## <a name="create-the-template-config"></a>Utwórz konfigurację szablonu

Szablony są rozpoznawane w programie .NET Core za pomocą specjalnego folderu i pliku konfiguracji, który istnieje w katalogu głównym szablonu. W tym samouczku folder szablonu znajduje się w lokalizacji _working\templates\consoleasync_.

Podczas tworzenia szablonu wszystkie pliki i foldery znajdujące się w folderze szablonów są uwzględniane jako część szablonu, z wyjątkiem folderu specjalnej konfiguracji. Ten folder konfiguracji ma nazwę _. Template. config_.

Najpierw utwórz nowy podfolder o nazwie _. Template. config_, a następnie wprowadź go. Następnie utwórz nowy plik o nazwie _Template. JSON_. Struktura folderów powinna wyglądać następująco.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Otwórz plik _Template. JSON_ przy użyciu ulubionego edytora tekstu i wklej go w poniższym kodzie JSON i Zapisz go.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

Ten plik konfiguracji zawiera wszystkie ustawienia szablonu. Można zobaczyć podstawowe ustawienia, takie jak `name` i `shortName`, ale również istnieje `tags/type` wartość, która jest ustawiona na `project`. Spowoduje to wyznaczenie szablonu jako szablonu projektu. Nie ma ograniczeń dotyczących typu tworzonego szablonu. Wartości `item` i `project` są typowymi nazwami zalecanymi przez platformę .NET Core, dzięki czemu użytkownicy mogą łatwo filtrować typ szukanego szablonu.

Element `classifications` reprezentuje kolumnę **Tagi** , która pojawia się po uruchomieniu `dotnet new` i wyświetleniu listy szablonów. Użytkownicy mogą również wyszukiwać w oparciu o znaczniki klasyfikacji. Nie należy mylić właściwości `tags` w pliku JSON z listą tagów `classifications`. Te dwa różne rzeczy są uważane za podobne. Pełny Schemat pliku *Template. JSON* znajduje się w [magazynie schematów JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat pliku *Template. JSON* , zobacz stronę [typu tworzenia szablonów programu dotnet](https://github.com/dotnet/templating/wiki).

Teraz, gdy masz prawidłowy plik _Template. config/Template. JSON_ , szablon jest gotowy do zainstalowania. Przed zainstalowaniem szablonu upewnij się, że usunięto wszystkie foldery i pliki dodatkowe pliki, które nie mają być dołączone do szablonu, takie jak foldery _bin_ lub _obj_ . W terminalu przejdź do folderu _consoleasync_ i uruchom `dotnet new -i .\`, aby zainstalować szablon znajdujący się w bieżącym folderze. Jeśli używasz systemu operacyjnego Linux lub macOS, użyj ukośnika: `dotnet new -i ./`.

To polecenie wyświetla listę zainstalowanych szablonów, które powinny obejmować użytkownika.

```dotnetcli
dotnet new -i .\
```

Dane wyjściowe są podobne do poniższych.

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a>Testowanie szablonu projektu

Teraz, gdy masz zainstalowany szablon elementu, przetestuj go.

1. Przejdź do folderu _testowego_

1. Utwórz nową aplikację konsolową przy użyciu następującego polecenia, które generuje projekt roboczy, który można łatwo przetestować przy użyciu polecenia `dotnet run`.

    ```dotnetcli
    dotnet new consoleasync
    ```

    Otrzymujesz następujące dane wyjściowe.

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. Uruchom projekt przy użyciu następującego polecenia.

    ```dotnetcli
    dotnet run
    ```

    Otrzymujesz następujące dane wyjściowe.

    ```console
    Hello World with C# 8.0!
    ```

Gratulacje! Szablon projektu został utworzony i wdrożony za pomocą platformy .NET Core. W ramach przygotowania do następnej części tej serii samouczków należy odinstalować utworzony szablon. Pamiętaj, aby usunąć wszystkie pliki z folderu _testowego_ . Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.

### <a name="uninstall-the-template"></a>Odinstaluj szablon

Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy go odinstalować z **bezwzględną** ścieżką pliku. Listę zainstalowanych szablonów można wyświetlić, uruchamiając polecenie `dotnet new -u`. Szablon powinien zostać wyświetlony jako ostatni. Użyj podanej ścieżki, aby odinstalować szablon przy użyciu polecenia `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.

```dotnetcli
dotnet new -u
```

Dane wyjściowe są podobne do poniższych.

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

Aby odinstalować szablon, uruchom następujące polecenie.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono szablon projektu. Aby dowiedzieć się, jak spakować szablon elementu i projektu do łatwego w użyciu pliku, Kontynuuj tę serię samouczków.

> [!div class="nextstepaction"]
> [Tworzenie pakietu szablonów](cli-templates-create-template-pack.md)
