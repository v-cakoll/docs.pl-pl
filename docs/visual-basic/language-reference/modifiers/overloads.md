---
title: Overloads (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 0d68846938aba809a7a3a6f7d27f185bb90a39cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819336"
---
# <a name="overloads-visual-basic"></a>Overloads (Visual Basic)
Określa, że właściwość lub procedura redeclares istniejących właściwości lub procedur o takiej samej nazwie.  
  
## <a name="remarks"></a>Uwagi  
 *Przeciążanie* w praktyce podawania więcej niż jedną definicję dla danej nazwy właściwość lub procedura w tym samym zakresie. Redeclaring właściwość lub procedura z innym podpisem jest czasami nazywane *ukrywanie poprzez podpis*.  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Możesz użyć `Overloads` tylko w instrukcji deklaracji właściwość lub procedura.  
  
-   **Modyfikatory połączone.** Nie można określić `Overloads` wraz z [cieni](../../../visual-basic/language-reference/modifiers/shadows.md) w tej samej deklaracji procedury.  
  
-   **Wymagane różnice.** *Podpisu* w tej deklaracji musi się różnić od podpisu co właściwość lub procedura, która przeciąża. Podpis składa się nazwa właściwość lub procedura wraz z następujących czynności:  
  
    -   Liczba parametrów  
  
    -   kolejność parametrów  
  
    -   typy danych parametrów  
  
    -   Liczba parametrów typu (w przypadku ogólnych procedura)  
  
    -   zwracany typ (tylko dla procedury operatora konwersji)  
  
     Wszystkie przeciążenia musi mieć taką samą nazwę, ale każdy musi różnić się od wszystkich innych w co najmniej jednej poprzedniej aspektach. Dzięki temu kompilator, aby odróżnić wyborze wersji do użycia, gdy kod wywołuje właściwość lub procedura.  
  
-   **Niedozwolone różnice.** Zmiana co najmniej jeden z następujących jest nieprawidłowa dla przeciążania właściwość lub procedura, ponieważ nie są one częścią podpisu:  
  
    -   Określa, czy zwraca wartość (w przypadku procedura)  
  
    -   Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)  
  
    -   nazwy parametrów lub parametrów typu  
  
    -   ograniczenia dotyczące parametrów typu (w przypadku ogólnych procedura)  
  
    -   słowa kluczowe modyfikator parametrów (takie jak `ByRef` lub `Optional`)  
  
    -   Właściwość lub procedura modyfikator słowa kluczowe (takie jak `Public` lub `Shared`)  
  
-   **Opcjonalny modyfikator właściwy.** Nie trzeba używać `Overloads` modyfikator podczas definiowania wielu przeciążone właściwości i procedury z tej samej klasy. Jednak jeśli używasz `Overloads` w jednej deklaracji, musisz ją wykorzystać we wszystkich z nich.  
  
-   **Przesłanianie i przeciążeniu.** `Overloads` można również w tle istniejącego elementu członkowskiego lub zestawu przeciążone elementy członkowskie w klasie bazowej. Kiedy używasz `Overloads` w ten sposób możesz deklarować właściwość lub metoda o tej samej nazwie i tę samą listę parametrów jako składowej klasy bazowej i nie trzeba dostarczać `Shadows` — słowo kluczowe.  
  
 Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.  
  
 `Overloads` Modyfikator mogą być używane w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Instrukcje: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
