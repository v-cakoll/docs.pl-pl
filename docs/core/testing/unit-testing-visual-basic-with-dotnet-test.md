---
title: Testowanie jednostkowe Visual Basic w .NET Core z testowaniem dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych w oprogramowaniu .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania Visual Basic krok po kroku przy użyciu testu dotnet i xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: d87550d692e0b7f3bfee1633bd00cbf501cc2e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502759"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Testowanie jednostkowe Visual Basic biblioteki .NET Core przy użyciu testu dotnet i xUnit

W tym samouczku pokazano, jak utworzyć rozwiązanie zawierające projekt testu jednostkowego i projekt biblioteki. Aby postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Utwórz rozwiązanie

W tej sekcji zostanie utworzone rozwiązanie zawierające projekty źródłowe i testowe. Gotowe rozwiązanie ma następującą strukturę katalogów:

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

Poniższe instrukcje zawierają opis kroków, które należy wykonać, aby utworzyć rozwiązanie testowe. Zobacz [polecenia, aby utworzyć rozwiązanie testowe](#create-test-cmd) , aby uzyskać instrukcje dotyczące tworzenia rozwiązania testowego w jednym kroku.

* Otwórz okno powłoki.
* Uruchom następujące polecenie:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  [`dotnet new sln`](../tools/dotnet-new.md)Polecenie tworzy nowe rozwiązanie w katalogu *testy jednostkowe-using-dotnet-test* .
* Zmień katalog na folder z testami *jednostkowymi-using-dotnet-test* .
* Uruchom następujące polecenie:

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   [`dotnet new classlib`](../tools/dotnet-new.md)Polecenie tworzy nowy projekt biblioteki klas w folderze *PrimeService* . Nowa biblioteka klas będzie zawierać kod do przetestowania.
* Zmień nazwę *Class1. vb* na *PrimeService. vb*.
* Zastąp kod w *PrimeService. vb* następującym kodem:
  
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

* Powyższy kod ma następujące działanie:
  * Zwraca <xref:System.NotImplementedException> komunikat informujący o tym, że nie został zaimplementowany.
  * Zostanie zaktualizowany w dalszej części samouczka.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* W katalogu *testy jednostkowe-using-dotnet-test* Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* Utwórz projekt *PrimeService. Tests* , uruchamiając następujące polecenie:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Poprzednie polecenie:
  * Tworzy projekt *PrimeService. Tests* w katalogu *PrimeService. Tests* . Projekt testowy używa [xUnit](https://xunit.net/) jako biblioteki testowej.
  * Konfiguruje moduł uruchamiający testy przez dodanie następujących `<PackageReference />` elementów do pliku projektu:
    * "Microsoft. NET. test. SDK"
    * xUnit
    * "xUnit. Runner. VisualStudio"

* Dodaj projekt testowy do pliku rozwiązania, uruchamiając następujące polecenie:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* Dodaj `PrimeService` bibliotekę klas jako zależność do projektu *PrimeService. Tests* :

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Polecenia służące do tworzenia rozwiązania

Ta sekcja podsumowuje wszystkie polecenia w poprzedniej sekcji. Pomiń tę sekcję, jeśli wykonano kroki opisane w poprzedniej sekcji.

Następujące polecenia tworzą rozwiązanie testowe na komputerze z systemem Windows. W przypadku systemów macOS i UNIX zaktualizuj `ren` polecenie do wersji systemu operacyjnego, `ren` Aby zmienić nazwę pliku:

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

Postępuj zgodnie z instrukcjami dla "Zastąp kod w *PrimeService. vb* następującym kodem" w poprzedniej sekcji.

## <a name="create-a-test"></a>Tworzenie testu

Popularnym podejściem do programowania testowego (TDD) jest napisanie testu przed implementacją kodu docelowego. W tym samouczku jest stosowane podejście TDD. `IsPrime`Metoda jest wywoływana, ale nie jest zaimplementowana. Wywołanie testowe `IsPrime` kończy się niepowodzeniem. Przy użyciu elementu TDD test jest zapisywana, że jest to niepowodzenie. Kod docelowy został zaktualizowany w celu przeprowadzenia testu. Powtarzaj to podejście, pisząc test zakończony niepowodzeniem, a następnie aktualizując kod docelowy do przekazania.

Aktualizowanie projektu *PrimeService. Tests* :

* Usuń *PrimeService. Tests/UnitTest1. vb*.
* Utwórz plik *PrimeService. Tests/PrimeService_IsPrimeShould. vb* .
* Zastąp kod w *PrimeService_IsPrimeShould. vb* następującym kodem:

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

Ten `[Fact]` atrybut deklaruje metodę testową, która jest uruchamiana przez program Test Runner. W folderze *PrimeService. Tests* Uruchom polecenie `dotnet test` . Polecenie [test dotnet](../tools/dotnet-test.md) kompiluje oba projekty i uruchamia testy. Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia program Test Runner przy użyciu projektu testów jednostkowych.

Test zakończy się niepowodzeniem, ponieważ `IsPrime` nie został zaimplementowany. Za pomocą podejścia TDD napisz tylko wystarczający kod, aby ten test zakończył się powodzeniem. Zaktualizuj `IsPrime` przy użyciu następującego kodu:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

Uruchom polecenie `dotnet test`. Test kończy się powodzeniem.

### <a name="add-more-tests"></a>Dodaj więcej testów

Dodaj testy z numerami podstawowymi dla 0 i-1. Można skopiować poprzedni test i zmienić następujący kod, aby użyć 0 i-1:

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

Kopiowanie kodu testowego w przypadku zmiany tylko parametru powoduje duplikowanie kodu i testowanie przeładowanie. Następujące atrybuty xUnit umożliwiają napisanie zestawu podobnych testów:

- `[Theory]`reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.
- `[InlineData]`atrybut określa wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj powyższe atrybuty xUnit, aby utworzyć pojedynczy teorii. Zastąp następujący kod:

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

przy użyciu następującego kodu:

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

W poprzednim kodzie `[Theory]` i `[InlineData]` Włącz testowanie kilku wartości mniejszej niż dwa. Dwa to najmniejszy numer podstawowy.

Uruchomienie `dotnet test` , dwa testy kończą się niepowodzeniem. Aby wszystkie testy zostały zakończone, zaktualizuj `IsPrime` metodę przy użyciu następującego kodu:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

Postępując zgodnie z podejściem TDD, Dodaj więcej testów zakończonych niepowodzeniem, a następnie zaktualizuj kod docelowy. Zobacz kompletną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).

Zakończona `IsPrime` Metoda nie jest wydajnym algorytmem testowania primality.

### <a name="additional-resources"></a>Zasoby dodatkowe

- [Oficjalna witryna xUnit.net](https://xunit.net/)
- [Testowanie logiki kontrolera w ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
