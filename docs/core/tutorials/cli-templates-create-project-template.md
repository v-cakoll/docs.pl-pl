---
title: Tworzenie szablonu projektu dla dotnet nowy
description: Dowiedz się, jak utworzyć szablon projektu dla polecenia dotnet new.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503537"
---
# <a name="tutorial-create-a-project-template"></a>Samouczek: Tworzenie szablonu projektu

Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projekty, pliki, a nawet zasoby. Ten samouczek jest częścią drugiej serii, która uczy, jak tworzyć, instalować `dotnet new` i odinstalowywać szablony do użycia z poleceniem.

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
>
> * Tworzenie zasobów szablonu projektu
> * Tworzenie folderu i pliku konfiguracji szablonu
> * Instalowanie szablonu ze ścieżki pliku
> * Testowanie szablonu elementu
> * Odinstalowywanie szablonu elementu

## <a name="prerequisites"></a>Wymagania wstępne

* Ukończ [część 1](cli-templates-create-item-template.md) tej serii samouczków.
* Otwórz terminal i przejdź do folderu _working\templates._

## <a name="create-a-project-template"></a>Tworzenie szablonu projektu

Szablony projektów tworzą gotowe do uruchomienia projekty, które ułatwiają użytkownikom uruchamianie z roboczym zestawem kodu. .NET Core zawiera kilka szablonów projektów, takich jak aplikacja konsoli lub biblioteki klas. W tym przykładzie utworzysz nowy projekt konsoli, który umożliwia C# 8.0 i tworzy punkt `async main` wejścia.

W terminalu przejdź do folderu _working\templates_ i utwórz nowy podfolder o nazwie _consoleasync_. Wprowadź podfolder i `dotnet new console` uruchom, aby wygenerować standardową aplikację konsoli. Będziesz edytować pliki utworzone przez ten szablon, aby utworzyć nowy szablon.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Modyfikowanie Program.cs

Otwórz _plik program.cs._ Projekt konsoli nie używa asynchronicznego punktu wejścia, więc dodajmy to. Zmień kod na następujący i zapisz plik.

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

## <a name="modify-consoleasynccsproj"></a>Modyfikowanie consoleasync.csproj

Zaktualizujmy wersję języka C#, która jest używana do wersji 8.0. Edytować plik _consoleasync.csproj_ i `<LangVersion>` dodać `<PropertyGroup>` ustawienie do węzła.

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

Przed ukończeniem szablonu projektu należy przetestować go, aby upewnić się, że kompiluje i działa poprawnie.

W terminalu uruchom następujące polecenie.

```dotnetcli
dotnet run
```

Otrzymasz następujące dane wyjściowe.

```console
Hello World with C# 8.0!
```

Foldery _obj_ i _bin_ utworzone za `dotnet run`pomocą programu . Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki związane z szablonem, a nie wszystkie pliki, które są wynikiem akcji kompilacji.

Teraz, gdy masz zawartość szablonu utworzone, należy utworzyć konfigurację szablonu w folderze głównym szablonu.

## <a name="create-the-template-config"></a>Tworzenie konfiguracji szablonu

Szablony są rozpoznawane w .NET Core przez specjalny folder i plik konfiguracyjny, które istnieją w katalogu głównym szablonu. W tym samouczku folder szablonu znajduje się w _obszarze roboczy\templates\consoleasync_.

Podczas tworzenia szablonu wszystkie pliki i foldery w folderze szablonu są uwzględniane jako część szablonu z wyjątkiem specjalnego folderu konfiguratornego. Ten folder konfiguracyjny nosi nazwę _.template.config_.

Najpierw utwórz nowy podfolder o nazwie _.template.config_, wprowadź go. Następnie utwórz nowy plik o nazwie _template.json_. Struktura folderów powinna wyglądać tak.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Otwórz _szablon.json_ z ulubionym edytorem tekstu i wklej w poniższym kodzie json i zapisz go.

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

Ten plik konfiguracyjny zawiera wszystkie ustawienia szablonu. Możesz zobaczyć podstawowe ustawienia, `name` `shortName` takie jak i `tags/type` ale jest też `project`wartość, która jest ustawiona na . Oznacza to szablon jako szablon projektu. Nie ma żadnych ograniczeń co do typu tworzonego szablonu. Wartości `item` `project` i są wspólne nazwy, które program .NET Core zaleca, dzięki czemu użytkownicy mogą łatwo filtrować typ szablonu, którego szukają.

Element `classifications` reprezentuje kolumnę **tagów** wyświetlaną `dotnet new` po uruchomieniu i uzyskanie listy szablonów. Użytkownicy mogą również wyszukiwać na podstawie tagów klasyfikacji. Nie należy mylić `tags` właściwości w pliku json z listą `classifications` tagów. Są to dwie różne rzeczy, które niestety mają podobną nazwę. Pełny schemat pliku *template.json* znajduje się w [Magazynie schematów JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat pliku *template.json,* zobacz [dotnet templating wiki](https://github.com/dotnet/templating/wiki).

Teraz, gdy masz prawidłowy plik _.template.config/template.json,_ szablon jest gotowy do zainstalowania. Przed zainstalowaniem szablonu upewnij się, że usunięto wszystkie dodatkowe foldery plików i pliki, których nie chcesz uwzględnić w szablonie, takie jak _foldery bin_ lub _obj._ W terminalu przejdź do folderu _consoleasync_ i uruchom, `dotnet new -i .\` aby zainstalować szablon znajdujący się w bieżącym folderze. Jeśli używasz systemu operacyjnego Linux lub macOS, użyj `dotnet new -i ./`ukośnika do przodu: .

To polecenie wyświetla listę zainstalowanych szablonów, która powinna zawierać twoje.

```dotnetcli
dotnet new -i .\
```

Otrzymasz dane wyjściowe podobne do następującego.

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

1. Utwórz nową aplikację konsoli za pomocą następującego polecenia, które `dotnet run` generuje projekt roboczy, który można łatwo przetestować za pomocą polecenia.

    ```dotnetcli
    dotnet new consoleasync
    ```

    Otrzymasz następujące dane wyjściowe.

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. Uruchom projekt za pomocą następującego polecenia.

    ```dotnetcli
    dotnet run
    ```

    Otrzymasz następujące dane wyjściowe.

    ```console
    Hello World with C# 8.0!
    ```

Gratulacje! Utworzono i wdrożono szablon projektu za pomocą programu .NET Core. W ramach przygotowań do następnej części tej serii samouczków należy odinstalować utworzony szablon. Upewnij się, że wszystkie pliki z folderu _testowego_ też. Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.

### <a name="uninstall-the-template"></a>Odinstalowywanie szablonu

Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy go odinstalować przy **użyciu bezwzględnej** ścieżki pliku. Możesz zobaczyć listę szablonów zainstalowanych `dotnet new -u` przez uruchomienie polecenia. Szablon powinien być wymieniony jako ostatni. Użyj ścieżki wymienionej, aby odinstalować szablon za `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` pomocą polecenia.

```dotnetcli
dotnet new -u
```

Otrzymasz dane wyjściowe podobne do następującego.

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

W tym samouczku utworzono szablon projektu. Aby dowiedzieć się, jak spakować szablony elementów i projektu do łatwego w użyciu pliku, kontynuuj tę serię samouczków.

> [!div class="nextstepaction"]
> [Tworzenie pakietu szablonów](cli-templates-create-template-pack.md)
