---
title: Testowanie jednostkowe C# z NUnit i .NET Core
description: Poznaj pojęcia dotyczące testów jednostkowych w językach C# i .NET Core, korzystając z interakcyjnego środowiska, które krok po kroku przy użyciu testu dotnet i NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240886"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testowanie jednostkowe C# z NUnit i .NET Core

W tym samouczku można za pośrednictwem interakcyjnego środowiska tworzenia przykładowego rozwiązania krok po kroku, aby dowiedzieć się pojęcia testowania jednostek. Jeśli wolisz postępować zgodnie z samouczkiem przy użyciu wstępnie utworzonego rozwiązania, [wyświetl lub pobierz przykładowy kod](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) przed rozpoczęciem. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.
- Wybrany edytor tekstu lub edytor kodu.

## <a name="creating-the-source-project"></a>Tworzenie projektu źródłowego

Otwórz okno powłoki. Utwórz katalog o nazwie *unit-testing-using-nunit* do przechowywania rozwiązania. W tym nowym katalogu uruchom następujące polecenie, aby utworzyć nowy plik rozwiązania dla biblioteki klas i projektu testowego:

```dotnetcli
dotnet new sln
```

Następnie utwórz katalog *PrimeService.* Poniższy konspekt pokazuje strukturę katalogów i plików do tej pory:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Utwórz *PrimeService* bieżący katalog i uruchom następujące polecenie, aby utworzyć projekt źródłowy:

```dotnetcli
dotnet new classlib
```

Zmień nazwę *Class1.cs* na *PrimeService.cs*. Tworzenie nieudanej implementacji `PrimeService` klasy:

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

Zmień katalog z powrotem na katalog *jednostek testujących-przyużyciu nunit.* Uruchom następujące polecenie, aby dodać projekt biblioteki klas do rozwiązania:

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Tworzenie projektu testowego

Następnie utwórz katalog *PrimeService.Tests.* Poniższy konspekt przedstawia strukturę katalogów:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Utwórz katalog *PrimeService.Tests* jako bieżący katalog i utwórz nowy projekt przy użyciu następującego polecenia:

```dotnetcli
dotnet new nunit
```

[Dotnet nowe](../tools/dotnet-new.md) polecenie tworzy projekt testowy, który używa NUnit jako biblioteki testowej. Wygenerowany szablon konfiguruje testrunner w pliku *PrimeService.Tests.csproj:*

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Projekt testowy wymaga innych pakietów do tworzenia i uruchamiania testów jednostkowych. `dotnet new`w poprzednim kroku dodano zestaw SDK testów firmy Microsoft, platformę testową NUnit i kartę testową NUnit. Teraz dodaj `PrimeService` bibliotekę klas jako inną zależność do projektu. Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Możesz zobaczyć cały plik w [repozytorium próbek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) w uspolu GitHub.

Poniższy konspekt przedstawia ostateczny układ rozwiązania:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

Wykonaj następujące polecenie w katalogu jednostek testujących jednostkę:Execute the following command in the *unit-testing-using-nunit directory:*

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Tworzenie pierwszego testu

Piszesz jeden test nie, sprawiają, że przechodzi, a następnie powtórzyć proces. W katalogu *PrimeService.Tests* zmień nazwę *pliku UnitTest1.cs* na *PrimeService_IsPrimeShould.cs* i zastąp całą jego zawartość następującym kodem:

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

Atrybut `[TestFixture]` oznacza klasę, która zawiera testy jednostkowe. Atrybut `[Test]` wskazuje, że metoda jest metodą testową.

Zapisz ten plik [`dotnet test`](../tools/dotnet-test.md) i wykonaj, aby utworzyć testy i biblioteki klas, a następnie uruchomić testy. Program testowy NUnit zawiera punkt wejścia programu do uruchamiania testów. `dotnet test`uruchamia testrunnerprzy użyciu utworzonego projektu testu jednostkowego.

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

W katalogu *unit-testing-using-nunit* `dotnet test` uruchom ponownie. Polecenie `dotnet test` uruchamia kompilację `PrimeService` dla projektu, `PrimeService.Tests` a następnie dla projektu. Po zbudowaniu obu projektów uruchamia ten pojedynczy test. Mija.

## <a name="adding-more-features"></a>Dodawanie kolejnych funkcji

Teraz, gdy dokonałeś jednego testu, nadszedł czas, aby napisać więcej. Istnieje kilka innych prostych przypadków liczb pierwszych: 0, -1. Można dodać nowe testy `[Test]` z atrybutem, ale szybko staje się żmudne. Istnieją inne atrybuty Jednostki Jednostki, które umożliwiają pisanie zestawu podobnych testów.  Atrybut `[TestCase]` służy do tworzenia zestawu testów, które wykonują ten sam kod, ale mają różne argumenty wejściowe. Atrybutu `[TestCase]` można użyć do określenia wartości dla tych danych wejściowych.

Zamiast tworzyć nowe testy, należy zastosować ten atrybut, aby utworzyć test oparty na pojedynczej podstawie danych. Test oparty na danych jest metodą, która testuje kilka wartości mniej niż dwie, co jest najniższą liczbą pierwszą:

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Uruchom `dotnet test`, a dwa z tych testów nie powiedzie się. Aby wszystkie testy zostały zdatce, zmień `if` `Main` klauzulę na początku metody w *pliku PrimeService.cs:*

```csharp
if (candidate < 2)
```

Kontynuuj iterowanie, dodając więcej testów, więcej teorii i więcej kodu w bibliotece głównej. Masz [gotową wersję testów](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) i [pełną implementację biblioteki.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)

Utworzono małą bibliotekę i zestaw testów jednostkowych dla tej biblioteki. Ustrukturyzowano rozwiązanie tak, aby dodawanie nowych pakietów i testów było częścią normalnego przepływu pracy. Większość czasu i wysiłku skoncentrowałeś na rozwiązywaniu celów aplikacji.
