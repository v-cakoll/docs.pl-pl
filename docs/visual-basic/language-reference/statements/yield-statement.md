---
title: "Yield — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bc2f5c2dca1fbd6039f10ddd6204673f60a679d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="yield-statement-visual-basic"></a>Yield — Instrukcja (Visual Basic)
Wysyła następnego elementu kolekcji do `For Each...Next` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagany. Wyrażenie, które jest umożliwiają niejawnej konwersji na typ funkcji iteracyjnej lub `Get` dostępu, który zawiera `Yield` instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 `Yield` Instrukcja zwraca jeden element w kolekcji w czasie. `Yield` Instrukcji znajduje się w funkcji iteracyjnej lub `Get` metody dostępu wykonać niestandardowe iteracji w kolekcji.  
  
 Korzystać z funkcji iteracyjnej przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md) lub zapytania LINQ. Każdej iteracji `For Each` pętli wywołuje funkcję iteratora. Gdy `Yield` instrukcji zostanie osiągnięta w funkcji iteracyjnej `expression` jest zwracany, i są przechowywane w bieżącej lokalizacji w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Niejawna konwersja musi istnieć z typu `expression` w `Yield` instrukcji, aby zwracany typ iteratora.  
  
 Można użyć `Exit Function` lub `Return` instrukcji, aby zakończyć iterację.  
  
 "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest on używany w `Iterator` funkcji lub `Get` dostępu.  
  
 Aby uzyskać więcej informacji o funkcje iteracyjne i `Get` metod dostępu, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Funkcje iteracyjne i metody dostępu Get  
 Deklaracja funkcji iteracyjnej lub `Get` akcesora musi spełniać następujące wymagania:  
  
-   Musi on zawierać [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modyfikator.  
  
-   Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Nie ma żadnych `ByRef` parametrów.  
  
 Funkcji iteracyjnej nie może wystąpić w zdarzenia, konstruktora wystąpienia, statycznego konstruktora lub destruktora statycznych.  
  
 Funkcji iteracyjnej można funkcji anonimowej. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 A `Yield` instrukcja może być wewnątrz `Try` zablokować z [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` bloku, który ma `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku.  
  
 A `Yield` instrukcja nie może być wewnątrz `Catch` bloku lub `Finally` bloku.  
  
 Jeśli `For Each` treści (poza funkcją iteratora) zgłasza wyjątek, `Catch` bloku w funkcji iteracyjnej nie została wykonana, ale `Finally` wykonaniu bloku w funkcji iteracyjnej. A `Catch` bloku wewnątrz funkcji iteracyjnej przechwytuje tylko wyjątki, które występuje wewnątrz funkcji iteracyjnej.  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Poniższy kod zwraca `IEnumerable (Of String)` z funkcji iteracyjnej, a następnie wykonuje iterację elementy `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Wywołanie `MyIteratorFunction` treści funkcji nie jest wykonywana. Zamiast tego wywołanie zwraca `IEnumerable(Of String)` do `elements` zmiennej.  
  
 Na iterację `For Each` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`. To wywołanie wykonuje treści `MyIteratorFunction` aż do następnego `Yield` osiągnięciu instrukcji. `Yield` Instrukcja zwraca wyrażenie określające nie tylko wartość `element` zmienna do użycia przez pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwości elementów, która jest `IEnumerable (Of String)`.  
  
 W każdej iteracji kolejnych `For Each` pętli, wykonanie treści iteratora kontynuuje działanie od miejsca przerwał, ponownie zatrzymywanie po osiągnięciu `Yield` instrukcji. `For Each` Pętli działanie jest kończone po zakończeniu funkcji iteracyjnej lub `Return` lub `Exit Function` osiągnięciu instrukcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. Każdej iteracji [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteracyjnej. Każde wywołanie funkcji iteracyjnej przechodzi do następnego wykonywanie `Yield` instrukcja, która występuje w ciągu następnej iteracji `For…Next` pętli.  
  
 Zwracany typ metody iteracyjnej jest <xref:System.Collections.Generic.IEnumerable%601>, typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `Get` dostępu, który jest iteratora. Deklaracja właściwości zawiera `Iterator` modyfikator.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Aby uzyskać dodatkowe przykłady, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../../../visual-basic/language-reference/statements/index.md)
