---
title: Zabezpieczenia dostawcy typów
description: Więcej informacji na temat zabezpieczenia dostawcy typów F#, w tym sposobu zmiany ustawień zaufania dla dostawcy typu.
ms.date: 05/16/2016
ms.openlocfilehash: 26f95ad3950b37a668c497f293b9941ed13a18c7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43861910"
---
# <a name="type-provider-security"></a>Zabezpieczenia dostawcy typów

Dostawcy typów są zestawy (dll) odwołuje się z projektu języka F# lub skryptu, które zawierają kod, aby nawiązać połączenie z zewnętrznymi źródłami danych, a następnie publikować informacje o typie środowiska typu F#. Zazwyczaj w przywoływanych zestawach tylko uruchamiania kodu po skompilowaniu i następnie wykonać ten kod (lub w przypadku skryptu, wyślij kod do programu F# Interactive). Jednak zestawu dostawcy typów będą uruchamiane w programie Visual Studio, gdy jedynie przeglądania kodu w edytorze. Dzieje się tak, ponieważ dostawców typów, które należy uruchomić, aby dodać dodatkowe informacje do edytora, takiego jak etykietki szybka podpowiedź, uzupełnianiu IntelliSense i tak dalej. W wyniku istnieją zapewnienia dodatkowego bezpieczeństwa informacje dotyczące typu zestawy dostawcy, ponieważ są automatycznie uruchamiane wewnątrz procesu programu Visual Studio.

## <a name="security-warning-dialog"></a>Okno dialogowe ostrzeżenia o zabezpieczeniach

Korzystając z zestawów dostawcy określonego typu po raz pierwszy, Visual Studio Wyświetla okno dialogowe zabezpieczeń, która ostrzega o tym, że dostawca typów zostanie uruchomiony. Przed Visual Studio ładuje dostawcę typów, daje możliwość zdecydować, jeśli ufasz temu określonego dostawcy. Jeśli ufasz źródłu dostawcy typu, wybierz "Zaufanej tego dostawcy typu". Jeśli nie ufasz źródła dostawcę typów, następnie wybierz pozycję "I nie ufasz tego typu dostawcy." Zaufaniem dostawcy włączy ją do uruchamiania w programie Visual Studio i dostarczyć IntelliSense i tworzyć funkcje. Jednak w przypadku złośliwego dostawcę typów, sama uruchamianie jej kodu mogą negatywnie wpłynąć na swojej maszynie.

Jeśli projekt zawiera kod, który odwołuje się do dostawców typów, które wybrano w oknie dialogowym nie ufać, następnie w czasie kompilacji kompilator zgłosi błąd wskazujący, że dostawca typów nie jest zaufany. Wszystkie typy, które są zależne od dostawcy typów niezaufanych są wskazywane przez czerwone symbole. Jest bezpieczne przeglądać kod w edytorze.

Jeśli zdecydujesz się zmienić ustawienie relacji zaufania, bezpośrednio w programie Visual Studio, wykonaj następujące kroki.

### <a name="to-change-the-trust-settings-for-type-providers"></a>Aby zmienić ustawienia zaufania dostawców typów

1. Na `Tools` menu, wybierz opcję `Options`i rozwiń `F# Tools` węzła.

2. Wybierz `Type Providers`, na liście dostawców typów, zaznacz pole wyboru dla dostawców typów ufasz i usuń zaznaczenie pola wyboru dla osób nie ufasz.

## <a name="see-also"></a>Zobacz także

- [Dostawcy typów](index.md)
