---
title: zwraca kontekstowe słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: 0d2c3f67715b9b2161a6c908576ac9f964ff13d6
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363128"
---
# <a name="yield-c-reference"></a>yield (odwołanie w C#)

W przypadku użycia `yield` [kontekstowego słowa kluczowego](index.md#contextual-keywords) w instrukcji wskazuje, że metoda, operator lub `get` akcesor, w którym występuje, jest iteratorem. Użycie `yield` do zdefiniowania iteratora eliminuje potrzebę jawnej dodatkowej klasy (klasy, która przechowuje stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> na przykład <xref:System.Collections.IEnumerable> ) podczas implementowania wzorca i <xref:System.Collections.IEnumerator> dla kolekcji niestandardowej Wprowadź.

Poniższy przykład pokazuje dwie formy `yield` instrukcji.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Uwagi

`yield return` Używasz instrukcji, aby zwrócić każdy element po jednym naraz.

Sekwencja zwrócona przez metodę iteratora może być używana przy użyciu instrukcji [foreach](foreach-in.md) lub zapytania LINQ. Każda iteracja `foreach` pętli wywołuje metodę iteratora. Gdy instrukcja zostanie osiągnięta w metodzie iteratora `expression` , jest zwracana, a bieżąca lokalizacja w kodzie jest zachowywana. `yield return` Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Możesz użyć `yield break` instrukcji, aby zakończyć iterację.

Aby uzyskać więcej informacji na temat iteratorów [](../../iterators.md), zobacz Iteratory.

## <a name="iterator-methods-and-get-accessors"></a>Metody iteratorów i uzyskiwania dostępu

Deklaracja iteratora musi spełniać następujące wymagania:

- Typem zwracanym musi być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.

- Deklaracja nie może [zawierać żadnych parametrów](in-parameter-modifier.md) [ref](ref.md) ani [out](out-parameter-modifier.md) .

Typ iteratora, który zwraca <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object`. `yield`  Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601>, musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego.

Nie można uwzględnić `yield return` instrukcji or `yield break` w:

- [Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).

- Metody, które zawierają bloki ze słowem kluczowym unsafe. Aby uzyskać więcej informacji, [](unsafe.md)Zobacz artykuł niebezpieczny.

## <a name="exception-handling"></a>Obsługa wyjątków

`yield return` Instrukcja nie może znajdować się w bloku try-catch. `yield return` Instrukcja może znajdować się w bloku try instrukcji try-finally.

`yield break` Instrukcja może znajdować się w bloku try lub bloku catch, ale nie w bloku finally.

Jeśli treść (poza metodą iteratora) zgłasza wyjątek `finally` , zostaje wykonany blok w metodzie iteratora. `foreach`

## <a name="technical-implementation"></a>Implementacja techniczna

Poniższy kod zwraca `IEnumerable<string>` metodę z metody iteratora, a następnie wykonuje iterację za pośrednictwem jej elementów.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Wywołanie `MyIteratorMethod` nie wykonuje treści metody. Zamiast tego wywołanie zwraca `IEnumerable<string>` `elements` zmienną.

W iteracji `foreach` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> Metoda jest wywoływana dla `elements`. To wywołanie wykonuje treść `MyIteratorMethod` przed osiągnięciem następnej `yield return` instrukcji. Wyrażenie zwrócone `yield return` przez instrukcję określa nie tylko wartość <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `element` zmiennej do użycia przez treść pętli `elements`, ale również właściwość, która jest `IEnumerable<string>`.

W każdej kolejnej iteracji `foreach` pętli wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po `yield return` osiągnięciu instrukcji. Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora `yield break` lub instrukcji. `foreach`

## <a name="example"></a>Przykład

Poniższy przykład zawiera `yield return` instrukcję, która znajduje się `for` wewnątrz pętli. Każda iteracja `foreach` treści instrukcji `Main` w metodzie `Power` tworzy wywołanie funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `yield return` instrukcji, która występuje w następnej iteracji `for` pętli.

Zwracanym typem metody iteratora jest <xref:System.Collections.IEnumerable>, który jest typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje `get` metodę dostępu, która jest iteratorem. W przykładzie każda `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iteratory](../../iterators.md)
