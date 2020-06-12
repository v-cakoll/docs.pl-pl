---
title: Tworzenie biblioteki klas .NET Standard przy użyciu Visual Studio Code
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard przy użyciu Visual Studio Code.
ms.date: 06/08/2020
ms.openlocfilehash: f7d2319bcea58f63ca40e43ba39745bdf1b394ce
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701802"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a>Samouczek: Tworzenie biblioteki .NET Standard przy użyciu Visual Studio Code

W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów. Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.

*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard. Po zakończeniu biblioteki klas można ją rozpowszechnić jako składnik innej firmy lub jako składnik pakietu z jedną lub wieloma aplikacjami.

## <a name="prerequisites"></a>Wymagania wstępne

1. [Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) . Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>Tworzenie rozwiązania

Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w. Rozwiązanie służy jako kontener dla jednego lub wielu projektów. Dodasz kolejne powiązane projekty do tego samego rozwiązania.

1. Uruchom program Visual Studio Code.

1. Wybierz pozycję **plik**  >  **Otwórz folder** (**Otwórz...** na macOS) z menu głównego

1. W oknie dialogowym **Otwieranie folderu** Utwórz folder *ClassLibraryProjects* , a następnie kliknij pozycję **Wybierz folder** (**Otwórz** w macOS).

1. Otwórz **Terminal** w Visual Studio Code, wybierając pozycję **Wyświetl**  >  **Terminal** z menu głównego.

   Zostanie otwarty **Terminal** z wierszem polecenia w folderze *ClassLibraryProjects* .

1. W **terminalu**wprowadź następujące polecenie:

   ```dotnetcli
   dotnet new sln
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>Tworzenie projektu biblioteki klas

Dodaj nowy projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.

1. W terminalu uruchom następujące polecenie, aby utworzyć projekt biblioteki:

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. Uruchom następujące polecenie, aby dodać projekt biblioteki do rozwiązania:

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard. W **Eksploratorze**Otwórz *StringLibrary/StringLibrary. csproj*.

   `TargetFramework`Element pokazuje, że projekt jest docelowy .NET Standard 2,0.

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. Otwórz *Class1.cs* i Zastąp kod następującym kodem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   Biblioteka klas, `UtilityLibraries.StringLibrary` ,,, zawiera metodę o nazwie `StartsWithUpper` . Ta metoda zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery. Standard Unicode rozróżnia wielkie litery od małych liter. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda zwraca `true` czy znak jest pisany wielką literą.

1. Zapisz plik.

1. Uruchom następujące polecenie, aby skompilować rozwiązanie i sprawdzić, czy projekt kompiluje się bez błędu.

   ```dotnetcli
   dotnet build
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a>Dodawanie aplikacji konsolowej do rozwiązania

Dodaj aplikację konsolową, która używa biblioteki klas. Aplikacja wyświetli monit o wprowadzenie ciągu i zgłoszenie, czy ciąg rozpoczyna się od wielkiej litery.

1. W terminalu uruchom następujące polecenie, aby utworzyć projekt aplikacji konsoli:

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. Uruchom następujące polecenie, aby dodać projekt aplikacji konsolowej do rozwiązania:

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. Otwórz *Pokaz/Program. cs* i Zastąp cały kod następującym kodem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz <kbd>Enter</kbd> bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.

1. Zapisz zmiany.

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas.

1. Uruchom następujące polecenie:

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. Uruchom następujące polecenie w terminalu:

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. Wypróbuj program, wprowadzając ciągi i naciskając klawisz <kbd>Enter</kbd>, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść.

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a>Zasoby dodatkowe

* [Tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core](libraries.md)
* [Wersje .NET Standard i obsługiwane przez nich platformy](../../standard/net-standard.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki. W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.

> [!div class="nextstepaction"]
> [Testowanie biblioteki .NET Standard za pomocą platformy .NET Core przy użyciu Visual Studio Code](testing-library-with-visual-studio-code.md)
