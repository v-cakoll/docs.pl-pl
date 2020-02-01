---
title: Organizowanie i testowanie projektów przy użyciu interfejs wiersza polecenia platformy .NET Core
description: W tym samouczku wyjaśniono sposób organizowania i testowania projektów programu .NET Core z poziomu wiersza polecenia.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 11d13ad1d74c69cdfe0626bda8823dd0609da85f
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920423"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="e3e84-103">Organizowanie i testowanie projektów przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e3e84-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="e3e84-104">Ten samouczek rozpoczyna [się od rozpoczęcia pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia, dzięki](cli-create-console-app.md)czemu nie utworzysz prostej aplikacji konsolowej do tworzenia zaawansowanych i dobrze zorganizowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3e84-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="e3e84-105">Po podaniu, jak używać folderów do organizowania kodu, w tym samouczku pokazano, jak zwiększyć aplikację konsolową za pomocą platformy testowania [xUnit](https://xunit.github.io/) .</span><span class="sxs-lookup"><span data-stu-id="e3e84-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="e3e84-106">Organizowanie kodu przy użyciu folderów</span><span class="sxs-lookup"><span data-stu-id="e3e84-106">Using folders to organize code</span></span>

<span data-ttu-id="e3e84-107">Jeśli chcesz wprowadzić nowe typy do aplikacji konsoli, możesz to zrobić przez dodanie plików zawierających typy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3e84-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="e3e84-108">Na przykład jeśli dodasz pliki zawierające `AccountInformation` i typy `MonthlyReportRecords` do projektu, struktura pliku projektu jest płaska i łatwa do przechodzenia:</span><span class="sxs-lookup"><span data-stu-id="e3e84-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="e3e84-109">Jednak jest to dobre rozwiązanie tylko wtedy, gdy rozmiar projektu jest stosunkowo mały.</span><span class="sxs-lookup"><span data-stu-id="e3e84-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="e3e84-110">Czy można przystąpić do tego, co się stanie, jeśli dodasz 20 typów do projektu?</span><span class="sxs-lookup"><span data-stu-id="e3e84-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="e3e84-111">Projekt w nieskończoność nie może być w łatwy sposób przechodzenia i konserwowania w wielu plikach, w których znajduje się katalog główny projektu.</span><span class="sxs-lookup"><span data-stu-id="e3e84-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="e3e84-112">Aby zorganizować projekt, Utwórz nowy folder i nadaj mu nazwę *modele* , aby przechowywać pliki typu.</span><span class="sxs-lookup"><span data-stu-id="e3e84-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="e3e84-113">Umieść pliki typu w folderze *modele* :</span><span class="sxs-lookup"><span data-stu-id="e3e84-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="e3e84-114">Projekty, które logicznie grupują pliki do folderów, są łatwe do przechodzenia i konserwowania.</span><span class="sxs-lookup"><span data-stu-id="e3e84-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="e3e84-115">W następnej sekcji utworzysz bardziej skomplikowany przykład z użyciem folderów i testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="e3e84-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="e3e84-116">Organizowanie i testowanie przy użyciu przykładu NewTypes zwierząt domowych</span><span class="sxs-lookup"><span data-stu-id="e3e84-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="e3e84-117">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="e3e84-117">Building the sample</span></span>

