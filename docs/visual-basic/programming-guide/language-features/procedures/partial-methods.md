---
title: "Metody częściowe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 975a86e33eb5744f94cd58efb227bf52eb07c1e8
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="partial-methods-visual-basic"></a>Metody częściowe (Visual Basic)
Metody częściowe umożliwiają deweloperom Wstawianie niestandardowej logiki do kodu. Zazwyczaj kod jest częścią klasy wygenerowany przez projektanta. Metody częściowe są zdefiniowane w klasie częściowej utworzonego przez generator kodu, a często są one używane do o tym, że element został zmieniony. Umożliwiają one developer do określania zachowania niestandardowego w odpowiedzi na zmianę.  
  
 Projektant generatora kodu definiuje tylko podpis metody i co najmniej jednego wywołania metody. Deweloperzy mogą udzielić im implementacji metody, jeśli chcesz dostosować zachowanie wygenerowanego kodu. Gdy implementacja nie została podana, wywołania metody zostaną usunięte przez kompilator, co powoduje nie dodatkowe obciążenie.  
  
## <a name="declaration"></a>Deklaracja  
 Wygenerowany kod oznacza definicję metody częściowej przez umieszczenie kluczowego `Partial` na początku wiersza podpisu.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Definicja musi spełniać następujące warunki:  
  
-   Metoda musi być `Sub`, a nie `Function`.  
  
-   Treść metody muszą być puste.  
  
-   Modyfikator dostępu musi być `Private`.  
  
## <a name="implementation"></a>Implementacja  
 Implementacja obejmuje głównie wypełnianie w treści metody częściowej. Implementacja zazwyczaj znajduje się w osobnej częściowej klasy z definicji i są zapisywane przez deweloperów, którzy chcą rozszerzyć wygenerowanego kodu.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Poprzedni przykład duplikatów podpisie w deklaracji dokładnie, ale zmiany są możliwe. W szczególności innych modyfikatorów można dodawać, takich jak `Overloads` lub `Overrides`. Tylko jeden `Overrides` modyfikator jest dozwolone. Aby uzyskać więcej informacji na temat Modyfikatory metody, zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Zastosowanie  
 Wywołanie metody częściowej, jak można wywołać żadnej innej `Sub` procedury. Jeśli zaimplementowano metody argumenty są oceniane i wykonaniu treści metody. Należy jednak pamiętać, że metoda częściowa implementacja jest opcjonalna. Jeśli metoda nie jest zaimplementowana, wywołanie jej nie ma wpływu, a nie są oceniane wyrażenia przekazywane jako argumenty do metody.  
  
## <a name="example"></a>Przykład  
 W pliku o nazwie Product.Designer.vb, zdefiniuj `Product` klasy, która ma `Quantity` właściwości.  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 W pliku o nazwie Product.vb zapewniać implementację dla `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Ponadto w metody Main projektu, należy zadeklarować `Product` wystąpienia i podaj wartość początkową dla jego `Quantity` właściwości.  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Okno komunikatu powinno się, że wyświetla ten komunikat:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Zobacz też  
 [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Sub — procedury](./sub-procedures.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Częściowe](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Generowanie kodu w składniku LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Dodawanie logiki biznesowej przy użyciu metody częściowe](../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
