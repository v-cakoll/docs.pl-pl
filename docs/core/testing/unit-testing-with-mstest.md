---
title: Testowanie jednostkowe C# z MSTest i .NET Core
description: Poznaj pojęcia dotyczące testów jednostkowych w językach C# i .NET Core, korzystając z interakcyjnego środowiska, które krok po kroku przy użyciu testu dotnet i programu MSTest jest oparte na interakcyjnym środowisku, w ramach tworzenia przykładowego rozwiązania.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240912"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>Testowanie jednostkowe C# z MSTest i .NET Core

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *unit-testing-using-mstest* do przechowywania rozwiązania. Wewnątrz tego nowego [`dotnet new sln`](../tools/dotnet-new.md) katalogu uruchom, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego. Następnie utwórz katalog *PrimeService.* Poniższy konspekt pokazuje do tej pory strukturę katalogów i plików:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Utwórz *PrimeService* bieżący [`dotnet new classlib`](../tools/dotnet-new.md) katalog i uruchom, aby utworzyć projekt źródłowy. Zmień nazwę *Class1.cs* na *PrimeService.cs*. Tworzenie nieudanej implementacji `PrimeService` klasy:

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

Zmień katalog z powrotem do katalogu *testów jednostkowych przy użyciu mstest.* Uruchom, [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) aby dodać projekt biblioteki klas do rozwiązania.

## <a name="create-the-test-project"></a>Tworzenie projektu testowego

Następnie utwórz katalog *PrimeService.Tests.* Poniższy konspekt przedstawia strukturę katalogów:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService.Tests* jako bieżący katalog [`dotnet new mstest`](../tools/dotnet-new.md)i utwórz nowy projekt przy użyciu . Dotnet nowe polecenie tworzy projekt testowy, który używa MSTest jako biblioteki testowej. Wygenerowany szablon konfiguruje testrunner w pliku *PrimeServiceTests.csproj:*

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano zestaw MSTest SDK, platformę testową MSTest i program mstest runner. Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) w uspolu GitHub.

Poniższy konspekt przedstawia ostateczny układ rozwiązania:

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

Wykonywanie [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) w katalogu *testów jednostkowych przy użyciu-mstest.*

## <a name="create-the-first-test"></a>Tworzenie pierwszego testu

Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces. Usuń *UnitTest1.cs* z katalogu *PrimeService.Tests* i utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs* z następującą zawartością:

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

[Atrybut TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) oznacza klasę, która zawiera testy jednostkowe. [TestMethod Atrybut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) wskazuje, że metoda jest metodą testową.

Zapisz ten plik [`dotnet test`](../tools/dotnet-test.md) i wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy. Program testowy MSTest zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

Test nie powiedzie się. Implementacja nie została jeszcze utworzona. Zrób ten test przejść, pisząc najprostszy kod w `PrimeService` klasie, która działa:

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

W katalogu *testów jednostkowych-using-mstest* uruchom `dotnet test` ponownie. Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia ten pojedynczy test. Mija.

## <a name="add-more-features"></a>Dodaj więcej funkcji

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1. Można dodać nowe testy z [TestMethod atrybut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale szybko staje się żmudne. Istnieją inne atrybuty MSTest, które umożliwiają pisanie zestawu podobnych testów.  [Atrybut DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) reprezentuje zestaw testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Atrybut [DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) służy do określania wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować te dwa atrybuty, aby utworzyć pojedynczy test oparty na danych. Test oparty na danych jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się. Aby wszystkie testy zostały zdatce, zmień klauzulę `if` na początku metody:

```csharp
if (candidate < 2)
```

Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)

Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy. Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Używanie struktury MSTest w testach jednostkowych](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [Dokumenty framework testów MSTest V2](https://github.com/Microsoft/testfx-docs)
