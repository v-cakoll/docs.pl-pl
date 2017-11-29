---
title: "Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fe20303f6f2ed692e54e44ee8cc65897531543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)
Jeśli chcesz `Get` i `Set` procedur we właściwości w celu mają różne poziomy dostępu, można użyć poziomu mniej ograniczająca w `Property` instrukcji i bardziej restrykcyjne poziomu w jednym `Get` lub `Set` instrukcji. Mieszanymi poziomami dostępu można używać we właściwości, gdy chce niektórych części kodu, aby można było pobrać wartości właściwości i części kodu, aby można było zmienić wartość.  
  
 Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarowanie właściwości z mieszanymi poziomami dostępu  
  
1.  Deklarowanie właściwości w zwykły sposób, a następnie określ poziom dostępu mniej restrykcyjny (takich jak `Public`) w `Property` instrukcji.  
  
2.  Deklarowanie albo `Get` lub `Set` procedurę określając bardziej restrykcyjne poziom dostępu (takie jak `Friend`).  
  
3.  Nie określaj poziom dostępu w procedurze właściwości. Zakłada się poziom dostępu zadeklarowany w `Property` instrukcji. Można ograniczyć dostęp tylko dla jednej z właściwości procedur.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     W poprzednim przykładzie `Get` procedura ma taką samą `Protected` dostępu jako właściwość, gdy `Set` procedura ma `Private` dostępu. Klasa pochodna od `employee` może odczytywać `salary` wartość, ale tylko `employee` klasy może go ustawić.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Procedury własności](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Porady: Tworzenie właściwości](./how-to-create-a-property.md)  
 [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Porady: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)  
 [Porady: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
