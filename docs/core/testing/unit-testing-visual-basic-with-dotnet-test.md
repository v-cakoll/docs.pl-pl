---
title: "Testy jednostkowe za pomocą Visual Basic w .NET Core za pomocą testu dotnet i xUnit"
description: "Dowiedz się koncepcje testu jednostki w .NET Core za pośrednictwem interaktywnego środowisko budowania rozwiązania Visual Basic próbki krok po kroku przy użyciu platformy dotnet testu i xUnit."
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: article
dev_langs:
- vb
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 01922e3ad3b19e13ebea755decf21c6b09e4be37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Biblioteki języka Visual Basic .NET Core za pomocą testu dotnet i xUnit testy jednostkowe

Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) przed rozpoczęciem. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Umożliwia otwarcie okna powłoki. Utwórz katalog o nazwie *unit-testing-vb-using-dotnet-test* do przechowywania rozwiązania.
Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania. Takie rozwiązanie ułatwia zarządzanie biblioteki klas i jednostkowy projekt testowy.
Utwórz katalog rozwiązania *PrimeService* katalogu. Masz dotychczasowych następującą strukturę katalogów i plików:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego. Zmień nazwę *Class1.VB* do *PrimeService.VB*. Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Zmień katalog z powrotem do *unit-testing-vb-using-dotnet-test* katalogu. Uruchom [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *PrimeService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md). To polecenie tworzy projekt testowy używającą xUnit jako biblioteka testów. Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku należy dodać xUnit i xUnit modułu uruchamiającego testy. Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.

Masz następujące układu ostatniego folderu:

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

Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) w *unit-testing-vb-using-dotnet-test* katalogu. 

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces. Usuń *UnitTest1.vb* z *PrimeService.Tests* katalogu i Utwórz nowy plik Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*. Dodaj następujący kod:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<Fact>` Atrybut oznacza metodę test jest uruchamiany przez moduł uruchamiający. Z *testowania — przy użyciu dotnet testu jednostkowego*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający xUnit zawiera punkt wejścia programu do uruchomienia testów. `dotnet test`Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Należy ten test przez pisania kodu najprostsza w `PrimeService` klasy, która działa:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

W *unit-testing-vb-using-dotnet-test* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test. Przekazuje ono.

## <a name="adding-more-features"></a>Dodawanie więcej funkcji.

Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej. Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1. Możesz dodać tych przypadkach jako nowe testy z `<Fact>` atrybut, ale szybko staje się nużące. Istnieją inne atrybuty xUnit, które pozwalają na zapis zestaw testów podobne.  A `<Theory>` atrybut reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe. Można użyć `<InlineData>` atrybutu, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować te atrybuty można utworzyć jeden teorii. Teorii jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie pierwsze:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem. Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:

```vb
if candidate < 2
```

Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego. Masz [Zakończono wersji testów](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService/PrimeService.vb).

Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy. Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.
