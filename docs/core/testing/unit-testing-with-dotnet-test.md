---
title: "Testowanie kodu C# w .NET Core za pomocą testu dotnet i xUnit jednostki"
description: "Dowiedz się pojęcia testu jednostki w języku C# i .NET Core za pośrednictwem interaktywnego środowisko tworzenia przykładowe rozwiązanie krok po kroku przy użyciu platformy dotnet testu i xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: a9e64fe37f05b7bbe05b1c5878e4b31084a1c8b6
ms.sourcegitcommit: 7296449e03f747528f9bc59954c74bf4e359cc1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Badanie C# .NET Core za pomocą testu dotnet i xUnit jednostki

Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) przed rozpoczęciem. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Umożliwia otwarcie okna powłoki. Utwórz katalog o nazwie *testowania — przy użyciu dotnet testu jednostkowego* do przechowywania rozwiązania.
Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania. Rozwiązanie o ułatwia zarządzanie biblioteki klas i jednostkowy projekt testowy.
Utwórz katalog rozwiązania *PrimeService* katalogu. Struktura katalogów i plików dotychczasowych powinna być następująca:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego. Zmień nazwę *Class1.cs* do *PrimeService.cs*. Aby użyć projektowanie oparte na testach (TDD), należy najpierw utworzyć niepowodzenie wykonania `PrimeService` klasy:

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

Zmień katalog z powrotem do *testowania — przy użyciu dotnet testu jednostkowego* katalogu.

Uruchom [dotnet sln](../tools/dotnet-sln.md) polecenie, aby dodać projektu biblioteki klas do rozwiązania:

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

Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new xunit` ](../tools/dotnet-new.md). To polecenie tworzy projekt testowy używającą xUnit jako biblioteka testów. Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.csproj* pliku podobny do następującego kodu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku należy dodać xUnit i xUnit modułu uruchamiającego testy. Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu. Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) w witrynie GitHub.

Poniżej przedstawiono układu ostatecznego rozwiązania:

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

Aby dodać projekt testowy do rozwiązania, uruchom [dotnet sln](../tools/dotnet-sln.md) w *testowania — przy użyciu dotnet testu jednostkowego* katalogu:

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces. Usuń *UnitTest1.cs* z *PrimeService.Tests* katalogu i Utwórz nowy plik C# o nazwie *PrimeService_IsPrimeShould.cs*. Dodaj następujący kod:

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

`[Fact]` Atrybut wskazuje metody testowej, który jest uruchamiany przez moduł uruchamiający. Z *PrimeService.Tests* folder, wykonaj [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy. Moduł uruchamiający xUnit zawiera punkt wejścia programu do uruchomienia testów. `dotnet test`Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.

Test zakończy się niepowodzeniem. Nie utworzono jeszcze implementacji. Należy ten test przez pisania kodu najprostsza w `PrimeService` klasy, która działa. Zastąp istniejące `IsPrime` implementacji metody z następującym kodem:

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

W *PrimeService.Tests* katalogu, uruchom `dotnet test` ponownie. `dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu. Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test. Przekazuje ono.

## <a name="adding-more-features"></a>Dodawanie więcej funkcji.

Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej. Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1. Możesz dodać tych przypadkach jako nowe testy z `[Fact]` atrybut, ale szybko staje się nużące. Istnieją inne atrybuty xUnit, które pozwalają na zapis zestaw testów podobne:

- `[Theory]`reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe.

- `[InlineData]`atrybut określa wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, zastosuj następujące dwa atrybuty `[Theory]` i `[InlineData]`, aby utworzyć jeden teorii w *PrimeService_IsPrimeShould.cs* pliku. Teorii jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie pierwsze:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test` ponownie, a dwa z tych testów powinna zakończyć się niepowodzeniem. Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku `IsPrime` metody w *PrimeService.cs* pliku:

```csharp
if (candidate < 2)
```

Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego. Masz [Zakończono wersji testów](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Dodatkowe zasoby

[Testowanie logiką kontrolera w ASP.NET Core](/aspnet/core/mvc/controllers/testing)
