---
title: yield (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c566e2c83a6c40acfd85c1822d28cbaa097e4449
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388169"
---
# <a name="yield-c-reference"></a>yield (odwołanie w C#)
Kiedy używasz `yield` — słowo kluczowe w instrukcji powoduje wskazanie metody, operatora lub `get` dostępu, w której występuje jest iteratorem. Za pomocą `yield` do zdefiniowania iteratora eliminuje konieczność jawnego użycia dodatkowej klasy (klasy przechowującej stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> przykład) podczas implementacji <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> wzorca dla kolekcji niestandardowej Typ.  
  
 W poniższym przykładzie pokazano dwa rodzaje `yield` instrukcji.  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `yield return` instrukcja zwraca każdy element w danym momencie.  
  
 Korzystanie z metody iteratora przy użyciu [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub zapytania LINQ. Każda iteracja `foreach` pętli wywołuje metodę iteratora. Gdy `yield return` osiągnięciu instrukcji w metodzie iteratora `expression` jest zwracany, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Możesz użyć `yield break` instrukcję, aby zakończyć iterację.  
  
 Aby uzyskać więcej informacji dotyczących iteratorów, zobacz [Iteratory](../../iterators.md).  
  
## <a name="iterator-methods-and-get-accessors"></a>Metody iteratorów i pobranie akcesora  
 Deklaracja iteratora musi spełniać następujące wymagania:  
  
-   Zwracany typ musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Deklaracja nie może zawierać żadnych [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów.  
  
 `yield` Typ iteratora zwracającego <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`.  Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcję, aby parametr typu ogólnego.  
  
 Nie można uwzględnić `yield return` lub `yield break` instrukcji w metodach mających następujące cechy:  
  
-   Metody anonimowe. Aby uzyskać więcej informacji, zobacz [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
-   Metody, które zawierają bloki ze słowem kluczowym unsafe. Aby uzyskać więcej informacji, zobacz [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 A `yield return` instrukcja nie może znajdować się w bloku try-catch. A `yield return` instrukcji może znajdować się w bloku try instrukcji try-finally.  
  
 A `yield break` instrukcji może znajdować się w bloku try lub bloku catch, ale nie bloku finally.  
  
 Jeśli `foreach` treści (poza metodą iteratora) zgłasza wyjątek, `finally` blokowanie w metodzie iteratora jest wykonywany.  
  
## <a name="technical-implementation"></a>Realizacja techniczna  
 Poniższy kod zwraca `IEnumerable<string>` z metody iteratora i następnie iterację przez jego elementów.  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 Wywołanie `MyIteratorMethod` treści metody nie jest wykonywany. Zamiast tego to wywołanie zwraca `IEnumerable<string>` do `elements` zmiennej.  
  
 Podczas iteracji `foreach` pętli, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana dla `elements`. To wywołanie wykonuje treść `MyIteratorMethod` aż do następnej `yield return` osiągnięta zostanie instrukcja. Wyrażenie zwracane przez `yield return` Instrukcja określa nie tylko wartość `element` do użycia w treści pętli, ale także <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwość `elements`, czyli `IEnumerable<string>`.  
  
 Na poszczególnych kolejnych iteracjach `foreach` pętli, wykonywanie treści iteratora jest kontynuowane od miejsca zostało przerwane, zatrzymywane ponownie po osiągnięciu `yield return` instrukcji. `foreach` Pętli jest ukończone Kiedy koniec metody iteratora lub `yield break` osiągnięta zostanie instrukcja.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `yield return` instrukcji, która znajduje się wewnątrz `for` pętli. Każda iteracja `foreach` treść instrukcji w `Main` metoda tworzy wywołanie `Power` funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `yield return` instrukcję, która występuje w ciągu następnej iteracji `for` pętli.  
  
 Zwracany typ metody iteratora jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `get` metodę dostępu, która jest iteratorem. W tym przykładzie każdy `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
- [Iteratory](../../iterators.md)
