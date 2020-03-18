---
title: Port z platformy .NET Framework do .NET Core
description: Zrozumienie procesu przenoszenia i odnajdowania narzędzi, które mogą okazać się przydatne podczas przenoszenia projektu .NET Framework do .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937318"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Omówienie przenoszenia z platformy .NET Framework do programu .NET Core

Może być kod, który jest obecnie uruchamiany w platformie .NET Framework, który jest zainteresowany przeniesieniem do .NET Core. Ten artykuł zawiera:

* Przegląd procesu przenoszenia.
* Lista narzędzi, które mogą okazać się przydatne podczas przenoszenia kodu do .NET Core.

## <a name="overview-of-the-porting-process"></a>Omówienie procesu przenoszenia

Zaleca się użycie następującego procesu podczas przenoszenia projektu do .NET Core:

1. Ponownie kieruj wszystkie projekty, które chcesz przenieść do celu .NET Framework 4.7.2 lub nowsze.

   Ten krok zapewnia, że można użyć alternatyw interfejsu API dla obiektów docelowych specyficznych dla platformy .NET Framework, gdy program .NET Core nie obsługuje określonego interfejsu API.

2. [Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) służy do analizowania zestawów i sprawdzania, czy są one przenośne do .NET Core.

   Narzędzie Analizator przenośności interfejsu API analizuje skompilowane zestawy i generuje raport. Ten raport zawiera podsumowanie przenoszenia wysokiego poziomu i podział każdego interfejsu API, który jest przy użyciu, który nie jest dostępny w net core.

3. Zainstaluj [analizator interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) <xref:System.PlatformNotSupportedException> w swoich projektach, aby zidentyfikować interfejsy API, które mogą zgłaszać na niektórych platformach i niektóre inne potencjalne problemy ze zgodnością.

   To narzędzie jest podobne do analizatora przenośności, ale zamiast analizować, czy kod może opierać się na .NET Core, <xref:System.PlatformNotSupportedException> analizuje, czy używasz interfejsu API w sposób, który będzie zgłaszać w czasie wykonywania. Chociaż nie jest to typowe, jeśli przechodzisz z .NET Framework 4.7.2 lub nowszego, warto to sprawdzić. Aby uzyskać więcej informacji na temat interfejsów API, które zgłaszają wyjątki w uspolonym .NET Core, zobacz [interfejsy API, które zawsze zgłaszają wyjątki w .NET Core](../compatibility/unsupported-apis.md).

4. Konwertuj wszystkie zależności `packages.config` na format [PackageReference](/nuget/consume-packages/package-references-in-project-files) za pomocą narzędzia do konwersji w programie Visual [Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Ten krok polega na konwertowaniu `packages.config` zależności ze starszego formatu. `packages.config`nie działa na .NET Core, więc ta konwersja jest wymagana, jeśli masz zależności pakietów.

5. Utwórz nowe projekty dla programu .NET Core i skopiuj pliki źródłowe lub spróbuj przekonwertować istniejący plik projektu za pomocą narzędzia.

   Program .NET Core używa uproszczonego (i innego) [formatu pliku projektu](../tools/csproj.md) niż .NET Framework. Aby kontynuować, musisz przekonwertować pliki projektu na ten format.

6. Przenieś kod testu.

   Ponieważ przeniesienie do .NET Core jest tak istotną zmianą w bazie kodu, zdecydowanie zaleca się przeniesienie projektów testowych, aby można było uruchamiać testy podczas przenoszenia kodu. MsTest, xUnit i NUnit działają na .NET Core.

Ponadto można próbować przenieść mniejsze rozwiązania lub poszczególne projekty w jednej operacji do formatu pliku projektu .NET Core za pomocą narzędzia [do tnet try-convert.](https://github.com/dotnet/try-convert) `dotnet try-convert`nie gwarantuje pracy dla wszystkich projektów i może powodować subtelne zmiany w zachowaniu, od których zależałeś. Użyj go jako _punktu wyjścia,_ który automatyzuje podstawowe rzeczy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migracji projektu.

## <a name="next-steps"></a>Następne kroki

>[!div class="nextstepaction"]
>[Analizowanie zależności](third-party-deps.md)
