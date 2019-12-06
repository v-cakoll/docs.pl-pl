---
title: Testy jednostkowe w .NET Core i .NET Standard
description: Ten artykuł zawiera krótkie omówienie testów jednostkowych dla projektów .NET Core i .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 63bbe2981f70093c94dde47510fd7786a1cc950b
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835463"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testy jednostkowe w .NET Core i .NET Standard

Program .NET Core ułatwia tworzenie testów jednostkowych. W tym artykule przedstawiono testy jednostkowe i pokazano, jak różnią się one od innych rodzajów testów. Połączone zasoby w dolnej części strony pokazują, jak dodać projekt testowy do rozwiązania. Po skonfigurowaniu projektu testowego będzie można uruchamiać testy jednostkowe przy użyciu wiersza polecenia lub programu Visual Studio.

Jeśli testujesz projekt **ASP.NET Core** , zobacz temat [testy integracji w programie ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).

Program .NET Core 2,0 lub nowszy obsługuje [.NET Standard 2,0](../../standard/net-standard.md)i będziemy używać ich w celu przedstawienia testów jednostkowych.

Możesz użyć wbudowanych szablonów projektu testów jednostkowych .NET Core 2,0 i nowszych dla C#, F# i Visual Basic jako punkt wyjścia dla projektu osobistego.

## <a name="what-are-unit-tests"></a>Co to są testy jednostkowe?

Posiadanie zautomatyzowanych testów to doskonały sposób, aby upewnić się, że aplikacja oprogramowania wykonuje działania wykonywane przez jego autorów. Istnieje wiele typów testów dla aplikacji oprogramowania. Obejmują one testy integracji, testy sieci Web, testy obciążenia i inne. **Testy jednostkowe** testują poszczególne składniki oprogramowania i metody. Testy jednostkowe powinny tylko testować kod w formancie dewelopera. Nie powinni testować obaw związanych z infrastrukturą. Zagadnienia dotyczące infrastruktury obejmują bazy danych, systemy plików i zasoby sieciowe. 

Należy również pamiętać o najlepszych rozwiązaniach dotyczących pisania testów. Na przykład [programowanie sterowane testami (TDD)](https://deviq.com/test-driven-development/) to gdy test jednostkowy jest zapisywana przed kodem, który ma zostać sprawdzona. TDD przypomina Tworzenie konspektu dla książki, zanim zapiszemy ją. Jest to pomocne, aby deweloperzy mogli pisać łatwiejszy, czytelny i wydajny kod. 

> [!NOTE]
> Zespół ASP.NET stosuje [te konwencje](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests) , aby ułatwić deweloperom tworzenie dobrych nazw dla klas i metod testowych.

Nie należy wprowadzać zależności od infrastruktury podczas pisania testów jednostkowych. Te testy są powolne i kruchy i powinny być zarezerwowane dla testów integracji. Można uniknąć tych zależności w aplikacji, postępując zgodnie z [zasadami jawnych zależności](https://deviq.com/explicit-dependencies-principle/) i przy użyciu [iniekcji zależności](/aspnet/core/fundamentals/dependency-injection). Możesz również utrzymać testy jednostkowe w osobnym projekcie od testów integracji. Gwarantuje to, że projekt testu jednostkowego nie zawiera odwołań do pakietów infrastruktury ani ich zależności.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat testów jednostkowych w projektach .NET Core:

Projekty testów jednostkowych programu .NET Core są obsługiwane w przypadku:

- [C#](../../csharp/index.yml)
- [F#](../../fsharp/index.yml)
- [Visual Basic](../../visual-basic/index.yml) 

Możesz również wybrać między:

- [xUnit](https://xunit.github.io) 
- [NUnit](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Więcej informacji można znaleźć w następujących przewodnikach:

- Utwórz testy jednostkowe za pomocą [ *xUnit* i *C#* z interfejs wiersza polecenia platformy .NET Core](unit-testing-with-dotnet-test.md).
- Utwórz testy jednostkowe za pomocą [ *nunit* i *C#* z interfejs wiersza polecenia platformy .NET Core](unit-testing-with-nunit.md).
- Utwórz testy jednostkowe za pomocą [ *MSTest* i *C#* z interfejs wiersza polecenia platformy .NET Core](unit-testing-with-mstest.md).
- Utwórz testy jednostkowe za pomocą [ *xUnit* i *F#* z interfejs wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-dotnet-test.md).
- Utwórz testy jednostkowe za pomocą [ *nunit* i *F#* z interfejs wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-nunit.md).
- Utwórz testy jednostkowe za pomocą [ *MSTest* i *F#* z interfejs wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-mstest.md).
- Utwórz testy jednostkowe za pomocą [ *xUnit* i *Visual Basic* z interfejs wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
- Utwórz testy jednostkowe za pomocą [ *NUnit* i *Visual Basic* z interfejs wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-nunit.md).
- Utwórz testy jednostkowe za pomocą [ *MSTest* i *Visual Basic* z interfejs wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-mstest.md).

Więcej informacji można znaleźć w następujących artykułach:

- Visual Studio Enterprise oferuje doskonałe narzędzia do testowania dla platformy .NET Core. Sprawdź [Live Unit Testing](/visualstudio/test/live-unit-testing) lub [pokrycie kodu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) , aby dowiedzieć się więcej.
- Aby uzyskać więcej informacji na temat uruchamiania selektywnych testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](selective-unit-tests.md)lub [uwzględnianie i wykluczanie testów w programie Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
- [Jak używać xUnit z platformą .NET Core i programem Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
