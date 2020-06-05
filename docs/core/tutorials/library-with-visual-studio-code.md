---
title: Tworzenie biblioteki klas .NET Standard w Visual Studio Code
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard przy użyciu Visual Studio Code.
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446955"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a>Samouczek: Tworzenie biblioteki .NET Standard w programie Visual Studio Code

*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard. Po zakończeniu biblioteki klas można zdecydować, czy chcesz ją rozpowszechnić jako pakiet NuGet, czy dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.

> [!NOTE]
> Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).

W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów. Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.

## <a name="prerequisites"></a>Wymagania wstępne

1. [Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) . Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>Tworzenie rozwiązania

Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w. Rozwiązanie służy jako kontener dla jednego lub wielu projektów. Dodasz kolejne powiązane projekty do tego samego rozwiązania.

1. Otwórz program Visual Studio Code.

1. Wybierz pozycję **plik**  >  **Otwórz folder** / **Otwórz...** z menu głównego, Utwórz folder *ClassLibraryProjects* , a następnie kliknij pozycję **Wybierz folder** / **Otwórz**.

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

1. Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas, uruchamiając następujące polecenie:

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. Otwórz *Pokaz/Program. cs* i Zastąp cały kod następującym kodem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz ENTER bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.

1. Zapisz zmiany.

1. Uruchom program.

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

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki. W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.

> [!div class="nextstepaction"]
> [Testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio Code](testing-library-with-visual-studio-code.md)
