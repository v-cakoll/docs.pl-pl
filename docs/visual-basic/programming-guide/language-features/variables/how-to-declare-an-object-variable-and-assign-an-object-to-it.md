---
title: 'Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: fb6411efc190dce335422369a8d2bbff564b9523
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819674"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic
Zadeklaruj zmienną [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Przypisz obiekt takiej zmiennej, umieszczając obiekt po znaku równości (`=`) w klauzuli instrukcji lub inicjowania przypisania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `Object` zmienną i przypisuje bieżące wystąpienie do niego.  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Możesz połączyć deklarację i przypisanie przez inicjowanie zmiennej jako części swojej deklaracji. Poniższy przykład jest równoważny do poprzedniego przykładu.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System> przestrzeni nazw.  
  
-   Klasy, struktury lub modułu, w której chcesz umieścić `Dim` instrukcji.  
  
-   Procedura, w której chcesz umieścić w instrukcji przypisania.  
  
## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
