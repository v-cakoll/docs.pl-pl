---
title: Metody częściowe (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 765a667f18340c53909c3ff1e9fcc5f2ffc0f9bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837471"
---
# <a name="partial-methods-visual-basic"></a>Metody częściowe (Visual Basic)
Metody częściowe umożliwiają deweloperom Wstawianie niestandardowej logiki do kodu. Zazwyczaj ten kod jest częścią klasy wygenerowany przez projektanta. Metody częściowe są zdefiniowane w częściowej klasie, który jest tworzony przez generator kodu, a często są one używane do powiadomienie, że coś, co zostało zmienione. Umożliwiają one dla deweloperów określić zachowanie niestandardowe w odpowiedzi na zmiany.  
  
 Projektant generatora kodu definiuje tylko podpis metody i co najmniej jedno wywołanie do metody. Deweloperzy mogą udzielić im implementacji metody, jeśli chcesz dostosować zachowanie wygenerowanego kodu. Podczas wdrożenia nie zostanie podany, wywołania metody są usuwane przez kompilator, co spowoduje nie dodatkowe obciążenie.  
  
## <a name="declaration"></a>Deklaracja  
 Wygenerowany kod oznacza definicji metody częściowej poprzez umieszczenie słowa kluczowego `Partial` na początku wiersza podpisu.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Definicja musi spełniać następujące warunki:  
  
-   Metoda musi być `Sub`, a nie `Function`.  
  
-   Treść metody musi być puste.  
  
-   Modyfikator dostępu musi być `Private`.  
  
## <a name="implementation"></a>Implementacja  
 Implementacja składa się przede wszystkim wypełnianie w treści metody częściowej. Implementacja zwykle znajduje się w osobnej klasy częściowej z definicji i są zapisywane przez dewelopera, który chce rozszerzyć wygenerowanego kodu.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Poprzedni przykład duplikuje dokładnie podpisu w deklaracji, ale zmiany są możliwe. W szczególności innych modyfikatorów można dodać, takich jak `Overloads` lub `Overrides`. Tylko jeden `Overrides` modyfikator jest dozwolone. Aby uzyskać więcej informacji na temat metody Modyfikatory zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Zastosowanie  
 Wywołanie metody częściowej, jak każdy inny wywoływałby `Sub` procedury. Jeśli metoda został zaimplementowany, argumenty są obliczane i treści metody jest wykonywane. Należy jednak pamiętać, że implementacja metody częściowej jest opcjonalna. Jeśli metoda nie jest zaimplementowana, wywołanie go nie ma wpływu, a następnie przekazywane jako argumenty do metody wyrażeń nie są sprawdzane.  
  
## <a name="example"></a>Przykład  
 W pliku o nazwie Product.Designer.vb, zdefiniuj `Product` klasy, która ma `Quantity` właściwości.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 W pliku o nazwie Product.vb, należy podać implementacja dla `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Na koniec w metody Main projektu, należy zadeklarować `Product` wystąpienia i podaj wartość początkową dla jego `Quantity` właściwości.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Okno komunikatu powinny wyglądać, która wyświetla ten komunikat:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Zobacz także

- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sub, procedury](./sub-procedures.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Generowanie kodu w składniku LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Dodawanie logiki biznesowej przy użyciu metod częściowych](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
