---
title: Testowanie jednostek kodu języka C# w .NET Core za pomocą polecenia dotnet test i struktury xUnit
description: Pojęcia dotyczące jednostek testów w języku C# i .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.openlocfilehash: 560ba58076fedbb1174da2cfe93796030aa9d46f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404298"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testowanie jednostek języka C# w .NET Core za pomocą polecenia dotnet test i struktury xUnit

Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych. Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) przed przystąpieniem do wykonywania. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwieranie okna powłoki. Utwórz katalog o nazwie *testowania — przy użyciu dotnet-test jednostkowy* do przechowywania rozwiązania.
Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania. Rozwiązanie ułatwia zarządzanie zarówno biblioteki klas, jak i projekt testów jednostkowych.
Utwórz katalog rozwiązania *PrimeService* katalogu. Struktura katalogów i plików pory powinna być następująca:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego. Zmień nazwę *Class1.cs* do *PrimeService.cs*. Aby korzystać z projektowania opartego na testach (TDD), należy najpierw utworzyć niepowodzenie wykonania `PrimeService` klasy:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

Zmień katalog kopii do *testowania — przy użyciu dotnet-test jednostkowy* katalogu.

Uruchom [dotnet sln](../tools/dotnet-sln.md) polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *PrimeService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit` ](../tools/dotnet-new.md). To polecenie umożliwia utworzenie projektu testowego, który używa rozwiązania xUnit, jako biblioteka testów. Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.csproj* pliku podobny do następującego kodu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe. `dotnet new` w poprzednim kroku dodawany xUnit, a moduł uruchamiający testy xUnit. Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

Na poniższym obrazie przedstawiono układ ostateczne rozwiązanie:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Aby dodać projekt testu w rozwiązaniu, uruchom [dotnet sln](../tools/dotnet-sln.md) polecenia w pliku *testowania — przy użyciu dotnet-test jednostkowy* katalogu:

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejścia TDD wymaga zapisywania niepowodzenie jednego testu, dzięki czemu przekazać, a następnie powtórzyć ten proces. Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs*. Dodaj następujący kod:

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` Atrybut oznacza metodę testową, która jest uruchamiany przez narzędzie test runner. Z *PrimeService.Tests* folderu wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający xUnit zawiera punkt wejścia programu, aby uruchomić testy. `dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.

Test nie powiedzie się. Nie utworzono jeszcze wdrożenia. Wprowadź ten test, przekazać przez napisanie kodu najprostsza `PrimeService` klasę, która działa. Zastąp istniejące `IsPrime` implementacji metody z następującym kodem:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

W *PrimeService.Tests* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu obu projektów, działa ten jeden test. Przekazuje on.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej. Istnieje kilka innych przypadkach proste dla liczb pierwszych: 0, -1. Możesz dodać te przypadki jako nowe testy za pomocą `[Fact]` atrybut, ale który szybko staje się uciążliwe. Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestaw testów podobne:

- `[Theory]` reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe.

- `[InlineData]` atrybut określa wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować te dwa atrybuty `[Theory]` i `[InlineData]`, aby utworzyć pojedynczy teorii w *PrimeService_IsPrimeShould.cs* pliku. Teorii to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test` ponownie, a dwa z tych testów powinna zakończyć się niepowodzeniem. Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku `IsPrime` method in Class metoda *PrimeService.cs* pliku:

```csharp
if (candidate < 2)
```

Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Testowanie logiką kontrolera w programie ASP.NET Core](/aspnet/core/mvc/controllers/testing)
