---
title: Kod testu C# jednostkowego w programie .NET Core przy użyciu testu dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych w C# oprogramowaniu i .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: eee8ab675ecc66b842a1447e3f2de1b6b9765c4d
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801906"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testowanie C# jednostkowe w programie .NET Core przy użyciu testu dotnet i xUnit

W tym samouczku pokazano, jak utworzyć rozwiązanie zawierające projekt testu jednostkowego i projekt kodu źródłowego. Aby postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Utwórz rozwiązanie

W tej sekcji zostanie utworzone rozwiązanie zawierające projekty źródłowe i testowe. Gotowe rozwiązanie ma następującą strukturę katalogów:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

Poniższe instrukcje zawierają opis kroków, które należy wykonać, aby utworzyć rozwiązanie testowe. Zobacz [polecenia, aby utworzyć rozwiązanie testowe](#create-test-cmd) , aby uzyskać instrukcje dotyczące tworzenia rozwiązania testowego w jednym kroku.

* Otwórz okno powłoki.
* Uruchom następujące polecenie:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  [`dotnet new sln`](../tools/dotnet-new.md) polecenie tworzy nowe rozwiązanie w katalogu *testy jednostkowe-using-dotnet-test* .
* Zmień katalog na folder z testami *jednostkowymi-using-dotnet-test* .
* Uruchom następujące polecenie:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   [`dotnet new classlib`](../tools/dotnet-new.md) polecenie tworzy nowy projekt biblioteki klas w folderze *PrimeService* . Nowa biblioteka klas będzie zawierać kod do przetestowania.
* Zmień nazwę *Class1.cs* na *PrimeService.cs*.
* Zastąp kod w *PrimeService.cs* następującym kodem:
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* Powyższy kod:
  * Zgłasza <xref:System.NotImplementedException> przy użyciu komunikatu wskazującego, że nie jest zaimplementowany.
  * Zostanie zaktualizowany w dalszej części samouczka.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* W katalogu *testy jednostkowe-using-dotnet-test* Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Utwórz projekt *PrimeService. Tests* , uruchamiając następujące polecenie:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Poprzednie polecenie:
  * Tworzy projekt *PrimeService. Tests* w katalogu *PrimeService. Tests* . Projekt testowy używa [xUnit](https://xunit.github.io/) jako biblioteki testowej.
  * Konfiguruje moduł uruchamiający testy przez dodanie następujących elementów `<PackageReference />`do pliku projektu:
    * "Microsoft. NET. test. SDK"
    * xUnit
    * "xUnit. Runner. VisualStudio"

* Dodaj projekt testowy do pliku rozwiązania, uruchamiając następujące polecenie:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Dodaj `PrimeService` bibliotekę klas jako zależność do projektu *PrimeService. Tests* :

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Polecenia służące do tworzenia rozwiązania

Ta sekcja podsumowuje wszystkie polecenia w poprzedniej sekcji. Pomiń tę sekcję, jeśli wykonano kroki opisane w poprzedniej sekcji.

Następujące polecenia tworzą rozwiązanie testowe na komputerze z systemem Windows. W przypadku systemów macOS i UNIX zaktualizuj polecenie `ren` do wersji systemu operacyjnego `ren`, aby zmienić nazwę pliku:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Postępuj zgodnie z instrukcjami dotyczącymi "Zastąp kod w *PrimeService.cs* następującym kodem" w poprzedniej sekcji.

## <a name="create-a-test"></a>Tworzenie testu

Popularnym podejściem do programowania testowego (TDD) jest napisanie testu przed implementacją kodu docelowego. W tym samouczku jest stosowane podejście TDD. Metoda `IsPrime` jest wywoływana, ale nie jest zaimplementowana. Wywołanie testowe do `IsPrime` nie powiodło się. Przy użyciu elementu TDD test jest zapisywana, że jest to niepowodzenie. Kod docelowy został zaktualizowany w celu przeprowadzenia testu. Powtarzaj to podejście, pisząc test zakończony niepowodzeniem, a następnie aktualizując kod docelowy do przekazania.

Aktualizowanie projektu *PrimeService. Tests* :

* Usuń *PrimeService. Tests/UnitTest1. cs*.
* Utwórz plik *PrimeService. Tests/PrimeService_IsPrimeShould. cs* .
* Zastąp kod w *PrimeService_IsPrimeShould. cs* następującym kodem:

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

Atrybut `[Fact]` deklaruje metodę testową, która jest uruchamiana przez program Test Runner. W folderze *PrimeService. Tests* Uruchom `dotnet test`. Polecenie [test dotnet](../tools/dotnet-test.md) kompiluje oba projekty i uruchamia testy. Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test` uruchamia program Test Runner przy użyciu projektu testów jednostkowych.

Test nie powiódł się, ponieważ `IsPrime` nie został zaimplementowany. Za pomocą podejścia TDD napisz tylko wystarczający kod, aby ten test zakończył się powodzeniem. Zaktualizuj `IsPrime` przy użyciu następującego kodu:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Uruchom narzędzie `dotnet test`. Test zakończy się pomyślnie.

### <a name="add-more-tests"></a>Dodaj więcej testów

Dodaj testy z numerami podstawowymi dla 0 i-1. Można skopiować poprzedni test i zmienić następujący kod, aby użyć 0 i-1:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Kopiowanie kodu testowego w przypadku zmiany tylko parametru powoduje duplikowanie kodu i testowanie przeładowanie. Następujące atrybuty xUnit umożliwiają napisanie zestawu podobnych testów:

- `[Theory]` reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.

- atrybut `[InlineData]` określa wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj powyższe atrybuty xUnit, aby utworzyć pojedynczy teorii. Zastąp następujący kod:

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

przy użyciu następującego kodu:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

W poprzednim kodzie `[Theory]` i `[InlineData]` Włącz testowanie kilku wartości mniejszej niż dwa. Dwa to najmniejszy numer podstawowy.

Uruchom `dotnet test`, dwa testy zakończą się niepowodzeniem. Aby wszystkie testy zostały zakończone, zaktualizuj metodę `IsPrime` przy użyciu następującego kodu:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Postępując zgodnie z podejściem TDD, Dodaj więcej testów zakończonych niepowodzeniem, a następnie zaktualizuj kod docelowy. Zobacz kompletną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

Zakończona `IsPrime` Metoda nie jest wydajnym algorytmem testowania primality.

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Oficjalna witryna xUnit.net](https://xunit.github.io)
- [Testowanie logiki kontrolera w ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
