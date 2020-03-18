---
title: Organizowanie i testowanie projektów za pomocą cli .NET Core
description: W tym samouczku wyjaśniono, jak organizować i testować projekty programu .NET Core z wiersza polecenia.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 0d61e0fc004cfcb6d78c49475c7b7f0f523aad2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239914"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="b5c82-103">Organizowanie i testowanie projektów za pomocą cli .NET Core</span><span class="sxs-lookup"><span data-stu-id="b5c82-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="b5c82-104">Ten samouczek następuje [Wprowadzenie do .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia,](cli-create-console-app.md)co prowadzi do tworzenia prostej aplikacji konsoli do tworzenia zaawansowanych i dobrze zorganizowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5c82-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="b5c82-105">Po pokazaniu, jak używać folderów do organizowania kodu, w tym samouczku pokazano, jak rozszerzyć aplikację konsoli za pomocą struktury testowania [xUnit.](https://xunit.github.io/)</span><span class="sxs-lookup"><span data-stu-id="b5c82-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="b5c82-106">Organizowanie kodu za pomocą folderów</span><span class="sxs-lookup"><span data-stu-id="b5c82-106">Using folders to organize code</span></span>

<span data-ttu-id="b5c82-107">Jeśli chcesz wprowadzić nowe typy do aplikacji na konsolę, możesz to zrobić, dodając do niej pliki zawierające te typy.</span><span class="sxs-lookup"><span data-stu-id="b5c82-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="b5c82-108">Na przykład w przypadku `AccountInformation` `MonthlyReportRecords` dodania plików zawierających i typów do projektu struktura plików projektu jest płaska i łatwa w nawigacji:</span><span class="sxs-lookup"><span data-stu-id="b5c82-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="b5c82-109">Jednak to działa dobrze tylko wtedy, gdy rozmiar projektu jest stosunkowo mały.</span><span class="sxs-lookup"><span data-stu-id="b5c82-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="b5c82-110">Czy możesz sobie wyobrazić, co się stanie, jeśli dodasz 20 typów do projektu?</span><span class="sxs-lookup"><span data-stu-id="b5c82-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="b5c82-111">Projekt na pewno nie będzie łatwy w nawigacji i konserwacji z tym wieloma plikami zaśmiecającymi katalog główny projektu.</span><span class="sxs-lookup"><span data-stu-id="b5c82-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="b5c82-112">Aby zorganizować projekt, utwórz nowy folder i nadać mu nazwę *Modele* do przechowywania plików typów.</span><span class="sxs-lookup"><span data-stu-id="b5c82-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="b5c82-113">Umieść pliki typów w folderze *Modele:*</span><span class="sxs-lookup"><span data-stu-id="b5c82-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="b5c82-114">Projekty, które logicznie grupują pliki w foldery, są łatwe w nawigacji i konserwacji.</span><span class="sxs-lookup"><span data-stu-id="b5c82-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="b5c82-115">W następnej sekcji utworzysz bardziej złożoną próbkę z folderami i testami jednostkowymi.</span><span class="sxs-lookup"><span data-stu-id="b5c82-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="b5c82-116">Organizowanie i testowanie przy użyciu newtypes zwierzęta próbki</span><span class="sxs-lookup"><span data-stu-id="b5c82-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="b5c82-117">Tworzenie próbki</span><span class="sxs-lookup"><span data-stu-id="b5c82-117">Building the sample</span></span>

<span data-ttu-id="b5c82-118">Aby wykonać następujące kroki, można wykonać wzdłuż za pomocą [NewTypes Zwierzęta próbki](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub utworzyć własne pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="b5c82-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="b5c82-119">Typy są logicznie zorganizowane w strukturę folderów, która pozwala na dodanie więcej typów później i testy są również logicznie umieszczone w folderach, co pozwala na dodanie więcej testów później.</span><span class="sxs-lookup"><span data-stu-id="b5c82-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="b5c82-120">Przykład zawiera dwa `Dog` typy `Cat`i , i ma `IPet`je zaimplementować wspólny interfejs, .</span><span class="sxs-lookup"><span data-stu-id="b5c82-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="b5c82-121">W `NewTypes` projekcie twoim celem jest zorganizowanie typów związanych ze zwierzętami domowymi w folderze *Zwierzęta domowe.*</span><span class="sxs-lookup"><span data-stu-id="b5c82-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="b5c82-122">Jeśli inny zestaw typów zostanie dodany później, *WildAnimals* na przykład, są one umieszczane w *NewTypes* folderu obok *folderu Zwierzęta.*</span><span class="sxs-lookup"><span data-stu-id="b5c82-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="b5c82-123">Folder *WildAnimals* może zawierać typy dla zwierząt, które `Squirrel` `Rabbit` nie są zwierzętami domowymi, takie jak i typy.</span><span class="sxs-lookup"><span data-stu-id="b5c82-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="b5c82-124">W ten sposób, jak typy są dodawane, projekt pozostaje dobrze zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="b5c82-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="b5c82-125">Utwórz następującą strukturę folderów ze wskazaną zawartością pliku:</span><span class="sxs-lookup"><span data-stu-id="b5c82-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="b5c82-126">*IPet.cs:*</span><span class="sxs-lookup"><span data-stu-id="b5c82-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="b5c82-127">*Dog.cs:*</span><span class="sxs-lookup"><span data-stu-id="b5c82-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="b5c82-128">*Cat.cs:*</span><span class="sxs-lookup"><span data-stu-id="b5c82-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="b5c82-129">*Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="b5c82-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="b5c82-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="b5c82-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="b5c82-131">Wykonaj następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b5c82-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="b5c82-132">Uzyskaj następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b5c82-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="b5c82-133">Opcjonalne ćwiczenie: Możesz dodać nowy typ `Bird`zwierzęcia, na przykład , rozszerzając ten projekt.</span><span class="sxs-lookup"><span data-stu-id="b5c82-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="b5c82-134">Spraw, aby `TalkToOwner` metoda ptaka dała `Tweet!` właścicielowi.</span><span class="sxs-lookup"><span data-stu-id="b5c82-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="b5c82-135">Ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b5c82-135">Run the app again.</span></span> <span data-ttu-id="b5c82-136">Dane wyjściowe obędą się między`Tweet!`</span><span class="sxs-lookup"><span data-stu-id="b5c82-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="b5c82-137">Testowanie próbki</span><span class="sxs-lookup"><span data-stu-id="b5c82-137">Testing the sample</span></span>

<span data-ttu-id="b5c82-138">Projekt `NewTypes` jest na miejscu i zorganizowałeś go, utrzymując typy związane ze zwierzętami domowymi w folderze.</span><span class="sxs-lookup"><span data-stu-id="b5c82-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="b5c82-139">Następnie utwórz projekt testowy i rozpocznij pisanie testów za pomocą struktury testów [xUnit.](https://xunit.github.io/)</span><span class="sxs-lookup"><span data-stu-id="b5c82-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="b5c82-140">Testowanie jednostkowe pozwala automatycznie sprawdzić zachowanie typów zwierząt domowych, aby potwierdzić, że działają prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="b5c82-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="b5c82-141">Wróć do folderu *src* i utwórz folder *testowy* z folderem *NewTypesTests* w nim.</span><span class="sxs-lookup"><span data-stu-id="b5c82-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="b5c82-142">W wierszu polecenia z folderu `dotnet new xunit` *NewTypesTests* wykonaj polecenie .</span><span class="sxs-lookup"><span data-stu-id="b5c82-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="b5c82-143">Spowoduje to wygenerowanie dwóch plików: *NewTypesTests.csproj* i *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="b5c82-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="b5c82-144">Projekt testowy nie może `NewTypes` obecnie przetestować typów `NewTypes` i wymaga odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5c82-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="b5c82-145">Aby dodać odwołanie do [`dotnet add reference`](../tools/dotnet-add-reference.md) projektu, użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="b5c82-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="b5c82-146">Lub masz również możliwość ręcznego dodawania odwołania `<ItemGroup>` do projektu, dodając węzeł do pliku *NewTypesTests.csproj:*</span><span class="sxs-lookup"><span data-stu-id="b5c82-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="b5c82-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="b5c82-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="b5c82-148">Plik *NewTypesTests.csproj* zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b5c82-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="b5c82-149">Odwołanie do `Microsoft.NET.Test.Sdk`pakietu , infrastruktury testowania .NET</span><span class="sxs-lookup"><span data-stu-id="b5c82-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="b5c82-150">Odwołanie do `xunit`pakietu , xUnit testing framework</span><span class="sxs-lookup"><span data-stu-id="b5c82-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="b5c82-151">Odniesienie do `xunit.runner.visualstudio`opakowania do , biegacza testowego</span><span class="sxs-lookup"><span data-stu-id="b5c82-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="b5c82-152">Odwołanie do `NewTypes`projektu , kod do testowania</span><span class="sxs-lookup"><span data-stu-id="b5c82-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="b5c82-153">Zmień nazwę *UnitTest1.cs,* aby *PetTests.cs* i zastąpić kod w pliku następującymi nazwami:</span><span class="sxs-lookup"><span data-stu-id="b5c82-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="b5c82-154">Opcjonalne ćwiczenie: Jeśli `Bird` wcześniej dodano typ, `Tweet!` który daje właścicielowi, dodaj metodę `BirdTalkToOwnerReturnsTweet`testową do `TalkToOwner` *pliku PetTests.cs,* aby `Bird` sprawdzić, czy metoda działa poprawnie dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="b5c82-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="b5c82-155">Mimo że można `expected` `actual` oczekiwać, że i wartości `Assert.NotEqual` są równe, wstępne twierdzenie z sprawdzaniem określa, że te wartości nie są *równe*.</span><span class="sxs-lookup"><span data-stu-id="b5c82-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="b5c82-156">Zawsze początkowo utworzyć test do niepowodzeniem w celu sprawdzenia logiki testu.</span><span class="sxs-lookup"><span data-stu-id="b5c82-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="b5c82-157">Po potwierdzeniu, że test nie powiedzie się, dostosuj potwierdzenie, aby umożliwić test do przejścia.</span><span class="sxs-lookup"><span data-stu-id="b5c82-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="b5c82-158">Poniżej przedstawiono pełną strukturę projektu:</span><span class="sxs-lookup"><span data-stu-id="b5c82-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="b5c82-159">Rozpocznij w katalogu *test/NewTypesTests.*</span><span class="sxs-lookup"><span data-stu-id="b5c82-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="b5c82-160">Przywróć projekt testowy za [`dotnet restore`](../tools/dotnet-restore.md) pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="b5c82-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="b5c82-161">Uruchom testy za [`dotnet test`](../tools/dotnet-test.md) pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="b5c82-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="b5c82-162">To polecenie uruchamia testrunner określony w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b5c82-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b5c82-163">Zgodnie z oczekiwaniami testowanie kończy się niepowodzeniem, a konsola wyświetla następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b5c82-163">As expected, testing fails, and the console displays the following output:</span></span>

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

<span data-ttu-id="b5c82-164">Zmień potwierdzeń testów `Assert.NotEqual` z: `Assert.Equal`</span><span class="sxs-lookup"><span data-stu-id="b5c82-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="b5c82-165">Ponownie uruchom testy za `dotnet test` pomocą polecenia i uzyskaj następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b5c82-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="b5c82-166">Testowanie zdań.</span><span class="sxs-lookup"><span data-stu-id="b5c82-166">Testing passes.</span></span> <span data-ttu-id="b5c82-167">Metody typów zwierząt domowych zwracają poprawne wartości podczas rozmowy z właścicielem.</span><span class="sxs-lookup"><span data-stu-id="b5c82-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="b5c82-168">Nauczyłeś się technik organizowania i testowania projektów przy użyciu xUnit.</span><span class="sxs-lookup"><span data-stu-id="b5c82-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="b5c82-169">Śmiało z tych technik stosowania ich w swoich własnych projektów.</span><span class="sxs-lookup"><span data-stu-id="b5c82-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="b5c82-170">*Szczęśliwego kodowania!*</span><span class="sxs-lookup"><span data-stu-id="b5c82-170">*Happy coding!*</span></span>
