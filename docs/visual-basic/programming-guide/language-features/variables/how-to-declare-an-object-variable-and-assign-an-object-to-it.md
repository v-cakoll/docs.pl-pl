---
title: 'Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4a682c7ae32ace0b1f859d52963342546a83f29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Dim — instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
