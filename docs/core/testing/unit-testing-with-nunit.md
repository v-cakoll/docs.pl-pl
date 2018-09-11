---
title: Jednostki testowania C# za pomocą NUnit i .NET Core
description: Pojęcia dotyczące jednostek testów w języku C# i .NET Core za pomocą interaktywnych doświadczenia przykładowe rozwiązanie krok po kroku za pomocą polecenia dotnet test i NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 253e07c16740a39566cf37ee5742a32342c78c49
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353645"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Jednostki testowania C# za pomocą NUnit i .NET Core

Ten samouczek przeprowadzi Cię przez środowisko interaktywne tworzenie przykładowe rozwiązanie krok po kroku, aby dowiedzieć się więcej pojęcia testów jednostkowych. Jeśli chcesz wykonać kroki samouczka przy użyciu wstępnie utworzone rozwiązania [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) przed przystąpieniem do wykonywania. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET core SDK 2.1 (v. 2.1.400)](https://www.microsoft.com/net/download) lub nowszy.
- Edytor tekstu lub ulubionego edytora kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwieranie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie-przy użyciu nunit* do przechowywania rozwiązania. Wewnątrz tego nowy katalog uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```console
dotnet new sln
```
 
Następnie należy utworzyć *PrimeService* katalogu. Następujące konspektu przedstawia strukturę katalogów i plików do tej pory:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```console
dotnet new classlib
```

Zmień nazwę *Class1.cs* do *PrimeService.cs*. Aby użyć Programowanie oparte na testach (TDD), należy utworzyć z implementacją niepowodzenie `PrimeService` klasy:

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

Zmień katalog kopii do *jednostki — testowanie-przy użyciu nunit* katalogu. Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *PrimeService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt, używając następującego polecenia:

```console
dotnet new nunit
```

[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteka testów. Wygenerowany szablon konfiguruje narzędzie test runner w *PrimeService.Tests.csproj* pliku:

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Projekt testowy wymaga innych pakietów, aby utworzyć i uruchomić testy jednostkowe. `dotnet new` w poprzednim kroku dodane testów firmy Microsoft zestawu SDK, struktury testów NUnit i NUnit adaptera testowego. Teraz Dodaj `PrimeService` biblioteki klas jako inny zależności do projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Widać cały plik w [repozytorium przykładów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

Następujące konspektu przedstawia wybrany układ ostateczne rozwiązanie:

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

Wykonaj następujące polecenie w *testowania — przy użyciu dotnet-test jednostkowy* katalogu:

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejścia TDD wymaga zapisywania niepowodzenie jednego testu, dzięki czemu przekazać, a następnie powtórzyć ten proces. W *PrimeService.Tests* katalogu, zmiana nazwy *UnitTest1.cs* plik *PrimeService_IsPrimeShould.cs* i zastąp jego całą zawartość następującym kodem:

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestFixture]` Atrybut wskazuje klasę, która zawiera testy jednostkowe. `[Test]` Atrybut wskazuje, metoda jest metodą testową.

Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do kompilacji, testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający NUnit zawiera punkt wejścia programu, aby uruchomić testy. `dotnet test` Uruchamia narzędzie test runner, za pomocą projektu testu jednostkowego, który został utworzony.

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

W *jednostki — testowanie-przy użyciu nunit* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenie uruchamia kompilację dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu obu projektów, działa ten jeden test. Przekazuje on.

## <a name="adding-more-features"></a>Dodawanie większej liczby funkcji

Teraz, gdy wprowadzono jeden przebieg testu, nadszedł czas na zapis więcej. Istnieje kilka innych przypadkach proste dla liczb pierwszych: 0, -1. Można dodać nowe testy za pomocą `[Test]` atrybut, ale który szybko staje się uciążliwe. Istnieją inne atrybuty NUnit, które umożliwiają pisanie zestaw testów podobne.  A `[TestCase]` atrybut jest używany do tworzenia zestaw testów, które wykonania tego samego kodu, ale mają różne argumenty wejściowe. Możesz użyć `[TestCase]` atrybutu, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować ten atrybut do utworzenia pojedynczego testu opartego na danych. Opartych na test danych to metoda, która sprawdza kilka wartości mniejszej niż dwa, czyli najniższy numer prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem. Aby wszystkie przebieg testów, należy zmienić `if` klauzuli na początku `Main` method in Class metoda *PrimeService.cs* pliku:

```csharp
if (candidate < 2)
```

Przejdź do iteracji, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [ukończoną wersję testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Gdy masz utworzoną małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Tak, aby dodawania nowych pakietów została ze strukturą rozwiązania i testów jest częścią normalnego przepływu pracy. Po skoncentrowany większość czasu i wysiłku niewiele rozwiązywania cele aplikacji.