<span data-ttu-id="e3e84-118">Poniższe kroki można wykonać przy użyciu [przykładowej NewTypes zwierząt domowych](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub utworzyć własne pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="e3e84-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="e3e84-119">Typy są logicznie zorganizowane ze strukturą folderów, która umożliwia dodanie więcej typów później, a testy są również logicznie umieszczane w folderach, co pozwala na dodanie dalszych testów później.</span><span class="sxs-lookup"><span data-stu-id="e3e84-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="e3e84-120">Przykład zawiera dwa typy, `Dog` i `Cat`i ma implementację wspólnego interfejsu, `IPet`.</span><span class="sxs-lookup"><span data-stu-id="e3e84-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="e3e84-121">W przypadku projektu `NewTypes` celem jest zorganizowanie typów związanych z PET w folderze *zwierząt domowych* .</span><span class="sxs-lookup"><span data-stu-id="e3e84-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="e3e84-122">Jeśli później zostanie dodany inny zestaw typów, *WildAnimals* na przykład, są umieszczane w folderze *NewTypes* obok folderu *zwierzęta* .</span><span class="sxs-lookup"><span data-stu-id="e3e84-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="e3e84-123">Folder *WildAnimals* może zawierać typy dla zwierząt, które nie są zwierzętami, takimi jak `Squirrel` i `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="e3e84-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="e3e84-124">W ten sposób, gdy są dodawane typy, projekt pozostaje dobrze zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="e3e84-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="e3e84-125">Utwórz następującą strukturę folderów z wyróżnioną zawartością pliku:</span><span class="sxs-lookup"><span data-stu-id="e3e84-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="e3e84-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="e3e84-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="e3e84-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="e3e84-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="e3e84-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="e3e84-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="e3e84-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="e3e84-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="e3e84-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="e3e84-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="e3e84-131">Wykonaj następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e3e84-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="e3e84-132">Uzyskaj następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e3e84-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="e3e84-133">Ćwiczenie opcjonalne: można dodać nowy typ PET, taki jak `Bird`, rozszerzając ten projekt.</span><span class="sxs-lookup"><span data-stu-id="e3e84-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="e3e84-134">Nadaj metodu `TalkToOwner` ptakowi `Tweet!` do właściciela.</span><span class="sxs-lookup"><span data-stu-id="e3e84-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="e3e84-135">Uruchom aplikację ponownie.</span><span class="sxs-lookup"><span data-stu-id="e3e84-135">Run the app again.</span></span> <span data-ttu-id="e3e84-136">Dane wyjściowe będą zawierać `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="e3e84-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="e3e84-137">Testowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="e3e84-137">Testing the sample</span></span>

<span data-ttu-id="e3e84-138">Projekt `NewTypes` jest na miejscu i został zorganizowany przez utrzymywanie typów związanych ze zwierzętami ze zwierząt domowych w folderze.</span><span class="sxs-lookup"><span data-stu-id="e3e84-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="e3e84-139">Następnie utwórz projekt testowy i zacznij pisać testy za pomocą platformy testów [xUnit](https://xunit.github.io/) .</span><span class="sxs-lookup"><span data-stu-id="e3e84-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="e3e84-140">Testy jednostkowe umożliwiają automatyczne sprawdzanie zachowania typów PET w celu potwierdzenia, że działają prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="e3e84-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="e3e84-141">Przejdź z powrotem do folderu *src* i Utwórz folder *testowy* z folderem *NewTypesTests* w nim.</span><span class="sxs-lookup"><span data-stu-id="e3e84-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="e3e84-142">W wierszu polecenia w folderze *NewTypesTests* należy wykonać `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="e3e84-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="e3e84-143">Spowoduje to utworzenie dwóch plików: *NewTypesTests. csproj* i *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="e3e84-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="e3e84-144">Projekt testowy nie może obecnie testować typów w `NewTypes` i wymaga odwołania projektu do projektu `NewTypes`.</span><span class="sxs-lookup"><span data-stu-id="e3e84-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="e3e84-145">Aby dodać odwołanie do projektu, użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="e3e84-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="e3e84-146">Lub można także ręcznie dodać odwołanie do projektu, dodając węzeł `<ItemGroup>` do pliku *NewTypesTests. csproj* :</span><span class="sxs-lookup"><span data-stu-id="e3e84-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="e3e84-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="e3e84-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="e3e84-148">Plik *NewTypesTests. csproj* zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="e3e84-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="e3e84-149">Odwołanie do pakietu do `Microsoft.NET.Test.Sdk`, infrastruktura testowa platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e3e84-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="e3e84-150">Odwołanie do pakietu do `xunit`, struktura testowania xUnit</span><span class="sxs-lookup"><span data-stu-id="e3e84-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="e3e84-151">Odwołanie do pakietu do `xunit.runner.visualstudio`, moduł uruchamiający testy</span><span class="sxs-lookup"><span data-stu-id="e3e84-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="e3e84-152">Odwołanie do projektu do `NewTypes`, kod do przetestowania</span><span class="sxs-lookup"><span data-stu-id="e3e84-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="e3e84-153">Zmień nazwę *UnitTest1.cs* na *PetTests.cs* i Zastąp kod w pliku następującym:</span><span class="sxs-lookup"><span data-stu-id="e3e84-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="e3e84-154">Opcjonalne ćwiczenie: w przypadku dodania typu `Bird` wcześniej, który generuje `Tweet!` do właściciela, Dodaj metodę testową do pliku *PetTests.cs* , `BirdTalkToOwnerReturnsTweet`, aby sprawdzić, czy metoda `TalkToOwner` działa prawidłowo dla typu `Bird`.</span><span class="sxs-lookup"><span data-stu-id="e3e84-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="e3e84-155">Chociaż oczekuje się, że wartości `expected` i `actual` są równe, wstępne potwierdzenie ze sprawdzaniem `Assert.NotEqual` określa, że te wartości *nie są równe*.</span><span class="sxs-lookup"><span data-stu-id="e3e84-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="e3e84-156">Zawsze należy utworzyć test, aby nie można było sprawdzić logiki testu.</span><span class="sxs-lookup"><span data-stu-id="e3e84-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="e3e84-157">Po upewnieniu się, że test zakończy się niepowodzeniem, Dostosuj potwierdzenie, aby zezwolić na przekazanie testu.</span><span class="sxs-lookup"><span data-stu-id="e3e84-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="e3e84-158">Poniżej przedstawiono kompletną strukturę projektu:</span><span class="sxs-lookup"><span data-stu-id="e3e84-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="e3e84-159">Uruchom w katalogu *test/NewTypesTests* .</span><span class="sxs-lookup"><span data-stu-id="e3e84-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="e3e84-160">Przywróć projekt testowy za pomocą polecenia [`dotnet restore`](../tools/dotnet-restore.md) .</span><span class="sxs-lookup"><span data-stu-id="e3e84-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="e3e84-161">Uruchom testy za pomocą polecenia [`dotnet test`](../tools/dotnet-test.md) .</span><span class="sxs-lookup"><span data-stu-id="e3e84-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="e3e84-162">To polecenie uruchamia program Test Runner określony w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e3e84-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="e3e84-163">Zgodnie z oczekiwaniami testowanie nie powiedzie się, a w konsoli programu zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e3e84-163">As expected, testing fails, and the console displays the following output:</span></span>

```output
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

<span data-ttu-id="e3e84-164">Zmień potwierdzenia testów z `Assert.NotEqual` na `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="e3e84-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="e3e84-165">Uruchom testy za pomocą polecenia `dotnet test` i uzyskaj następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e3e84-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="e3e84-166">Testowanie przebiega.</span><span class="sxs-lookup"><span data-stu-id="e3e84-166">Testing passes.</span></span> <span data-ttu-id="e3e84-167">Metody typów PET zwracają poprawne wartości podczas rozmowy z właścicielem.</span><span class="sxs-lookup"><span data-stu-id="e3e84-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="e3e84-168">Wiesz już, jak można organizować i testować projekty przy użyciu xUnit.</span><span class="sxs-lookup"><span data-stu-id="e3e84-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="e3e84-169">Przejdź do tych technik, stosując je we własnych projektach.</span><span class="sxs-lookup"><span data-stu-id="e3e84-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="e3e84-170">*Radosne kodowanie!*</span><span class="sxs-lookup"><span data-stu-id="e3e84-170">*Happy coding!*</span></span>
