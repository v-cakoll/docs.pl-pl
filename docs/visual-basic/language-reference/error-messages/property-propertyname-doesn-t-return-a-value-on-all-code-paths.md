---
title: Właściwość „<propertyname>” nie zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: a535a6b951dc9872109527f78d7de5f3fcdd3292
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821884"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu
Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu. Może wystąpić wyjątek pustej referencji, w czasie wykonywania, gdy zostanie użyty wynik.  
  
 Właściwość `Get` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kodu, która nie zwraca wartości.  
  
 Może zwracać wartość z właściwością `Get` procedury w dowolnym z następujących sposobów:  
  
-   Przypisz wartości do danej nazwy właściwości, a następnie wykonaj `Exit Property` instrukcji.  
  
-   Przypisz wartości do danej nazwy właściwości, a następnie wykonaj `End Get` instrukcji.  
  
-   Zawiera wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Jeśli kontrola przechodzi do `Exit Property` lub `End Get` i nie przypisano żadnej wartości Nazwa właściwości `Get` procedura zwraca wartość domyślną typu danych właściwości. Aby uzyskać więcej informacji, zobacz 'Zachowanie' w [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42107  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź logikę przepływu sterowania i upewnij się, że przypisanie wartości przed każdej instrukcji, który powoduje, że wynik.  
  
     Ułatwia to zagwarantować, każdy zwracany z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji. Jeśli to zrobisz, ostatnią instrukcję przed `End Get` powinien być `Return` instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
