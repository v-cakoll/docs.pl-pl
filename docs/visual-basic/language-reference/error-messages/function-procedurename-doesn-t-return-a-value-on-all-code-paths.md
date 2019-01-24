---
title: Funkcja &#39; &lt;nazwaprocedury&gt; &#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: b6cc5143aafb6c2554b183a1fc5fb3b1331ec5d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552193"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Funkcja &#39; &lt;nazwaprocedury&gt; &#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu
Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu. Czy nie brakuje instrukcji "Return"?  
  
 A `Function` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kodu, która nie zwraca wartości.  
  
 Może zwracać wartość z zakresu od `Function` procedury w dowolnym z następujących sposobów:  
  
-   Zawiera wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Przypisz wartość do `Function` procedury nazwę, a następnie wykonaj `Exit Function` instrukcji.  
  
-   Przypisz wartość do `Function` procedury nazwę, a następnie wykonaj `End Function` instrukcji.  
  
 Jeśli kontrola przechodzi do `Exit Function` lub `End Function` i nie przypisano żadnej wartości do nazwy procedury, procedura zwraca wartość domyślną typu danych zwrotnych. Aby uzyskać więcej informacji, zobacz "Zachowanie" w [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42105  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź logikę przepływu sterowania i upewnij się, że przypisanie wartości przed każdej instrukcji, który powoduje, że wynik.  
  
     Ułatwia to zagwarantować, każdy zwracany z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji. Jeśli to zrobisz, ostatnią instrukcję przed `End Function` powinien być `Return` instrukcji.  
  
## <a name="see-also"></a>Zobacz także
- [Procedury funkcji](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
