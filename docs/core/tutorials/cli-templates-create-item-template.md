---
title: Tworzenie szablonu elementu dla dotnet nowy - .NET Core CLI
description: Dowiedz się, jak utworzyć szablon elementu dla nowego polecenia dotnet. Szablony elementów mogą zawierać dowolną liczbę plików.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503556"
---
# <a name="tutorial-create-an-item-template"></a>Samouczek: Tworzenie szablonu elementu

Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projekty, pliki, a nawet zasoby. Ten samouczek jest częścią pierwszej serii, która uczy, jak tworzyć, instalować i odinstalowywać szablony do użycia z poleceniem. `dotnet new`

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
>
> * Tworzenie klasy dla szablonu elementu
> * Tworzenie folderu i pliku konfiguracji szablonu
> * Instalowanie szablonu ze ścieżki pliku
> * Testowanie szablonu elementu
> * Odinstalowywanie szablonu elementu

## <a name="prerequisites"></a>Wymagania wstępne

* [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.
* Przeczytaj artykuł [referencyjny Niestandardowe szablony dla dotnet nowy](../tools/custom-templates.md).

  W artykule referencyjnym wyjaśniono podstawy dotyczące szablonów i sposobu ich łączenia. Niektóre z tych informacji zostaną powtórzone tutaj.

* Otwórz terminal i przejdź do folderu _working\templates._

## <a name="create-the-required-folders"></a>Tworzenie wymaganych folderów

Ta seria używa "folderu roboczego", w którym znajduje się źródło szablonu, oraz "folderu testowego" używanego do testowania szablonów. Folder roboczy i folder testów powinny znajdować się w tym samym folderze nadrzędnym.

Najpierw utwórz folder nadrzędny, nazwa nie ma znaczenia. Następnie utwórz podfolder o nazwie _praca_. Wewnątrz folderu _roboczego_ utwórz podfolder o nazwie _szablony_.

Następnie utwórz folder w folderze nadrzędnym o nazwie _test_. Struktura folderów powinna wyglądać następująco.

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Tworzenie szablonu elementu

Szablon elementu jest określonym typem szablonu, który zawiera jeden lub więcej plików. Te typy szablonów są przydatne, gdy chcesz wygenerować coś takiego jak plik konfiguracyjny, kod lub plik rozwiązania. W tym przykładzie utworzysz klasę, która dodaje metodę rozszerzenia do typu ciągu.

W terminalu przejdź do folderu _working\templates_ i utwórz nowy podfolder o nazwie _rozszerzenia_. Wprowadź folder.

```console
working
└───templates
    └───extensions
```

Utwórz nowy plik o nazwie _CommonExtensions.cs_ i otwórz go za pomocą ulubionego edytora tekstu. Ta klasa zapewni metodę `Reverse` rozszerzenia o nazwie, która odwraca zawartość ciągu. Wklej w następującym kodzie i zapisz plik:

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

Teraz, gdy masz zawartość szablonu utworzone, należy utworzyć konfigurację szablonu w folderze głównym szablonu.

## <a name="create-the-template-config"></a>Tworzenie konfiguracji szablonu

Szablony są rozpoznawane w .NET Core przez specjalny folder i plik konfiguracyjny, które istnieją w katalogu głównym szablonu. W tym samouczku folder szablonu znajduje się w _obszarze roboczo-szablony\rozszerzenia_.

Podczas tworzenia szablonu wszystkie pliki i foldery w folderze szablonu są uwzględniane jako część szablonu z wyjątkiem specjalnego folderu konfiguratornego. Ten folder konfiguracyjny nosi nazwę _.template.config_.

Najpierw utwórz nowy podfolder o nazwie _.template.config_, wprowadź go. Następnie utwórz nowy plik o nazwie _template.json_. Struktura folderów powinna wyglądać tak:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Otwórz _szablon.json_ za pomocą ulubionego edytora tekstu i wklej w poniższym kodzie JSON i zapisz go.

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

Ten plik konfiguracyjny zawiera wszystkie ustawienia szablonu. Możesz zobaczyć podstawowe ustawienia, `name` takie `shortName`jak i , `tags/type` ale jest też `item`wartość, która jest ustawiona na . Ta kategoryzuje szablon jako szablon elementu. Nie ma żadnych ograniczeń co do typu tworzonego szablonu. Wartości `item` `project` i są wspólne nazwy, które program .NET Core zaleca, dzięki czemu użytkownicy mogą łatwo filtrować typ szablonu, którego szukają.

Element `classifications` reprezentuje kolumnę **tagów** wyświetlaną `dotnet new` po uruchomieniu i uzyskanie listy szablonów. Użytkownicy mogą również wyszukiwać na podstawie tagów klasyfikacji. Nie należy mylić `tags` właściwości \*w pliku json `classifications` z listą tagów. Są to dwie różne rzeczy, które niestety mają podobną nazwę. Pełny schemat pliku *template.json* znajduje się w [Magazynie schematów JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat pliku *template.json,* zobacz [dotnet templating wiki](https://github.com/dotnet/templating/wiki).

Teraz, gdy masz prawidłowy plik _.template.config/template.json,_ szablon jest gotowy do zainstalowania. W terminalu przejdź do folderu _rozszerzeń_ i uruchom następujące polecenie, aby zainstalować szablon znajdujący się w bieżącym folderze:

* **W systemie Windows**:`dotnet new -i .\`
* **W systemie Linux lub macOS**:`dotnet new -i ./`

To polecenie wyświetla listę zainstalowanych szablonów, która powinna zawierać twoje.

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

Teraz, gdy masz zainstalowany szablon elementu, przetestuj go. Przejdź do _folderu test/_ i utwórz nową aplikację konsoli z . `dotnet new console` Spowoduje to wygenerowanie projektu roboczego, `dotnet run` który można łatwo przetestować za pomocą polecenia.

```dotnetcli
dotnet new console
```

Otrzymasz dane wyjściowe podobne do następującego.

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

Uruchom projekt za pomocą.

```dotnetcli
dotnet run
```

Otrzymasz następujące dane wyjściowe.

```console
Hello World!
```

Następnie uruchom, `dotnet new stringext` aby wygenerować _CommonExtensions.cs_ z szablonu.

```dotnetcli
dotnet new stringext
```

Otrzymasz następujące dane wyjściowe.

```console
The template "Example templates: string extensions" was created successfully.
```

Zmień kod w _Program.cs,_ aby odwrócić `"Hello World"` ciąg z metody rozszerzenia dostarczone przez szablon.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Uruchom program ponownie, a zobaczysz, że wynik jest odwrócony.

```dotnetcli
dotnet run
```

Otrzymasz następujące dane wyjściowe.

```console
!dlroW olleH
```

Gratulacje! Utworzono i wdrożono szablon elementu za pomocą programu .NET Core. W ramach przygotowań do następnej części tej serii samouczków należy odinstalować utworzony szablon. Upewnij się, że wszystkie pliki z folderu _testowego_ też. Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.

## <a name="uninstall-the-template"></a>Odinstalowywanie szablonu

Ponieważ szablon został zainstalowany według ścieżki pliku, należy go odinstalować za pomocą **bezwzględnej** ścieżki pliku. Możesz zobaczyć listę szablonów zainstalowanych `dotnet new -u` przez uruchomienie polecenia. Szablon powinien być wymieniony jako ostatni. Użyj ścieżki wymienionej, aby odinstalować szablon za `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` pomocą polecenia.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

Aby odinstalować szablon, uruchom następujące polecenie.

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono szablon elementu. Aby dowiedzieć się, jak utworzyć szablon projektu, kontynuuj tę serię samouczków.

> [!div class="nextstepaction"]
> [Tworzenie szablonu projektu](cli-templates-create-project-template.md)
