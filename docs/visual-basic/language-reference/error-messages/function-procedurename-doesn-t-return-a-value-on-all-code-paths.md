---
title: Funkcja „<procedurename>" nie zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 9782bb49a3327c6a8bd9938eca7cb3e899818784
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281063"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu
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
