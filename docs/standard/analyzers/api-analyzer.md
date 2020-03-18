---
title: Analizator interfejsu API .NET
description: Dowiedz się, jak analizator interfejsu API platformy .NET może pomóc w wykrywaniu przestarzałych interfejsów API i problemów ze zgodnością platformy.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156137"
---
# <a name="net-api-analyzer"></a>Analizator interfejsu API .NET

Analizator interfejsu API .NET jest analizatorem Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla interfejsów API języka C# na różnych platformach i wykrywa wywołania przestarzałych interfejsów API. Może być przydatne dla wszystkich deweloperów języka C# na każdym etapie rozwoju.

Analizator interfejsu API jest dostarczany jako pakiet NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po odwołaniu się do niego w projekcie automatycznie monitoruje kod i wskazuje problematyczne użycie interfejsu API. Możesz również uzyskać sugestie dotyczące możliwych poprawek, klikając żarówkę. Menu rozwijane zawiera opcję pomijania ostrzeżeń.

> [!NOTE]
> Analizator interfejsu API .NET jest nadal wersją w wersji wstępnej.

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 i nowsze wersje lub Visual Studio dla komputerów Mac (wszystkie wersje).

## <a name="discover-deprecated-apis"></a>Odkryj przestarzałe interfejsy API

### <a name="what-are-deprecated-apis"></a>Co to są przestarzałe interfejsy API?

