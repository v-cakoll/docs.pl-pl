---
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350761"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Określa, że co najmniej jedna zadeklarowana zmienna lokalna ma nadal istnieć i zachować najnowsze wartości po zakończeniu procedury, w której zostały zadeklarowane.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle zmienna lokalna w procedurze przestaje istnieć, gdy tylko procedura zostanie zatrzymana. Zmienna statyczna nadal istnieje i zachowuje jej najnowszą wartość. Przy następnym wywoływaniu procedury przez kod zmienna nie zostanie zainicjowana i nadal będzie zawierać najnowszą wartość, którą przypisano do niej. Zmienna statyczna nadal istnieje dla okresu istnienia klasy lub modułu, w którym jest zdefiniowana.  
  
## <a name="rules"></a>Reguły  
  
- **Kontekst deklaracji.** `Static` można używać tylko w zmiennych lokalnych. Oznacza to, że kontekst deklaracji dla zmiennej `Static` musi być procedurą lub blokiem procedury i nie może być plikiem źródłowym, przestrzenią nazw, klasą, strukturą ani modułem.  
  
     Nie można użyć `Static` wewnątrz procedury struktury.  
  
- Nie można wywnioskować typów danych `Static` zmiennych lokalnych. Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
- **Połączone modyfikatory.** Nie można określić `Static` razem z `ReadOnly`, `Shadows`lub `Shared` w tej samej deklaracji.  
  
## <a name="behavior"></a>Zachowanie  
 Po zadeklarowaniu zmiennej statycznej w procedurze `Shared` jest dostępna tylko jedna kopia zmiennej statycznej dla całej aplikacji. Procedurę `Shared` można wywołać przy użyciu nazwy klasy, a nie zmiennej, która wskazuje na wystąpienie klasy.  
  
 Po zadeklarowaniu zmiennej statycznej w procedurze, która nie jest `Shared`, dla każdego wystąpienia klasy dostępna jest tylko jedna kopia zmiennej. Procedurę nieudostępnioną można wywołać przy użyciu zmiennej, która wskazuje na konkretne wystąpienie klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 Zmienna `Static` `totalSales` jest inicjowana do 0 tylko raz. Za każdym razem, gdy wprowadzasz `updateSales`, `totalSales` nadal ma ostatnio obliczoną wartość.  
  
 Modyfikator `Static` może być używany w tym kontekście:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
