---
title: Testowanie jednostkowe Visual Basic w .NET Core z testowaniem dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych w oprogramowaniu .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania Visual Basic krok po kroku przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: c587aaa5c4c50ec66ac6cd8cd7aefd7b0ca1a80c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715424"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Testowanie jednostkowe Visual Basic biblioteki .NET Core przy użyciu testu dotnet i xUnit

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Tests-VB-using-dotnet-test* w celu przechowania rozwiązania.
W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) , aby utworzyć nowe rozwiązanie. To rozwiązanie ułatwia zarządzanie zarówno biblioteką klas, jak i projektem testów jednostkowych.
W katalogu rozwiązania Utwórz katalog *PrimeService* . W tej chwili istnieje następujący katalog i struktura pliku:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Ustaw *PrimeService* w bieżącym katalogu i uruchom [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy. Zmień nazwę *Class1. vb* na *PrimeService. vb*. Tworzysz nieprawidłową implementację klasy `PrimeService`:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Zmień katalog z powrotem na katalog *testy jednostkowe — VB-using-dotnet-test* . Uruchom [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie Utwórz katalog *PrimeService. Tests* . Poniższy konspekt przedstawia strukturę katalogów:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt przy użyciu [`dotnet new xunit -lang VB`](../tools/dotnet-new.md). To polecenie tworzy projekt testowy, który używa xUnit jako biblioteki testowej. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w *PrimeServiceTests. vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new` w poprzednim kroku został dodany xUnit i moduł uruchamiający xUnit. Teraz dodaj bibliotekę klas `PrimeService` jako inną zależność do projektu. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.

Istnieje następujący końcowy układ folderu:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Wykonaj [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) w katalogu *testowania jednostkowego — VB-using-dotnet-test* . 

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. Usuń *UnitTest1. vb* z katalogu *PrimeService. Tests* i Utwórz nowy plik Visual Basic o nazwie *PrimeService_IsPrimeShould. vb*. Dodaj następujący kod:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Atrybut `<Fact>` oznacza metodę testową, która jest uruchamiana przez program Test Runner. Z poziomu *testu jednostkowego-using-dotnet-test*wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchomić testy. Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test` uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w klasie `PrimeService`, która działa:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

W katalogu *testy jednostkowe — VB-using-dotnet-test* uruchom ponownie `dotnet test`. `dotnet test` polecenie uruchamia kompilację dla projektu `PrimeService`, a następnie dla projektu `PrimeService.Tests`. Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0,-1. Te przypadki można dodać jako nowe testy z atrybutem `<Fact>`, ale szybko żmudnym. Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestawu podobnych testów.  Atrybut `<Theory>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Możesz użyć atrybutu `<InlineData>`, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty, aby utworzyć jedno teoretyczne. Teoretyczna jest metoda, która sprawdza kilka wartości mniejszej niż dwa, które jest najniższą liczbą:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem. Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić klauzulę `if` na początku metody:

```vb
if candidate < 2
```

Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej. Masz [ukończoną wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [kompletną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).

Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy. Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.
