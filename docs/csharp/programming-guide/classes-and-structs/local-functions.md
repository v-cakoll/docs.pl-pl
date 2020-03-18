---
title: Funkcje lokalne - Przewodnik programowania C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170238"
---
# <a name="local-functions-c-programming-guide"></a>Funkcje lokalne (Przewodnik programowania C#)

Począwszy od języka C# 7.0, C# obsługuje *funkcje lokalne*. Funkcje lokalne są metodami prywatnymi typu, które są zagnieżdżone w innym etece. Można je wywołać tylko z ich zawierającego członka. Funkcje lokalne mogą być deklarowane i wywoływane z:

- Metody, zwłaszcza metody iteratori i metody asynchroniczne
- Konstruktorów
- Akcesory
- Akcesory zdarzeń
- Metody anonimowe
- Wyrażenia lambda
- Finalizatory
- Inne funkcje lokalne

Jednak nie można zadeklarować funkcji lokalnych wewnątrz elementu członkowskiego zabudowanego wyrażeniem.

> [!NOTE]
> W niektórych przypadkach można użyć wyrażenia lambda do zaimplementowania funkcji również obsługiwane przez funkcję lokalną. Aby uzyskać porównanie, zobacz [Funkcje lokalne w porównaniu z wyrażeniami Lambda](../../local-functions-vs-lambdas.md).

Funkcje lokalne sprawiają, że intencja kodu jest wyczyszczona. Każdy, kto czyta kod, może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej. W przypadku projektów zespołowych uniemożliwiają one również innemu deweloperowi omyłkowo wywołanie metody bezpośrednio z innego miejsca w klasie lub strukturze.

## <a name="local-function-syntax"></a>Składnia funkcji lokalnej

Funkcja lokalna jest zdefiniowana jako zagnieżdżona metoda wewnątrz elementu członkowskiego zawierającego. Jego definicja ma następującą składnię:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Funkcje lokalne mogą używać [modyfikatorów asynchronicznych](../../language-reference/keywords/async.md) i [niebezpiecznych.](../../language-reference/keywords/unsafe.md)

Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w dołączanym elementem członkowskim, w tym jego parametry metody, są dostępne w funkcji lokalnej.

W przeciwieństwie do definicji metody definicja funkcji lokalnej nie może zawierać modyfikatora dostępu do elementów członkowskich. Ponieważ wszystkie funkcje lokalne są prywatne, w tym `private` modyfikator dostępu, takie jak słowo kluczowe, generuje błąd kompilatora CS0106, "Modyfikator "prywatny" jest nieprawidłowy dla tego elementu."

> [!NOTE]
> Przed c# 8.0 funkcje lokalne `static` nie może zawierać modyfikatora. W `static` tym słowo kluczowe generuje błąd kompilatora CS0106, "Modyfikator "statyczne" jest nieprawidłowy dla tego elementu."

Ponadto atrybutów nie można zastosować do funkcji lokalnej lub do jej parametrów i parametrów typu.

W poniższym przykładzie zdefiniowano funkcję lokalną o nazwie, `AppendPathSeparator` która jest prywatna dla metody o nazwie: `GetText`

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Funkcje lokalne i wyjątki

Jedną z przydatnych funkcji funkcji lokalnych jest to, że mogą one zezwolić na wyjątki do powierzchni natychmiast. Dla iteratorów metody wyjątki są wyświetlane tylko wtedy, gdy zwracana sekwencja jest wyliczana, a nie po pobraniu iteratora. W przypadku metod asynchronicznej wszelkie wyjątki generowane w metodzie asynchronicznej są obserwowane, gdy oczekuje się zwróconego zadania.

W poniższym `OddSequence` przykładzie zdefiniowano metodę, która wylicza liczby nieparzyste między określonym zakresem. Ponieważ przekazuje liczbę większą niż 100 do metody `OddSequence` wyliczania, metoda zgłasza . <xref:System.ArgumentOutOfRangeException> Jak pokazuje dane wyjściowe z przykładu, powierzchnie wyjątków tylko wtedy, gdy iterate liczb, a nie podczas pobierania wyliczacza.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Zamiast tego można zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iterator, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funkcje lokalne mogą służyć w podobny sposób do obsługi wyjątków poza operacją asynchroniczną. Zwykle wyjątki generowane w metodzie asynchronicznej wymagają zbadania wewnętrznych <xref:System.AggregateException>wyjątków . Funkcje lokalne umożliwiają kod szybko nie powiedzie się i pozwalają na wyjątek być generowane i obserwowane synchronicznie.

W poniższym przykładzie użyto metody `GetMultipleAsync` asynchronicznej o nazwie, aby wstrzymać na określoną liczbę sekund i zwrócić wartość, która jest losową wielokrotnością tej liczby sekund. Maksymalne opóźnienie wynosi 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5. Jak pokazano w poniższym przykładzie, wyjątek, który jest `GetMultipleAsync` generowany, gdy wartość <xref:System.AggregateException> 6 `GetMultipleAsync` jest przekazywana do metody jest opakowany w po rozpoczęciu wykonywania metody.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Tak jak w przypadku iterator metody, możemy refaktoryzacji kodu z tego przykładu, aby wykonać sprawdzanie poprawności przed wywołaniem metody asynchronicznej. Jak pokazuje dane wyjściowe z <xref:System.ArgumentOutOfRangeException> poniższego przykładu, nie jest zawinięte w <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a>Zobacz też

- [Metody](methods.md)
