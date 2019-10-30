---
title: Port z .NET Framework do platformy .NET Core
description: Poznaj proces przenoszenia i odnajdywanie narzędzi, które mogą okazać się przydatne podczas przenoszenia projektu .NET Framework do programu .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89f00e5c6ce7f3cea7a3135c9b2856c54a70da40
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038533"
---
# <a name="overview-of-the-porting-process-from-net-framework-to-net-core"></a>Przegląd procesu przenoszenia z .NET Framework do platformy .NET Core

Być może masz kod, który jest obecnie uruchomiony na .NET Framework, które interesują się portem .NET Core. Ten artykuł zawiera następujące informacje:

* Przegląd procesu przenoszenia.
* Lista narzędzi, które mogą być przydatne podczas przenoszenia kodu do programu .NET Core.

## <a name="overview-of-the-porting-process"></a>Przegląd procesu przenoszenia

Zalecamy użycie następującego procesu podczas przenoszenia projektu do programu .NET Core:

1. Przekieruj wszystkie projekty, które chcesz przenieść, aby określić .NET Framework 4.7.2 lub wyższy.

   Ten krok zapewnia, że można użyć alternatywnych interfejsów API dla konkretnych .NET Framework docelowych, gdy platforma .NET Core nie obsługuje określonego interfejsu API.

2. Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i sprawdź, czy są one przenośne do programu .NET Core.

   Narzędzie analizatora przenośności API analizuje skompilowane zestawy i generuje raport. Ten raport przedstawia podsumowanie wysokiego poziomu dotyczące przenoszenia i podział wszystkich używanych interfejsów API, które nie są dostępne w systemie NET Core.

3. Zainstaluj [Analizator interfejsów API platformy .NET](../../standard/analyzers/api-analyzer.md) w swoich projektach, aby identyfikować interfejsy API zgłaszające <xref:System.PlatformNotSupportedException> na niektórych platformach oraz inne potencjalne problemy ze zgodnością.

   To narzędzie jest podobne do analizatora przenośności, ale zamiast analizowania, jeśli elementy mogą być kompilowane na platformie .NET Core, zostaną przeanalizowane, jeśli używasz interfejsu API w sposób, który będzie generować <xref:System.PlatformNotSupportedException> w czasie wykonywania. Chociaż nie jest to typowe w przypadku przechodzenia z .NET Framework 4.7.2 lub wyższym, warto sprawdzić.

4. Przekonwertuj wszystkie zależności `packages.config` na format [PackageReference](/nuget/consume-packages/package-references-in-project-files) za pomocą [narzędzia konwersji w programie Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Ten krok obejmuje przekonwertowanie zależności ze starszego formatu `packages.config`. `packages.config` nie działa w oprogramowaniu .NET Core, dlatego ta konwersja jest wymagana, jeśli istnieją zależności pakietów.

5. Utwórz nowe projekty dla platformy .NET Core i skopiuj pliki źródłowe lub spróbuj skonwertować istniejący plik projektu za pomocą narzędzia.

   W przypadku programu .NET Core jest stosowany uproszczony (i różny) [Format pliku projektu](../tools/csproj.md) niż .NET Framework. Aby kontynuować, musisz przekonwertować pliki projektu w ten format.

6. Port kodu testu.

   Ponieważ przenoszenie do programu .NET Core jest taka znacząca zmiana w bazie kodu, zdecydowanie zaleca się przeprowadzenie testów do portu, dzięki czemu można uruchamiać testy podczas przenoszenia kodu do programu. MSTest, xUnit i NUnit działają na platformie .NET Core.

Ponadto możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty do formatu pliku projektu .NET Core za pomocą narzędzia [dotnet try-Convert](https://github.com/dotnet/try-convert) w ramach jednej operacji. `dotnet try-convert` nie ma gwarancji dla wszystkich projektów i może spowodować drobne zmiany w zachowaniu, które mogą się okazać zależne. Powinien być używany jako _punkt wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migracji projektu.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
