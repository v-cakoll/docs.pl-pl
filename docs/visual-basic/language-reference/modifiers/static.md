---
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 3b323d5fb1c4f1357b9f476213793c69d29b7208
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402697"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Określa, że co najmniej jedna zadeklarowana zmienna lokalna ma nadal istnieć i zachować najnowsze wartości po zakończeniu procedury, w której zostały zadeklarowane.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle zmienna lokalna w procedurze przestaje istnieć, gdy tylko procedura zostanie zatrzymana. Zmienna statyczna nadal istnieje i zachowuje jej najnowszą wartość. Przy następnym wywoływaniu procedury przez kod zmienna nie zostanie zainicjowana i nadal będzie zawierać najnowszą wartość, którą przypisano do niej. Zmienna statyczna nadal istnieje dla okresu istnienia klasy lub modułu, w którym jest zdefiniowana.  
  
## <a name="rules"></a>Reguły  
  
- **Kontekst deklaracji.** Można używać `Static` tylko w zmiennych lokalnych. Oznacza to, że kontekst deklaracji dla `Static` zmiennej musi być procedurą lub blokiem procedury i nie może być plikiem źródłowym, przestrzenią nazw, klasą, strukturą ani modułem.  
  
     Nie można użyć `Static` wewnątrz procedury struktury.  
  
- `Static`Nie można wywnioskować typów danych zmiennych lokalnych. Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md).  
  
- **Połączone modyfikatory.** Nie można określić `Static` razem z `ReadOnly` , `Shadows` , lub `Shared` w tej samej deklaracji.  
  
## <a name="behavior"></a>Zachowanie  
 Po zadeklarowaniu zmiennej statycznej w `Shared` procedurze dla całej aplikacji dostępna jest tylko jedna kopia zmiennej statycznej. Wywoływanie `Shared` procedury przy użyciu nazwy klasy, a nie zmiennej, która wskazuje na wystąpienie klasy.  
  
 Po zadeklarowaniu zmiennej statycznej w procedurze, która nie jest `Shared` , dla każdego wystąpienia klasy dostępna jest tylko jedna kopia zmiennej. Procedurę nieudostępnioną można wywołać przy użyciu zmiennej, która wskazuje na konkretne wystąpienie klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie `Static` .  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`Zmienna `totalSales` jest inicjowana do 0 tylko raz. Za każdym razem, gdy wprowadzasz `updateSales` , `totalSales` nadal ma ostatnio obliczoną wartość.  
  
 `Static`Modyfikator może być używany w tym kontekście:  
  
 [Dim, instrukcja](../statements/dim-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Shadows](shadows.md)
- [Shared](shared.md)
- [Okres istnienia w Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Deklaracja zmiennej](../../programming-guide/language-features/variables/variable-declaration.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
