---
title: "Porady: umieszczanie wartości we właściwości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44e7c4a92ea3d087c12e74aa2ede33a52c8730cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Porady: umieszczanie wartości we właściwości (Visual Basic)
Wartości są przechowywane we właściwości ustawiając właściwości nazwy po lewej stronie instrukcji przypisania.  
  
 Właściwość `Set` procedury przechowuje wartość, ale nie zostanie jawnie wywołana go według nazwy. Użyj właściwości, tak jak w przypadku zmiennej. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]wykonywania wywołań do procedury właściwości.  
  
### <a name="to-store-a-value-in-a-property"></a>Do przechowywania wartości we właściwości  
  
1.  Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.  
  
     W poniższym przykładzie ustawiono wartość [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` właściwości południe niejawnie wywoływanie jej `Set` procedury.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3.  Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty. Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
4.  Generowane po prawej stronie instrukcji przypisania wartość jest przechowywana we właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [Procedury własności](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Porady: Tworzenie właściwości](./how-to-create-a-property.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Porady: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
