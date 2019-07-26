---
title: Testowanie C# jednostkowe za pomocą nunit i .NET Core
description: Poznaj koncepcje testów jednostkowych w C# oprogramowaniu i .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i NUnit.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 53e8ebd6e4c3f07ace72df5e7dc916ecd30ce831
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433918"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testowanie C# jednostkowe za pomocą nunit i .NET Core

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core 2,1 SDK](https://www.microsoft.com/net/download) lub jego nowsze wersje.
- Edytor tekstu lub Edytor kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Test-using-nunit* , aby pomieścić rozwiązanie. W tym nowym katalogu Uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```console
dotnet new sln
```
 
Następnie Utwórz katalog *PrimeService* . Poniższy konspekt przedstawia strukturę katalogu i pliku do tej pory:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Ustaw *PrimeService* w bieżącym katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```console
dotnet new classlib
```

Zmień nazwę *Class1.cs* na *PrimeService.cs*. Tworzysz nieprawidłową implementację `PrimeService` klasy:

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

Zmień katalog z powrotem do katalogu *testowego nunit* . Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie Utwórz katalog *PrimeService. Tests* . Poniższy konspekt przedstawia strukturę katalogów:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą następującego polecenia:

```console
dotnet new nunit
```

Polecenie [dotnet New](../tools/dotnet-new.md) umożliwia utworzenie projektu testowego, który używa nunit jako biblioteki testowej. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeService. tests. csproj* :

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano zestaw Microsoft Test SDK, NUnit Test Framework oraz adapter testowy NUnit. Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

W poniższym konspekcie przedstawiono końcowy układ rozwiązania:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

Wykonaj następujące polecenie w katalogu *Unit-Test-using-nunit* :

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. W katalogu *PrimeService. Tests* Zmień nazwę pliku *UnitTest1.cs* na *PrimeService_IsPrimeShould. cs* i Zastąp całą zawartość następującym kodem:

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        public PrimeService_IsPrimeShould()
        {
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            PrimeService primeService = CreatePrimeService();
            var result = primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
        
        /*
        More tests
        */
        
        private PrimeService CreatePrimeService()
        {
             return new PrimerService();
        }
    }
}
```

Ten `[TestFixture]` atrybut oznacza klasę, która zawiera testy jednostkowe. `[Test]` Atrybut wskazuje, że metoda jest metodą testową.

Zapisz ten plik i wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy. Program NUnit Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa:

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

W katalogu *testy jednostkowe-using-nunit* Uruchom `dotnet test` ponownie. Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test` Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1. Można dodać nowe testy z `[Test]` atrybutem, ale szybko żmudnym. Istnieją inne atrybuty NUnit, które umożliwiają pisanie zestawu podobnych testów.  `[TestCase]` Atrybut służy do tworzenia zestawu testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Możesz użyć atrybutu, `[TestCase]` aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj ten atrybut, aby utworzyć pojedynczy test oparty na danych. Test oparty na danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, co jest najniższym numerem:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem. Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku `Main` metody w pliku *PrimeService.cs* :

```csharp
if (candidate < 2)
```

Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej. Masz ukończoną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i kompletną implementację [biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy. Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.
