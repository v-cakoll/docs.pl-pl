---
title: "Porady: tworzenie zmiennej, która nie zmienia wartości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Porady: tworzenie zmiennej, która nie zmienia wartości (Visual Basic)
Pojęcia zmienna, która nie zmienia jej wartość może się wydawać sprzeczne. Istnieją sytuacje, gdy stałej nie jest możliwe, ale warto mieć zmiennej z wartością stałą. W takim przypadku można zdefiniować zmienną członkowską z [tylko do odczytu](../../../../visual-basic/language-reference/modifiers/readonly.md) — słowo kluczowe.  
  
 Nie można użyć [instrukcja Const](../../../../visual-basic/language-reference/statements/const-statement.md) Aby zadeklarować i przypisać wartość stałą w następujących okolicznościach:  
  
-   `Const` Instrukcji nie akceptuje typu danych, którego chcesz użyć  
  
-   Nie wiadomo, wartość w czasie kompilacji  
  
-   Nie można obliczyć wartości stałej w czasie kompilacji  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Aby utworzyć zmienną, która nie zmienia wartości  
  
1.  Na poziomie modułu, należy zadeklarować zmienną członkowską z [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)i obejmują [tylko do odczytu](../../../../visual-basic/language-reference/modifiers/readonly.md) — słowo kluczowe.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Można określić `ReadOnly` tylko w zmiennej członkowskiej. Oznacza to, że należy zdefiniować zmiennej na poziomie modułu, poza dowolnej procedury.  
  
2.  Jeśli można obliczyć wartości w jednej instrukcji w czasie kompilacji, użyj klauzuli inicjowania w `Dim` instrukcji. Postępuj zgodnie z [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli znakiem równości (`=`), a następnie za pomocą wyrażenia. Upewnij się, że kompilator może służyć do oceny tego wyrażenia stałej wartości.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Można przypisać wartości do `ReadOnly` zmiennej tylko raz. Po wykonaniu żaden kod kiedykolwiek można zmienić jej wartość.  
  
     Jeśli nie znasz wartość w czasie kompilacji lub nie można obliczyć w czasie kompilacji w jednej instrukcji, można go przypisać w czasie wykonywania w konstruktorze. Aby to zrobić, należy zadeklarować `ReadOnly` zmiennej na poziomie klasy lub struktury. W Konstruktorze tej klasy lub struktury obliczania wartości ustalonej zmiennej i przypisz go do zmiennej przed powrotem z konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Const — instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)