Rodzina .NET to zestaw dużych produktów, które są stale uaktualniane, aby lepiej zaspokajać potrzeby klientów. To naturalne, aby przestarzałe niektóre interfejsy API i zastąpić je nowymi. Interfejs API jest uważany za przestarzały, gdy istnieje lepsza alternatywa. Jednym ze sposobów informowania, że interfejs API jest przestarzały i nie <xref:System.ObsoleteAttribute> powinien być używany, jest oznaczenie go atrybutem. Wadą tego podejścia jest to, że istnieje tylko jeden identyfikator diagnostyczny dla wszystkich przestarzałych interfejsów API (dla Języka C#, [CS0612).](../../csharp/misc/cs0612.md) Oznacza to, że:

- Nie da się mieć dedykowanych dokumentów dla każdego przypadku.
- Nie da się pominąć określonej kategorii ostrzeżeń. Można pominąć wszystkie lub żadne z nich.
- Aby poinformować użytkowników o nowym uniewinnieniu, należy zaktualizować pakiet zestawu lub kierowania, do którego istnieje odwołanie.

Analizator interfejsu API używa kodów błędów specyficznych dla interfejsu API, które zaczynają się od DE (co oznacza błąd zaniechania), co umożliwia kontrolę nad wyświetlaniem poszczególnych ostrzeżeń. Przestarzałe interfejsy API identyfikowane przez analizator są zdefiniowane w repocie [dotnet/platform-compat.](https://github.com/dotnet/platform-compat)

### <a name="add-the-api-analyzer-to-your-project"></a>Dodawanie analizatora interfejsu API do projektu

1. Otwórz program Visual Studio.
2. Otwórz projekt, na którym chcesz uruchomić analizator.
3. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. (Ta opcja jest również dostępna w menu **Projekt).**
4. Na karcie NuGet Package Manager:
   1. Wybierz "nuget.org" jako źródło pakietu.
   2. Przejdź do karty **Przeglądanie.**
   3. Wybierz **pozycję Dołącz wersję wyjmą .**
   4. Wyszukaj pozycję **Microsoft.DotNet.Analyzers.Compatibility**.
   5. Wybierz ten pakiet na liście.
   6. Wybierz przycisk **Zainstaluj.**
   7. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.

### <a name="use-the-api-analyzer"></a>Korzystanie z analizatora interfejsu API

Gdy przestarzały interfejs API, <xref:System.Net.WebClient>taki jak , jest używany w kodzie, analizator interfejsu API wyróżnia go zieloną linią falistą. Po najechaniu kursorem na wywołanie interfejsu API wyświetlana jest żarówka z informacjami o zaniechaniu interfejsu API, jak w poniższym przykładzie:

!["Zrzut ekranu WebClient API z zieloną linią falistą i żarówką po lewej stronie"](media/api-analyzer/green-squiggle.jpg)

Okno **Lista błędów** zawiera ostrzeżenia o unikatowym identyfikatorze dla przestarzałego interfejsu API, jak pokazano w poniższym przykładzie (`DE004`):

!["Zrzut ekranu okna listy błędów z identyfikatorem i opisem ostrzeżenia"](media/api-analyzer/warnings-id-and-descriptions.jpg "Okno listy błędów zawierające ostrzeżenia.")

Klikając identyfikator, przejdź do strony internetowej ze szczegółowymi informacjami o tym, dlaczego interfejs API został przestarzały i sugestie dotyczące alternatywnych interfejsów API, które mogą być używane.

Wszelkie ostrzeżenia można pominąć, klikając prawym przyciskiem myszy wyróżniony element członkowski i wybierając **opcję Pomiń \<identyfikator diagnostyczny>**. Istnieją dwa sposoby pomijania ostrzeżeń:

- [lokalnie (w źródle)](#suppress-warnings-locally)
- [globalnie (w pliku tłumienia)](#suppress-warnings-globally) - zalecane

### <a name="suppress-warnings-locally"></a>Pomijanie ostrzeżeń lokalnie

Aby pominąć ostrzeżenia lokalnie, kliknij prawym przyciskiem myszy element członkowski, dla którego chcesz pominąć ostrzeżenia, a następnie wybierz polecenie **Szybkie akcje i refaktoryzacja** > **Pomiń identyfikator\< *diagnostyczny*identyfikator diagnostyczny>**  >  **w źródle**. [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) ostrzeżenie preprocesor dyrektywy jest dodawany do ![kodu źródłowego w zakresie zdefiniowanym: "Zrzut ekranu kodu w ramce z #pragma ostrzeżenie wyłączyć"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppress-warnings-globally"></a>Pomijanie ostrzeżeń na całym świecie

Aby pominąć ostrzeżenia globalnie, kliknij prawym przyciskiem myszy element członkowski, dla którego chcesz pominąć ostrzeżenia, a następnie wybierz polecenie **Szybkie akcje i refaktoryzacja** > **Pomiń identyfikator\< *diagnostyczny*identyfikator diagnostyczny>**  >  **w pliku pomijania**.

!["Zrzut ekranu WebClient API z zieloną linią falistą i żarówką po lewej stronie"](media/api-analyzer/suppress-in-sup-file.jpg)

GlobalSuppressions.cs *GlobalSuppressions.cs* plik zostanie dodany do projektu po pierwszym wygaszeniu. Do tego pliku dołączane są nowe globalne tłumienie.

!["Zrzut ekranu WebClient API z zieloną linią falistą i żarówką po lewej stronie"](media/api-analyzer/suppression-file.jpg)

Globalne tłumienie jest zalecanym sposobem zapewnienia spójności użycia interfejsu API w projektach.

## <a name="discover-cross-platform-issues"></a>Odkryj problemy między platformami

Podobnie jak przestarzałe interfejsy API, analizator identyfikuje wszystkie interfejsy API, które nie są między platformami. Na przykład <xref:System.Console.WindowWidth?displayProperty=nameWithType> działa w systemie Windows, ale nie w systemie Linux i macOS. Identyfikator diagnostyczny jest wyświetlany w oknie **Lista błędów.** Ostrzeżenie to można pominąć, klikając prawym przyciskiem myszy i wybierając polecenie **Szybkie akcje i refaktoryzacja**. W przeciwieństwie do przypadków zaniechania, w których masz dwie opcje (albo zachować przy użyciu przestarzałego członka i pominąć ostrzeżenia lub nie używać go w ogóle), tutaj, jeśli rozwijasz kod tylko dla niektórych platform, można pominąć wszystkie ostrzeżenia dla wszystkich innych platform, które nie plan, aby uruchomić kod na. Aby to zrobić, wystarczy edytować plik projektu `PlatformCompatIgnore` i dodać właściwość, która zawiera listę wszystkich platform, które mają być ignorowane. Akceptowane wartości `Linux`to: `macOS`, `Windows`, i .

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Jeśli kod jest przeznaczony dla wielu platform i chcesz skorzystać z interfejsu API nie jest obsługiwany `if` na niektórych z nich, można chronić tę część kodu za pomocą instrukcji:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Można również warunkowo skompilować na platformę docelową/system operacyjny, ale obecnie trzeba to zrobić [ręcznie](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Obsługiwana diagnostyka

Obecnie analizator obsługuje następujące przypadki:

- Użycie standardowego interfejsu API .NET, który jest wyrzucany <xref:System.PlatformNotSupportedException> (PC001).
- Użycie standardowego interfejsu API .NET, który nie jest dostępny w .NET Framework 4.6.1 (PC002).
- Użycie natywnego interfejsu API, który nie istnieje w uspo (PC003).
- Użycie interfejsów API Delegate.BeginInvoke i EndInvoke (PC004).
- Użycie interfejsu API oznaczonego jako przestarzałe (DEXXXX).

## <a name="ci-machine"></a>Maszyna CI

Wszystkie te diagnostyki są dostępne nie tylko w IDE, ale także w wierszu polecenia w ramach tworzenia projektu, który obejmuje serwer pw.

## <a name="configuration"></a>Konfigurowanie

Użytkownik decyduje, jak diagnostyka powinna być traktowana: jako ostrzeżenia, błędy, sugestie lub do wyłączenia. Na przykład jako architekt można zdecydować, że problemy ze zgodnością powinny być traktowane jako błędy, wywołania niektórych przestarzałych interfejsów API generują ostrzeżenia, podczas gdy inne generują tylko sugestie. Można skonfigurować to oddzielnie według identyfikatora diagnostycznego i projektu. Aby to zrobić w **Eksploratorze rozwiązań,** przejdź do węzła **Zależności** w projekcie. Rozwiń węzły Zależności > **Analizatory** > **Microsoft.DotNet.Analyzers.Compatibility**. **Dependencies** Kliknij prawym przyciskiem myszy identyfikator diagnostyczny, wybierz pozycję **Ustaw ważność zestawu reguł** i wybierz żądaną opcję.

!["Zrzut ekranu przedstawiający Eksploratora rozwiązań z diagnostyką i wyskakujące okno dialogowe z ważnością zestawu reguł"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Zobacz też

- Wprowadzenie do wpisu w blogu [Analizatora interfejsu API.](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/)
- Film [demonstracyjny API Analyzer](https://youtu.be/eeBEahYXGd0) w YouTube.
