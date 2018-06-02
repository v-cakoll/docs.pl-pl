---
title: Analizator interfejs API .NET
description: Dowiedz się, jak analizator interfejsu API platformy .NET mogą pomóc wykrywanie przestarzałe interfejsy API i problemy ze zgodnością platformy.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 4394bc77b499db1960d61bad5e828f77f1144c65
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696887"
---
# <a name="net-api-analyzer"></a>Analizator interfejs API .NET

Analizator interfejs API .NET jest analizator Roslyn, który wykryje zgodność potencjalne zagrożenie dla interfejsów API języka C# na różnych platformach i wykrywa wywołania interfejsów API przestarzałe. Może być przydatne dla wszystkich deweloperów języka C# na każdym etapie programowania.

Analizator interfejsu API jest dostarczany jako pakietu NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po odwołanie w projekcie, automatycznie monitoruje kod i wskazuje problematyczne użycia interfejsu API. Sugestie na możliwe poprawek można również uzyskać, klikając żarówkę. Menu rozwijane zawiera opcję pomijania ostrzeżeń.

> [!NOTE]
> Analizator interfejs API .NET jest nadal wersji wstępnej.

## <a name="prerequisites"></a>Wymagania wstępne

* Visual Studio 2017 lub Visual Studio dla komputerów Mac (wszystkie wersje).

## <a name="discovering-deprecated-apis"></a>Odnajdywanie przestarzałe interfejsy API

### <a name="what-are-deprecated-apis"></a>Co to są przestarzałe interfejsy API?

