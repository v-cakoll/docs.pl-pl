---
title: Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core
description: W tym samouczku wyjaśniono, jak organizowanie i testowanie projektów .NET Core z poziomu wiersza polecenia.
author: cartermp
ms.author: mairaw
ms.date: 09/10/2018
ms.openlocfilehash: 8131e51577bcad9191c0cacb61317fa146bf476d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580361"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="bc34d-103">Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="bc34d-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="bc34d-104">W tym samouczku następuje [rozpoczęcie pracy z platformą .NET Core w Windows/Linux/macOS przy użyciu wiersza polecenia](using-with-xplat-cli.md), otwieranie poza tworzenia aplikacji konsolowej proste do tworzenia zaawansowanych i dobrze zorganizowanego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc34d-104">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="bc34d-105">Po pokazujący, jak używać folderów do organizowania kodu, w tym samouczku dowiesz się, jak rozszerzyć aplikację konsoli przy użyciu [xUnit](https://xunit.github.io/) struktury testowania.</span><span class="sxs-lookup"><span data-stu-id="bc34d-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="bc34d-106">Za pomocą folderów do organizowania kodu</span><span class="sxs-lookup"><span data-stu-id="bc34d-106">Using folders to organize code</span></span>

<span data-ttu-id="bc34d-107">Wprowadzenie nowych typów do aplikacji konsoli, możesz to zrobić, dodając pliki zawierające typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc34d-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="bc34d-108">Na przykład w przypadku dodania plików zawierających `AccountInformation` i `MonthlyReportRecords` typów do projektu, struktura pliku projektu jest daje płaski i nawigację:</span><span class="sxs-lookup"><span data-stu-id="bc34d-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="bc34d-109">Jednak ta działa tylko w dobrze po stosunkowo mały rozmiar projektu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="bc34d-110">Możesz sobie wyobrazić co się stanie po dodaniu 20 typów do projektu?</span><span class="sxs-lookup"><span data-stu-id="bc34d-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="bc34d-111">Zdecydowanie projektu nie być łatwe do nawigowania i obsługa z tym wiele plików littering katalogu głównego projektu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="bc34d-112">Aby zorganizować projekt, Utwórz nowy folder i nadaj mu nazwę *modeli* do przechowywania plików typu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="bc34d-113">Umieść pliki typu do *modeli* folderu:</span><span class="sxs-lookup"><span data-stu-id="bc34d-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="bc34d-114">Projekty, które logicznie grupy plików do folderów, które są łatwe do nawigowania i obsługa.</span><span class="sxs-lookup"><span data-stu-id="bc34d-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="bc34d-115">W następnej sekcji utworzysz przykładowe bardziej złożonych z folderów i testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="bc34d-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="bc34d-116">Organizowanie i testowanie, korzystając z przykładu zwierzęta NewTypes</span><span class="sxs-lookup"><span data-stu-id="bc34d-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="bc34d-117">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="bc34d-117">Building the sample</span></span>

