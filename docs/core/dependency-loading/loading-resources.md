---
title: Algorytm ładowania zestawu satelitarnego — .NET Core
description: Opis szczegółów algorytmu ładowania zestawu satelickiego w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105315"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algorytm ładowania zestawu satelitarnego

Zestawy satelickie są używane do przechowywania zlokalizowanych zasobów dostosowane do języka i kultury.

Zestawy satelickie używają innego algorytmu ładowania niż ogólne zestawy zarządzane.

## <a name="when-are-satellite-assemblies-loaded"></a>Kiedy są ładowane zestawy satelickie?

Zestawy satelickie są ładowane podczas ładowania zlokalizowanego zasobu.

Podstawowy interfejs API do załadowania zlokalizowanych zasobów <xref:System.Resources.ResourceManager?displayProperty=fullName> jest klasą. Ostatecznie Klasa wywoła <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodę dla każdej z nich <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. <xref:System.Resources.ResourceManager>

Interfejsy API wyższego poziomu mogą być abstrakcyjne dla interfejsu API niskiego poziomu.

## <a name="algorithm"></a>Algorytm

Proces rezerwowy zasobów platformy .NET Core obejmuje następujące kroki:

1. `active` Określ<xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie. We wszystkich przypadkach `active` wystąpienie jest <xref:System.Runtime.Loader.AssemblyLoadContext>zestawem wykonawczym.

2. `active` Wystąpienie próbuje załadować zestaw satelicki dla wymaganej kultury w kolejności priorytetu przez:
    - Sprawdzanie jego pamięci podręcznej.
    - Sprawdzanie katalogu aktualnie wykonywanego zestawu dla podkatalogu zgodnego z żądanym <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (na przykład `es-MX`).

        > [!NOTE]
        > Ta funkcja nie została zaimplementowana w środowisku .NET Core przed 3,0.
        >
        > [!NOTE]
        > W przypadku systemu Linux i macOS w podkatalogu jest rozróżniana wielkość liter i musi to być:
        > - Dokładnie dopasowanie wielkości liter.
        > - Małymi literami.

    - `active` Jeśli<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> jest wystąpieniem, uruchamiając domyślną logikę [sondowania zestawu dla satelity (zasobu)](default-probing.md#satellite-resource-assembly-probing) .

    - Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkcji.

    - Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> poziomu zdarzenia.

    - Podnoszenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> poziomu zdarzenia.

3. Jeśli jest ładowany zestaw satelicki:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Zdarzenie jest zgłaszane.
   - Zestaw jest przeszukiwany dla żądanego zasobu. Jeśli środowisko uruchomieniowe odnajdzie zasób w zestawie, użyje go. Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.

    > [!NOTE]
    > Aby znaleźć zasób w ramach zestawu satelickiego, środowisko uruchomieniowe wyszukuje plik zasobów żądany przez <xref:System.Resources.ResourceManager> dla bieżącego. <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> W pliku zasobów szuka żądanej nazwy zasobu. Jeśli nie zostanie znaleziony, zasób jest traktowany jako nieodnaleziony.

4. Środowisko uruchomieniowe następnym szuka zestawów kultur nadrzędnych za pomocą wielu możliwych poziomów, za każdym razem, gdy powtarzają się kroki 2 & 3.

    Każda kultura ma tylko jeden element nadrzędny, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwość.

    Wyszukiwanie kultur nadrzędnych jest zatrzymywane, gdy <xref:System.Globalization.CultureInfo.Parent%2A> właściwość kultury to. <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>

    Dla programu <xref:System.Globalization.CultureInfo.InvariantCulture>nie powrócimy do kroków 2 & 3, ale należy kontynuować krok 5.

5. Jeśli zasób nadal nie zostanie znaleziony, zostanie użyta domyślna kultura (rezerwowa).

   Zazwyczaj zasoby dla kultury domyślnej są zawarte w głównym zestawie aplikacji. Można jednak określić <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> właściwość. Ta wartość wskazuje, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelity, a nie głównym zestawem.

    > [!NOTE]
    > Domyślna kultura to ostateczna rezerwa. Dlatego zaleca się, aby zawsze obejmować pełny zestaw zasobów w domyślnym pliku zasobów. Pomaga to zapobiegać zgłaszaniu wyjątków. Mając pełny zestaw, należy podać rezerwę dla wszystkich zasobów i upewnić się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzny dla kultury.

6. Ostateczny
   - Jeśli środowisko wykonawcze nie odnajdzie pliku zasobów dla kultury domyślnej (rezerwowej), <xref:System.Resources.MissingManifestResourceException> zostanie zgłoszony wyjątek lub. <xref:System.Resources.MissingSatelliteAssemblyException>
   - Jeśli plik zasobów zostanie znaleziony, ale żądany zasób nie istnieje, żądanie zwróci wartość `null`.
