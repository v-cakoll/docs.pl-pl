---
title: Testowanie jednostek w .NET Core i .NET Standard
description: Testowanie jednostek w projektach .NET Core i .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: b63b2706a9a97413a7166c87ae25cbe964e4610b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170018"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testowanie jednostek w .NET Core i .NET Standard

.NET core ułatwia tworzenie testów jednostkowych. Ten artykuł wprowadza testów jednostkowych i pokazano, jak różnią się od innych rodzajów testów. Połączone zasoby w dolnej części strony pokazują, jak dodać projekt testu do rozwiązania. Po skonfigurowaniu projektu testu, będzie można uruchomić testy jednostkowe przy użyciu wiersza polecenia lub programu Visual Studio.

.NET core 2.0 i jego nowsze wersje obsługują [.NET Standard 2.0](../../standard/net-standard.md), i użyjemy jej bibliotek do zademonstrowania testów jednostkowych.

Można użyć wbudowanych .NET Core 2.0 i nowszych szablony projektu testu jednostki dla C#, F# i Visual Basic jako punktu wyjścia dla osobistych projektu.

## <a name="what-are-unit-tests"></a>Co to są testy jednostkowe?

Testy automatyczne jest doskonałym sposobem na upewnij się, że aplikacja jest co jego autorzy mają, mu. Istnieje wiele typów testów dla aplikacji. Obejmują one testy integracji, testy sieci web, testy obciążenia i inne. **Testy jednostkowe** testowanie składników oprogramowania i metody. Testy jednostkowe należy przetestować tylko kod znajdujących się pod kontrolą dewelopera. Należy Testuj uwagi infrastrukturze. Problemy z infrastrukturą obejmują baz danych, systemy plików i zasobów sieciowych. 

Ponadto należy pamiętać, są najlepsze rozwiązania dotyczące pisania testów. Na przykład [testów opartych na rozwój (TDD)](https://deviq.com/test-driven-development/) jest, gdy test jednostkowy jest zapisywany przed kodem jest przeznaczona do sprawdzenia. Projektowanie oparte na testach przypomina tworzenie konspektu dla książki, zanim napiszemy ją. Jego celem jest pomoc deweloperom pisanie kodu prostsze, bardziej czytelne i wydajne. 

> [!NOTE]
> Poniżej zespołu ASP.NET [tych konwencji](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests) pomagające deweloperom pozwoli uzyskać dobrą nazwy metod i klas testów.

Nie należy wprowadzać zależności w infrastrukturze podczas pisania testów jednostkowych. Te upewnij testy powolne i kruchy i powinna być zarezerwowana dla testów integracji. Można uniknąć tych zależności w aplikacji, postępując zgodnie z [jawne zależności zasady](https://deviq.com/explicit-dependencies-principle/) i przy użyciu [wstrzykiwanie zależności](/aspnet/core/fundamentals/dependency-injection). Testy jednostkowe można również przechowywać w osobnym projekcie z testów integracji. Dzięki temu projektu testu jednostkowego nie ma odwołań do lub zależności w pakietach infrastruktury.

Więcej informacji na temat testowanie jednostek w projektach .NET Core:

Projekty testów jednostkowych .NET core są obsługiwane:
* [C#](../../csharp/index.md)
* [F#](../../fsharp/index.md)
* [Visual Basic](../../visual-basic/index.md) 

Można również wybrać:
* [xUnit](https://xunit.github.io) 
* [NUnit](https://nunit.org)
* [MSTest](https://github.com/Microsoft/vstest-docs)

Możesz dowiedzieć się więcej, zobacz następujące instruktaże:

* Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *C#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-dotnet-test.md).
* Tworzenie testów jednostkowych przy użyciu [ *NUnit* i *C#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-nunit.md).
* Tworzenie testów jednostkowych przy użyciu [ *MSTest* i *C#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-mstest.md).
* Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *F#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Tworzenie testów jednostkowych przy użyciu [ *NUnit* i *F#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-nunit.md).
* Tworzenie testów jednostkowych przy użyciu [ *MSTest* i *F#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-mstest.md).
* Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *języka Visual Basic* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Tworzenie testów jednostkowych przy użyciu [ *NUnit* i *języka Visual Basic* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-nunit.md).
* Tworzenie testów jednostkowych przy użyciu [ *MSTest* i *języka Visual Basic* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-mstest.md).

Możesz dowiedzieć się więcej, zobacz następujące artykuły:

* Program Visual Studio Enterprise oferuje doskonałe narzędzia testujące dla platformy .NET Core. Zapoznaj się z [Live Unit Testing](/visualstudio/test/live-unit-testing) lub [pokrycia kodu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) Aby dowiedzieć się więcej.
* Aby uzyskać więcej informacji na temat sposobu uruchamiania selektywnych testów jednostkowych, zobacz [uruchamianie selektywnych testów jednostkowych](selective-unit-tests.md), lub [dołączaniu i wykluczaniu testy za pomocą programu Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* [Jak korzystać xUnit przy użyciu platformy .NET Core i Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
