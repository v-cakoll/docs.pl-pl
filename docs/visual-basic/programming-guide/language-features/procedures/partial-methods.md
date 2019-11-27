---
title: Metody częściowe
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
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352633"
---
# <a name="partial-methods-visual-basic"></a>Metody częściowe (Visual Basic)
Metody częściowe umożliwiają deweloperom Wstawianie niestandardowych logiki do kodu. Zazwyczaj kod jest częścią klasy generowanej przez projektanta. Metody częściowe są zdefiniowane w klasie częściowej, która jest tworzona przez generator kodu i często są używane do dostarczania powiadomienia, że coś uległo zmianie. Umożliwiają deweloperowi określenie zachowania niestandardowego w reakcji na zmianę.  
  
 Projektant generatora kodu definiuje tylko sygnaturę metody i jedno lub więcej wywołań metody. Deweloperzy mogą następnie podać implementacje dla metody, jeśli chcą dostosować zachowanie wygenerowanego kodu. Gdy implementacja nie zostanie dostarczona, wywołania metody są usuwane przez kompilator, co spowodowało brak dodatkowych obciążeń związanych z wydajnością.  
  
## <a name="declaration"></a>Oświadczeń  
 Wygenerowany kod oznacza definicję metody częściowej poprzez umieszczenie słowa kluczowego `Partial` na początku wiersza podpisu.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Definicja musi spełniać następujące warunki:  
  
- Metoda musi być `Sub`, a nie `Function`.  
  
- Treść metody musi pozostać pusta.  
  
- Modyfikator dostępu musi być `Private`.  
  
## <a name="implementation"></a>Implementacja  
 Implementacja składa się głównie z wypełniania treści metody częściowej. Implementacja zazwyczaj należy do oddzielnej klasy częściowej z definicji i jest zapisywana przez dewelopera, który chce zwiększyć wygenerowany kod.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Poprzedni przykład duplikuje sygnaturę w deklaracji dokładnie, ale możliwe jest zróżnicowanie. W szczególności można dodać inne modyfikatory, takie jak `Overloads` lub `Overrides`. Dozwolony jest tylko jeden modyfikator `Overrides`. Aby uzyskać więcej informacji na temat modyfikatorów metod, zobacz [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Zastosowanie  
 Metodę częściową należy wywołać, ponieważ wywołamy dowolną inną procedurę `Sub`. Jeśli metoda została zaimplementowana, argumenty są oceniane i jest wykonywana treść metody. Należy jednak pamiętać, że implementacja metody częściowej jest opcjonalna. Jeśli metoda nie jest zaimplementowana, wywołanie jej nie ma żadnego wpływu, a wyrażenia przekazane jako argumenty metody nie są oceniane.  
  
## <a name="example"></a>Przykład  
 W pliku o nazwie Product. Designer. vb Zdefiniuj klasę `Product`, która ma właściwość `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 W pliku o nazwie Product. vb wprowadź implementację `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Na koniec w głównej metodzie projektu Zadeklaruj wystąpienie `Product` i podaj wartość początkową dla swojej właściwości `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Zostanie wyświetlone okno komunikatu z komunikatem:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Zobacz także

- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sub, procedury](./sub-procedures.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Generowanie kodu w składniku LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Dodawanie logiki biznesowej przy użyciu metod częściowych](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
