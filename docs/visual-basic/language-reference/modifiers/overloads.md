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
ms.openlocfilehash: b68c13d192845fc4bedf1b34a40165ccc1a5ff75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601917"
---
# <a name="overloads-visual-basic"></a>Overloads (Visual Basic)
Określa, że właściwość lub procedura programistyczny ponownie deklaruje co najmniej jednej właściwości istniejących lub procedury o takiej samej nazwie.  
  
## <a name="remarks"></a>Uwagi  
 *Przeciążanie* praktyką podawania więcej niż jedną definicję dla danej nazwy właściwość lub procedura w tym samym zakresie. Ponownego deklarowania właściwość lub procedurę o innym podpisie jest czasami nazywany *ukrywanie poprzez podpis*.  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Overloads` tylko w instrukcji deklaracji właściwość lub procedura.  
  
-   **Łączna modyfikatorów.** Nie można określić `Overloads` razem z [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) w tej samej deklaracji procedury.  
  
-   **Wymagane różnice.** *Podpisu* w tej deklaracji musi być inna niż podpisu co właściwość lub procedura, która przeciąża. Sygnatura obejmuje nazwę właściwość lub procedura wraz z następujących czynności:  
  
    -   Liczba parametrów  
  
    -   kolejność parametrów  
  
    -   typy danych parametrów  
  
    -   Liczba parametrów typu (dla procedury ogólny)  
  
    -   zwracany typ (tylko dla procedury operatora konwersji)  
  
     Wszystkie przeciążenia musi mieć taką samą nazwę, ale każdy musi różnić się od wszystkich innych w co najmniej jednego z poprzednich względem. Umożliwia kompilatorowi rozróżnienie wersji do użycia, gdy kod wywołuje właściwość lub procedura.  
  
-   **Niedozwolone różnice.** Zmiana jednego lub więcej z następujących jest nieprawidłowa dla przeładowanie właściwość lub procedura, ponieważ nie są częścią podpisu:  
  
    -   Określa, czy zwraca wartość (procedura)  
  
    -   Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)  
  
    -   nazwy parametrów lub parametry typu  
  
    -   ograniczenia dotyczące parametrów typu (dla procedury ogólny)  
  
    -   słowa kluczowe modyfikator parametrów (takich jak `ByRef` lub `Optional`)  
  
    -   Właściwość lub procedura modyfikator słowa kluczowe (takich jak `Public` lub `Shared`)  
  
-   **Modyfikator opcjonalne.** Nie trzeba używać `Overloads` modyfikator podczas definiowania wielu przeciążone właściwości lub procedury opisane w tej samej klasy. Jednak jeśli używasz `Overloads` w jednej deklaracji, należy użyć go we wszystkich z nich.  
  
-   **Przesłanianie i przeciążeniu.** `Overloads` można również tle istniejącego elementu członkowskiego lub zestawu przeciążone elementy członkowskie w klasie podstawowej. Jeśli używasz `Overloads` w ten sposób można zadeklarować właściwości lub metody o tej samej nazwie i tej samej listy parametrów jako element członkowski klasy podstawowej i nie zostanie podana `Shadows` — słowo kluczowe.  
  
 Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` , aby pracować z C# łatwiej biblioteki interfejsów API.  
  
 `Overloads` Modyfikatora można używać w tych sytuacjach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
