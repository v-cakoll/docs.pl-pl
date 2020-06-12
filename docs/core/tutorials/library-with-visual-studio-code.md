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
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="befda-103">Samouczek: Tworzenie biblioteki .NET Standard przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="befda-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="befda-104">W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="befda-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="befda-105">Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="befda-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="befda-106">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="befda-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="befda-107">Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="befda-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="befda-108">Po zakończeniu biblioteki klas można ją rozpowszechnić jako składnik innej firmy lub jako składnik pakietu z jedną lub wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="befda-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="befda-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="befda-109">Prerequisites</span></span>

1. <span data-ttu-id="befda-110">[Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="befda-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="befda-111">Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="befda-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="befda-112">[Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="befda-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="befda-113">Tworzenie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="befda-113">Create a solution</span></span>

<span data-ttu-id="befda-114">Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w.</span><span class="sxs-lookup"><span data-stu-id="befda-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="befda-115">Rozwiązanie służy jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="befda-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="befda-116">Dodasz kolejne powiązane projekty do tego samego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="befda-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="befda-117">Uruchom program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="befda-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="befda-118">Wybierz pozycję **plik**  >  **Otwórz folder** (**Otwórz...** na macOS) z menu głównego</span><span class="sxs-lookup"><span data-stu-id="befda-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="befda-119">W oknie dialogowym **Otwieranie folderu** Utwórz folder *ClassLibraryProjects* , a następnie kliknij pozycję **Wybierz folder** (**Otwórz** w macOS).</span><span class="sxs-lookup"><span data-stu-id="befda-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="befda-120">Otwórz **Terminal** w Visual Studio Code, wybierając pozycję **Wyświetl**  >  **Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="befda-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="befda-121">Zostanie otwarty **Terminal** z wierszem polecenia w folderze *ClassLibraryProjects* .</span><span class="sxs-lookup"><span data-stu-id="befda-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="befda-122">W **terminalu**wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="befda-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="befda-123">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="befda-124">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="befda-124">Create a class library project</span></span>

<span data-ttu-id="befda-125">Dodaj nowy projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="befda-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="befda-126">W terminalu uruchom następujące polecenie, aby utworzyć projekt biblioteki:</span><span class="sxs-lookup"><span data-stu-id="befda-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="befda-127">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="befda-128">Uruchom następujące polecenie, aby dodać projekt biblioteki do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="befda-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="befda-129">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="befda-130">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="befda-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="befda-131">W **Eksploratorze**Otwórz *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="befda-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="befda-132">`TargetFramework`Element pokazuje, że projekt jest docelowy .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="befda-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="befda-133">Otwórz *Class1.cs* i Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="befda-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="befda-134">Biblioteka klas, `UtilityLibraries.StringLibrary` ,,, zawiera metodę o nazwie `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="befda-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="befda-135">Ta metoda zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="befda-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="befda-136">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="befda-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="befda-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda zwraca `true` czy znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="befda-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="befda-138">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="befda-138">Save the file.</span></span>

1. <span data-ttu-id="befda-139">Uruchom następujące polecenie, aby skompilować rozwiązanie i sprawdzić, czy projekt kompiluje się bez błędu.</span><span class="sxs-lookup"><span data-stu-id="befda-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="befda-140">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-140">The terminal output looks like the following example:</span></span>

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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="befda-141">Dodawanie aplikacji konsolowej do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="befda-141">Add a console app to the solution</span></span>

<span data-ttu-id="befda-142">Dodaj aplikację konsolową, która używa biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="befda-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="befda-143">Aplikacja wyświetli monit o wprowadzenie ciągu i zgłoszenie, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="befda-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="befda-144">W terminalu uruchom następujące polecenie, aby utworzyć projekt aplikacji konsoli:</span><span class="sxs-lookup"><span data-stu-id="befda-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="befda-145">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="befda-146">Uruchom następujące polecenie, aby dodać projekt aplikacji konsolowej do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="befda-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="befda-147">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="befda-148">Otwórz *Pokaz/Program. cs* i Zastąp cały kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="befda-148">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="befda-149">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="befda-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="befda-150">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="befda-150">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="befda-151">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="befda-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="befda-152">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="befda-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="befda-153">Jeśli użytkownik naciśnie klawisz <kbd>Enter</kbd> bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="befda-153">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="befda-154">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="befda-154">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="befda-155">Dodaj odwołanie do projektu</span><span class="sxs-lookup"><span data-stu-id="befda-155">Add a project reference</span></span>

<span data-ttu-id="befda-156">Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="befda-156">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="befda-157">Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="befda-157">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="befda-158">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="befda-158">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="befda-159">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-159">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="befda-160">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="befda-160">Run the app</span></span>

1. <span data-ttu-id="befda-161">Uruchom następujące polecenie w terminalu:</span><span class="sxs-lookup"><span data-stu-id="befda-161">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="befda-162">Wypróbuj program, wprowadzając ciągi i naciskając klawisz <kbd>Enter</kbd>, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="befda-162">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="befda-163">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="befda-163">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="befda-164">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="befda-164">Additional resources</span></span>

* [<span data-ttu-id="befda-165">Tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="befda-165">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="befda-166">[Wersje .NET Standard i obsługiwane przez nich platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="befda-166">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="befda-167">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="befda-167">Next steps</span></span>

<span data-ttu-id="befda-168">W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki.</span><span class="sxs-lookup"><span data-stu-id="befda-168">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="befda-169">W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="befda-169">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="befda-170">Testowanie biblioteki .NET Standard za pomocą platformy .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="befda-170">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
