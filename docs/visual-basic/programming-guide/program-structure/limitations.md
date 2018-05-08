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
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-limitations"></a>Ograniczenia Visual Basic
Wcześniejszych wersji programu Visual Basic wymuszane granic w kodzie, takie jak długość nazwy zmiennych, liczba zmiennych dozwolone w modułach i rozmiar modułu. W języku Visual Basic .NET te ograniczenia mają zostały rozluźnić, zapewniając większą swobodę w pisania i organizowanie kodu.  
  
 Limity fizycznych są zależne więcej czasu wykonywania pamięci niż na zagadnienia dotyczące kompilacji. Jeśli zastosowanie ostrożnego rozwiązań w zakresie programowania i dzielenia dużych aplikacji na wiele klas i modułów, oznacza to, że bardzo mało prawdopodobieństwo napotkania ograniczenie wewnętrzne Visual Basic.  
  
 Poniżej przedstawiono pewne ograniczenia, które mogą wystąpić w ekstremalnych przypadkach:  
  
-   **Długość nazwy.** Istnieje maksymalna liczba znaków w nazwie co zadeklarowany element. Maksymalna dotyczą ciągu całego kwalifikacji jest kwalifikowana nazwa elementu. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Długość wiersza.** Brak maksimum 65535 znaków w fizycznego wiersza kodu źródłowego. Wiersz kodu źródłowego logicznej może być dłużej, jeśli używasz znaki kontynuacji wiersza. Zobacz [porady: przerywanie i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Wymiary tablicy.** Istnieje maksymalna liczba wymiarów, które można zadeklarować tablicy. Ogranicza liczbę indeksów, można użyć do określenia elementu tablicy. Zobacz [tablicy wymiarów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Długość ciągu.** Istnieje maksymalna liczba znaków Unicode, których można przechowywać w jednym ciągu. Zobacz [dane typu ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Długość ciągu środowiska.** Brak znaków 32768 do dowolnego ciągu środowiska używany jako argument wiersza polecenia. Jest to ograniczenie na wszystkich platformach.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
