---
title: Testowanie jednostkowe kodu C# w .NET Core przy użyciu testu dotnet i xUnit
description: Poznaj pojęcia dotyczące testów jednostkowych w językach C# i .NET Core, korzystając z interakcyjnego środowiska, które krok po kroku przy użyciu testu dotnet i xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240899"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testowanie jednostkowe C# w .NET Core przy użyciu testu dotnet i xUnit

W tym samouczku pokazano, jak utworzyć rozwiązanie zawierające projekt testu jednostkowego i projekt kodu źródłowego. Aby postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Tworzenie rozwiązania

W tej sekcji tworzone jest rozwiązanie zawierające projekty źródłowe i testowe. Ukończone rozwiązanie ma następującą strukturę katalogów:

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

Poniższe instrukcje zawierają kroki, aby utworzyć rozwiązanie testowe. Zobacz [Polecenia, aby utworzyć rozwiązanie testowe,](#create-test-cmd) aby uzyskać instrukcje dotyczące tworzenia rozwiązania testowego w jednym kroku.

* Otwórz okno powłoki.
* Uruchom następujące polecenie:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  Polecenie [`dotnet new sln`](../tools/dotnet-new.md) tworzy nowe rozwiązanie w katalogu *testów jednostkowych z używających dotnet-testów.*
* Zmień katalog na folder *testów jednostkowych z wykorzystaniem dotnet-test.*
* Uruchom następujące polecenie:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   Polecenie [`dotnet new classlib`](../tools/dotnet-new.md) tworzy nowy projekt biblioteki klas w folderze *PrimeService.* Nowa biblioteka klas będzie zawierać kod, który ma zostać przetestowany.
* Zmień nazwę *Class1.cs* na *PrimeService.cs*.
* Zamień kod w *PrimeService.cs* na następujący kod:
  
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

* Powyższy kod ma następujące działanie:
  * Zgłasza wiadomość <xref:System.NotImplementedException> z informacją, że nie jest zaimplementowana.
  * Jest aktualizowany w dalszej części samouczka.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* W katalogu *testów jednostkowych z używając dotnet-test* uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Utwórz projekt *PrimeService.Tests,* uruchamiając następujące polecenie:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Poprzednie polecenie:
  * Tworzy *PrimeService.Tests* projektu w katalogu *PrimeService.Tests.* Projekt testowy używa [xUnit](https://xunit.github.io/) jako biblioteki testowej.
  * Konfiguruje program testowy, `<PackageReference />`dodając następujące elementy do pliku projektu:
    * "Microsoft.NET.Test.Sdk"
    * "xunit"
    * "xunit.runner.visualstudio"

* Dodaj projekt testowy do pliku rozwiązania, uruchamiając następujące polecenie:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Dodaj `PrimeService` bibliotekę klas jako zależność do *primeservice.tests* projektu:

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Polecenia służące do tworzenia rozwiązania

W tej sekcji podsumowano wszystkie polecenia w poprzedniej sekcji. Pomiń tę sekcję, jeśli wykonanie kroków w poprzedniej sekcji.

Następujące polecenia utworzyć rozwiązanie testowe na komputerze z systemem Windows. W przypadku systemów macOS `ren` i Unix zaktualizuj polecenie do wersji systemu operacyjnego, `ren` aby zmienić nazwę pliku:

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

Postępuj zgodnie z instrukcjami "Zamień kod w *PrimeService.cs* na następujący kod" w poprzedniej sekcji.

## <a name="create-a-test"></a>Tworzenie testu

Popularnym podejściem w rozwoju opartym na testach (TDD) jest napisanie testu przed wdrożeniem kodu docelowego. Ten samouczek używa podejścia TDD. Metoda `IsPrime` jest wywoływana, ale nie zaimplementowana. Wywołanie testowe `IsPrime` nie powiedzie się. Z TDD test jest zapisywany, który jest znany nie powiedzie się. Kod docelowy jest aktualizowany, aby test przeszedł. Powtarzasz to podejście, zapisując test niepowysady, a następnie aktualizujesz kod docelowy do przekazania.

Zaktualizuj projekt *PrimeService.Tests:*

* Usuń *PrimeService.Tests/UnitTest1.cs*.
* Utwórz plik *PrimeService.Tests/PrimeService_IsPrimeShould.cs.*
* Zamień kod w *PrimeService_IsPrimeShould.cs* na następujący kod:

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

Atrybut `[Fact]` deklaruje metodę testową, która jest uruchamiana przez test runner. Z *primeservice.tests* folderu `dotnet test`uruchom . Polecenie [testu dotnet](../tools/dotnet-test.md) tworzy zarówno projekty, jak i uruchamia testy. Program testowy xUnit zawiera punkt wejścia programu do uruchomienia testów. `dotnet test`uruchamia testowiec za pomocą projektu testu jednostkowego.

Test nie `IsPrime` powiedzie się, ponieważ nie został zaimplementowany. Przy użyciu podejścia TDD, napisać tylko tyle kodu, aby ten test przebiega. Zaktualizuj `IsPrime` za pomocą następującego kodu:

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

Uruchom polecenie `dotnet test`. Test przebiega pomyślnie.

### <a name="add-more-tests"></a>Dodaj więcej testów

Dodaj testy liczb pierwszych dla 0 i -1. Można skopiować poprzedni test i zmienić następujący kod, aby użyć 0 i -1:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Kopiowanie kodu testu, gdy tylko parametr zmienia wyniki w duplikacji kodu i bloat test. Następujące atrybuty xUnit umożliwiają zapisywanie zestawu podobnych testów:

- `[Theory]`reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.

- `[InlineData]`atrybut określa wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować poprzednie atrybuty xUnit, aby utworzyć jedną teorię. Zamień następujący kod:

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

z następującym kodem:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

W poprzednim kodzie `[Theory]` `[InlineData]` i włączyć testowanie kilku wartości mniej niż dwa. Dwa to najmniejsza liczba pierwsza.

Uruchom `dotnet test`, dwa testy nie powiodły się. Aby wszystkie testy zostały zdatnięte, zaktualizuj `IsPrime` metodę za pomocą następującego kodu:

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

Zgodnie z podejściem TDD, dodaj więcej testów nieudanych, a następnie zaktualizuj kod docelowy. Zobacz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

Ukończona `IsPrime` metoda nie jest wydajnym algorytmem testowania pierwotności.

### <a name="additional-resources"></a>Zasoby dodatkowe

- [xUnit.net oficjalna strona](https://xunit.github.io)
- [Testowanie logiki kontrolera w ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
