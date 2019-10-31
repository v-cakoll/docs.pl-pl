---
title: Zmiany środowiska uruchomieniowego i przekierowania — .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196699"
---
# <a name="application-compatibility-in-the-net-framework"></a>Zgodność aplikacji w .NET Framework

Zgodność jest ważnym celem każdej wersji platformy .NET. Zgodność gwarantuje, że każda wersja jest dodatkiem, dlatego poprzednie wersje będą nadal działały. Z drugiej strony zmiany poprzedniej funkcjonalności (na przykład w celu zwiększenia wydajności, rozwiązywania problemów z zabezpieczeniami lub rozwiązywania usterek) mogą spowodować problemy ze zgodnością w istniejącym kodzie lub istniejące aplikacje, które działają w nowszej wersji.

Każda aplikacja odwołuje się do określonej wersji .NET Framework przez:

- Definiowanie platformy docelowej w programie Visual Studio.
- Określanie platformy docelowej w pliku projektu.
- Zastosowanie <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.

W przypadku migrowania z jednej wersji .NET Framework do innej, istnieją dwa typy zmian do uwzględnienia:

- [Zmiany środowiska uruchomieniowego](#runtime-changes)
- [Przekierowywanie zmian](#retargeting-changes)

## <a name="runtime-changes"></a>Zmiany środowiska uruchomieniowego

Problemy dotyczące środowiska uruchomieniowego to te, które powstają, gdy nowe środowisko uruchomieniowe jest umieszczane na komputerze i zmiany zachowania aplikacji. W przypadku uruchamiania w nowszej wersji niż domowa, .NET Framework używa zachowania *quirked* do naśladowania starszej wersji. Aplikacja działa w nowszej wersji, ale działa tak, jakby była uruchomiona w starszej wersji. Wiele problemów ze zgodnością między wersjami .NET Framework jest korygowanych przez ten model quirking. Na przykład, jeśli plik binarny został skompilowany dla .NET Framework 4,0, ale jest uruchamiany na komputerze z .NET Framework 4,5 lub nowszym, działa on w .NET Framework 4,0 tryb zgodności. Oznacza to, że wiele zmian w nowszej wersji nie ma wpływu na dane binarne.

Wersja .NET Framework, do której odwołuje się aplikacja, jest określana przez docelową wersję zestawu wejścia dla domeny aplikacji, w której działa kod. Wszystkie dodatkowe zestawy ładowane w tej domenie aplikacji są przeznaczone dla tej wersji. Na przykład, w przypadku pliku wykonywalnego, wersja, do której należy wykonywalny, jest tryb zgodności wszystkie zestawy w tej domenie aplikacji działają w ramach programu.

Aby wyświetlić listę zmian w czasie wykonywania, które są stosowane w danym środowisku, wybierz aktualnie docelową wersję .NET Framework, a następnie wersję, do której chcesz przeprowadzić migrację:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Przekierowywanie zmian

Zmiany przekierowania są tymi, które powstają, gdy zestaw jest ponownie kompilowany w celu przekierowania do nowszej wersji. Przeznaczenie do nowszej wersji oznacza, że zestaw jest zachodzi na nowe funkcje, a także potencjalne problemy ze zgodnością dla starych funkcji.

Aby wyświetlić listę zmian docelowych, które są stosowane do danego środowiska, wybierz aktualnie używaną wersję .NET Framework, a następnie wersję, do której chcesz przeprowadzić migrację:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Klasyfikacja wpływu

W temacie opisującym środowisko uruchomieniowe i przekierowywanie zmian, na przykład [zmiany ukierunkowania migracji z 4.7.2 do 4,8](retargeting/4.7.2-4.8.md), poszczególne elementy są klasyfikowane według ich oczekiwanego wpływu w następujący sposób:

\ **Główne**
Znacząca zmiana wpływająca na dużą liczbę aplikacji lub wymagająca istotnej modyfikacji kodu.

\ **pomocnicze**
Zmiana wpływająca na niewielką liczbę aplikacji lub wymagająca drobnej modyfikacji kodu.

\ **przypadku krawędzi**
Zmiana wpływająca na aplikacje w ramach bardzo konkretnych scenariuszy, które nie są wspólne.

\ **przezroczyste**
Zmiana, która nie ma zauważalnego wpływu na deweloperów lub użytkownika aplikacji. Aplikacja nie powinna wymagać modyfikacji ze względu na tę zmianę.

## <a name="see-also"></a>Zobacz także

- [Wersje i zależności](versions-and-dependencies.md)
- [Co nowego](../whats-new/index.md)
- [Co jest przestarzałe](../whats-new/whats-obsolete.md)
