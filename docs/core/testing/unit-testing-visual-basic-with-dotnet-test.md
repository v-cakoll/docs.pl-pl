---
title: Testowanie jednostkowe Visual Basic w .NET Core z testowaniem dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych w oprogramowaniu .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania Visual Basic krok po kroku przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: ed1291a980f9a39284525877bab8d0a93389fbd0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702959"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="16f69-103">Testowanie jednostkowe Visual Basic biblioteki .NET Core przy użyciu testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="16f69-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="16f69-104">W tym samouczku pokazano, jak utworzyć rozwiązanie zawierające projekt testu jednostkowego i projekt biblioteki.</span><span class="sxs-lookup"><span data-stu-id="16f69-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="16f69-105">Aby postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="16f69-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="16f69-106">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="16f69-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="16f69-107">Utwórz rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="16f69-107">Create the solution</span></span>

<span data-ttu-id="16f69-108">W tej sekcji zostanie utworzone rozwiązanie zawierające projekty źródłowe i testowe.</span><span class="sxs-lookup"><span data-stu-id="16f69-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="16f69-109">Gotowe rozwiązanie ma następującą strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="16f69-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="16f69-110">Poniższe instrukcje zawierają opis kroków, które należy wykonać, aby utworzyć rozwiązanie testowe.</span><span class="sxs-lookup"><span data-stu-id="16f69-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="16f69-111">Zobacz [polecenia, aby utworzyć rozwiązanie testowe](#create-test-cmd) , aby uzyskać instrukcje dotyczące tworzenia rozwiązania testowego w jednym kroku.</span><span class="sxs-lookup"><span data-stu-id="16f69-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="16f69-112">Otwórz okno powłoki.</span><span class="sxs-lookup"><span data-stu-id="16f69-112">Open a shell window.</span></span>
* <span data-ttu-id="16f69-113">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="16f69-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="16f69-114">[`dotnet new sln`](../tools/dotnet-new.md)Polecenie tworzy nowe rozwiązanie w katalogu *testy jednostkowe-using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="16f69-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="16f69-115">Zmień katalog na folder z testami *jednostkowymi-using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="16f69-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="16f69-116">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="16f69-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="16f69-117">[`dotnet new classlib`](../tools/dotnet-new.md)Polecenie tworzy nowy projekt biblioteki klas w folderze *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="16f69-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="16f69-118">Nowa biblioteka klas będzie zawierać kod do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="16f69-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="16f69-119">Zmień nazwę *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="16f69-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="16f69-120">Zastąp kod w *PrimeService. vb* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="16f69-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="16f69-121">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="16f69-121">The preceding code:</span></span>
  * <span data-ttu-id="16f69-122">Zwraca <xref:System.NotImplementedException> komunikat informujący o tym, że nie został zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="16f69-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="16f69-123">Zostanie zaktualizowany w dalszej części samouczka.</span><span class="sxs-lookup"><span data-stu-id="16f69-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="16f69-124">W katalogu *testy jednostkowe-using-dotnet-test* Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="16f69-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="16f69-125">Utwórz projekt *PrimeService. Tests* , uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="16f69-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="16f69-126">Poprzednie polecenie:</span><span class="sxs-lookup"><span data-stu-id="16f69-126">The preceding command:</span></span>
  * <span data-ttu-id="16f69-127">Tworzy projekt *PrimeService. Tests* w katalogu *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="16f69-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="16f69-128">Projekt testowy używa [xUnit](https://xunit.net/) jako biblioteki testowej.</span><span class="sxs-lookup"><span data-stu-id="16f69-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="16f69-129">Konfiguruje moduł uruchamiający testy przez dodanie następujących `<PackageReference />` elementów do pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="16f69-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="16f69-130">"Microsoft. NET. test. SDK"</span><span class="sxs-lookup"><span data-stu-id="16f69-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="16f69-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="16f69-131">"xunit"</span></span>
    * <span data-ttu-id="16f69-132">"xUnit. Runner. VisualStudio"</span><span class="sxs-lookup"><span data-stu-id="16f69-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="16f69-133">Dodaj projekt testowy do pliku rozwiązania, uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="16f69-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="16f69-134">Dodaj `PrimeService` bibliotekę klas jako zależność do projektu *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="16f69-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="16f69-135">Polecenia służące do tworzenia rozwiązania</span><span class="sxs-lookup"><span data-stu-id="16f69-135">Commands to create the solution</span></span>

<span data-ttu-id="16f69-136">Ta sekcja podsumowuje wszystkie polecenia w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="16f69-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="16f69-137">Pomiń tę sekcję, jeśli wykonano kroki opisane w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="16f69-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="16f69-138">Następujące polecenia tworzą rozwiązanie testowe na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="16f69-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="16f69-139">W przypadku systemów macOS i UNIX zaktualizuj `ren` polecenie do wersji systemu operacyjnego, `ren` Aby zmienić nazwę pliku:</span><span class="sxs-lookup"><span data-stu-id="16f69-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="16f69-140">Postępuj zgodnie z instrukcjami dla "Zastąp kod w *PrimeService. vb* następującym kodem" w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="16f69-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="16f69-141">Tworzenie testu</span><span class="sxs-lookup"><span data-stu-id="16f69-141">Create a test</span></span>

