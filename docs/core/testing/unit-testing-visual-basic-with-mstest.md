---
title: Jednostka badanie Visual Basic .NET Core za pomocą testu dotnet i MSTest
description: Dowiedz się koncepcje testu jednostki w .NET Core za pośrednictwem interaktywnego środowisko budowania rozwiązania Visual Basic próbki krok po kroku przy użyciu przełącznika MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.openlocfilehash: 501bbedca28af1eaaadb0848bfcffc93a7aac92a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215154"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a>Biblioteki języka Visual Basic .NET Core za pomocą testu dotnet i MStest testy jednostkowe

Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) przed rozpoczęciem. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Umożliwia otwarcie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie vb-mstest* do przechowywania rozwiązania.
Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania. Takie rozwiązanie ułatwia zarządzanie biblioteki klas i jednostkowy projekt testowy.
Utwórz katalog rozwiązania *PrimeService* katalogu. Masz dotychczasowych następującą strukturę katalogów i plików:

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego. Zmień nazwę *Class1.VB* do *PrimeService.VB*. Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Zmień katalog z powrotem do *jednostki — testowanie vb — przy użyciu stest* katalogu. Uruchom [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.

## <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *PrimeService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest -lang VB` ](../tools/dotnet-new.md). To polecenie tworzy projekt testowy używającą MSTest jako biblioteka testów. Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych. `dotnet new` w poprzednim kroku dodane MSTest i MSTest runner. Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.

Masz następujące układu ostatecznego rozwiązania:

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie vb-mstest* katalogu.

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces. Usuń *UnitTest1.vb* z *PrimeService.Tests* katalogu i Utwórz nowy plik Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*. Dodaj następujący kod:

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestClass>` Atrybut wskazuje klasę, która zawiera testy. `<TestMethod>` Atrybut oznacza metodę, która jest uruchamiana przez moduł uruchamiający. Z *jednostki — testowanie vb-mstest*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający MSTest zawiera punkt wejścia programu do uruchomienia testów. `dotnet test` Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Należy ten test przez pisania kodu najprostsza w `PrimeService` klasy, która działa:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

W *jednostki — testowanie vb-mstest* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test. Przekazuje ono.

## <a name="adding-more-features"></a>Dodawanie więcej funkcji.

Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej. Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1. Możesz dodać tych przypadkach jako nowe testy z `<TestMethod>` atrybut, ale szybko staje się nużące. Istnieją inne atrybuty MSTest, które pozwalają na zapis zestaw testów podobne.  A `<DataTestMethod>` atrybut reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe. Można użyć `<DataRow>` atrybutu, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować te atrybuty można utworzyć jeden teorii. Teorii jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie pierwsze:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem. Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:

```vb
if candidate < 2
```

Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego. Masz [Zakończono wersji testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).

Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy. Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.
