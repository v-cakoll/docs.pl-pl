---
title: 'Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bfda451cefff699561253910715d8450414b00ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650871"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)
Wartości są przechowywane w zmiennej ustawiając nazwę zmiennej po lewej stronie instrukcji przypisania.  
  
## <a name="putting-data-in-a-variable"></a>Wprowadzanie danych w zmiennej  
  
#### <a name="to-store-a-value-in-a-variable"></a>Do przechowywania wartości w zmiennej  
  
-   Po lewej stronie instrukcji przypisania, użyj nazwy zmiennej.  
  
     W poniższym przykładzie ustawiono wartość zmiennej `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     Wartość generowane po prawej stronie instrukcji przypisania jest przechowywana w zmiennej.  
  
## <a name="getting-data-from-a-variable"></a>Pobieranie danych ze zmienną  
 Możesz pobrać wartość zmiennej, łącznie z nazwą zmiennej w wyrażeniu.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Aby pobrać wartość zmiennej  
  
-   Użyj nazwy zmiennej w wyrażeniu. Można użyć zmiennej dowolnym służy stałą lub literałem, z wyjątkiem w wyrażeniu, który definiuje wartość stałą.  
  
     —lub—  
  
-   Użyj nazwy zmiennej po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
     Poniższy przykład odczytuje wartość zmiennej `startValue` , a następnie używa wartości zmiennej `counter` w wyrażeniu.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     Wartość zmiennej uczestniczy w wyrażeniu, tak jak będzie stałą, a następnie jest ona przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
