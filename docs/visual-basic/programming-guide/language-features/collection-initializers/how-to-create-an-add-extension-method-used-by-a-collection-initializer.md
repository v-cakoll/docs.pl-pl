---
title: 'Porady: tworzenie i dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d19ac8b03b992eb9b09b5cb45fdcceadad3a822a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Porady: tworzenie i dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)
Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic wyszukuje `Add` metody typu kolekcji dla której parametry `Add` metody pasują do typów wartości na liście inicjatora kolekcji. To `Add` metoda jest używana do wypełniania kolekcji wartościami z inicjatora kolekcji.  
  
 Jeśli pasujących `Add` metoda istnieje i nie można zmodyfikować kod dla kolekcji, można dodać metodę rozszerzenia o nazwie `Add` pobierającej parametrów, które są wymagane przez inicjator kolekcji. Jest to zwykle, co należy zrobić, gdy używasz inicjatory kolekcji dla kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać metody rozszerzenia do ogólnego <xref:System.Collections.Generic.List%601> wpisz, aby inicjatora kolekcji można dodawać obiekty określonego typu `Employee`. Metody rozszerzenia pozwala na użycie składni inicjatora kolekcji skrócone.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjatory kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
