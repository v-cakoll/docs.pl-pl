---
title: 'Porady: umieszczanie wartości we właściwości (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f00303b290e324612ad3ac7af673690b4cf4e15
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Porady: umieszczanie wartości we właściwości (Visual Basic)
Wartości są przechowywane we właściwości ustawiając właściwości nazwy po lewej stronie instrukcji przypisania.  
  
 Właściwość `Set` procedury przechowuje wartość, ale nie zostanie jawnie wywołana go według nazwy. Użyj właściwości, tak jak w przypadku zmiennej. Visual Basic wywołań procedur właściwości.  
  
### <a name="to-store-a-value-in-a-property"></a>Do przechowywania wartości we właściwości  
  
1.  Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.  
  
     W poniższym przykładzie ustawiono wartość Visual Basic `TimeOfDay` właściwości południe niejawnie wywoływanie jej `Set` procedury.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.  
  
3.  Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty. Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.  
  
4.  Generowane po prawej stronie instrukcji przypisania wartość jest przechowywana we właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [Procedury właściwości](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)  
 [Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
