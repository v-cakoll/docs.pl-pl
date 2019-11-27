---
title: Testowanie jednostkowe Visual Basic w .NET Core z testowaniem dotnet i NUnit
description: Poznaj koncepcje testów jednostkowych w oprogramowaniu .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania Visual Basic krok po kroku przy użyciu NUnit.
author: rprouse
ms.date: 10/04/2018
ms.custom: seodec18
ms.openlocfilehash: 4776916c316e18de954c8ccaa985075dc2ea0fc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428728"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Testowanie jednostkowe Visual Basic biblioteki .NET Core przy użyciu testu dotnet i NUnit

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje.
- Edytor tekstu lub Edytor kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Tests-VB-nunit* , aby obtrzymać rozwiązanie. W tym nowym katalogu Uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```dotnetcli
dotnet new sln
```

Następnie Utwórz katalog *PrimeService* . Poniższy konspekt przedstawia strukturę plików do tej pory:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Ustaw *PrimeService* w bieżącym katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```dotnetcli
dotnet new classlib -lang VB
```

Zmień nazwę *Class1. vb* na *PrimeService. vb*. Tworzysz nieprawidłową implementację klasy `PrimeService`:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Zmień katalog z powrotem na katalog *Test Unit-VB-using-MSTest* . Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie Utwórz katalog *PrimeService. Tests* . Poniższy konspekt przedstawia strukturę katalogów:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą następującego polecenia:

```dotnetcli
dotnet new nunit -lang VB
```

Polecenie [dotnet New](../tools/dotnet-new.md) umożliwia utworzenie projektu testowego, który używa nunit jako biblioteki testowej. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeServiceTests. vbproj* :

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new` w poprzednim kroku został dodany NUnit i adapter testowy NUnit. Teraz dodaj bibliotekę klas `PrimeService` jako inną zależność do projektu. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.

Dysponujesz następującym końcowym układem rozwiązań:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

Wykonaj następujące polecenie w katalogu *Unit-Test-VB-nunit* :

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. W katalogu *PrimeService. Tests* Zmień nazwę pliku *UnitTest1. vb* na *PrimeService_IsPrimeShould. vb* i Zastąp całą zawartość następującym kodem:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Atrybut `<TestFixture>` wskazuje klasę, która zawiera testy. Atrybut `<Test>` oznacza metodę, która jest uruchamiana przez program Test Runner. W ramach *testów jednostkowych-VB-nunit*wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchomić testy. Program NUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test` uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w klasie `PrimeService`, która działa:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

W katalogu *testy jednostkowe — VB-nunit* ponownie uruchom `dotnet test`. `dotnet test` polecenie uruchamia kompilację dla projektu `PrimeService`, a następnie dla projektu `PrimeService.Tests`. Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0,-1. Te przypadki można dodać jako nowe testy z atrybutem `<Test>`, ale szybko żmudnym. Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestawu podobnych testów.  Atrybut `<TestCase>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Możesz użyć atrybutu `<TestCase>`, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty, aby utworzyć serię testów, które testują kilka wartości mniejszej niż dwa, czyli najniższy numer podstawowy:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem. Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić klauzulę `if` na początku metody `Main` w pliku *PrimeServices.cs* :

```vb
if candidate < 2
```

Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej. Masz [ukończoną wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [kompletną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy. Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.
