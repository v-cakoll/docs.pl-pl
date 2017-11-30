---
title: 'Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