<span data-ttu-id="bc34d-118">Dla następujących kroków możesz albo kontynuować pracę przy użyciu [przykładowe zwierzęta NewTypes](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub tworzyć własne pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="bc34d-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="bc34d-119">Typy są logicznie pogrupowane w strukturę folderów, która zezwala na dodawanie większej liczby typów później, a testy również logicznie są umieszczane w folderach, umożliwiające dodanie więcej testów później.</span><span class="sxs-lookup"><span data-stu-id="bc34d-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="bc34d-120">Przykład zawiera dwa typy `Dog` i `Cat`i ma mu w zaimplementowaniu wspólny interfejs `IPet`.</span><span class="sxs-lookup"><span data-stu-id="bc34d-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="bc34d-121">Aby uzyskać `NewTypes` projektu, dowiesz się, jak organizowania typów powiązanych pet do *zwierzęta* folderu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="bc34d-122">Jeśli inny zestaw typów zostanie dodany później *WildAnimals* na przykład, są umieszczane w *NewTypes* folder wraz z *zwierzęta* folderu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="bc34d-123">*WildAnimals* folderu może zawierają typy służące do zwierząt, które nie są zwierząt domowych, takich jak `Squirrel` i `Rabbit` typów.</span><span class="sxs-lookup"><span data-stu-id="bc34d-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="bc34d-124">W ten sposób podczas dodawania typów projektu pozostaje dobrze zorganizowane.</span><span class="sxs-lookup"><span data-stu-id="bc34d-124">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="bc34d-125">Utwórz następującą strukturę folderów z zawartością pliku wskazanego:</span><span class="sxs-lookup"><span data-stu-id="bc34d-125">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="bc34d-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="bc34d-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="bc34d-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="bc34d-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="bc34d-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="bc34d-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="bc34d-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="bc34d-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="bc34d-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="bc34d-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="bc34d-131">Wykonaj następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="bc34d-131">Execute the following command:</span></span>

```console
dotnet run
```

<span data-ttu-id="bc34d-132">Uzyskaj następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bc34d-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="bc34d-133">Opcjonalne Ćwiczenia: można dodać nowy typ domowych, takich jak `Bird`, rozszerzając tego projektu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="bc34d-134">Należy z lotu ptaka `TalkToOwner` zapewniają metody `Tweet!` do właściciela.</span><span class="sxs-lookup"><span data-stu-id="bc34d-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="bc34d-135">Ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="bc34d-135">Run the app again.</span></span> <span data-ttu-id="bc34d-136">Dane wyjściowe będą zawierać `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="bc34d-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="bc34d-137">Badanie próbki</span><span class="sxs-lookup"><span data-stu-id="bc34d-137">Testing the sample</span></span>

<span data-ttu-id="bc34d-138">`NewTypes` Projektu w miejscu, a ułożone ją, przechowując typy związane z zwierzęta w folderze.</span><span class="sxs-lookup"><span data-stu-id="bc34d-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="bc34d-139">Następnie utwórz projekt testu i zacząć pisać testy z [xUnit](https://xunit.github.io/) struktury testowej.</span><span class="sxs-lookup"><span data-stu-id="bc34d-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="bc34d-140">Testy jednostkowe umożliwia automatyczne sprawdzenie dostępności bevahior pet typów, aby upewnić się, że są one działających prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="bc34d-140">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="bc34d-141">Tworzenie *test* folder z *NewTypesTests* folder znajdujący się w nim.</span><span class="sxs-lookup"><span data-stu-id="bc34d-141">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="bc34d-142">W wierszu polecenia z *NewTypesTests* folderu wykonaj `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="bc34d-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="bc34d-143">Pozwala to na utworzenie dwóch plików: *NewTypesTests.csproj* i *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="bc34d-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="bc34d-144">Projekt testowy nie może obecnie testowanie typów w `NewTypes` i wymaga odwołania projektu do `NewTypes` projektu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="bc34d-145">Aby dodać odwołanie do projektu, należy użyć [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="bc34d-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="bc34d-146">Istnieje również opcja ręcznego dodawania odwołania projektu, dodając `<ItemGroup>` węzeł *NewTypesTests.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="bc34d-146">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="bc34d-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="bc34d-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="bc34d-148">*NewTypesTests.csproj* plik zawiera następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bc34d-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="bc34d-149">Odwołanie do pakietu `Microsoft.NET.Test.Sdk`, .NET, testowanie infrastruktury</span><span class="sxs-lookup"><span data-stu-id="bc34d-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="bc34d-150">Odwołanie do pakietu `xunit`, xUnit, struktury testowania</span><span class="sxs-lookup"><span data-stu-id="bc34d-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="bc34d-151">Odwołanie do pakietu `xunit.runner.visualstudio`, narzędzia test runner</span><span class="sxs-lookup"><span data-stu-id="bc34d-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="bc34d-152">Odwołanie do projektu `NewTypes`, kod do testowania</span><span class="sxs-lookup"><span data-stu-id="bc34d-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="bc34d-153">Zmień nazwę *UnitTest1.cs* do *PetTests.cs* i Zastąp kod w pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="bc34d-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="bc34d-154">Opcjonalne Ćwiczenia: Jeśli dodano `Bird` wcześniej typ, który daje `Tweet!` do właściciela, należy dodać metody testowej, aby *PetTests.cs* pliku `BirdTalkToOwnerReturnsTweet`, aby sprawdzić, czy `TalkToOwner` metoda działa prawidłowo dla `Bird` typu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="bc34d-155">Mimo że można oczekiwać, że `expected` i `actual` wartości są równe, początkowe potwierdzenie z `Assert.NotEqual` wyboru określa, czy te wartości są *równa*.</span><span class="sxs-lookup"><span data-stu-id="bc34d-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="bc34d-156">Zawsze utworzyć test, aby zakończyć się niepowodzeniem, aby sprawdzić logikę testu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="bc34d-157">Po upewnieniu się, że test zakończy się niepowodzeniem, należy dostosować potwierdzenie, aby zezwolić na test kończył się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bc34d-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="bc34d-158">Poniżej przedstawiono strukturę kompletnego projektu:</span><span class="sxs-lookup"><span data-stu-id="bc34d-158">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="bc34d-159">Rozpocznij w *testów/NewTypesTests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="bc34d-160">Przywróć projekt testowy z [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="bc34d-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="bc34d-161">Uruchom testy przy użyciu [ `dotnet test` ](../tools/dotnet-test.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="bc34d-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="bc34d-162">To polecenie uruchamia narzędzie test runner, określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-162">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="bc34d-163">Zgodnie z oczekiwaniami, testowania kończy się niepowodzeniem i konsoli wyświetlane następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="bc34d-163">As expected, testing fails, and the console displays the following output:</span></span>

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="bc34d-164">Zmień potwierdzenia testów z `Assert.NotEqual` do `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="bc34d-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="bc34d-165">Ponownie uruchom testy z `dotnet test` polecenia i uzyskać następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="bc34d-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="bc34d-166">Testowanie przebiegów.</span><span class="sxs-lookup"><span data-stu-id="bc34d-166">Testing passes.</span></span> <span data-ttu-id="bc34d-167">Typów pet zwracają poprawne wartości w przypadku do właściciela.</span><span class="sxs-lookup"><span data-stu-id="bc34d-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="bc34d-168">Wyjaśniono techniki organizowanie i testowanie projektów przy użyciu xUnit.</span><span class="sxs-lookup"><span data-stu-id="bc34d-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="bc34d-169">Przejdź do przodu, za pomocą tych metod, stosując je do własnych projektów.</span><span class="sxs-lookup"><span data-stu-id="bc34d-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="bc34d-170">*Udanego kodowania!*</span><span class="sxs-lookup"><span data-stu-id="bc34d-170">*Happy coding!*</span></span>

