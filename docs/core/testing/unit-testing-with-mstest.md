---
title: Jednostki testowania C# przy użyciu MSTest i .NET Core
description: Pojęcia dotyczące jednostek testów w języku C# i .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i struktury MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.custom: seodec18
ms.openlocfilehash: c396be926d743b672cb4611dc5569ecb48b09fec
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397488"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>Jednostki testowania C# przy użyciu MSTest i .NET Core

Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych. Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) przed przystąpieniem do wykonywania. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwieranie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie-przy użyciu mstest* do przechowywania rozwiązania. Wewnątrz tego nowy katalog uruchamiania [ `dotnet new sln` ](../tools/dotnet-new.md) do utworzenia nowego pliku rozwiązania projekt testu i biblioteki klas. Następnie należy utworzyć *PrimeService* katalogu. Następujące konspektu przedstawia strukturę katalogów i plików tej pory:

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do utworzenia projektu źródłowego. Zmień nazwę *Class1.cs* do *PrimeService.cs*. Tworzenie wdrożenia niepowodzenie `PrimeService` klasy:

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

Zmień katalog kopii do *jednostki — testowanie-przy użyciu mstest* katalogu. Uruchom [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas w rozwiązaniu. 

### <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *PrimeService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest` ](../tools/dotnet-new.md). Nowe polecenie dotnet tworzy projekt testowy, który używa MSTest jako biblioteka testów. Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeServiceTests.csproj* pliku:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe. `dotnet new` w poprzednim kroku, które są dodawane do zestawu SDK MSTest, MSTest przetestować framework i modułu uruchamiającego MSTest. Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

Następujące konspektu przedstawia wybrany układ ostateczne rozwiązanie:

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Wykonaj [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie-przy użyciu mstest* katalogu. 

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Jeden zapisu kończy się niepowodzeniem testu, ułatwiają — dostęp próbny, a następnie powtórz ten proces. Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy C# plik o nazwie *PrimeService_IsPrimeShould.cs* o następującej zawartości:

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestClass]` Atrybut wskazuje klasę, która zawiera testy jednostkowe. `[TestMethod]` Atrybut wskazuje, metoda jest metodą testową. 

Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający MSTest zawiera punkt wejścia programu, aby uruchomić testy. `dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.

Test nie powiedzie się. Nie utworzono jeszcze wdrożenia. Wprowadź ten test, przekazać przez napisanie kodu najprostsza `PrimeService` klasę, która działa:

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

W *jednostki — testowanie-przy użyciu mstest* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu obu projektów, działa ten jeden test. Przekazuje on.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej. Istnieje kilka innych przypadkach proste dla liczby pierwsze: 0, -1. Można dodać nowe testy za pomocą `[TestMethod]` atrybut, ale który szybko staje się uciążliwe. Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestaw testów podobne.  A `[DataTestMethod]`atrybut reprezentuje zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe. Możesz użyć `[DataRow]` atrybutu, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować te atrybuty do utworzenia pojedynczego testu opartego na danych. Opartych na test danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem. Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku metody:

```csharp
if (candidate < 2)
```

Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy. Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.
