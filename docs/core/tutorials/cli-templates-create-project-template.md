---
title: Utwórz nowy szablon projektu służący do dotnet
description: Dowiedz się, jak utworzyć szablon projektu służący do nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877181"
---
# <a name="tutorial-create-a-project-template"></a>Samouczek: Tworzenie szablonu projektu

Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projektów, plików i nawet zasobów. Niniejszy samouczek jest drugą częścią serii, pokazujący sposób tworzenia, instalowanie i odinstalowywanie szablonów do użytku z programem `dotnet new` polecenia.

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
> * Tworzenie zasobów szablonu projektu
> * Utwórz folder konfiguracji szablonu i pliku
> * Zainstaluj szablon ze ścieżki plików
> * Testowanie szablonu elementu
> * Odinstaluj szablon elementu

## <a name="prerequisites"></a>Wymagania wstępne

* Pełne [część 1](cli-templates-create-item-template.md) z tej serii samouczka.
* Otwórz terminal i przejdź do _working\templates\\_  folderu.

## <a name="create-a-project-template"></a>Tworzenie szablonu projektu

Projekt szablony produktu gotowe do uruchomienia projektów, które ułatwiają użytkownikom na początek z zestawu roboczego kodu. .NET core zawiera kilka szablonów projektu, np. aplikację konsolową w języku lub biblioteki klas. W tym przykładzie utworzysz nowy projekt konsoli, która umożliwia C# 8.0 i tworzy `async main` punktu wejścia.

W terminalu przejdź do _working\templates\\_  folderze i utworzyć nowy podfolder o nazwie _consoleasync_. Wprowadź podfolderu, a następnie uruchom `dotnet new console` do generowania aplikacji konsoli standardowej. Pliki tworzone przez ten szablon, aby utworzyć nowy szablon będzie edycji.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Modyfikowanie pliku Program.cs

Otwórz _program.cs_ pliku. Projekt konsoli nie Użyj punktu wejścia asynchroniczne, więc dodać. Zmień swój kod do następujących, a następnie zapisz plik:

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

Zaktualizujmy C# wersji językowej projektu używa do wersji 8.0. Edytuj _consoleasync.csproj_ pliku i Dodaj `<LangVersion>` ustawienie `<PropertyGroup>` węzła.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Skompiluj projekt

Przed ukończeniem szablonu projektu należy przetestować ją, aby upewnić się, że kompiluje i działa poprawnie. W terminalu Uruchom `dotnet run` polecenia i powinien zostać wyświetlony następujący komunikat:

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

Możesz usunąć _obj_ i _bin_ foldery utworzone za pomocą `dotnet run`. Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki związane z szablonu i nie wszystkie pliki wynik akcji kompilacji.

Teraz, gdy zawartość utworzony szablon, musisz utworzyć konfiguracji szablonu w folderze głównym szablonu.

## <a name="create-the-template-config"></a>Tworzenie konfiguracji szablonu

Szablony są rozpoznawane w programie .NET Core, przez plik specjalny folder i konfiguracji, który istnieje w katalogu głównym szablonu. W tym samouczku folderu szablon znajduje się w _working\templates\consoleasync\\_ .

Podczas tworzenia szablonu, wszystkie pliki i foldery w folderze szablonu są dołączane jako część szablonu z wyjątkiem folder konfiguracji specjalnych. Ten folder konfiguracji nosi nazwę _. template.config_.

Najpierw utwórz nowy podfolder o nazwie _. template.config_, wprowadź go. Następnie utwórz nowy plik o nazwie _template.json_. Twoja struktura folderów powinien wyglądać następująco:

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Otwórz _template.json_ tekstem ulubionym edytorze i wklej następujący kod json kod i zapisz go:

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

Ten plik konfiguracji zawiera wszystkie ustawienia dla szablonu. Widać podstawowe ustawienia, takie jak `name` i `shortName` , ale również istnieje `tags/type` wartość, która jest równa `project`. Określa szablon jako szablon projektu. Nie ma żadnych ograniczeń na typ tworzonego szablonu. `item` i `project` wartości to pospolite nazwy, które platformy .NET Core zaleca, aby użytkownicy z łatwością można filtrować szablonu są wyszukiwane.

`classifications` Element reprezentuje **tagi** kolumny zostanie wyświetlony po uruchomieniu `dotnet new` i Uzyskaj listę szablonów. Użytkownicy mogą również przeszukiwać na podstawie klasyfikacji tagów. Nie należy mylić `tags` właściwości w pliku json z `classifications` lista tagów. Są one dwie różne rzeczy Niestety o nazwie podobnie. Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat *template.json* plików, zobacz [wiki szablonów dotnet](https://github.com/dotnet/templating/wiki).

Teraz, gdy masz prawidłową _.template.config/template.json_ pliku, szablon będzie gotowy do zainstalowania. Przed zainstalowaniem tego szablonu, upewnij się, że usuniesz wszelkie dodatkowe pliki folderów i plików, nie chcesz, zawarte w szablonie, takie jak _bin_ lub _obj_ folderów. W terminalu przejdź do _consoleasync_ folderu i uruchom `dotnet new -i .\` zainstalował szablonu znajdujący się w bieżącym folderze. Jeśli używasz systemu operacyjnego Linux lub MacOS, należy użyć ukośnika: `dotnet new -i ./`.

To polecenie wyświetla listę zainstalowane, szablony, które powinien zawierać należy do Ciebie.

```console
C:\working\templates\consoleasync> dotnet new -i .\
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

Teraz, gdy szablon elementu, który jest zainstalowany, należy go przetestować. Przejdź do _test_ folderze i utworzyć nową aplikację konsoli przy użyciu `dotnet new console`. Spowoduje to wygenerowanie projektu pracy, możesz łatwo przeprowadzić test za `dotnet run` polecenia.

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

Gratulacje! Utworzyć i wdrożyć szablon projektu za pomocą programu .NET Core. W ramach przygotowania do następnej części tej serii samouczków należy odinstalować szablon, który został utworzony. Upewnij się usunąć wszystkie pliki z _test_ folderu zbyt. To będzie wrócić do stanu czystego gotowy do następnej sekcji głównej części tego samouczka.

### <a name="uninstall-the-template"></a>Odinstaluj szablonu

Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy odinstalować ją za pomocą **bezwzględne** ścieżki pliku. Można wyświetlić listę szablonów zainstalowane, uruchamiając `dotnet new -u` polecenia. Szablon powinien zostać wyświetlony ostatnio. Użyj ścieżki wymienionymi w celu odinstalowania szablon, korzystając z `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` polecenia.

```console
C:\working> dotnet new -u
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

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono szablon projektu. Aby dowiedzieć się, jak spakować szablonów elementów i projektów w pliku łatwy w użyciu, przejdź w tej serii samouczków.

> [!div class="nextstepaction"]
> [Tworzenie szablonowego pakietu](cli-templates-create-template-pack.md)
