---
title: Jednostka testowania w .NET Core
description: Testy jednostkowe jest wyjątkowo proste. Zobacz temat jak korzystać jednostki testowania w projektach platformy .NET Core i .NET Standard.
keywords: .NET, testy jednostkowe .NET core .NET Standard
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.workload:
- dotnetcore
ms.openlocfilehash: cb78a66a3a6a7158a86a76d62e5230c75b51a416
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testowanie w .NET Core i .NET Standard jednostki

.NET core został zaprojektowany z pola na uwadze, dzięki czemu tworzenia testów jednostkowych dla aplikacji jest łatwiejsze niż kiedykolwiek przedtem. W tym artykule przedstawiono krótkie jednostki testów (i jak są one różne od innych rodzajów testów). Połączonych zasobów pokazują, jak dodać projekt testowy do rozwiązania, a następnie uruchom testy jednostkowe przy użyciu wiersza polecenia lub programu Visual Studio.

Obsługuje .NET core 2.0 [.NET 2.0 standardowe](../../standard/net-standard.md). Biblioteki używany do przedstawiania testowania w tej sekcji jednostki zależne .NET Standard i będzie działać w innych typów projektów.

Począwszy od programu .NET Core 2.0, Brak szablonów projektu testu jednostki dla języka Visual Basic i F # oraz jak C#.

## <a name="getting-started-with-testing"></a>Wprowadzenie do testowania

Zestaw testów automatycznych jest jednym z najlepszych sposobów upewnij się, że aplikacja jest twórców przeznaczenie wykonania. Istnieją różne rodzaje testów dla aplikacji, w tym testy integracji, testy sieci web, testy obciążenia i innych. Testy jednostkowe, testujące składniki oprogramowania lub metody są najniższego poziomu testów. Testy jednostkowe należy przetestować tylko kod w formancie projektanta i nie należy przetestować dotyczy infrastruktury, takich jak bazy danych, systemy plików i zasobów sieciowych. Testy jednostkowe mogą być napisane przy użyciu [testu Driven Development (TDD)](http://deviq.com/test-driven-development/), lub można dodać do istniejącego kodu, aby potwierdzić jego poprawności. W obu przypadkach należy je mały, dobrze nazwane i szybkie, ponieważ najlepiej chcesz będzie można uruchamiać setki je przed wypchnięciem zmian do repozytorium udostępniony kod projektu.

> [!NOTE]
> Deweloperzy napotykają z powtarzający się z dobrej nazwy metod i klasy testowe. Jako punkt początkowy, następuje zespołu produktu ASP.NET [tych konwencji](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Podczas pisania testów jednostkowych, należy zachować ostrożność przypadkowo nie spowodują zależne od infrastruktury. Te nadają się testy wolniejszy i bardziej łamliwa i w związku z tym powinna być zarezerwowana dla testów integracji. Można uniknąć ukryte zależności w kodzie aplikacji, postępując [jawne zależności zasady](http://deviq.com/explicit-dependencies-principle/) i przy użyciu [iniekcji zależności](/aspnet/core/fundamentals/dependency-injection) żądania zależności w ramach. Można również przechowywać testy jednostkowe w oddzielny projekt z testów integracji i upewnij się, że Twoje jednostkowy projekt testowy nie ma odwołań do ani zależności od infrastruktury pakietów.

Dowiedz się więcej na temat testowania w projektach platformy .NET Core jednostek:

Projektów testów jednostkowych dla .NET Core są obsługiwane w przypadku [C#](../../csharp/index.md), [F #](../../fsharp/index.md) i [Visual Basic](../../visual-basic/index.md). Można również wybrać [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) i [MSTest](https://github.com/Microsoft/vstest-docs).

Możesz przeczytać temat kombinacji w te wskazówki:

* Tworzenie testów jednostkowych za pomocą [ *XUnit* i *C#* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-dotnet-test.md).
* Tworzenie testów jednostkowych za pomocą [ *NUnit* i *C#* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-nunit.md).
* Tworzenie testów jednostkowych za pomocą [ *MSTest* i *C#* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-mstest.md).
* Tworzenie testów jednostkowych za pomocą [ *XUnit* i *F #* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Tworzenie testów jednostkowych za pomocą [ *NUnit* i *F #* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-nunit.md).
* Tworzenie testów jednostkowych za pomocą [ *MSTest* i *F #* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-mstest.md).
* Tworzenie testów jednostkowych za pomocą [ *XUnit* i *Visual Basic* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Tworzenie testów jednostkowych za pomocą [ *NUnit* i *Visual Basic* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-nunit.md).
* Tworzenie testów jednostkowych za pomocą [ *MSTest* i *Visual Basic* z poziomu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-mstest.md).

Można wybrać w różnych językach dla bibliotek klas i urządzenia testowych bibliotek. Aby dowiedzieć się jak przez dopasowanie i mieszanie wskazówki wymienionych powyżej.

* Visual Studio Enterprise oferuje doskonałą narzędzia do testowania dla platformy .NET Core. Zapoznaj się z [Live testów jednostkowych](/visualstudio/test/live-unit-testing) lub [pokrycie kodu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) Aby dowiedzieć się więcej.
* Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów selektywnego jednostki, zobacz [przeprowadzanie testów jednostkowych selektywne](selective-unit-tests.md), lub [Włączanie i wyłączanie testami w Visual Studio](/visualstudio/test/live-unit-testing#including-and-excluding-test-projects-and-test-methods).
* Zespół XUnit został zapisany Samouczek przedstawiający [sposobu korzystania z platformy .NET Core i Visual Studio xUnit](http://xunit.github.io/docs/getting-started-dotnet-core.html).
