---
title: Testowanie jednostkowe języka Visual Basic w programie .NET Core z testem dotnetowym i jednostką xUnit
description: Poznaj pojęcia dotyczące testów jednostkowych w programie .NET Core, korzystając z interaktywnego środowiska, w ramach które krok po kroku tworzenie przykładowego rozwiązania Visual Basic przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240951"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Testowanie jednostkowe bibliotek programu Visual Basic .NET Core przy użyciu testu dotnet i xUnit

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *unit-testing-vb-using-dotnet-test* do przechowywania rozwiązania.
Wewnątrz tego nowego [`dotnet new sln`](../tools/dotnet-new.md) katalogu uruchom, aby utworzyć nowe rozwiązanie. Ta praktyka ułatwia zarządzanie zarówno biblioteki klas i projektu testu jednostkowego.
W katalogu rozwiązania utwórz katalog *PrimeService.* Do tej pory masz następującą strukturę katalogów i plików:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Utwórz *PrimeService* bieżący [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) katalog i uruchom, aby utworzyć projekt źródłowy. Zmień nazwę *Class1.VB* na *PrimeService.VB*. Tworzenie nieudanej implementacji `PrimeService` klasy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Zmień katalog z powrotem do *katalogu testów jednostkowych-vb-using-dotnet-test.* Uruchom, [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) aby dodać projekt biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie utwórz katalog *PrimeService.Tests.* Poniższy konspekt przedstawia strukturę katalogów:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService.Tests* jako bieżący katalog [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)i utwórz nowy projekt przy użyciu . To polecenie tworzy projekt testowy, który używa xUnit jako biblioteki testów. Wygenerowany szablon konfiguruje testrunner w *PrimeServiceTests.vbproj:*

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano xUnit i xUnit runner. Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) w uspolu GitHub.

Masz następujący ostateczny układ folderu:

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

Wykonaj [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) w katalogu *testów jednostkowych-vb-using-dotnet-test.*

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces. Usuń *UnitTest1.vb* z katalogu *PrimeService.Tests* i utwórz nowy plik Języka Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*. Dodaj następujący kod:

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

Atrybut `<Fact>` oznacza metodę testową, która jest uruchamiana przez test runner. Z *jednostki testowania za pomocą dotnet-test*, wykonaj [`dotnet test`](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchomić testy. Program testowy xUnit zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

Test nie powiedzie się. Implementacja nie została jeszcze utworzona. Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

W katalogu *testów jednostkowych-vb-using-dotnet-test* uruchom `dotnet test` ponownie. Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia ten pojedynczy test. Mija.

## <a name="adding-more-features"></a>Dodawanie kolejnych funkcji

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1. Można dodać te przypadki jako `<Fact>` nowe testy z atrybutem, ale szybko staje się nużące. Istnieją inne atrybuty xUnit, które umożliwiają napisanie zestawu podobnych testów.  Atrybut `<Theory>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Atrybutu `<InlineData>` można użyć do określenia wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, zastosuj te dwa atrybuty, aby utworzyć jedną teorię. Teoria jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się. Aby wszystkie testy zostały zdatce, zmień klauzulę `if` na początku metody:

```vb
if candidate < 2
```

Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)

Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy. Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.
