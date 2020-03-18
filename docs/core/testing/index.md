---
title: Testowanie jednostkowe w programach .NET Core i .NET Standard
description: Ten artykuł zawiera krótkie omówienie testów jednostkowych dla projektów .NET Core i .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 1263bfe337b9d6609c0ca7df70aa299a61a7f1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78157404"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testowanie jednostkowe w programach .NET Core i .NET Standard

Program .NET Core ułatwia tworzenie testów jednostkowych. W tym artykule przedstawiono testy jednostkowe i ilustruje, jak różnią się one od innych rodzajów testów. Połączone zasoby w dolnej części strony pokazują, jak dodać projekt testowy do rozwiązania. Po skonfigurowaniu projektu testowego będzie można uruchomić testy jednostkowe przy użyciu wiersza polecenia lub programu Visual Studio.

Jeśli testujesz projekt **ASP.NET Core,** zobacz [Testy integracji w ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).

.NET Core 2.0 i nowsze obsługuje [.NET Standard 2.0](../../standard/net-standard.md), a my użyjemy jego bibliotek do zademonstrowania testów jednostkowych.

Istnieje możliwość użycia wbudowanych szablonów projektów testów jednostkowych .NET Core 2.0 i nowszych dla języka C#, F# i Visual Basic jako punktu wyjścia dla projektu osobistego.

## <a name="what-are-unit-tests"></a>Co to są testy jednostkowe?

Posiadanie zautomatyzowanych testów to świetny sposób na zapewnienie, że aplikacja robi to, co jej autorzy zamierzają zrobić. Istnieje wiele typów testów dla aplikacji. Należą do nich testy integracji, testy sieci web, testy obciążenia i inne. **Testy jednostkowe** testują poszczególne składniki i metody oprogramowania. Testy jednostkowe powinny testować tylko kod w ramach kontroli dewelopera. Nie powinny one testować problemów związanych z infrastrukturą. Problemy z infrastrukturą obejmują bazy danych, systemy plików i zasoby sieciowe.

Należy również pamiętać, że istnieją najlepsze rozwiązania dotyczące pisania testów. Na przykład [test driven development (TDD)](https://deviq.com/test-driven-development/) jest, gdy test jednostkowy jest zapisywany przed kodem jest przeznaczony do sprawdzania. TDD jest jak tworzenie konspektu książki, zanim ją napiszemy. Ma pomóc deweloperom pisać prostszy, bardziej czytelny i wydajny kod.

> [!NOTE]
> Zespół ASP.NET następuje [po tych konwencjach,](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) aby pomóc deweloperom wymyślić dobre nazwy dla klas testowych i metod.

Staraj się nie wprowadzać zależności od infrastruktury podczas zapisywania testów jednostkowych. Dzięki tym testy są powolne i kruche i powinny być zarezerwowane dla testów integracji. Można uniknąć tych zależności w aplikacji, postępując zgodnie z [zasadą jawne zależności](https://deviq.com/explicit-dependencies-principle/) i przy użyciu [iniekcji zależności](/aspnet/core/fundamentals/dependency-injection). Można również zachować testy jednostkowe w oddzielnym projekcie z testów integracji. Dzięki temu projekt testu jednostkowego nie ma odwołań do pakietów infrastruktury ani zależności.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat testowania jednostkowego w projektach .NET Core:

Projekty testów jednostkowych .NET Core są obsługiwane dla:

- [C #](../../csharp/index.yml)
- [F #](../../fsharp/index.yml)
- [Visual Basic](../../visual-basic/index.yml)

Można również wybrać między:

- [Xunit](https://xunit.github.io)
- [Nunit](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Więcej informacji można uzyskać w poniższych instruktatach:

- Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *C#* przy użyciu .NET Core CLI](unit-testing-with-dotnet-test.md).
- Tworzenie testów jednostkowych przy użyciu [ *nunit* i *C#* przy użyciu .NET Core CLI](unit-testing-with-nunit.md).
- Tworzenie testów jednostkowych przy użyciu [ *programu MSTest* i *C#* przy użyciu procesora CLI .NET Core](unit-testing-with-mstest.md).
- Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *F#* przy użyciu .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).
- Tworzenie testów jednostkowych przy użyciu [ *nunit* i *F#* przy użyciu .NET Core CLI](unit-testing-fsharp-with-nunit.md).
- Tworzenie testów jednostkowych przy użyciu [ *programu MSTest* i *F#* przy użyciu procesora CLI .NET Core](unit-testing-fsharp-with-mstest.md).
- Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *Visual Basic* za pomocą procesora .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).
- Tworzenie testów jednostkowych przy użyciu [ *funkcji NUnit* i *Visual Basic* przy użyciu procesora CLI .NET Core](unit-testing-visual-basic-with-nunit.md).
- Tworzenie testów jednostkowych przy użyciu [ *programu MSTest* i *języka Visual Basic* przy użyciu procesora CLI .NET Core](unit-testing-visual-basic-with-mstest.md).

Więcej informacji można uzyskać w następujących artykułach:

- Visual Studio Enterprise oferuje doskonałe narzędzia do testowania .NET Core. Zapoznaj się z [testami jednostkowych na żywo](/visualstudio/test/live-unit-testing) lub [zasięgiem kodu,](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) aby dowiedzieć się więcej.
- Aby uzyskać więcej informacji na temat uruchamiania selektywnych testów jednostkowych, zobacz [Uruchamianie testów jednostkowych selektywnych](selective-unit-tests.md)lub [w tym i wykluczanie testów z programu Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
- [Jak używać xUnit z .NET Core i Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
