---
title: yield contextual — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712783"
---
# <a name="yield-c-reference"></a>yield (odwołanie w C#)

Korzystając z `yield` [kontekstowe słowo kluczowe](index.md#contextual-keywords) w instrukcji, należy wskazać, `get` że metoda, operator lub akcesor, w którym pojawia się jest iteratorem. Za `yield` pomocą do definiowania iterator eliminuje potrzebę jawne klasy dodatkowej (klasa, <xref:System.Collections.Generic.IEnumerator%601> która przechowuje stan dla <xref:System.Collections.IEnumerable> wyliczenia, zobacz na przykład) podczas implementowania i <xref:System.Collections.IEnumerator> wzorzec dla typu kolekcji niestandardowej.

W poniższym przykładzie przedstawiono `yield` dwie formy instrukcji.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Uwagi

Instrukcja `yield return` służy do zwracania każdego elementu po jednym naraz.

Sekwencja zwrócona z metody iteratora mogą być używane przy użyciu [foreach](foreach-in.md) instrukcji lub kwerendy LINQ. Każda iteracja `foreach` pętli wywołuje metodę iterator. Po `yield return` osiągnięciu instrukcji w metodzie iterator, `expression` jest zwracany, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Można użyć `yield break` instrukcji, aby zakończyć iterację.

Aby uzyskać więcej informacji na temat iteratorów, zobacz [Iterytory](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody iteratori i uzyskać akcesory

Deklaracja iteratora musi spełniać następujące wymagania:

- Typ powrotu <xref:System.Collections.IEnumerable>musi <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>być <xref:System.Collections.Generic.IEnumerator%601>, , , lub .

- Deklaracja nie może mieć żadnych [parametrów](in-parameter-modifier.md) [ref](ref.md) lub [out.](out-parameter-modifier.md)

Typ `yield` iterator, który <xref:System.Collections.IEnumerable> zwraca <xref:System.Collections.IEnumerator> `object`lub jest .  Jeśli iterator <xref:System.Collections.Generic.IEnumerable%601> zwraca <xref:System.Collections.Generic.IEnumerator%601>lub , musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego .

Nie można dołączyć `yield return` ani `yield break` oświadczenia w:

- [Wyrażenia Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).

- Metody, które zawierają bloki ze słowem kluczowym unsafe. Aby uzyskać więcej informacji, zobacz [niebezpieczne](unsafe.md).

## <a name="exception-handling"></a>Obsługa wyjątków

Instrukcji `yield return` nie można zlokalizować w bloku try-catch. Instrukcja `yield return` może znajdować się w bloku try instrukcji try-finally.

Instrukcja `yield break` może znajdować się w bloku try lub catch bloku, ale nie finally bloku.

Jeśli `foreach` treść (poza metody iterator) zgłasza wyjątek, `finally` blok w metodzie iteratorem jest wykonywany.

## <a name="technical-implementation"></a>Wdrożenie techniczne

Poniższy kod zwraca `IEnumerable<string>` z metody iterator, a następnie iteruje za pośrednictwem jego elementów.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Wywołanie `MyIteratorMethod` nie wykonuje treści metody. Zamiast tego wywołanie zwraca do `IEnumerable<string>` zmiennej. `elements`

W iteracji `foreach` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> metoda jest wywoływana `elements`dla . To wywołanie wykonuje `MyIteratorMethod` treść aż `yield return` do osiągnięcia następnej instrukcji. Wyrażenie zwracane przez `yield return` instrukcję określa nie tylko `element` wartość zmiennej do zużycia <xref:System.Collections.Generic.IEnumerator%601.Current%2A> przez `elements`treść pętli, ale także właściwość , która jest . `IEnumerable<string>`

Przy każdej kolejnej `foreach` iteracji pętli wykonanie treści iteratora jest kontynuowane od miejsca, w `yield return` którym zostało wyłączone, ponownie zatrzymując się, gdy osiągnie oświadczenie. Pętla `foreach` kończy się po osiągnięciu końca metody iterator lub `yield break` instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład ma `yield return` instrukcję, która `for` znajduje się wewnątrz pętli. Każda iteracja `foreach` treści instrukcji `Main` w metodzie tworzy `Power` wywołanie funkcji iterator. Każde wywołanie funkcji iterator przechodzi do następnego wykonania `yield return` instrukcji, która występuje podczas `for` następnej iteracji pętli.

Zwracany typ metody iteratorem jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratorego. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Przykład

W poniższym `get` przykładzie przedstawiono akcesor, który jest iteratorem. W przykładzie każda `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iteratory](../../iterators.md)