Rodzina .NET jest zestaw produktów dużych stale uaktualnionych do potrzeb potrzeb klientów. Jest fizyczne, aby zastąpić niektórych interfejsów API i zastąp je nowymi plikami. Interfejs API zostanie uznane za przestarzałe, gdy istnieje lepszym. Jednym ze sposobów poinformuj o tym, że interfejs API jest przestarzały i nie powinny być używane jest oznaczenie go przy użyciu <xref:System.ObsoleteAttribute> atrybutu. Wadą tego podejścia jest, że istnieje tylko jeden identyfikator diagnostycznych dla wszystkich interfejsów API przestarzałe (język C#, [CS0612](../../csharp/misc/cs0612.md)). Oznacza to, że:
- Nie jest możliwe są wyposażone w dedykowane dokumentów dla każdego przypadku.
- Nie można pominąć określonej kategorii ostrzeżenia. Można pominąć wszystkie lub żadne z nich.
- Aby informować użytkowników o nowych amortyzacja, przywoływanego zestawu lub przeznaczonych dla pakietu ma zostać zaktualizowany.

Analizator interfejsu API wykorzystuje interfejs API specyficzne kody błędów, które rozpoczynają się z DE (oznaczającą błąd amortyzacja), która zapewnia kontrolę nad wyświetlania ostrzeżeń indywidualnych. Przestarzałe interfejsy API zidentyfikowane przez analizatora są zdefiniowane w [dotnet/platform — compat](https://github.com/dotnet/platform-compat) repozytorium.

### <a name="using-the-api-analyzer"></a>Za pomocą analizatora interfejsu API

Gdy przestarzałe interfejsu API, takich jak <xref:System.Net.WebClient>, jest używana w kodzie interfejsu API analizatora wyróżnia ją z linii o dowolnym kształcie zielony. Po umieszczeniu na wywołania interfejsu API, żarówka wyświetlane są informacje o amortyzacja interfejsu API, jak w poniższym przykładzie:

!["Zrzut ekranu WebClient interfejsu API z zielonym dowolnym kształcie wiersza i żarówki po lewej stronie"](media/api-analyzer/green-squiggle.jpg)

**Listy błędów** okno zawiera ostrzeżenia o unikatowym identyfikatorze za przestarzały interfejsu API, jak pokazano w poniższym przykładzie (`DE004`): 

!["Zrzut ekranu przedstawiający identyfikator i opis tego ostrzeżenia w oknie Lista błędów"](media/api-analyzer/warnings.jpg)

Klikając identyfikator, przejdź do strony sieci Web, szczegółowe informacje na temat przyczyny została uznana za przestarzałą interfejsu API i sugestie dotyczące alternatywnych interfejsów API, które mogą być używane.

Można pominąć wszelkie ostrzeżenia zaznaczony element członkowski prawym przyciskiem myszy i wybierając **Pomiń \<Identyfikator diagnostyczny >**. Istnieją dwa sposoby pomijanie ostrzeżeń: 

* [lokalnie (w źródle)](#suppressing-warnings-locally)
* [globalny (w pliku pominięć)](#suppressing-warnings-globally) — jest to zalecane

### <a name="suppressing-warnings-locally"></a>Pomijanie ostrzeżeń lokalnie

Aby pominąć ostrzeżenia lokalnie, kliknij prawym przyciskiem myszy element członkowski ma być pomijanie ostrzeżeń dla, a następnie wybierz **szybkie akcje i Refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny* \<Identyfikator diagnostyczny >** > **w źródle**. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) ostrzeżenie dyrektywy preprocesora jest dodawana do kodu źródłowego w zakresie zdefiniowanym: !["Zrzut ekranu przedstawiający kodu w ramce z Wyłącz ostrzeżenia #pragma"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Pomijanie ostrzeżeń globalny

Aby pominąć ostrzeżenia globalnie, kliknij prawym przyciskiem myszy element członkowski ma być pomijanie ostrzeżeń dla, a następnie wybierz **szybkie akcje i Refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny* \<Identyfikator diagnostyczny >** > **w pliku pominięć**.

!["Zrzut ekranu WebClient interfejsu API z zielonym dowolnym kształcie wiersza i żarówki po lewej stronie"](media/api-analyzer/suppress-in-sup-file.jpg)

A *GlobalSuppressions.cs* plik zostanie dodany do projektu po pierwszym pomijania. Nowe pominięcia globalne są dołączane do tego pliku.

!["Zrzut ekranu WebClient interfejsu API z zielonym dowolnym kształcie wiersza i żarówki po lewej stronie"](media/api-analyzer/suppression-file.jpg)

Pomijanie globalnego jest zalecanym sposobem zapewnienia spójności interfejsu API użycia wielu projektów.

## <a name="discovering-cross-platform-issues"></a>Wykrywanie problemów i platform

Podobnie jak przestarzałe interfejsy API, wszystkich interfejsów API, które nie są międzyplatformowa identyfikuje analizatora. Na przykład <xref:System.Console.WindowWidth?displayProperty=nameWithType> działa w systemie Windows, ale nie w systemie Linux i macOS. Identyfikator diagnostyczny jest wyświetlany w obszarze **listy błędów** okna. Można pominąć tego ostrzeżenia, klikając prawym przyciskiem myszy i wybierając **szybkie akcje i Refaktoryzacje**. W odróżnieniu od amortyzacja przypadków, gdy są dostępne dwie opcje (nadal używaj przestarzały element członkowski i pomijanie ostrzeżeń lub nie używać na wszystkich), w tym miejscu Jeśli projektujesz kodu tylko dla niektórych platform, można pominąć wszystkie ostrzeżenia dla innych platform, nie musisz Zaplanuj uruchamianie kodzie. W tym celu wystarczy edytowanie pliku projektu i dodawanie `PlatformCompatIgnore` właściwość, która zawiera listę wszystkich platform, które mają być ignorowane. Dopuszczalne wartości to: `Linux`, `macOS`, i `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Jeśli kod jest przeznaczony dla wielu platform i chcesz korzystać z interfejsu API nie jest obsługiwana w przypadku niektórych z nich, można zabezpieczyć części kodu przy użyciu `if` instrukcji:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Można również warunkowo kompilowania dla docelowego systemu operacyjnego/framework, ale należy obecnie w tym [ręcznie](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Obsługiwane diagnostyki

Analizatora obsługuje obecnie następujących przypadkach:

* Użycie API standardowe .NET, która zgłasza <xref:System.PlatformNotSupportedException> (PC001).
* Użycie standardowych interfejs API programu .NET, który nie jest dostępna w programie .NET Framework 4.6.1 (PC002).
* Użycie natywnego interfejsu API, który nie istnieje w platformy uniwersalnej systemu Windows (PC003).
* Użycie interfejsu API, który jest oznaczony jako przestarzały (DEXXXX).

## <a name="ci-machine"></a>Elementu konfiguracji komputera

Te funkcje diagnostyki jest dostępna nie tylko w środowisku IDE, ale również w wierszu polecenia w ramach tworzenia projektu, która obejmuje serwer elementu konfiguracji.

## <a name="configuration"></a>Konfiguracja

Użytkownik decyduje o tym, jak powinny być traktowane diagnostyki: jako ostrzeżenia, błędów, sugestie lub być wyłączone. Na przykład jako architekta, można określić czy problemy ze zgodnością powinny być traktowane jako błędy, wywołania niektórych przestarzałych interfejsów API generowania ostrzeżeń, podczas gdy inne generować tylko sugestie. Można skonfigurować to oddzielnie za pomocą Identyfikatora diagnostycznych i przez projekt. Dlatego w celu **Eksploratora rozwiązań**, przejdź do **zależności** węźle projektu. Rozwiń węzły **zależności** > **analizatorów** > **Microsoft.DotNet.Analyzers.Compatibility**. Kliknij prawym przyciskiem myszy Identyfikator diagnostyczny wybierz **ustawić ważność ustawić reguły** i wybierz odpowiednią opcję.

!["Zrzut ekranu przedstawiający Eksploratora rozwiązań przedstawiający diagnostyki i wyskakujące okno dialogowe z reguły ustawić ważność"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Zobacz także

* [Wprowadzenie do interfejsu API analizator](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) wpis w blogu.
* [Analizator interfejsu API](https://youtu.be/eeBEahYXGd0) pokaz wideo w serwisie YouTube.
