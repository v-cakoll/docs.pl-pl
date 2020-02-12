---
title: Analizator interfejsów API platformy .NET
description: Dowiedz się, jak Analizator interfejsu API platformy .NET może pomóc w wykrywaniu przestarzałych interfejsów API i problemów ze zgodnością platformy.
author: oliag
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: efbfa89f431bd02cdf86b8eff8704aec63a29b6c
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124250"
---
# <a name="net-api-analyzer"></a>Analizator interfejsów API platformy .NET

Analizator interfejsu API platformy .NET to Analizator Roslyn, który wykrywa potencjalne zagrożenia zgodności dla C# interfejsów API na różnych platformach i wykrywa wywołania przestarzałych interfejsów API. Mogą być przydatne dla wszystkich C# deweloperów na dowolnym etapie opracowywania.

Analizator interfejsu API jest dostarczany jako pakiet NuGet [Microsoft. dotnet. analizatory. zgodność](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po odwoływaniu się do niego w projekcie program automatycznie monitoruje kod i wskazuje na problematyczne użycie interfejsu API. Możesz również uzyskać sugestie dotyczące możliwych poprawek, klikając żarówkę. Menu rozwijane zawiera opcję pomijania ostrzeżeń.

> [!NOTE]
> Analizator interfejsu API platformy .NET jest nadal w wersji wstępnej.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2017 lub jego nowsze wersje lub Visual Studio dla komputerów Mac (wszystkie wersje).

## <a name="discovering-deprecated-apis"></a>Odnajdywanie przestarzałych interfejsów API

### <a name="what-are-deprecated-apis"></a>Co to są przestarzałe interfejsy API?

Rodzina .NET to zestaw dużych produktów, które są stale uaktualniane, aby lepiej spełniały potrzeby klientów. Jest to naturalne, aby zastąpić niektóre interfejsy API i zamienić je na nowe. Interfejs API jest uznawany za przestarzały, gdy istnieje lepsza alternatywa. Jednym ze sposobów, aby poinformować, że interfejs API jest przestarzały i nie powinien być używany, to oznaczanie go atrybutem <xref:System.ObsoleteAttribute>. Wadą tego podejścia jest to, że istnieje tylko jeden identyfikator diagnostyczny dla wszystkich przestarzałych interfejsów API C#(dla, [CS0612](../../csharp/misc/cs0612.md)). Oznacza to, że:

- Nie jest możliwe posiadanie dedykowanych dokumentów dla każdego przypadku.
- Nie można pominąć pewnej kategorii ostrzeżeń. Możesz pominąć wszystkie lub żadne z nich.
- Aby poinformować użytkowników o nowym zaniechaniu, należy zaktualizować zestaw lub pakiet docelowy, do którego istnieje odwołanie.

Analizator interfejsu API korzysta z kodów błędów specyficznych dla interfejsu API, które zaczynają się od DE (co oznacza błąd zaniechania), co umożliwia kontrolę nad wyświetlaniem indywidualnych ostrzeżeń. Przestarzałe interfejsy API identyfikowane przez analizator są zdefiniowane w repozytorium [dotnet/platform-COMPAT](https://github.com/dotnet/platform-compat) .

### <a name="using-the-api-analyzer"></a>Korzystanie z analizatora interfejsu API

Gdy przestarzały interfejs API, taki jak <xref:System.Net.WebClient>, jest używany w kodzie, Analizator interfejsu API podświetla go przy użyciu zielonej linii falistej. Po umieszczeniu wskaźnika myszy na wywołaniu interfejsu API żarówka jest wyświetlana z informacjami o zaniechaniu interfejsu API, jak w poniższym przykładzie:

!["Zrzut ekranu interfejsu API WebClient z zieloną falistej linią i żarówką po lewej stronie"](media/api-analyzer/green-squiggle.jpg)

Okno **Lista błędów** zawiera ostrzeżenia o UNIKATOWYm identyfikatorze na przestarzały interfejs API, jak pokazano w poniższym przykładzie (`DE004`): 

!["Zrzut ekranu okna Lista błędów przedstawiający identyfikator i opis ostrzeżenia"](media/api-analyzer/warnings-id-and-descriptions.jpg "Okno Lista błędów, które zawiera ostrzeżenia.")

Klikając identyfikator, przejdź do strony sieci Web ze szczegółowymi informacjami o tym, dlaczego interfejs API był przestarzały i sugestie dotyczące alternatywnych interfejsów API, których można użyć.

Wszystkie ostrzeżenia można pominąć przez kliknięcie prawym przyciskiem myszy wyróżnionego elementu członkowskiego i wybranie opcji **pomiń \<identyfikator diagnostyczny >** . Istnieją dwa sposoby pomijania ostrzeżeń: 

- [lokalnie (w źródle)](#suppressing-warnings-locally)
- [globalnie (w pliku pominięć)](#suppressing-warnings-globally) — zalecane

### <a name="suppressing-warnings-locally"></a>Pomijanie ostrzeżeń lokalnie

Aby pominąć ostrzeżenia lokalnie, kliknij prawym przyciskiem myszy element członkowski, dla którego chcesz pominąć ostrzeżenia, a następnie wybierz polecenie **szybkie akcje i refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny*\<identyfikator diagnostyczny >**  > **w źródle**. Dyrektywa preprocesora ostrzeżeń [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) jest dodawana do kodu źródłowego w określonym zakresie: !["zrzut ekranu kodu z ramką #pragma wyłączyć"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Pomijanie ostrzeżeń globalnie

Aby pominąć ostrzeżenia globalnie, kliknij prawym przyciskiem myszy element członkowski, dla którego chcesz pominąć ostrzeżenia, a następnie wybierz polecenie **szybkie akcje i refaktoryzacje** > **pominąć *Identyfikator diagnostyczny*\<identyfikator diagnostyczny >**  > **w pliku**pominięć.

!["Zrzut ekranu interfejsu API WebClient z zieloną falistej linią i żarówką po lewej stronie"](media/api-analyzer/suppress-in-sup-file.jpg)

Plik *GlobalSuppressions.cs* jest dodawany do projektu po pierwszym pominięciu. Do tego pliku są dołączane nowe, globalne pomijania.

!["Zrzut ekranu interfejsu API WebClient z zieloną falistej linią i żarówką po lewej stronie"](media/api-analyzer/suppression-file.jpg)

Globalne pomijanie jest zalecanym sposobem zapewnienia spójności użycia interfejsu API między projektami.

## <a name="discovering-cross-platform-issues"></a>Wykrywanie problemów na wielu platformach

Podobnie jak w przypadku przestarzałych interfejsów API, Analizator identyfikuje wszystkie interfejsy API, które nie są dla wielu platform. Na przykład <xref:System.Console.WindowWidth?displayProperty=nameWithType> działa w systemie Windows, ale nie w systemie Linux i macOS. Identyfikator diagnostyki jest wyświetlany w oknie **Lista błędów** . Możesz pominąć to ostrzeżenie, klikając prawym przyciskiem myszy i wybierając polecenie **szybkie akcje i refaktoryzacje**. W przeciwieństwie do przypadków wycofania, w których są dostępne dwie opcje (można nadal korzystać z przestarzałego elementu członkowskiego i pomijać ostrzeżenia lub nie używać ich wcale), tutaj jeśli tworzysz kod tylko dla niektórych platform, możesz pominąć wszystkie ostrzeżenia dla wszystkich innych platform, które nie są Zaplanuj, aby uruchomić swój kod. Aby to zrobić, wystarczy edytować plik projektu i dodać właściwość `PlatformCompatIgnore`, która wyświetla listę wszystkich platform do zignorowania. Akceptowane są następujące wartości: `Linux`, `macOS`i `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Jeśli Twój kod jest przeznaczony dla wielu platform i chcesz skorzystać z interfejsu API nieobsługiwanego przez niektóre z nich, możesz zabezpieczyć tę część kodu za pomocą instrukcji `if`:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Można również wykonać warunkowe kompilowanie na platformę docelową/system operacyjny, ale obecnie trzeba to zrobić [ręcznie](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Obsługiwana Diagnostyka

Obecnie Analizator obsługuje następujące przypadki:

- Użycie interfejsu API .NET Standard, który zgłasza <xref:System.PlatformNotSupportedException> (PC001).
- Użycie interfejsu API .NET Standard, który nie jest dostępny w .NET Framework 4.6.1 (PC002).
- Użycie natywnego interfejsu API, który nie istnieje w platformy UWP (PC003).
- Użycie interfejsów API Delegate. BeginInvoke i EndInvoke (PC004).
- Użycie interfejsu API, który jest oznaczony jako przestarzały (rozxxxx).

## <a name="ci-machine"></a>Komputer CI

Wszystkie te diagnostyki są dostępne nie tylko w środowisku IDE, ale również w wierszu polecenia w ramach konstruowania projektu, który obejmuje serwer CI.

## <a name="configuration"></a>Konfiguracja

Użytkownik decyduje o sposobie traktowania diagnostyki: w postaci ostrzeżeń, błędów, sugestii lub wyłączania. Na przykład jako architekt można zdecydować, że problemy ze zgodnością powinny być traktowane jako błędy, wywołania niektórych przestarzałych interfejsów API generują ostrzeżenia, podczas gdy inne tylko generują sugestie. Można ją skonfigurować osobno według identyfikatora diagnostyki i projektu. W tym celu w **Eksplorator rozwiązań**przejdź do węzła **zależności** w ramach projektu. Rozwiń węzły **zależności** > **analizatory** > **Microsoft. dotnet. analizatory. zgodność**. Kliknij prawym przyciskiem myszy identyfikator diagnostyczny, wybierz pozycję **Ustaw ważność zestawu reguł** i wybierz żądaną opcję.

!["Zrzut ekranu przedstawiający Eksplorator rozwiązań pokazujący diagnostykę i wyskakujące okno dialogowe z ważnością zestawu reguł"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Zobacz też

- Wprowadzenie do wpisu w blogu [analizatora interfejsu API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .
- Wideo z pokazem [interfejsu API Analyzer](https://youtu.be/eeBEahYXGd0) w serwisie YouTube.
