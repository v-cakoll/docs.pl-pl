---
title: Testowanie C# .NET Core i NUnit jednostki
description: Dowiedz się pojęcia testu jednostki w języku C# i .NET Core za pośrednictwem interaktywnego środowisko tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i NUnit.
author: rprouse
ms.date: 12/01/2017
ms.openlocfilehash: 8cf9e28353dd4dad6143f0dc3f8c0a8245715ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214409"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testowanie C# .NET Core i NUnit jednostki

Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) przed rozpoczęciem. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Umożliwia otwarcie okna powłoki. Utwórz katalog o nazwie *jednostki — testowanie — przy użyciu nunit* do przechowywania rozwiązania. Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do utworzenia nowego pliku rozwiązania dla biblioteki klas i projektu testowego. Następnie należy utworzyć *PrimeService* katalogu. Następujące konspektu dotychczasowych przedstawia strukturę katalogów i plików:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego. Zmień nazwę *Class1.cs* do *PrimeService.cs*. Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:

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

Zmień katalog z powrotem do *jednostki — testowanie — przy użyciu nunit* katalogu. Uruchom [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.

## <a name="install-the-nunit-project-template"></a>Zainstaluj NUnit szablonu projektu

NUnit przetestować projekt, który szablony muszą być zainstalowane przed utworzeniem projektu testowego. To tylko należy jednak wykonać jeden raz na każdym komputerze dewelopera, w których zostaną utworzone nowe projekty NUnit. Uruchom [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) zainstalować szablony NUnit.

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a>Tworzenie projektu testu

Następnie należy utworzyć *PrimeService.Tests* katalogu. Następujące konspektu przedstawia strukturę katalogów:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new nunit` ](../tools/dotnet-new.md). Nowe polecenie dotnet tworzy projekt testowy używającą NUnit jako biblioteka testów. Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.csproj* pliku:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych. `dotnet new` w poprzednim kroku dodać Microsoft test zestawu SDK, struktury testowej NUnit i NUnit adapter testowy. Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

Następujące konspektu przedstawiono układu ostatecznego rozwiązania:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) w *testowania — przy użyciu dotnet testu jednostkowego* katalogu.

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces. Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs* o następującej treści:

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

`[TestFixture]` Atrybut określa klasę, która zawiera testy jednostkowe. `[Test]` Atrybut oznacza metodę metody testowej.

Zapisz ten plik i wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający NUnit zawiera punkt wejścia programu do uruchomienia testów. `dotnet test` Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Należy ten test jest przekazywany za pomocą pisania kodu najprostsza w `PrimeService` klasy, która działa:

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

W *jednostki — testowanie — przy użyciu nunit* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test. Przekazuje ono.

## <a name="adding-more-features"></a>Dodawanie więcej funkcji.

Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej. Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1. Można dodać nowe testy z `[Test]` atrybut, ale szybko staje się nużące. Istnieją inne atrybuty NUnit, które pozwalają na zapis zestaw testów podobne.  A `[TestCase]` atrybut służy do tworzenia zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe. Można użyć `[TestCase]` atrybutu, aby określić wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, zastosuj ten atrybut można utworzyć jeden testu opartego na danych. Dane zmiennych testu jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem. Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:

```csharp
if (candidate < 2)
```

Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego. Masz [Zakończono wersji testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki. Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy. Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.
