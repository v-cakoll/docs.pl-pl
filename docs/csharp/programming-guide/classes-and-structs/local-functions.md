---
title: Funkcje lokalne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 7b6b46a33430a4a58c78245a0ab3bed1e0fbcd9c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455374"
---
# <a name="local-functions-c-programming-guide"></a>Funkcje lokalne (C# Przewodnik programowania)

Począwszy od C# 7,0, C# obsługuje *funkcje lokalne*. Funkcje lokalne są prywatnymi metodami typu, które są zagnieżdżone w innym elemencie członkowskim. Mogą być wywoływane tylko z ich składowych. Funkcje lokalne można zadeklarować w i wywołać z:

- Metody, zwłaszcza metody iteratorów i metody asynchroniczne
- Konstruktorów
- Metody dostępu do właściwości
- Metody dostępu zdarzeń
- Metody anonimowe
- Wyrażenia lambda
- Finalizatory
- Inne funkcje lokalne

Jednak funkcji lokalnych nie można deklarować wewnątrz elementu członkowskiego będącego w posiadaniu wyrażenia.

> [!NOTE]
> W niektórych przypadkach można użyć wyrażenia lambda, aby zaimplementować funkcje również obsługiwane przez funkcję lokalną. Aby zapoznać się z porównaniem, zobacz [funkcje lokalne w porównaniu z wyrażeniami lambda](../../local-functions-vs-lambdas.md).

Funkcje lokalne sprawiają, że zamiar kodu jest przejrzysty. Każda osoba odczytująca kod może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej. W przypadku projektów zespołowych uniemożliwiają one również innym deweloperom błędne wywoływanie metody bezpośrednio z innych miejsc w klasie lub strukturze.
 
## <a name="local-function-syntax"></a>Składnia funkcji lokalnych

Funkcja lokalna jest definiowana jako metoda zagnieżdżona wewnątrz składowej zawierającej. Jego definicja ma następującą składnię:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Funkcje lokalne mogą używać modyfikatorów [Async](../../language-reference/keywords/async.md) i [UNSAFE](../../language-reference/keywords/unsafe.md) . 

Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w składowej zawierającej, łącznie z parametrami metody, są dostępne w funkcji lokalnej. 

W przeciwieństwie do definicji metody lokalnej definicja funkcji nie może zawierać następujących elementów:

- Modyfikator dostępu składowej. Ponieważ wszystkie funkcje lokalne są prywatne, w tym modyfikator dostępu, taki jak `private` słowo kluczowe, generuje błąd kompilatora CS0106 "modyfikator" Private "jest nieprawidłowy dla tego elementu".
 
- [Static](../../language-reference/keywords/static.md) — słowo kluczowe. W tym `static` słowo kluczowe generuje błąd kompilatora CS0106, "modyfikator" static "jest nieprawidłowy dla tego elementu".

Ponadto atrybuty nie mogą być stosowane do funkcji lokalnej ani do jej parametrów i parametrów typu. 
 
W poniższym przykładzie zdefiniowano funkcję lokalną o nazwie `AppendPathSeparator`, która jest prywatna dla metody o nazwie `GetText`:
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Lokalne funkcje i wyjątki

Jedną z użytecznych funkcji lokalnych funkcji jest możliwość natychmiastowego zezwolenia na korzystanie z wyjątków. W przypadku iteratorów metod wyjątki są nakierowane tylko wtedy, gdy zwracana sekwencja jest wyliczana, a nie podczas pobierania iteratora. W przypadku metod asynchronicznych wszystkie wyjątki zgłoszone w metodzie asynchronicznej są zaobserwowane, gdy zwracane zadanie jest oczekiwane. 

W poniższym przykładzie zdefiniowano metodę `OddSequence`, która wylicza nieparzyste liczby między określonym zakresem. Ponieważ przekazuje liczbę większą niż 100 do metody modułu wyliczającego `OddSequence` Metoda generuje <xref:System.ArgumentOutOfRangeException>. Ponieważ dane wyjściowe z przykładu pokazują, powierzchnie wyjątków tylko w przypadku iteracji liczby, a nie podczas pobierania modułu wyliczającego.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Zamiast tego można zgłosić wyjątek podczas sprawdzania poprawności i przed pobraniem iteratora, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funkcji lokalnych można używać w podobny sposób, aby obsługiwać wyjątki poza operacją asynchroniczną. Zwykle wyjątki zgłoszone w metodzie asynchronicznej wymagają sprawdzenia wewnętrznych wyjątków <xref:System.AggregateException>. Funkcje lokalne umożliwiają szybkie i niepowodzenie wykonywania kodu oraz umożliwiają synchroniczną i zaobserwowany wyjątek.

Poniższy przykład używa metody asynchronicznej o nazwie `GetMultipleAsync`, aby wstrzymywać przez określoną liczbę sekund i zwracać wartość, która jest losowo wielokrotnością tej liczby sekund. Maksymalne opóźnienie wynosi 5 sekund; wyniki <xref:System.ArgumentOutOfRangeException>, jeśli wartość jest większa niż 5. Jak pokazano na poniższym przykładzie, wyjątek, który jest generowany, gdy wartość 6 jest przekazana do metody `GetMultipleAsync` jest opakowany w <xref:System.AggregateException> po rozpoczęciu wykonywania metody `GetMultipleAsync`.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Podobnie jak w iteratorze metody, możemy resłużyć kod z tego przykładu, aby przeprowadzić walidację przed wywołaniem metody asynchronicznej. Jak pokazano na poniższym przykładzie, <xref:System.ArgumentOutOfRangeException> nie jest opakowany w <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Zobacz także

- [Metody](methods.md)
