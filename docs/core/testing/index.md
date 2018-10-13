---
title: Testowanie jednostek w platformy .NET Core
description: Testowanie jednostek jest łatwiejsze niż dotychczas. Zobacz, jak używać testowanie jednostek w projektach .NET Core i .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 5b54e7936fb19a94fad9585c00904ae67a59e064
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2018
ms.locfileid: "49314867"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testowanie jednostek w .NET Core i .NET Standard

.NET core został zaprojektowany z testowalnością, pamiętając, tak, aby tworzenie testów jednostkowych dla aplikacji jest łatwiejsze niż kiedykolwiek przedtem. W tym artykule przedstawiono pokrótce jednostek testów (i jak będą się różnić od innych rodzajów testów). Połączone zasoby pokazują, jak dodać projekt testu do rozwiązania, a następnie uruchom testy jednostkowe przy użyciu wiersza polecenia lub programu Visual Studio.

.NET core 2.0 obsługuje [.NET Standard 2.0](../../standard/net-standard.md). Biblioteki używany do przedstawiania testowanie jednostek w tej sekcji zależą od .NET Standard i będzie działać w innych typów projektów.

Począwszy od programu .NET Core 2.0, Brak szablonów projektu testu jednostki dla języka C#, F # i Visual Basic.

## <a name="getting-started-with-testing"></a>Wprowadzenie do testowania

Zestaw testów automatycznych jest jednym z najlepszych sposobów upewnij się, że aplikacja oprogramowania jest jego autorzy przeznaczenie mu. Istnieją różne rodzaje testów dla aplikacji oprogramowania, w tym testy integracji, testy sieci web, testy obciążenia i inne. Testy jednostkowe, które testują składników oprogramowania, jak i metody są najniższego poziomu testów. Testy jednostkowe tylko należy przetestować kod znajdujących się pod kontrolą dewelopera, a nie należy testować obaw infrastruktury, takich jak bazy danych, systemy plików i zasobów sieciowych. Testy jednostkowe mogą być napisane przy użyciu [testów opartych na rozwój (TDD)](https://deviq.com/test-driven-development/), lub można ich dodać do istniejącego kodu, aby potwierdzić gwarantującym jego poprawnego działania. W obu przypadkach należy je małe, dobrze nazwane i szybkiego działania, ponieważ najlepiej chcesz można było uruchomić setki je przed wypchnięciem zmian do projektu udostępnionego kodu repozytorium.

> [!NOTE]
> Deweloperzy napotykają problemy z pojawi się z dobrej nazw dla swojej klasy testów i metody. Jako punktu wyjścia, następuje zespół pracujący nad produktem ASP.NET [tych konwencji](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Podczas pisania testów jednostkowych, należy zachować ostrożność, nie spowodują przypadkowo zależności w infrastrukturze. Te nadają się testy wolniejszy i bardziej kruchy i dlatego powinna być zarezerwowana dla testów integracji. Możesz uniknąć tych ukrytych zależności w kodzie aplikacji, postępując zgodnie z [jawne zależności zasady](https://deviq.com/explicit-dependencies-principle/) i przy użyciu [wstrzykiwanie zależności](/aspnet/core/fundamentals/dependency-injection) do żądania z zależności w ramach. Można zapobiec w osobnym projekcie testów integracji testy jednostkowe i upewnij się, że projektu testu jednostkowego nie ma odwołań do lub zależności w pakietach infrastruktury.

Dowiedz się więcej na temat testowanie jednostek w projektach .NET Core:

Projekty testów jednostkowych dla platformy .NET Core są obsługiwane w przypadku [C#](../../csharp/index.md), [F #](../../fsharp/index.md) i [języka Visual Basic](../../visual-basic/index.md). Możesz również wybrać [xUnit](https://xunit.github.io), [NUnit](https://nunit.org) i [MSTest](https://github.com/Microsoft/vstest-docs).

Możesz przeczytać o kombinacji w tych przewodników:

* Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *C#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-dotnet-test.md).
* Tworzenie testów jednostkowych przy użyciu [ *NUnit* i *C#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-nunit.md).
* Tworzenie testów jednostkowych przy użyciu [ *MSTest* i *C#* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-with-mstest.md).
* Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *F #* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Tworzenie testów jednostkowych przy użyciu [ *NUnit* i *F #* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-nunit.md).
* Tworzenie testów jednostkowych przy użyciu [ *MSTest* i *F #* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-fsharp-with-mstest.md).
* Tworzenie testów jednostkowych przy użyciu [ *xUnit* i *języka Visual Basic* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Tworzenie testów jednostkowych przy użyciu [ *NUnit* i *języka Visual Basic* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-nunit.md).
* Tworzenie testów jednostkowych przy użyciu [ *MSTest* i *języka Visual Basic* przy użyciu interfejsu wiersza polecenia platformy .NET Core](unit-testing-visual-basic-with-mstest.md).

Można wybrać różne języki dla bibliotek klas i danej jednostki. przetestuj bibliotek. Możesz dowiedzieć się jak, mieszanie i dopasowywanie przewodniki wymienionych powyżej.

* Program Visual Studio Enterprise oferuje doskonałe narzędzia testujące dla platformy .NET Core. Zapoznaj się z [Live Unit Testing](/visualstudio/test/live-unit-testing) lub [pokrycia kodu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) Aby dowiedzieć się więcej.
* Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](selective-unit-tests.md), lub [dołączaniu i wykluczaniu testy za pomocą programu Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* Zespół xUnit zapisane samouczek, który pokazuje [sposobu użycia xUnit przy użyciu platformy .NET Core i Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
