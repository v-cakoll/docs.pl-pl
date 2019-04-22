---
title: Ograniczenia Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 10f67c02d25ec275d1c3e98197d51c25aa250c19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824913"
---
# <a name="visual-basic-limitations"></a>Ograniczenia Visual Basic
Wcześniejszych wersjach programu Visual Basic wymuszane granic w kodzie, takie jak długość nazwy zmiennych, liczba zmiennych dozwolone w modułach i rozmiar modułu. W języku Visual Basic .NET mają został złagodzone te ograniczenia, dzięki czemu masz większą swobodę w pisanie i organizowanie kodu.  
  
 Limity fizycznych są zależne, więcej pamięci środowiska wykonawczego niż na zagadnienia dotyczące kompilacji. Jeśli dokładne zbadanie problemu wskazówki programowania i dzielenia dużych aplikacji na wiele klas i moduły występuje bardzo niewielkie prawdopodobieństwo napotkania ograniczenie wewnętrzne języka Visual Basic.  
  
 Poniżej przedstawiono pewne ograniczenia, które mogą wystąpić w ekstremalnych przypadkach:  
  
-   **Długość nazwy.** Ma maksymalną liczbę znaków w nazwie każdej zadeklarowany element. Ta wartość maksymalna ma zastosowanie do kwalifikacji cały ciąg, jeśli jest kwalifikowana nazwa elementu. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Długość wiersza.** Występuje maksymalnie 65535 znaków fizycznego wiersza kodu źródłowego. Wiersz kodu źródłowego logicznej może być dłużej, jeśli używasz znaki kontynuacji wiersza. Zobacz [jak: Przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Wymiary tablicy.** Istnieje maksymalna liczba wymiarów, które można zadeklarować tablicy. To ogranicza liczbę indeksów, można użyć do określenia elementu tablicy. Zobacz [tablicy wymiarów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Długość ciągu.** Istnieje maksymalna liczba znaków Unicode, które można przechowywać w jednym ciągu. Zobacz [typu danych String](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Długość ciągu środowiska.** Brak wynosić 32 768 znaków ciągu środowiska, używane jako argument wiersza polecenia. Jest to ograniczenie na wszystkich platformach.  
  
## <a name="see-also"></a>Zobacz także

- [Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
