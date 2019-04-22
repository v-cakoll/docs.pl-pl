---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: de4f67fc5b60de48383a8ca886cff02b03830318
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814179"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Określa co najmniej jeden zadeklarowany zmienne lokalne są nadal istnieć i zachowywać swoje ostatnie wartości po zakończeniu procedury, w którym są one zgłoszone.  
  
## <a name="remarks"></a>Uwagi  
 Normalnie zmienna lokalna w procedurach przestanie istnieć tak szybko, jak zatrzymuje procedury. Zmienna statyczna nadal istnieje i zachowuje swoją wartość najbardziej aktualne. Przy następnym kod wywołuje procedurę, zmienna nie są ponownie inicjowane i nadal utrzymuje najpóźniejszą wartość przypisana do niego. Zmienna statyczna w dalszym ciągu dla okresu istnienia klasę lub moduł, który jest zdefiniowany w istnieje.  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Możesz użyć `Static` tylko w zmiennych lokalnych. Oznacza to, że kontekst deklaracji `Static` zmienna musi być procedurą lub blokiem w procedurze, a nie może być plikiem źródłowym, przestrzeń nazw, klasy, struktury lub modułu.  
  
     Nie można użyć `Static` wewnątrz procedury struktury.  
  
-   Typy danych `Static` nie można wywnioskować zmiennych lokalnych. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modyfikatory połączone.** Nie można określić `Static` wraz z `ReadOnly`, `Shadows`, lub `Shared` w tej samej deklaracji.  
  
## <a name="behavior"></a>Zachowanie  
 Kiedy Deklarujesz zmienną statyczną w `Shared` procedura, tylko jedna kopia zmienna statyczna jest dostępna dla całej aplikacji. Należy wywołać `Shared` nazwę procedury przy użyciu klasy, nie zmienną, która wskazuje na wystąpienie klasy.  
  
 Kiedy Deklarujesz zmienną statyczną w procedurze, która nie jest `Shared`tylko jedną kopię zmiennej jest dostępna dla każdego wystąpienia klasy. Wywołujesz procedurę nieudostępnione, używając zmiennej, który wskazuje na konkretne wystąpienie klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static` Zmiennej `totalSales` jest inicjowana wartością 0 tylko jeden raz. Za każdym razem, należy wprowadzić `updateSales`, `totalSales` środki, nieopłacone najbardziej aktualną wartość, która została obliczona dla niego.  
  
 `Static` Modyfikatora można używać w tym kontekście:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
