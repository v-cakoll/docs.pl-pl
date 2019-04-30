---
title: 'Instrukcje: Przenoszenie danych do i z zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756601"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Instrukcje: Przenoszenie danych do i z zmiennej (Visual Basic)
Wartość jest przechowywana w zmiennej, umieszczając nazwę zmiennej po lewej stronie instrukcji przypisania.  
  
## <a name="putting-data-in-a-variable"></a>Umieszczenie danych w zmiennej  
  
#### <a name="to-store-a-value-in-a-variable"></a>Do przechowywania wartości w zmiennej  
  
- Użyj nazwy zmiennej po lewej stronie instrukcji przypisania.  
  
     W poniższym przykładzie ustawiono wartość zmiennej `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     Wartość generowane po prawej stronie instrukcji przypisania są przechowywane w zmiennej.  
  
## <a name="getting-data-from-a-variable"></a>Pobieranie danych ze zmiennej  
 Aby uzyskać wartość zmiennej, łącznie z nazwą zmiennej w wyrażeniu.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Aby pobrać wartość ze zmiennej  
  
- Użyj nazwy zmiennej w wyrażeniu. Można użyć zmiennej dowolnego miejsca umożliwia stałą lub literałem, z wyjątkiem w wyrażeniu, który definiuje wartość stałą.  
  
     —lub—  
  
- Użyj nazwy zmiennej po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość zmiennej `startValue` , a następnie używa wartości zmiennej `counter` w wyrażeniu.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     Wartość zmiennej uczestniczy w wyrażeniu, tak jak będzie stałą, a następnie jest on przechowywany w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
