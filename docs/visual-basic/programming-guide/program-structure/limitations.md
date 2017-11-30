---
title: Ograniczenia Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a>Ograniczenia Visual Basic
Starsze niż [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wymuszane granic w kodzie, takie jak długość nazwy zmiennych dozwolona liczba zmienne w modułach i rozmiar modułu. W języku Visual Basic .NET te ograniczenia mają zostały rozluźnić, zapewniając większą swobodę w pisania i organizowanie kodu.  
  
 Limity fizycznych są zależne więcej czasu wykonywania pamięci niż na zagadnienia dotyczące kompilacji. Jeśli zastosowanie ostrożnego rozwiązań w zakresie programowania i dzielenia dużych aplikacji na wiele klas i modułów, a następnie jest bardzo mało prawdopodobieństwo napotkania wewnętrznego [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ograniczenia.  
  
 Poniżej przedstawiono pewne ograniczenia, które mogą wystąpić w ekstremalnych przypadkach:  
  
-   **Długość nazwy.** Istnieje maksymalna liczba znaków w nazwie co zadeklarowany element. Maksymalna dotyczą ciągu całego kwalifikacji jest kwalifikowana nazwa elementu. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Długość wiersza.** Brak maksimum 65535 znaków w fizycznego wiersza kodu źródłowego. Wiersz kodu źródłowego logicznej może być dłużej, jeśli używasz znaki kontynuacji wiersza. Zobacz [porady: przerywanie i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Wymiary tablicy.** Istnieje maksymalna liczba wymiarów, które można zadeklarować tablicy. Ogranicza liczbę indeksów, można użyć do określenia elementu tablicy. Zobacz [tablicy wymiarów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Długość ciągu.** Istnieje maksymalna liczba znaków Unicode, których można przechowywać w jednym ciągu. Zobacz [dane typu ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Długość ciągu środowiska.** Brak znaków 32768 do dowolnego ciągu środowiska używany jako argument wiersza polecenia. Jest to ograniczenie na wszystkich platformach.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
