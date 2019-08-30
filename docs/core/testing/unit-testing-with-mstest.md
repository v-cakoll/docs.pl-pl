---
title: Testowanie C# jednostkowe za pomocą MSTest i .NET Core
description: Poznaj koncepcje testów jednostkowych w C# oprogramowaniu i .NET Core za pośrednictwem interaktywnego środowiska tworzenia przykładowego rozwiązania krok po kroku przy użyciu testu dotnet i MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.custom: seodec18
ms.openlocfilehash: ae4ddd4df902cf8c3d50e50614b12af8dc0aebed
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168167"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>Testowanie C# jednostkowe za pomocą MSTest i .NET Core

Ten samouczek przeprowadzi Cię przez interaktywny proces tworzenia przykładowego rozwiązania krok po kroku, aby poznać koncepcje dotyczące testowania jednostkowego. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie skompilowanego rozwiązania, przed rozpoczęciem [Wyświetl lub Pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) . Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-source-project"></a>Utwórz projekt źródłowy

Otwórz okno powłoki. Utwórz katalog o nazwie *Unit-Test-using-MSTest* , aby pomieścić rozwiązanie. W tym nowym katalogu Uruchom [`dotnet new sln`](../tools/dotnet-new.md) polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego. Następnie Utwórz katalog *PrimeService* . W poniższym konspekcie przedstawiono strukturę katalogów i plików:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Ustaw *PrimeService* w bieżącym katalogu i uruchom [`dotnet new classlib`](../tools/dotnet-new.md) , aby utworzyć projekt źródłowy. Zmień nazwę *Class1.cs* na *PrimeService.cs*. Tworzysz nieprawidłową implementację `PrimeService` klasy:

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

Zmień katalog z powrotem do katalogu *testowego MSTest* . Uruchom [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) , aby dodać projekt biblioteki klas do rozwiązania. 

## <a name="create-the-test-project"></a>Utwórz projekt testu

Następnie Utwórz katalog *PrimeService. Tests* . Poniższy konspekt przedstawia strukturę katalogów:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService. Tests* jako bieżący katalog i Utwórz nowy projekt za pomocą [`dotnet new mstest`](../tools/dotnet-new.md)polecenia. Polecenie dotnet New umożliwia utworzenie projektu testowego, który używa MSTest jako biblioteki testowej. Wygenerowany szablon służy do konfigurowania modułu uruchamiającego testy w pliku *PrimeServiceTests. csproj* :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano zestaw MSTest SDK, platformę test MSTest i moduł uruchamiający MSTest. Teraz Dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Cały plik można zobaczyć w [repozytorium Samples](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

W poniższym konspekcie przedstawiono końcowy układ rozwiązania:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Wykonaj [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) w katalogu *testowym jednostkowym-using-MSTest* . 

## <a name="create-the-first-test"></a>Tworzenie pierwszego testu

Napiszesz jeden test zakończony niepowodzeniem, upewnij się, a następnie powtórz ten proces. Usuń *UnitTest1.cs* z katalogu *PrimeService. Tests* i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould. cs* z następującą zawartością:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

[Atrybut TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) oznacza klasę, która zawiera testy jednostkowe. [Atrybut TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) wskazuje, że metoda jest metodą testową. 

Zapisz ten plik i wykonaj [`dotnet test`](../tools/dotnet-test.md) , aby skompilować testy i bibliotekę klas, a następnie uruchom testy. Program MSTest Test Runner zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia program Test Runner przy użyciu utworzonego projektu testu jednostkowego.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Wykonaj ten test, pisząc najprostszy kod w `PrimeService` klasie, która działa:

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

W katalogu *testy jednostkowe-using-MSTest* Uruchom `dotnet test` ponownie. Polecenie uruchamia kompilację `PrimeService` dla `PrimeService.Tests` projektu, a następnie dla projektu. `dotnet test` Po skompilowaniu obu projektów jest uruchamiany ten pojedynczy test. Przekazuje.

## <a name="add-more-features"></a>Dodaj więcej funkcji

Teraz, po wykonaniu jednego przebiegu testowego, należy napisać więcej. Istnieje kilka innych prostych przypadków dla numerów pierwszych: 0, -1. Można dodać nowe testy z atrybutem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale szybko żmudnym. Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestawu podobnych testów.  [Atrybut DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Można użyć [atrybutu DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) , aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, Zastosuj te dwa atrybuty w celu utworzenia pojedynczego testu opartego na danych. Test oparty na danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, co jest najniższym numerem:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`i dwa z tych testów zakończą się niepowodzeniem. Aby wszystkie testy zostały zakończone pomyślnie, należy zmienić `if` klauzulę na początku metody:

```csharp
if (candidate < 2)
```

Kontynuuj iteracje, dodając więcej testów, więcej teorie i więcej kodu w bibliotece głównej. Masz ukończoną [wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i kompletną implementację [biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Utworzono niewielką bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Rozbudowane rozwiązanie jest przeznaczone do dodawania nowych pakietów i testów jest częścią normalnego przepływu pracy. Zbyt najwięcej czasu i wysiłku na rozwiązywanie celów aplikacji.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Użyj struktury MSTest w testach jednostkowych](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [Dokumentacja platformy testowej MSTest v2](https://github.com/Microsoft/testfx-docs)
