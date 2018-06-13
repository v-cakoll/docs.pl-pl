---
title: 'Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648879"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic
Deklarowanie zmiennej [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) , określając `As Object` w [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Przypisz obiekt takiej zmiennej umieszczając obiekt po znaku równości (`=`) w klauzuli przypisania instrukcji lub inicjowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `Object` zmienną i przypisuje bieżące wystąpienie do niego.  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Deklaracja i przypisania można połączyć za inicjowanie zmiennej jako części swojej deklaracji. Poniższy przykład jest odpowiednikiem poprzedniego przykładu.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System> przestrzeni nazw.  
  
-   Klasy, struktury lub moduł, w której chcesz umieścić `Dim` instrukcji.  
  
-   Procedura, w której chcesz umieścić w instrukcji przypisania.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
