---
title: Yield kontekstowego słowa kluczowego — odwołanie w C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: d3fe4cf92ca17457bd541f092f5d146ba6c1c095
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794419"
---
# <a name="yield-c-reference"></a>yield (odwołanie w C#)

W przypadku użycia `yield` [kontekstowego słowa kluczowego](index.md#contextual-keywords) w instrukcji wskazuje, że metoda, operator lub akcesor, `get` w którym występuje, jest iteratorem. Użycie `yield` do zdefiniowania iteratora eliminuje potrzebę jawnej dodatkowej klasy (klasy, która przechowuje stan wyliczenia, zobacz <xref:System.Collections.Generic.IEnumerator%601> na przykład) podczas implementowania <xref:System.Collections.IEnumerable> <xref:System.Collections.IEnumerator> wzorca i dla niestandardowego typu kolekcji.

Poniższy przykład pokazuje dwie formy `yield` instrukcji.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Uwagi

Używasz instrukcji, `yield return` Aby zwrócić każdy element po jednym naraz.

Sekwencja zwrócona przez metodę iteratora może być używana przy użyciu instrukcji [foreach](foreach-in.md) lub zapytania LINQ. Każda iteracja `foreach` pętli wywołuje metodę iteratora. Gdy `yield return` instrukcja zostanie osiągnięta w metodzie iteratora, `expression` jest zwracana, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Możesz użyć instrukcji, `yield break` Aby zakończyć iterację.

Aby uzyskać więcej informacji na temat iteratorów, zobacz [Iteratory](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody iteratorów i uzyskiwania dostępu

Deklaracja iteratora musi spełniać następujące wymagania:

- Typem zwracanym musi być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> ,, <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> .

- Deklaracja nie może [zawierać żadnych parametrów](in-parameter-modifier.md) [ref](ref.md) ani [out](out-parameter-modifier.md) .

`yield`Typ iteratora, który zwraca <xref:System.Collections.IEnumerable> lub <xref:System.Collections.IEnumerator> jest `object` .  Jeśli iterator zwraca <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerator%601> , musi istnieć niejawna konwersja z typu wyrażenia w `yield return` instrukcji do parametru typu ogólnego.

Nie można uwzględnić `yield return` instrukcji or `yield break` w:

- [Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) i [metody anonimowe](../operators/delegate-operator.md).

- Metody, które zawierają bloki ze słowem kluczowym unsafe. Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny](unsafe.md).

## <a name="exception-handling"></a>Obsługa wyjątków

`yield return`Instrukcja nie może znajdować się w bloku try-catch. `yield return`Instrukcja może znajdować się w bloku try instrukcji try-finally.

`yield break`Instrukcja może znajdować się w bloku try lub bloku catch, ale nie w bloku finally.

Jeśli `foreach` treść (poza metodą iteratora) zgłasza wyjątek, `finally` zostaje wykonany blok w metodzie iteratora.

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

W iteracji `foreach` pętli <xref:System.Collections.IEnumerator.MoveNext%2A> Metoda jest wywoływana dla `elements` . To wywołanie wykonuje treść `MyIteratorMethod` przed `yield return` osiągnięciem następnej instrukcji. Wyrażenie zwrócone przez `yield return` instrukcję określa nie tylko wartość `element` zmiennej do użycia przez treść pętli, ale również <xref:System.Collections.Generic.IEnumerator%601.Current%2A> Właściwość `elements` , która jest `IEnumerable<string>` .

W każdej kolejnej iteracji `foreach` pętli wykonywanie treści iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `yield return` instrukcji. `foreach`Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora lub `yield break` instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład zawiera `yield return` instrukcję, która znajduje się wewnątrz `for` pętli. Każda iteracja `foreach` treści instrukcji w `Main` metodzie tworzy wywołanie `Power` funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `yield return` instrukcji, która występuje w następnej iteracji `for` pętli.

Zwracanym typem metody iteratora jest <xref:System.Collections.IEnumerable> , który jest typem interfejsu iteratora. Kiedy metoda iteratora jest wywoływana, zwraca obiekt wyliczeniowy, który zawiera potęgi liczb.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje `get` metodę dostępu, która jest iteratorem. W przykładzie każda `yield return` instrukcja zwraca wystąpienie klasy zdefiniowanej przez użytkownika.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iteratory](../../iterators.md)
