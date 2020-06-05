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
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a><span data-ttu-id="9ec8f-103">Samouczek: Tworzenie biblioteki .NET Standard w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ec8f-103">Tutorial: Create a .NET Standard library in Visual Studio Code</span></span>

<span data-ttu-id="9ec8f-104">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="9ec8f-105">Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="9ec8f-106">Po zakończeniu biblioteki klas można zdecydować, czy chcesz ją rozpowszechnić jako pakiet NuGet, czy dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-106">When you finish your class library, you can decide whether you want to distribute it as a NuGet package or include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="9ec8f-107">Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="9ec8f-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="9ec8f-108">W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="9ec8f-109">Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ec8f-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9ec8f-110">Prerequisites</span></span>

1. <span data-ttu-id="9ec8f-111">[Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="9ec8f-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="9ec8f-112">Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="9ec8f-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="9ec8f-113">[Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="9ec8f-113">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="9ec8f-114">Tworzenie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9ec8f-114">Create a solution</span></span>

<span data-ttu-id="9ec8f-115">Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="9ec8f-116">Rozwiązanie służy jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="9ec8f-117">Dodasz kolejne powiązane projekty do tego samego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="9ec8f-118">Otwórz program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-118">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="9ec8f-119">Wybierz pozycję **plik**  >  **Otwórz folder** / **Otwórz...** z menu głównego, Utwórz folder *ClassLibraryProjects* , a następnie kliknij pozycję **Wybierz folder** / **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-119">Select **File** > **Open Folder**/**Open...** from the main menu, create a *ClassLibraryProjects* folder, and click **Select Folder**/**Open**.</span></span>

1. <span data-ttu-id="9ec8f-120">Otwórz **Terminal** w Visual Studio Code, wybierając pozycję **Wyświetl**  >  **Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="9ec8f-121">Zostanie otwarty **Terminal** z wierszem polecenia w folderze *ClassLibraryProjects* .</span><span class="sxs-lookup"><span data-stu-id="9ec8f-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="9ec8f-122">W **terminalu**wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="9ec8f-123">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="9ec8f-124">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="9ec8f-124">Create a class library project</span></span>

<span data-ttu-id="9ec8f-125">Dodaj nowy projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="9ec8f-126">W terminalu uruchom następujące polecenie, aby utworzyć projekt biblioteki:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="9ec8f-127">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="9ec8f-128">Uruchom następujące polecenie, aby dodać projekt biblioteki do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="9ec8f-129">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="9ec8f-130">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="9ec8f-131">W **Eksploratorze**Otwórz *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="9ec8f-132">`TargetFramework`Element pokazuje, że projekt jest docelowy .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="9ec8f-133">Otwórz *Class1.cs* i Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="9ec8f-134">Biblioteka klas, `UtilityLibraries.StringLibrary` ,,, zawiera metodę o nazwie `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="9ec8f-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="9ec8f-135">Ta metoda zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="9ec8f-136">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="9ec8f-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda zwraca `true` czy znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="9ec8f-138">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-138">Save the file.</span></span>

1. <span data-ttu-id="9ec8f-139">Uruchom następujące polecenie, aby skompilować rozwiązanie i sprawdzić, czy projekt kompiluje się bez błędu.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="9ec8f-140">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-140">The terminal output looks like the following example:</span></span>

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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="9ec8f-141">Dodawanie aplikacji konsolowej do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9ec8f-141">Add a console app to the solution</span></span>

<span data-ttu-id="9ec8f-142">Dodaj aplikację konsolową, która używa biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="9ec8f-143">Aplikacja wyświetli monit o wprowadzenie ciągu i zgłoszenie, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="9ec8f-144">W terminalu uruchom następujące polecenie, aby utworzyć projekt aplikacji konsoli:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="9ec8f-145">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="9ec8f-146">Uruchom następujące polecenie, aby dodać projekt aplikacji konsolowej do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="9ec8f-147">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="9ec8f-148">Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-148">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="9ec8f-149">Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-149">To allow it to call methods in the class library, create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="9ec8f-150">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-150">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. <span data-ttu-id="9ec8f-151">Otwórz *Pokaz/Program. cs* i Zastąp cały kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-151">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="9ec8f-152">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-152">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="9ec8f-153">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-153">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="9ec8f-154">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-154">The program prompts the user to enter a string.</span></span> <span data-ttu-id="9ec8f-155">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-155">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="9ec8f-156">Jeśli użytkownik naciśnie klawisz ENTER bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-156">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="9ec8f-157">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-157">Save your changes.</span></span>

1. <span data-ttu-id="9ec8f-158">Uruchom program.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-158">Run the program.</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="9ec8f-159">Wypróbuj program, wprowadzając ciągi i naciskając klawisz <kbd>Enter</kbd>, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-159">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="9ec8f-160">Dane wyjściowe terminalu wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ec8f-160">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="9ec8f-161">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9ec8f-161">Additional resources</span></span>

* [<span data-ttu-id="9ec8f-162">Tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ec8f-162">Develop libraries with the .NET Core CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="9ec8f-163">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9ec8f-163">Next steps</span></span>

<span data-ttu-id="9ec8f-164">W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-164">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="9ec8f-165">W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9ec8f-165">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9ec8f-166">Testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ec8f-166">Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
