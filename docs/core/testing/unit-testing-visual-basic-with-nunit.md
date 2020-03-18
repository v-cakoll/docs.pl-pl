---
title: Testowanie jednostkowe języka Visual Basic w programie .NET Core z testem dotnetowym i jednostką NUnit
description: Poznaj pojęcia dotyczące testów jednostkowych w programie .NET Core, korzystając z interaktywnego środowiska, w ramach które krok po kroku przy użyciu funkcji NUnit można znaleźć w przykładzie rozwiązania Visual Basic.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: a33447457344b241b4c2376d777b0deb7f556874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240925"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Testowanie jednostkowe bibliotek programu Visual Basic .NET Core przy użyciu testu dotnet i jednostki NUnit

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *unit-testing-vb-nunit* do przechowywania rozwiązania. W tym nowym katalogu uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```dotnetcli
dotnet new sln
```

Następnie utwórz katalog *PrimeService.* Poniższy konspekt pokazuje strukturę plików do tej pory:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Utwórz *PrimeService* bieżący katalog i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```dotnetcli
dotnet new classlib -lang VB
```

Zmień nazwę *Class1.VB* na *PrimeService.VB*. Tworzenie nieudanej implementacji `PrimeService` klasy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Zmień katalog z powrotem na katalog *testów jednostkowych-vb-using-mstest.* Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie utwórz katalog *PrimeService.Tests.* Poniższy konspekt przedstawia strukturę katalogów:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService.Tests* jako bieżący katalog i utwórz nowy projekt przy użyciu następującego polecenia:

```dotnetcli
dotnet new nunit -lang VB
```

[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteki testowej. Wygenerowany szablon konfiguruje testrunner w pliku *PrimeServiceTests.vbproj:*

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano NUnit i kartę testową NUnit. Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) w uspolu GitHub.

Masz następujący ostateczny układ rozwiązania:

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

Wykonaj następujące polecenie w katalogu *jednostek testujących-vb-nunit:*

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces. W katalogu *PrimeService.Tests* zmień nazwę pliku *UnitTest1.vb* na *PrimeService_IsPrimeShould.VB* i zastąp całą jego zawartość następującym kodem:

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

Atrybut `<TestFixture>` wskazuje klasę, która zawiera testy. Atrybut `<Test>` oznacza metodę, która jest uruchamiana przez test runner. Z *jednostki testowania vb-nunit*, [`dotnet test`](../tools/dotnet-test.md) wykonaj do kompilacji testów i biblioteki klas, a następnie uruchomić testy. Program testowy NUnit zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

Test nie powiedzie się. Implementacja nie została jeszcze utworzona. Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

W katalogu *testów jednostkowych vb-nunit* uruchom `dotnet test` ponownie. Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia ten pojedynczy test. Mija.

## <a name="adding-more-features"></a>Dodawanie kolejnych funkcji

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1. Można dodać te przypadki jako `<Test>` nowe testy z atrybutem, ale szybko staje się nużące. Istnieją inne atrybuty xUnit, które umożliwiają napisanie zestawu podobnych testów.  Atrybut `<TestCase>` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Atrybutu `<TestCase>` można użyć do określenia wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować te dwa atrybuty, aby utworzyć serię testów, które testują kilka wartości mniejszych niż dwa, co jest najniższą liczbą pierwszą:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się. Aby wszystkie testy zostały zdatce, zmień `if` `Main` klauzulę na początku metody w *pliku PrimeServices.cs:*

```vb
if candidate < 2
```

Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)

Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy. Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.
