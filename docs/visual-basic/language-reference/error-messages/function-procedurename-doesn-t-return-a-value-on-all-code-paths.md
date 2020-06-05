---
title: Funkcja „<procedurename>" nie zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: edb2195f4e83c2315aa929936aff8af88ca8556c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374138"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>Funkcja „\<procedurename>" nie zwraca wartości we wszystkich ścieżkach kodu
Funkcja " \<procedurename> " nie zwraca wartości we wszystkich ścieżkach kodu. Czy brakuje instrukcji "return"?  
  
 `Function`Procedura zawiera co najmniej jedną możliwą ścieżkę za pomocą kodu, który nie zwraca wartości.  
  
 Można zwrócić wartość z `Function` procedury w dowolny z następujących sposobów:  
  
- Dołącz wartość do [instrukcji return](../statements/return-statement.md).  
  
- Przypisz wartość do `Function` nazwy procedury, a następnie wykonaj `Exit Function` instrukcję.  
  
- Przypisz wartość do `Function` nazwy procedury, a następnie wykonaj `End Function` instrukcję.  
  
 Jeśli kontrola przechodzi do `Exit Function` lub `End Function` i nie przypisano żadnej wartości do nazwy procedury, procedura zwraca wartość domyślną zwracanego typu danych. Aby uzyskać więcej informacji, zobacz "zachowanie" w [instrukcji funkcji](../statements/function-statement.md).  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42105  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Sprawdź logikę przepływu sterowania i upewnij się, że przypiszesz wartość przed każdą instrukcją, która powoduje zwrócenie.  
  
     Łatwiej jest zagwarantować, że każde zwrócenie z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji. Jeśli to zrobisz, ostatnią instrukcją przed `End Function` powinien być `Return` instrukcja.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury funkcji](../../programming-guide/language-features/procedures/function-procedures.md)
- [Function, instrukcja](../statements/function-statement.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
