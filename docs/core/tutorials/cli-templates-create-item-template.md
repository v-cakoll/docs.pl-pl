---
title: Utwórz szablon elementu dla platformy dotnet new - interfejsu wiersza polecenia platformy .NET Core
description: Dowiedz się, jak utworzyć szablon elementu dla nowego polecenia dotnet. Szablony elementów może zawierać dowolną liczbę plików.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877178"
---
# <a name="tutorial-create-an-item-template"></a>Samouczek: Utworzyć szablon elementu

Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projektów, plików i nawet zasobów. Niniejszy samouczek jest drugą częścią serii, pokazujący sposób tworzenia, instalowanie i odinstalowywanie szablonów do użytku z programem `dotnet new` polecenia.

W tej części serii, dowiesz się, jak:

> [!div class="checklist"]
> * Utwórz klasę dla szablonu elementu
> * Utwórz folder konfiguracji szablonu i pliku
> * Zainstaluj szablon ze ścieżki plików
> * Testowanie szablonu elementu
> * Odinstaluj szablon elementu

## <a name="prerequisites"></a>Wymagania wstępne

* [Zestaw SDK programu .NET core 2.2](https://www.microsoft.com/net/core) lub nowszy.
* Zapoznaj się z artykułami odwołanie [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md).

  Dokumentacja wyjaśniono podstawowe informacje o szablonach i jak są one Podsumowując. Niektóre z tych informacji będzie powtarzać w tym miejscu.

* Otwórz terminal i przejdź do _working\templates\\_  folderu.

## <a name="create-the-required-folders"></a>Utwórz wymagane foldery

W tej serii używa "folderu roboczego" gdzie znajduje się Twoje źródło szablonu i używane do testowania szablonów "testowania folderu". Folder roboczy i folder testowania powinny znajdować się w tym samym folderze nadrzędnym.

Najpierw utwórz folder nadrzędny, nazwa nie ma znaczenia. Następnie utwórz podfolder o nazwie _pracy_. Wewnątrz _pracy_ folderze utwórz podfolder o nazwie _szablony_.

Następnie utwórz folder w folderze nadrzędnym, o nazwie _testu_. Struktura folderów powinien wyglądać następująco:

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Utworzyć szablon elementu

Szablon elementu jest określonego typu szablonu, który zawiera jeden lub więcej plików. Te typy szablonów są przydatne, gdy chcesz wygenerować coś, takich jak konfiguracja, kodu lub pliku rozwiązania. W tym przykładzie utworzysz klasę, która dodaje metodę rozszerzenia typu string.

W terminalu przejdź do _working\templates\\_  folderze i utworzyć nowy podfolder o nazwie _rozszerzenia_. Wprowadź folder.

```console
working
└───templates
    └───extensions
```

Utwórz nowy plik o nazwie _CommonExtensions.cs_ i otwórz go za pomocą ulubionego edytora tekstu. Ta klasa zapewni metodę rozszerzenia o nazwie `Reverse` który odwraca zawartość ciągu. Wklej następujący kod, a następnie zapisz plik:

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

Teraz, gdy zawartość utworzony szablon, musisz utworzyć konfiguracji szablonu w folderze głównym szablonu.

## <a name="create-the-template-config"></a>Tworzenie konfiguracji szablonu

Szablony są rozpoznawane w programie .NET Core, przez plik specjalny folder i konfiguracji, który istnieje w katalogu głównym szablonu. W tym samouczku folderu szablon znajduje się w _working\templates\extensions\\_ .

Podczas tworzenia szablonu, wszystkie pliki i foldery w folderze szablonu są dołączane jako część szablonu z wyjątkiem folder konfiguracji specjalnych. Ten folder konfiguracji nosi nazwę _. template.config_.

Najpierw utwórz nowy podfolder o nazwie _. template.config_, wprowadź go. Następnie utwórz nowy plik o nazwie _template.json_. Twoja struktura folderów powinien wyglądać następująco:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Otwórz _template.json_ tekstem ulubionym edytorze i wklej następujący kod JSON kod i zapisz go:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

Ten plik konfiguracji zawiera ustawienia szablonu. Widać podstawowe ustawienia, takie jak `name` i `shortName`, ale jest również `tags/type` wartość, która jest równa `item`. Ta klasyfikuje szablon jako szablon elementu. Nie ma żadnych ograniczeń na typ tworzonego szablonu. `item` i `project` wartości to pospolite nazwy, które platformy .NET Core zaleca, aby użytkownicy z łatwością można filtrować szablonu są wyszukiwane.

`classifications` Element reprezentuje **tagi** kolumny zostanie wyświetlony po uruchomieniu `dotnet new` i Uzyskaj listę szablonów. Użytkownicy mogą również przeszukiwać na podstawie klasyfikacji tagów. Nie należy mylić `tags` właściwość \*plik JSON z `classifications` lista tagów. Są one dwie różne rzeczy Niestety o nazwie podobnie. Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat *template.json* plików, zobacz [wiki szablonów dotnet](https://github.com/dotnet/templating/wiki).

Teraz, gdy masz prawidłową _.template.config/template.json_ pliku, szablon będzie gotowy do zainstalowania. W terminalu przejdź do _rozszerzenia_ folderu i uruchom następujące polecenie, aby zainstalować szablon znajdujący się w bieżącym folderze:

* **Na Windows**: `dotnet new -i .\`
* **W systemie Linux lub macOS**: `dotnet new -i ./`

To polecenie wyświetla listę zainstalowane, szablony, które powinien zawierać należy do Ciebie.

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a>Testowanie szablonu elementu

Teraz, gdy szablon elementu, który jest zainstalowany, należy go przetestować. Przejdź do _testów /_ folderze i utworzyć nową aplikację konsoli przy użyciu `dotnet new console`. Spowoduje to wygenerowanie projektu pracy, możesz łatwo przeprowadzić test za `dotnet run` polecenia.

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

Następnie uruchom `dotnet new stringext` do generowania _CommonExtensions.cs_ z szablonu.

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

Zmień kod w _Program.cs_ odwrócić `"Hello World"` ciągu przy użyciu metody rozszerzenia udostępniane przez szablon.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Ponownie uruchom program i zobaczysz, że wynik zostanie odwrócony.

```console
C:\test> dotnet run
!dlroW olleH
```

Gratulacje! Utworzyć i wdrożyć szablon elementu za pomocą programu .NET Core. W ramach przygotowania do następnej części tej serii samouczków należy odinstalować szablon, który został utworzony. Upewnij się usunąć wszystkie pliki z _test_ folderu zbyt. To będzie wrócić do stanu czystego gotowy do następnej sekcji głównej części tego samouczka.

## <a name="uninstall-the-template"></a>Odinstaluj szablonu

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono szablon elementu. Aby dowiedzieć się, jak utworzyć szablon projektu, przejdź w tej serii samouczków.

> [!div class="nextstepaction"]
> [Tworzenie szablonu projektu](cli-templates-create-project-template.md)
