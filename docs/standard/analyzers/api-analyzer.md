---
title: Analizator interfejsu API platformy .NET
description: Dowiedz się, jak analizatora interfejsu API platformy .NET mogą pomóc wykryć przestarzałe interfejsy API i problemy ze zgodnością platformy.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 84dd0717725f3538f9c9b2e3b5573f1385e549ac
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680272"
---
# <a name="net-api-analyzer"></a>Analizator interfejsu API platformy .NET

Analizator interfejsu API platformy .NET jest analizator Roslyn, który wykryje potencjalne zagrożenia zgodność dla C# interfejsów API na różnych platformach i wykrywa wywołania interfejsów API przestarzałych. Może być przydatne w przypadku wszystkich C# deweloperom na każdym etapie cyklu rozwoju.

Analizator interfejsu API jest dostarczany jako pakiet NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Po odwołanie w projekcie, automatycznie monitoruje kod i wskazuje problematyczne użycie interfejsu API. Możesz także uzyskać sugestie na możliwe poprawki, klikając ikony żarówki. Menu rozwijane zawiera opcję, aby pominąć ostrzeżenia.

> [!NOTE]
> Analizator interfejsu API platformy .NET jest nadal w wersji wstępnej.

## <a name="prerequisites"></a>Wymagania wstępne

* Visual Studio 2017 lub Visual Studio for Mac (wszystkie wersje).

## <a name="discovering-deprecated-apis"></a>Odnajdywanie przestarzałe interfejsy API

### <a name="what-are-deprecated-apis"></a>Co to są przestarzałe interfejsy API?

