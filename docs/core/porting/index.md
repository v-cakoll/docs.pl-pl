---
title: Przenoszenie z programu .NET Framework na platformę .NET Core
description: Poznaj proces przenoszenia i odnajdywanie narzędzi, które mogą okazać się przydatne podczas przenoszenia projektu .NET Framework do programu .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: c6797a5b3a97ddd01f86498d896e859baf8997be
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158291"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Przegląd portów z .NET Framework do platformy .NET Core

Być może masz kod, który jest obecnie uruchomiony na .NET Framework, które interesują się portem .NET Core. Ten artykuł zawiera:

* Przegląd procesu przenoszenia.
* Lista narzędzi, które mogą być przydatne podczas przenoszenia kodu do programu .NET Core.

## <a name="overview-of-the-porting-process"></a>Przegląd procesu przenoszenia

Przenoszenie do platformy .NET Core (lub .NET Standard) z .NET Framework dla wielu projektów jest stosunkowo proste. Istnieją pewne zmiany, które są wymagane, ale wiele z nich korzysta z wzorców przedstawionych poniżej. Projekty, w których model aplikacji jest dostępny w środowisku .NET Core (takie jak biblioteki, aplikacje konsolowe i aplikacje klasyczne), zwykle wymagają niewielkich zmian. Projekty wymagające nowego modelu aplikacji, takie jak przeniesienie do ASP.NET Core z ASP.NET, wymagają nieco większej pracy, ale wiele wzorców ma analogowe, które mogą być używane podczas konwersji. Ten dokument powinien pomóc w zidentyfikowaniu głównych strategii, które zostały wykorzystane przez użytkowników w celu pomyślnego przekonwertowania baz kodu na docelowe .NET Standard lub .NET Core i przeanalizować je na dwóch poziomach: dla całego rozwiązania i projektu. Zobacz linki na dole, aby poznać wskazówki dotyczące konwersji specyficznych dla modelu aplikacji.

Zalecamy użycie następującego procesu podczas przenoszenia projektu do programu .NET Core. Każdy z tych kroków wprowadza potencjalne miejsca do zmian w zachowaniu, dlatego należy upewnić się, że Twoja biblioteka lub aplikacja jest odpowiednio testowana przed przejściem do kolejnych kroków. Pierwszym etapem jest przygotowanie projektu do przełączenia do .NET Standard lub .NET Core. Jeśli masz testy jednostkowe, najlepiej ją przekonwertować najpierw, aby można było kontynuować testowanie zmian w produkcie, nad którym pracujesz. Ponieważ przenoszenie do programu .NET Core to znacząca zmiana w bazie kodu, zdecydowanie zaleca się, aby przenieść projekty testowe, aby można było uruchamiać testy podczas przenoszenia kodu do trybu. MSTest, xUnit i NUnit działają na platformie .NET Core.

## <a name="getting-started"></a>Wprowadzenie

W trakcie procesu zostaną użyte następujące narzędzia:

- Visual Studio 2019
- Pobierz [Analizator przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md)
- _Opcjonalne_ Zainstaluj program [dotnet try-Convert](https://github.com/dotnet/try-convert)

## <a name="porting-a-solution"></a>Przenoszenie rozwiązania

W przypadku wielu projektów w rozwiązaniu port może wydawać się bardziej skomplikowany, ponieważ należy zająć się projektami w określonej kolejności. Proces konwersji powinien być podejściem do dołu, gdzie projekty bez zależności od innych projektów w rozwiązaniu są konwertowane jako pierwsze i są kontynuowane przez całe rozwiązanie.

Aby można było zidentyfikować projekty zamówień, można użyć następujących narzędzi:

- [Diagramy zależności w programie Visual Studio](/visualstudio/modeling/create-layer-diagrams-from-your-code) mogą utworzyć ukierunkowany wykres kodu w rozwiązaniu.
- Uruchom `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` , aby wygenerować dokument JSON zawierający listę odwołań projektu.

## <a name="per-project-steps"></a>Na kroki projektu

Zalecamy użycie następującego procesu podczas przenoszenia projektu do programu .NET Core:

1. Przekonwertuj wszystkie `packages.config` zależności na format [PackageReference](/nuget/consume-packages/package-references-in-project-files) za pomocą [narzędzia konwersji w programie Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Ten krok obejmuje przekonwertowanie zależności z starszego `packages.config` formatu. `packages.config`nie działa w programie .NET Core, dlatego ta konwersja jest wymagana, jeśli masz zależności pakietu. Wymaga również tylko zależności, które są bezpośrednio używane w projekcie, co sprawia, że dalsze kroki są łatwiejsze poprzez zmniejszenie liczby zależności, którymi należy zarządzać.

1. Przekonwertuj plik projektu na nową strukturę plików stylu zestawu SDK. Można tworzyć nowe projekty dla platformy .NET Core i kopiować je na pliki źródłowe lub próbować skonwertować istniejący plik projektu za pomocą narzędzia.

   W przypadku programu .NET Core jest stosowany uproszczony (i różny) [Format pliku projektu](../tools/csproj.md) niż .NET Framework. Aby kontynuować, musisz przekonwertować pliki projektu w ten format. Ten styl projektu umożliwia również kierowanie .NET Framework, co w tym momencie nadal będzie miało miejsce docelowe.

   Możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty w jednej operacji do formatu pliku projektu .NET Core za pomocą narzędzia [dotnet try-Convert](https://github.com/dotnet/try-convert) . `dotnet try-convert`nie ma gwarancji na wszystkie projekty i może spowodować drobne zmiany w zachowaniu, od którego zależy. Użyj jej jako _punktu wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migrowania projektu, ponieważ istnieje wiele różnic w obiektach docelowych używanych przez projekty stylów zestawu SDK w porównaniu do plików projektu starego stylu.

1. Przekieruj wszystkie projekty, które chcesz przenieść do elementu docelowego .NET Framework 4.7.2 lub wyższy.

   Ten krok zapewnia, że można użyć alternatywnych interfejsów API dla konkretnych .NET Framework docelowych, gdy platforma .NET Core nie obsługuje określonego interfejsu API.

1. Zaktualizuj wszystkie zależności do najnowszej wersji. Projekty mogą używać starszych wersji bibliotek, które mogą nie obsługiwać .NET Standard. Jednak późniejsze wersje mogą obsługiwać je za pomocą prostego przełącznika. Może to wymagać zmiany kodu, jeśli istnieją istotne zmiany w bibliotekach.

1. Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i sprawdź, czy są one przenośne do programu .NET Core.

   Narzędzie analizatora przenośności platformy .NET analizuje skompilowane zestawy i generuje raport. Ten raport przedstawia podsumowanie wysokiego poziomu dotyczące przenoszenia i podział wszystkich używanych interfejsów API, które nie są dostępne w systemie NET Core. Korzystając z narzędzia, przesyłaj tylko poszczególne projekty, które są konwertowane, aby skoncentrować się na zmianach interfejsu API, które mogą być potrzebne. Wiele interfejsów API ma równoważną dostępność w programie .NET Core, do której chcesz się przełączyć.

   Podczas odczytywania raportów wygenerowanych przez analizatora ważne informacje to rzeczywiste interfejsy API, które są używane, a nie musi to być procent obsługi platformy docelowej. Wiele interfejsów API ma równoważne opcje w .NET Standard/Core i dlatego zrozumienie scenariuszy, w których biblioteka lub aplikacja potrzebuje interfejsu API, aby pomóc w ustaleniu implikacji przenoszenia.

   Istnieją sytuacje, w których interfejsy API nie są równoważne i należy wykonać niektóre dyrektywy preprocesora kompilatora (czyli), `#if NET45`w specjalnym przypadku platform. W tym momencie projekt nadal będzie ukierunkowany na .NET Framework. W przypadku każdego z tych celów zaleca się użycie dobrze znanych warunków, które można zrozumieć jako scenariusz.  Na przykład obsługa AppDomain w programie .NET Core jest ograniczona, ale w przypadku scenariusza ładowania i zwalniania zestawów istnieje nowy interfejs API, który jest niedostępny w programie .NET Core. Typowy sposób obsługi tego kodu w kodzie będzie wyglądać następująco:

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. Zainstaluj [Analizator interfejsów API platformy .NET](../../standard/analyzers/api-analyzer.md) w swoich projektach, aby identyfikować <xref:System.PlatformNotSupportedException> interfejsy API, które zgłaszają na niektórych platformach i inne potencjalne problemy ze zgodnością.

   To narzędzie jest podobne do analizatora przenośności, ale zamiast analizowania, czy kod może kompilować na platformie .NET Core, analizuje, czy używasz interfejsu API w sposób, który będzie <xref:System.PlatformNotSupportedException> zgłaszać w czasie wykonywania. Chociaż nie jest to typowe w przypadku przechodzenia z .NET Framework 4.7.2 lub wyższym, warto sprawdzić. Aby uzyskać więcej informacji na temat interfejsów API, które generują wyjątki w programie .NET Core, zobacz [interfejsy API, które zawsze generują wyjątki w programie .NET Core](../compatibility/unsupported-apis.md).

1. W tym momencie można przełączyć się na kierowanie .NET Core (ogólnie dla aplikacji) lub .NET Standard (dla bibliotek).

   Wybór między platformą .NET Core i .NET Standard jest w dużym stopniu zależny od tego, gdzie projekt zostanie uruchomiony. Jeśli jest to biblioteka, która będzie używana przez inne aplikacje lub dystrybuowana za pośrednictwem programu NuGet, preferencją jest zwykle docelowa .NET Standard. Jednak mogą istnieć interfejsy API, które są dostępne tylko na platformie .NET Core w celu uzyskania wydajności lub innych przyczyn. w takim przypadku platforma .NET Core powinna być przeznaczona do użycia z potencjalnie .NET Standard kompilacją, a także z ograniczoną wydajnością lub funkcjonalnością. Według .NET Standard, projekt będzie gotowy do uruchomienia na nowych platformach (takich jak webassembly). Jeśli projekt ma zależności od określonych platform aplikacji (takich jak ASP.NET Core), wartość docelowa będzie ograniczona przez obsługiwane zależności.

   Jeśli nie istnieją dyrektywy preprocesora do warunkowego kompilowania kodu dla .NET Framework lub .NET Standard, będzie to tak proste, jak znalezienie następujących w pliku projektu:

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   i przełączenie go do żądanej struktury. W przypadku platformy .NET Core 3,1:

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   Jeśli jednak jest to biblioteka, dla której chcesz kontynuować obsługę kompilacji specyficznych dla .NET Framework [, możesz ją](../../standard/library-guidance/cross-platform-targeting.md) zastąpić, zastępując ją następującym:

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   Jeśli używasz interfejsów API specyficznych dla systemu Windows (takich jak dostęp do rejestru), zainstaluj [pakiet zgodności systemu Windows](./windows-compat-pack.md).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Analizowanie](third-party-deps.md)
> 
> [pakietu NuGet pakietu](../deploying/creating-nuget-packages.md)[programu zależności ASP.NET do migracji ASP.NET Core](/aspnet/core/migration/proper-to-2x)
