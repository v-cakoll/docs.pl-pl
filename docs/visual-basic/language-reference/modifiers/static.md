---
title: Static (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e08f46076281e766a5bc0b99cd61fee9cd41ece5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Określa, że co najmniej jeden zadeklarowany zmienne lokalne są nadal istnieje i zachowywać swoje ostatnie wartości po zakończeniu procedury, w którym jest zadeklarowany.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle zmienną lokalną w procedurze przestanie istnieć zaraz po zatrzymaniu procedury. Zmienna statyczna nadal istnieje i zachowuje jej najbardziej aktualną wartość. Przy następnym kod wywołuje procedurę, zmienna nie są ponownie inicjowane i nadal zawiera najnowszą wartość przypisana do niego. Zmienna statyczna nadal istnieje przez czas ich istnienia klasę lub moduł, który jest zdefiniowany w.  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Static` tylko dla zmiennych lokalnych. Oznacza to, że w kontekście deklaracji `Static` zmiennej musi być procedurę lub blok w procedurze, a nie można go plik źródłowy, przestrzeni nazw, klasy, struktury lub modułu.  
  
     Nie można użyć `Static` wewnątrz procedury struktury.  
  
-   Typy danych `Static` nie można wywnioskować zmiennych lokalnych. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Łączna modyfikatorów.** Nie można określić `Static` razem z `ReadOnly`, `Shadows`, lub `Shared` w tej samej deklaracji.  
  
## <a name="behavior"></a>Zachowanie  
 Gdy deklaruje zmienną statyczną w `Shared` procedura, tylko jedną kopię zmienna statyczna jest dostępna dla całej aplikacji. Należy wywołać `Shared` nazwę procedury przy użyciu klasy nie zmiennej, która wskazuje na wystąpienie klasy.  
  
 Gdy deklaruje zmienną statyczną w procedurze, która nie jest `Shared`tylko jedną kopię zmienna jest dostępna dla każdego wystąpienia klasy. Należy wywołać procedurę nieudostępnione przy użyciu zmiennej, która wskazuje konkretne wystąpienie tej klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 `Static` Zmiennej `totalSales` jest ustawiana na 0 tylko jeden raz. Za każdym razem, możesz wprowadzić `updateSales`, `totalSales` nadal ma wartość najnowszych obliczona dla niego.  
  
 `Static` Modyfikatora można używać w tym kontekście:  
  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Udostępnione](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