Rodzina .NET to zbiór dużych produktów, które są stale uaktualnienia, aby lepiej spełniać potrzeby klientów. To naturalne wycofana niektóre interfejsy API i zastąpić je przy użyciu nowych. Interfejs API jest uznawane za przestarzałe, gdy istnieje lepszą alternatywą. Jednym ze sposobów informuje, że interfejs API jest przestarzały i nie powinna być używana jest do oznaczania za pomocą <xref:System.ObsoleteAttribute> atrybutu. Wadą tego podejścia jest to, że istnieje tylko jeden identyfikator diagnostyczny dla wszystkich interfejsów API przestarzałych (dla C#, [CS0612](../../csharp/misc/cs0612.md)). Oznacza to, że:
- Nie jest możliwe są wyposażone w dedykowane dokumentów w każdym przypadku.
- Nie jest możliwe pominąć określoną kategorią ostrzeżenia. Można pominąć wszystkich lub żadnej z nich.
- Aby informować użytkowników o nowych wycofywania, przywoływanego zestawu lub przeznaczonych dla pakietu ma zostać zaktualizowany.

Analizator interfejsu API używa kody błędów specyficzne dla interfejsu API, które zaczynają się DE (oznaczającą błąd wycofywania), który zapewnia kontrolę nad wyświetlaniem poszczególne ostrzeżenia. Przestarzałe interfejsy API identyfikowane za pomocą analizatora są zdefiniowane w [dotnet/platform — compat](https://github.com/dotnet/platform-compat) repozytorium.

### <a name="using-the-api-analyzer"></a>Za pomocą analizatora interfejsu API

Gdy przestarzałe API, takich jak <xref:System.Net.WebClient>, jest używana w kodzie, interfejs API analizatora wyróżnia ją za pomocą zielona linia falista. Po najechaniu kursorem na wywołania interfejsu API, żarówka jest wyświetlana przy użyciu informacji na temat wycofania interfejsów API, jak w poniższym przykładzie:

!["Zrzut ekranu z WebClient interfejsu API za pomocą zielona linia falista i żarówki po lewej stronie"](media/api-analyzer/green-squiggle.jpg)

**Lista błędów** okno zawiera ostrzeżenia o unikatowym identyfikatorze za przestarzałe API, jak pokazano w poniższym przykładzie (`DE004`): 

!["Zrzut ekranu przedstawiający ostrzeżenie jego identyfikator i opis okno Lista błędów"](media/api-analyzer/warnings-id-and-descriptions.jpg "okno Lista błędów, które zawiera ostrzeżenia.")

Klikając identyfikator, możesz przejść do strony sieci Web za pomocą szczegółowe informacje na temat przyczyny interfejsu API została zakończona i sugestie dotyczące alternatywne interfejsy API, które mogą być używane.

Wszelkie ostrzeżenia, można pominąć, klikając prawym przyciskiem myszy na elemencie członkowskim wyróżnione i wybierając **Pomiń \<Identyfikator diagnostyczny >**. Istnieją dwa sposoby, aby pominąć ostrzeżenia: 

* [lokalnie (w źródle)](#suppressing-warnings-locally)
* [globalnie (w pliku pominięć)](#suppressing-warnings-globally) — jest to zalecane

### <a name="suppressing-warnings-locally"></a>Pomijanie ostrzeżeń lokalnie

Aby pominąć ostrzeżenia lokalnie, kliknij prawym przyciskiem myszy elementu członkowskiego, aby pomijanie ostrzeżeń dla, a następnie wybierz pozycję **szybkie akcje i Refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny* \<Identyfikator diagnostyczny >** > **w źródle**. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) ostrzeżenie dyrektywy preprocesora jest dodawany do kodu źródłowego w zakresie zdefiniowane: !["Wyłącz zrzut ekranu przedstawiający kodu w ramce ostrzeżenia #pragma"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Pomijanie ostrzeżeń globalnie

Aby pominąć ostrzeżenia globalnie, kliknij prawym przyciskiem myszy elementu członkowskiego, aby pomijanie ostrzeżeń dla, a następnie wybierz pozycję **szybkie akcje i Refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny* \<Identyfikator diagnostyczny >** > **w pliku pominięć**.

!["Zrzut ekranu z WebClient interfejsu API za pomocą zielona linia falista i żarówki po lewej stronie"](media/api-analyzer/suppress-in-sup-file.jpg)

A *GlobalSuppressions.cs* plik zostanie dodany do projektu po pierwszym pomijania. Nowe pominięcia globalne są dołączane do tego pliku.

!["Zrzut ekranu z WebClient interfejsu API za pomocą zielona linia falista i żarówki po lewej stronie"](media/api-analyzer/suppression-file.jpg)

Globalne pomijanie jest zalecanym sposobem zapewnienia spójności użycie interfejsu API w projektach.

## <a name="discovering-cross-platform-issues"></a>Wykrywanie problemów dla wielu platform

Podobnie jak przestarzałe interfejsy API, analizator identyfikuje wszystkie interfejsy API, które nie są dla wielu platform. Na przykład <xref:System.Console.WindowWidth?displayProperty=nameWithType> działa na Windows, ale nie w systemie Linux i macOS. Identyfikator diagnostyki jest wyświetlany w **lista błędów** okna. Można pominąć tego ostrzeżenia, klikając prawym przyciskiem myszy i wybierając polecenie **szybkie akcje i Refaktoryzacje**. W przeciwieństwie do obsługi przypadki, w którym masz dwie opcje (Zachowaj przy użyciu przestarzałe elementu członkowskiego i pominąć ostrzeżenia lub należy go używać na wszystkich), w tym miejscu, jeśli tworzysz kod tylko dla określonych platform można pominąć wszystkie ostrzeżenia dla innych platform nie należy zaplanować i uruchomić kod w. Aby to zrobić, wystarczy do edycji pliku projektu i dodawanie `PlatformCompatIgnore` właściwość, która zawiera listę wszystkich platform, które mają być ignorowane. Akceptowane wartości to: `Linux`, `macOS`, i `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Jeśli Twój kod jest przeznaczony dla wielu platform i chcesz móc korzystać z interfejsu API, które nie są obsługiwane na niektórych z nich, możesz chronić część kodu za pomocą `if` instrukcji:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Możesz również warunkowo skompilować dla docelowego systemu operacyjnego/framework, ale obecnie trzeba to zrobić [ręcznie](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Obsługiwane diagnostyki

Obecnie analizatora obsługuje następujących przypadkach:

* Użycie standardowych API platformy .NET i zgłasza <xref:System.PlatformNotSupportedException> (PC001).
* Użycie standardowych interfejs API programu .NET, która nie jest dostępna dla programu .NET Framework 4.6.1 (PC002).
* Użycie natywnych interfejsów API, który nie istnieje na platformy uniwersalnej systemu Windows (PC003).
* Użycie interfejsu API, który jest oznaczony jako przestarzały (DEXXXX).

## <a name="ci-machine"></a>Ciągła Integracja maszyny

Te funkcje diagnostyki są dostępne nie tylko w środowisku IDE, ale również w wierszu polecenia w ramach tworzenia projektu, która obejmuje serwer ciągłej integracji.

## <a name="configuration"></a>Konfiguracja

Użytkownik decyduje, jak powinny być traktowane diagnostyki: jako ostrzeżenia, błędy, sugestie lub wyłączenia. Na przykład jako Architekt może określić czy problemy ze zgodnością powinny być traktowane jako błędy, wywołania do niektórych przestarzałych API generowanie ostrzeżenia i inne jedynie generować sugestie. Możesz skonfigurować to osobno według Identyfikatora diagnostycznego, a także przez projekt. Dlatego w celu **Eksploratora rozwiązań**, przejdź do **zależności** węzeł w węźle projektu. Rozwiń węzły **zależności** > **analizatory** > **Microsoft.DotNet.Analyzers.Compatibility**. Kliknij prawym przyciskiem myszy Identyfikator diagnostyczny wybierz **Ustaw ważność zestawu reguł** i wybierz odpowiednią opcję.

!["Zrzut ekranu Eksploratora rozwiązań przedstawiający dane diagnostyczne i wyskakującego okna dialogowego z ważność zestawu reguł"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do interfejsu API analizatora](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) wpis w blogu.
- [Interfejs API analizatora](https://youtu.be/eeBEahYXGd0) pokaz wideo w serwisie YouTube.