<span data-ttu-id="16f69-142">Popularnym podejściem do programowania testowego (TDD) jest napisanie testu przed implementacją kodu docelowego.</span><span class="sxs-lookup"><span data-stu-id="16f69-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="16f69-143">W tym samouczku jest stosowane podejście TDD.</span><span class="sxs-lookup"><span data-stu-id="16f69-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="16f69-144">`IsPrime`Metoda jest wywoływana, ale nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="16f69-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="16f69-145">Wywołanie testowe `IsPrime` kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="16f69-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="16f69-146">Przy użyciu elementu TDD test jest zapisywana, że jest to niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="16f69-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="16f69-147">Kod docelowy został zaktualizowany w celu przeprowadzenia testu.</span><span class="sxs-lookup"><span data-stu-id="16f69-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="16f69-148">Powtarzaj to podejście, pisząc test zakończony niepowodzeniem, a następnie aktualizując kod docelowy do przekazania.</span><span class="sxs-lookup"><span data-stu-id="16f69-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="16f69-149">Aktualizowanie projektu *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="16f69-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="16f69-150">Usuń *PrimeService. Tests/UnitTest1. vb*.</span><span class="sxs-lookup"><span data-stu-id="16f69-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="16f69-151">Utwórz plik *PrimeService. Tests/PrimeService_IsPrimeShould. vb* .</span><span class="sxs-lookup"><span data-stu-id="16f69-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="16f69-152">Zastąp kod w *PrimeService_IsPrimeShould. vb* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="16f69-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="16f69-153">Ten `[Fact]` atrybut deklaruje metodę testową, która jest uruchamiana przez program Test Runner.</span><span class="sxs-lookup"><span data-stu-id="16f69-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="16f69-154">W folderze *PrimeService. Tests* Uruchom polecenie `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="16f69-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="16f69-155">Polecenie [test dotnet](../tools/dotnet-test.md) kompiluje oba projekty i uruchamia testy.</span><span class="sxs-lookup"><span data-stu-id="16f69-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="16f69-156">Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="16f69-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="16f69-157">`dotnet test`uruchamia program Test Runner przy użyciu projektu testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="16f69-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="16f69-158">Test zakończy się niepowodzeniem, ponieważ `IsPrime` nie został zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="16f69-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="16f69-159">Za pomocą podejścia TDD napisz tylko wystarczający kod, aby ten test zakończył się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="16f69-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="16f69-160">Zaktualizuj `IsPrime` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="16f69-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="16f69-161">Uruchom polecenie `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="16f69-161">Run `dotnet test`.</span></span> <span data-ttu-id="16f69-162">Test kończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="16f69-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="16f69-163">Dodaj więcej testów</span><span class="sxs-lookup"><span data-stu-id="16f69-163">Add more tests</span></span>

<span data-ttu-id="16f69-164">Dodaj testy z numerami podstawowymi dla 0 i-1.</span><span class="sxs-lookup"><span data-stu-id="16f69-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="16f69-165">Można skopiować poprzedni test i zmienić następujący kod, aby użyć 0 i-1:</span><span class="sxs-lookup"><span data-stu-id="16f69-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="16f69-166">Kopiowanie kodu testowego w przypadku zmiany tylko parametru powoduje duplikowanie kodu i testowanie przeładowanie.</span><span class="sxs-lookup"><span data-stu-id="16f69-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="16f69-167">Następujące atrybuty xUnit umożliwiają napisanie zestawu podobnych testów:</span><span class="sxs-lookup"><span data-stu-id="16f69-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="16f69-168">`[Theory]`reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="16f69-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="16f69-169">`[InlineData]`atrybut określa wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="16f69-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="16f69-170">Zamiast tworzyć nowe testy, Zastosuj powyższe atrybuty xUnit, aby utworzyć pojedynczy teorii.</span><span class="sxs-lookup"><span data-stu-id="16f69-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="16f69-171">Zastąp następujący kod:</span><span class="sxs-lookup"><span data-stu-id="16f69-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="16f69-172">przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="16f69-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="16f69-173">W poprzednim kodzie `[Theory]` i `[InlineData]` Włącz testowanie kilku wartości mniejszej niż dwa.</span><span class="sxs-lookup"><span data-stu-id="16f69-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="16f69-174">Dwa to najmniejszy numer podstawowy.</span><span class="sxs-lookup"><span data-stu-id="16f69-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="16f69-175">Uruchomienie `dotnet test` , dwa testy kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="16f69-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="16f69-176">Aby wszystkie testy zostały zakończone, zaktualizuj `IsPrime` metodę przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="16f69-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="16f69-177">Postępując zgodnie z podejściem TDD, Dodaj więcej testów zakończonych niepowodzeniem, a następnie zaktualizuj kod docelowy.</span><span class="sxs-lookup"><span data-stu-id="16f69-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="16f69-178">Zobacz kompletną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="16f69-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="16f69-179">Zakończona `IsPrime` Metoda nie jest wydajnym algorytmem testowania primality.</span><span class="sxs-lookup"><span data-stu-id="16f69-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="16f69-180">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="16f69-180">Additional resources</span></span>

- [<span data-ttu-id="16f69-181">Oficjalna witryna xUnit.net</span><span class="sxs-lookup"><span data-stu-id="16f69-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="16f69-182">Testowanie logiki kontrolera w ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="16f69-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
