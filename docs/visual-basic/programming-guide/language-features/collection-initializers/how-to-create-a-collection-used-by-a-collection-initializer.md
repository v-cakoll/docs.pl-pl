---
title: 'Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cff862f16530bc268628d9406ae81d23f2761926
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)
Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic wyszukuje `Add` metody typu kolekcji dla której parametry `Add` metody pasują do typów wartości na liście inicjatora kolekcji. To `Add` metoda jest używana do wypełniania kolekcji wartościami z inicjatora kolekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `OrderCollection` kolekcji zawierającej publiczny `Add` metody używanego przez inicjator kolekcji można dodawać obiekty określonego typu `Order`. `Add` Metoda pozwala na użycie składni inicjatora kolekcji skrócone.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjatory kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Porady: tworzenie Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
