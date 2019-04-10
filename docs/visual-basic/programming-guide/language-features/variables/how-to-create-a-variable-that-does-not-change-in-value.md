---
title: 'Instrukcje: Tworzenie zmiennej, która nie zmienia wartości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 7180e5141572d219ed02c57103e9d4b80cde536e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342937"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Instrukcje: Tworzenie zmiennej, która nie zmienia wartości (Visual Basic)
Pojęcie zmienną, która nie zmienia jej wartość może się wydawać sprzeczne. Istnieją sytuacje, gdy stała nie jest możliwe, ale warto mieć zmienną o stałej wartości. W takim przypadku można zdefiniować zmienną składową za pomocą [tylko do odczytu](../../../../visual-basic/language-reference/modifiers/readonly.md) — słowo kluczowe.  
  
 Nie można użyć [instrukcja Const](../../../../visual-basic/language-reference/statements/const-statement.md) zadeklarować i przypisać wartości stałej w następujących okolicznościach:  
  
-   `Const` Instrukcji nie akceptuje typu danych, którego chcesz użyć  
  
-   Nie wiadomo, wartość w czasie kompilacji  
  
-   Nie można obliczyć wartości stałej w czasie kompilacji  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Aby utworzyć zmienną, która nie zmienia wartości  
  
1. Na poziomie modułu, należy zadeklarować zmienną składową za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)i obejmują [tylko do odczytu](../../../../visual-basic/language-reference/modifiers/readonly.md) — słowo kluczowe.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Można określić `ReadOnly` tylko w zmiennej składowej. Oznacza to, że trzeba zdefiniować zmienną na poziomie modułu, poza dowolnej procedury.  
  
2. Jeśli można obliczyć wartości w pojedynczej instrukcji w czasie kompilacji, należy użyć w klauzuli inicjowania `Dim` instrukcji. Postępuj zgodnie z [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli znakiem równości (`=`), a następnie przez wyrażenie. Upewnij się, że kompilator może ocenić tego wyrażenia stałej wartości.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Można przypisać wartości do `ReadOnly` zmiennej tylko raz. Po wykonaniu tej czynności żaden kod nigdy nie można zmienić jego wartość.  
  
     Jeśli nie znasz wartości w czasie kompilacji lub nie można obliczyć w czasie kompilacji w pojedynczej instrukcji, można je przypisać w czasie wykonywania w konstruktorze. Aby to zrobić, należy zadeklarować `ReadOnly` zmiennej na poziomie klasy lub struktury. W Konstruktorze tej klasy lub struktury obliczenia stałą wartość zmiennej, a następnie przypisać ją do zmiennej przed zwróceniem z konstruktora.  
  
## <a name="see-also"></a>Zobacz także

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const — Instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)
