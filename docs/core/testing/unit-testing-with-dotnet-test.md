---
title: Kod testu C# jednostkowego w programie .NET Core przy użyciu testu dotnet i xUnit
description: Poznaj koncepcje testów jednostkowych w C# oprogramowaniu i .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: d85e3e69721d8933565b1c80fb7ed21b2291e60e
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117282"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testowanie C# jednostkowe w programie .NET Core przy użyciu testu dotnet i xUnit

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Test-using-dotnet-Testuj* , aby obtrzymać rozwiązanie.
W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie. Rozwiązanie ułatwia zarządzanie zarówno biblioteką klas, jak i projektem testów jednostkowych.
W katalogu rozwiązania Utwórz katalog *PrimeService* . W tej chwili struktura katalogów i plików powinna być następująca:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Ustaw *PrimeService* w bieżącym katalogu i uruchom [`dotnet new classlib`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy. Zmień nazwę *Class1.cs* na *PrimeService.cs*. Najpierw utwórz nieprawidłową implementację `PrimeService` klasy:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

Zmień katalog z powrotem na katalog *testów jednostkowych-using-dotnet-test* .

Uruchom polecenie [dotnet sln](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania:

```dotnetcli
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie Utwórz katalog *PrimeService. Tests* . Poniższy konspekt przedstawia strukturę katalogów:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new xunit`](../tools/dotnet-new.md)polecenia. To polecenie tworzy projekt testowy, który używa [xUnit](https://xunit.github.io/) jako biblioteki testowej. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeServiceTests. csproj* podobnie jak w poniższym kodzie:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano xUnit i moduł uruchamiający xUnit. Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

Poniżej przedstawiono końcowy układ rozwiązania:

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

Aby dodać projekt testowy do rozwiązania, uruchom polecenie [dotnet sln](../tools/dotnet-sln.md) w katalogu *Unit-Test-using-dotnet* :

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. Usuń *UnitTest1.cs* z katalogu *PrimeService. Tests* i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould. cs*. Dodaj następujący kod:

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

Ten `[Fact]` atrybut wskazuje metodę testową, która jest uruchamiana przez program Test Runner. W folderze *PrimeService. Tests* wykonaj [`dotnet test`](../tools/dotnet-test.md) polecenie, aby skompilować testy i bibliotekę klas, a następnie uruchom testy. Program xUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa. Zastąp istniejącą `IsPrime` implementację metody następującym kodem:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

W katalogu *PrimeService. Tests* ponownie uruchom `dotnet test` polecenie. Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test` Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1. Te przypadki można dodać jako nowe testy z `[Fact]` atrybutem, ale szybko żmudnym. Istnieją inne atrybuty xUnit, które umożliwiają pisanie zestawu podobnych testów:

- `[Theory]`reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe.

- `[InlineData]`atrybut określa wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty `[Theory]` i `[InlineData]`, aby utworzyć pojedynczy teorii w pliku *PrimeService_IsPrimeShould. cs* . Teoretyczna jest metoda, która sprawdza kilka wartości mniejszej niż dwa, które jest najniższą liczbą:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test` ponownie, a dwa z tych testów nie powiodą się. Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku `IsPrime` metody w pliku *PrimeService.cs* :

```csharp
if (candidate < 2)
```

Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej. Masz [ukończoną wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [kompletną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Oficjalna witryna xUnit.net](https://xunit.github.io)
- [Testowanie logiki kontrolera w ASP.NET Core](/aspnet/core/mvc/controllers/testing)
