---
title: Port kodu z .NET Framework i .NET Core
description: Zrozumieć proces przenoszenia i Odkryj narzędzia, które mogą być przydatne podczas przenoszenia projektu .NET Framework i .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 870320c8467237e87a2675ec5cfb57647026d8ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663235"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>Przyłącz kod z .NET Framework i .NET Core

Jeśli masz kod, który jest uruchamiany w środowisku .NET Framework, może Cię zainteresować za uruchamianie kodu na platformę .NET Core. Poniżej przedstawiono omówienie procesu przenoszenia i listę narzędzi może się okazać przydatne podczas przenoszenia kodu platformy .NET Core.

## <a name="overview-of-the-porting-process"></a>Omówienie procesu przenoszenia

Jest to proces, firma Microsoft zaleca należy wykonać podczas przenoszenia projektu .NET Core. Każdy krok procesu zostało opisane bardziej szczegółowo w dalszej artykułów.

1. Identyfikuj i uwzględnić zależności innych firm.

   Ten krok obejmuje zrozumienie, jakie zależności innych firm są, jak zależeć na ich, w jaki sposób, aby sprawdzić, czy działają one również na platformy .NET Core i kroki można wykonać, jeśli tak nie jest. Obejmuje ona również, jak można migrować zależności za pośrednictwem do [PackageReference](/nuget/consume-packages/package-references-in-project-files) formatu, który jest używany w programie .NET Core.

2. Przekieruj wszystkie projekty, które chcesz dodać port dla środowiska .NET Framework 4.7.2 lub nowszej.

   Ten krok zapewnia, że można użyć interfejsu API alternatyw dla celów specyficzne dla platformy .NET Framework w przypadku platformy .NET Core nie obsługuje określony interfejs API.

3. Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i opracować plan do portu, na podstawie jej wyników.

   Narzędzie Analizator przenośności interfejsu API analizuje zestawy skompilowane i generuje raport zawierający podsumowanie wysokiego poziomu przenośność i podział każdy interfejs API używasz, nie jest dostępna na platformie .NET Core. Możesz użyć tego raportu, wraz z analizą Twojej bazy kodu, aby opracować plan dla jak Twój kod będzie portu za pośrednictwem.

4. Przyłącz kod testów.

   Eksportowanie do programu .NET Core jest znacząca zmiana bazie kodu, ma zdecydowanie zaleca uzyskanie przenoszone, testy, aby uruchomić testy zgodnie z portu kodu za pośrednictwem. MSTest, xUnit i NUnit obsługiwać platformę .NET Core.

5. Wykonaj swój plan w celu przenoszenia!

Na poniższej liście przedstawiono narzędzia, że może się okazać przydatne podczas przenoszenia proces:

* Narzędzia .NET portability Analyzer - [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) lub [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), łańcuch narzędzi, który można wygenerować raport jak przenośny kod jest między .NET Framework i .NET Core za pomocą zestaw, zestaw z rozbiciem na poszczególne problemy. Aby uzyskać więcej informacji, zobacz [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md).
* Analizator interfejsu API platformy .NET — analizatora Roslyn, który wykryje potencjalne zagrożenia zgodność dla C# interfejsów API na różnych platformach i wykrywa wywołania interfejsów API przestarzałych. Aby uzyskać więcej informacji, zobacz [analizatora interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md).
* Odwrócone wyszukiwanie pakietu - A [usługi sieci web przydatne](https://packagesearch.azurewebsites.net) umożliwiająca wyszukiwania dla typu i znajdowania pakiety zawierające tego typu.

Ponadto, możesz spróbować rozwiązań mniejszych portu lub poszczególnych projektów do formatu pliku projektu .NET Core za pomocą [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) narzędzia.

> [!WARNING] 
> CsprojToVs2017 to narzędzia innych firm. Nie ma żadnej gwarancji, która będzie działać w przypadku wszystkich swoich projektach i może spowodować, że wprowadzono subtelne zmiany w zachowaniu, który, na których polegasz. CsprojToVs2017 powinien być używany jako _punkt początkowy_ który automatyzuje podstawowe czynności, które można zautomatyzować. Nie jest gwarantowana rozwiązania do migrowania formatów plików projektu.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
