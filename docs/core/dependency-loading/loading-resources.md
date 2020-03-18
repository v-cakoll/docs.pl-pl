---
title: Algorytm ładowania zestawu satelitarnego - .NET Core
description: Opis szczegółów algorytmu ładowania zestawu satelitarnego w .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70105315"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algorytm ładowania zestawu satelitarnego

Zestawy satelickie są używane do przechowywania zlokalizowanych zasobów dostosowanych do języka i kultury.

Zestawy satelickie używają innego algorytmu ładowania niż ogólne zestawy zarządzane.

## <a name="when-are-satellite-assemblies-loaded"></a>Kiedy są ładowane zespoły satelickie?

Zestawy satelickie są ładowane podczas ładowania zlokalizowanego zasobu.

Podstawowy interfejs API do ładowania <xref:System.Resources.ResourceManager?displayProperty=fullName> zlokalizowanych zasobów jest klasą. Ostatecznie <xref:System.Resources.ResourceManager> klasa wywoła <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodę dla <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>każdego .

Interfejsy API wyższego poziomu mogą abstrakcyjne interfejsu API niskiego poziomu.

## <a name="algorithm"></a>Algorytm

Proces rezerwowy zasobu .NET Core obejmuje następujące kroki:

1. `active` <xref:System.Runtime.Loader.AssemblyLoadContext> Określ wystąpienie. We wszystkich przypadkach `active` wystąpienie jest zestawu wykonującego <xref:System.Runtime.Loader.AssemblyLoadContext>.

2. Wystąpienie `active` próbuje załadować zestaw satelicki dla żądanej kultury w kolejności priorytetowej przez:
    - Sprawdzanie jego pamięci podręcznej.
    - Sprawdzanie katalogu aktualnie wykonywanego zestawu dla podkatalogu <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> zgodnego `es-MX`z żądanym (na przykład).

        > [!NOTE]
        > Ta funkcja nie została zaimplementowana w .NET Core przed 3.0.
        >
        > [!NOTE]
        > W systemie Linux i macOS podkatalog jest rozróżniany i musi:
        > - Dokładnie pasuje do przypadku.
        > - Bądź w małych liter.

    - Jeśli `active` jest <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> wystąpieniem, uruchamiając domyślną logikę [sondowania zestawu satelity (zasobu).](default-probing.md#satellite-resource-assembly-probing)

    - Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkcji.

    - Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> zdarzenia.

    - Podnoszenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia.

3. Jeśli zespół satelitarny jest załadowany:
   - Zdarzenie <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> jest wywoływane.
   - Zestaw jest przeszukiwany w poszukiwaniu żądanego zasobu. Jeśli czas wykonywania znajdzie zasób w zestawie, używa go. Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.

    > [!NOTE]
    > Aby znaleźć zasób w zestawie satelickim, czas <xref:System.Resources.ResourceManager> uruchomieniwy wyszukuje plik zasobu wymagany przez bieżącego <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>pliku . W pliku zasobu wyszukuje żądana nazwa zasobu. Jeśli którykolwiek z nich nie zostanie znaleziony, zasób jest traktowany jako nieznaleziony.

4. W czasie wykonywania obok przeszukuje zestawy kultury nadrzędnej za pośrednictwem wielu potencjalnych poziomów, za każdym razem powtarzając kroki 2 & 3.

    Każda kultura ma tylko jeden element nadrzędny, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwość.

    Wyszukiwanie kultur nadrzędnych zatrzymuje się, <xref:System.Globalization.CultureInfo.Parent%2A> gdy <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>właściwość kultury jest .

    Dla <xref:System.Globalization.CultureInfo.InvariantCulture>, nie wracamy do kroków 2 & 3, ale raczej kontynuować krok 5.

5. Jeśli zasób nadal nie zostanie znaleziony, używany jest zasób dla domyślnej (rezerwowej) kultury.

   Zazwyczaj zasoby dla kultury domyślnej są uwzględniane w głównym zestawie aplikacji. Można jednak określić <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> dla <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> właściwości. Ta wartość wskazuje, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelickim, a nie głównym.

    > [!NOTE]
    > Domyślna kultura jest ostatecznym rezerwowym. W związku z tym zaleca się, aby zawsze uwzględnić wyczerpujący zestaw zasobów w domyślnym pliku zasobów. Pomaga to zapobiec zgłaszaniu wyjątków. Mając wyczerpujący zestaw, należy podać rezerwowy dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzne dla kultury.

6. Wreszcie
   - Jeśli czas wykonywania nie znajdzie pliku zasobów dla domyślnej (rezerwowej) kultury, zgłaszany jest wyjątek <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException> wyjątek.
   - Jeśli plik zasobu zostanie znaleziony, ale żądany zasób nie jest obecny, żądanie zwraca `null`.
