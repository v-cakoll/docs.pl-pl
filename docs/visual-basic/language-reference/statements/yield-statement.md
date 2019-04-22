---
title: Yield — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: fea91731694f18625e43c5545b353851e72234a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821091"
---
# <a name="yield-statement-visual-basic"></a>Yield — Instrukcja (Visual Basic)
Wysyła następnego elementu kolekcji do `For Each...Next` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a>Parametry  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagana. Wyrażenie, które jest niejawnie konwertowany na typ funkcji iteratora lub `Get` dostępu, który zawiera `Yield` instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 `Yield` Instrukcja zwraca jeden element kolekcji naraz. `Yield` Instrukcja znajduje się w funkcji iteratora lub `Get` akcesora wykonywania niestandardowych iteracji przez kolekcję.  
  
 Korzystać z funkcji iteratora przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md) lub kwerendę LINQ. Każda iteracja `For Each` pętli wywołuje funkcję iteratora. Gdy `Yield` w funkcji iteratora osiągnięta zostanie instrukcja `expression` jest zwracany, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Musi istnieć niejawna konwersja typu `expression` w `Yield` instrukcję, aby zwracany typ iteratora.  
  
 Możesz użyć `Exit Function` lub `Return` instrukcję, aby zakończyć iterację.  
  
 "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest on używany w `Iterator` funkcji lub `Get` metody dostępu.  
  
 Aby uzyskać więcej informacji na temat funkcji iteratora i `Get` metod dostępu, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Iterator funkcje i metody dostępu Get  
 Deklaracja funkcji iteratora lub `Get` metody dostępu muszą spełniać następujące wymagania:  
  
-   Musi on zawierać [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md) modyfikator.  
  
-   Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Nie może zawierać żadnych `ByRef` parametrów.  
  
 Funkcji iteratora nie może wystąpić w zdarzeń, konstruktora wystąpienia, statyczny Konstruktor lub destruktor statyczne.  
  
 Funkcji iteratora, może być funkcją anonimową. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 A `Yield` instrukcji może znajdować się wewnątrz `Try` bloku [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` blok, który ma `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku.  
  
 A `Yield` instrukcja nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.  
  
 Jeśli `For Each` treści (poza funkcji iteratora) zgłasza wyjątek, `Catch` nie jest wykonywany blok w funkcji iteratora, ale `Finally` wykonaniu bloku w funkcji iteratora. A `Catch` bloku sterującego funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Poniższy kod zwraca `IEnumerable (Of String)` z funkcji iteratora i następnie iterację przez elementy `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Wywołanie `MyIteratorFunction` nie jest wykonywany treści funkcji. Zamiast tego to wywołanie zwraca `IEnumerable(Of String)` do `elements` zmiennej.  
  
 Podczas iteracji `For Each` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`. To wywołanie wykonuje treść `MyIteratorFunction` aż do następnej `Yield` osiągnięta zostanie instrukcja. `Yield` Instrukcja zwraca wyrażenie, które określa nie tylko wartość `element` do użycia w treści pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwości elementów, która jest `IEnumerable (Of String)`.  
  
 Na poszczególnych kolejnych iteracjach `For Each` pętli, wykonywanie treści iteratora jest kontynuowane od miejsca zostało przerwane, zatrzymywane ponownie po osiągnięciu `Yield` instrukcji. `For Each` Pętli działanie jest kończone po zakończeniu funkcji iteratora lub `Return` lub `Exit Function` osiągnięta zostanie instrukcja.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. Każda iteracja [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcję, która występuje w ciągu następnej iteracji `For…Next` pętli.  
  
 Zwracany typ metody iteratora jest <xref:System.Collections.Generic.IEnumerable%601>, typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `Get` metodę dostępu, która jest iteratorem. Deklaracja właściwości zawiera `Iterator` modyfikator.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje](../../../visual-basic/language-reference/statements/index.md)
