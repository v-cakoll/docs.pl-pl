---
title: Kod portu z .NET Framework do programu .NET Core
description: Poznaj proces przenoszenia i odnajdywanie narzędzi, które mogą okazać się przydatne podczas przenoszenia projektu .NET Framework do programu .NET Core.
author: cartermp
ms.date: 09/13/2019
ms.custom: seodec18
ms.openlocfilehash: b6c02932b5d9c7ccc2743dd38dddf2904f9c24e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039663"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>Przenoszenie kodu z .NET Framework do programu .NET Core

Jeśli masz kod, który jest uruchamiany na .NET Framework, możesz chcieć również uruchomić kod na platformie .NET Core. Poniżej przedstawiono omówienie procesu przenoszenia i listy narzędzi, które mogą być przydatne podczas przenoszenia kodu do programu .NET Core.

## <a name="overview-of-the-porting-process"></a>Przegląd procesu przenoszenia

Jest to proces, który zalecamy podczas przenoszenia projektu do programu .NET Core. Każdy krok procesu został szczegółowo omówiony w dalszych artykułach.

1. Zidentyfikuj i zapoznaj się z zależnościami innych firm.

   Ten krok polega na zrozumieniu zależności od innych firm, sposobach ich zawieszania, sposobie sprawdzania, czy są one również uruchamiane na platformie .NET Core, oraz czynności, które można wykonać, jeśli nie. Opisano w nim również, jak można migrować zależności do formatu [PackageReference](/nuget/consume-packages/package-references-in-project-files) , który jest używany w programie .NET Core.

2. Przekieruj wszystkie projekty, które chcesz przenieść, aby określić .NET Framework 4.7.2 lub wyższy.

   Ten krok zapewnia, że można użyć alternatywnych interfejsów API dla konkretnych .NET Framework docelowych, gdy platforma .NET Core nie obsługuje określonego interfejsu API.

3. Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i opracowywania planu na potrzeby portów na podstawie jego wyników.

   Narzędzie analizatora przenośności API analizuje skompilowane zestawy i generuje raport, który pokazuje podsumowanie wysokiego poziomu przenośności oraz podział wszystkich używanych interfejsów API, które nie są dostępne na stronie publicznej platformy .NET Core. Możesz użyć tego raportu wraz z analizą bazy kodu, aby opracować plan na potrzeby przenoszenia kodu.

4. Gdy plik projektu zostanie przekonwertowany na wersję docelową platformy .NET Core, można użyć [analizatora API platformy .NET](../../standard/analyzers/api-analyzer.md) opartego na Roslyn <xref:System.PlatformNotSupportedException> do identyfikowania interfejsów API zgłaszanych na niektórych platformach i innych potencjalnych problemów ze zgodnością.

5. Przenoszenie kodu testów.

   Ponieważ przenoszenie do programu .NET Core jest taka znacząca zmiana w bazie kodu, zdecydowanie zaleca się przeprowadzenie testów do portu, dzięki czemu można uruchamiać testy podczas przenoszenia kodu do programu. MSTest, xUnit i NUnit obsługują platformę .NET Core.

6. Wykonaj swój plan na potrzeby przenoszenia.

Poniższa lista zawiera narzędzia przydatne do użycia podczas procesu przenoszenia:

* Analizator przenośności .NET — [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) lub [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), narzędzie, które może generować raport dotyczący sposobu, w jaki przenośny kod jest między .NET Framework i docelową platformą .NET Core. Raport zawiera podział zestawu na zestaw dla typu i interfejsów API, których brakuje na docelowej platformie .NET Core. Aby uzyskać więcej informacji, zobacz [Analizator przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md). Zaleca się uruchomienie narzędzia analizatora przenośności platformy .NET przed rozpoczęciem przenoszenia, ponieważ ułatwi to zidentyfikowanie wszelkich luk w brakujących interfejsach API na określonej stronie publicznej platformy .NET.
* Analizator interfejsu API .NET — Roslyn, który odnajduje interfejs API .NET Standard, <xref:System.PlatformNotSupportedException> który zgłasza na niektórych platformach, wykrywa wywołania przestarzałych interfejsów API i odkryje inne potencjalne zagrożenia dla C# środowiska API na różnych platformach. Aby uzyskać więcej informacji, zobacz [.NET API Analyzer](../../standard/analyzers/api-analyzer.md). Ten analizator jest pomocny po utworzeniu projektu .NET Core, aby identyfikować różnice w działaniu środowiska uruchomieniowego na różnych platformach.
* Wyszukiwanie pakietów wstecznych — [przydatna usługa sieci Web](https://packagesearch.azurewebsites.net) , która umożliwia wyszukiwanie typu i znajdowanie pakietów zawierających ten typ.

Ponadto możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) .

> [!WARNING]
> CsprojToVs2017 jest narzędziem innej firmy. Nie ma gwarancji, że będzie ona działała we wszystkich projektach i może spowodować drobne zmiany w zachowaniu, od którego zależy. CsprojToVs2017 powinien być używany jako _punkt wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migrowania formatów plików projektu.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
