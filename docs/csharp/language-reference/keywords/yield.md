---
title: zwraca kontekstowe słowo C# kluczowe — odwołanie
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712783"
---
# <a name="yield-c-reference"></a>yield (odwołanie w C#)

W przypadku korzystania z `yield` [kontekstowego słowa kluczowego](index.md#contextual-keywords) w instrukcji wskazuje, że metoda, operator lub akcesor `get`, w którym występuje, jest to iterator. Użycie `yield` do zdefiniowania iteratora eliminuje potrzebę jawnej dodatkowej klasy (klasy, która przechowuje stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> na przykład) podczas implementowania wzorca <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> dla niestandardowego typu kolekcji.

Poniższy przykład przedstawia dwie formy instrukcji `yield`.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Uwagi

Używasz instrukcji `yield return`, aby zwrócić każdy element po jednym naraz.

Sekwencja zwrócona przez metodę iteratora może być używana przy użyciu instrukcji [foreach](foreach-in.md) lub zapytania LINQ. Każda iteracja pętli `foreach` wywołuje metodę iteratora. Po osiągnięciu instrukcji `yield return` w metodzie iteratora jest zwracana `expression`, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Możesz użyć instrukcji `yield break`, aby zakończyć iterację.

Aby uzyskać więcej informacji na temat iteratorów [Iteratory](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody iteratorów i uzyskiwania dostępu

Deklaracja iteratora musi spełniać następujące wymagania:

- Typem zwracanym musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.

- Deklaracja nie może [zawierać żadnych parametrów](in-parameter-modifier.md) [ref](ref.md) ani [out](out-parameter-modifier.md) .

`yield` typ iteratora zwracającego <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`.  Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi istnieć niejawna konwersja z typu wyrażenia w instrukcji `yield return` do parametru typu ogólnego.

Nie można uwzględnić instrukcji `yield return` lub `yield break` w:

- [Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).

- Metody, które zawierają bloki ze słowem kluczowym unsafe. Aby uzyskać więcej informacji, [niebezpieczny](unsafe.md)

## <a name="exception-handling"></a>Obsługa wyjątków

Instrukcja `yield return` nie może znajdować się w bloku try-catch. Instrukcja `yield return` może znajdować się w bloku try instrukcji try-finally.

Instrukcja `yield break` może znajdować się w bloku try lub bloku catch, ale nie w bloku finally.

Jeśli treść `foreach` (poza metodą iteratora) zgłosi wyjątek, zostanie wykonany blok `finally` w metodzie iteratora.

## <a name="technical-implementation"></a>Implementacja techniczna

Poniższy kod zwraca `IEnumerable<string>` z metody iteratora, a następnie iteruje przez jego elementy.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Wywołanie `MyIteratorMethod` nie wykonuje treści metody. Zamiast tego wywołanie zwraca `IEnumerable<string>` do zmiennej `elements`.

W przypadku iteracji pętli `foreach` Metoda <xref:System.Collections.IEnumerator.MoveNext%2A> jest wywoływana dla `elements`. To wywołanie wykonuje treść `MyIteratorMethod` do momentu osiągnięcia następnej instrukcji `yield return`. Wyrażenie zwrócone przez instrukcję `yield return` określa nie tylko wartość zmiennej `element` do użycia przez treść pętli, ale również właściwość <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`, która jest `IEnumerable<string>`.

W każdej kolejnej iteracji pętli `foreach` wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `yield return`. Pętla `foreach` kończy się, gdy zostanie osiągnięty koniec metody iteratora lub instrukcji `yield break`.

## <a name="example"></a>Przykład

Poniższy przykład zawiera instrukcję `yield return`, która znajduje się wewnątrz pętli `for`. Każda iteracja treści instrukcji `foreach` w metodzie `Main` tworzy wywołanie funkcji iteratora `Power`. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania instrukcji `yield return`, która występuje w następnej iteracji pętli `for`.

Zwracany typ metody iteratora to <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład demonstruje metodę dostępu `get`, która jest iteratorem. W przykładzie każda instrukcja `yield return` zwraca wystąpienie klasy zdefiniowanej przez użytkownika.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iteratory](../../iterators.md)
