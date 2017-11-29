---
title: "Zabezpieczenia dostawcy typów"
description: "Więcej informacji o zabezpieczenia dostawcy typów w języku F #, łącznie ze sposobem zmiany ustawień zaufania dla dostawcy typów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a>Zabezpieczenia dostawcy typów

Dostawcy typów to zestawy (dll) odwołuje się programu F # projekt lub skrypt zawierające kod, aby nawiązać połączenia z zewnętrznymi źródłami danych, a następnie publikować informacje o tym typie środowiska typu F #. Zazwyczaj kodu w przywoływanych zestawach jest uruchamiany tylko kompilacji, a następnie wykonania kodu (lub w przypadku skryptu, wyślij kod do narzędzia F # Interactive). Jednak zestawu dostawcy typu zostanie uruchomiony w programie Visual Studio podczas kod jest jedynie w edytorze. Dzieje się tak, ponieważ typ dostawcy muszą Uruchom, aby dodać dodatkowe informacje do edytora, takiego jak szybka podpowiedź, zakończeń IntelliSense i tak dalej. W związku z tym istnieją zagadnienia dotyczące dodatkowych zabezpieczeń dla typu zestawy dostawcy, ponieważ są automatycznie uruchamiane wewnątrz procesu programu Visual Studio.


## <a name="security-warning-dialog"></a>Okno dialogowe ostrzeżenia o zabezpieczeniach
Korzystając z zestawu dostawcy określonego typu po raz pierwszy, program Visual Studio Wyświetla okno dialogowe zabezpieczeń, które ostrzega o tym, że dostawca typów jest uruchomiony. Przed Visual Studio ładuje typ dostawcy, daje możliwość zdecydować, jeśli ufasz temu określonego dostawcy. Jeśli ufasz źródłu typu dostawcy, następnie wybierz pozycję "I zaufanie ten dostawca typów". Jeśli nie ufasz źródło typ dostawcy, następnie wybierz pozycję "I nie masz zaufania tego typu dostawcy." Zaufanie dostawcy umożliwia uruchamianie w programie Visual Studio i podaj IntelliSense i tworzenia funkcji. Jednak w przypadku złośliwego typ dostawcy samego uruchomienia jej kodu może naruszyć bezpieczeństwo komputera.

Jeśli projekt zawiera kod, który odwołuje się do dostawców typów, które wybrano w oknie dialogowym niezaufane, następnie w czasie kompilacji, kompilator będzie zgłaszać błąd, który wskazuje, że dostawca typów jest niezaufanych. Żadnych typów, które są zależne od dostawcy typów niezaufanych są oznaczone czerwoną zygzaki. Jest to bezpieczne przeglądanie kodu w edytorze.

Jeśli zdecydujesz się zmienić ustawienie zaufania bezpośrednio w programie Visual Studio, wykonaj następujące kroki.


#### <a name="to-change-the-trust-settings-for-type-providers"></a>Aby zmienić ustawienia zaufania dostawców typów

1. Na `Tools` menu, wybierz opcję `Options`i rozwiń `F# Tools` węzła.
<br />

2. Wybierz `Type Providers`, na liście dostawców typów, zaznacz pole wyboru dla zaufanych dostawców typów i usuń zaznaczenie pola wyboru dla tych nie ufasz.
<br />


## <a name="see-also"></a>Zobacz też
[Dostawcy typów](index.md)
