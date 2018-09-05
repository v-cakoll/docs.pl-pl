---
title: Funkcje lokalne (C# Programming Guide)
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42b980bcbb47ed98b9cb8d7234044ae2c92c3124
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529492"
---
# <a name="local-functions-c-programming-guide"></a>Funkcje lokalne (C# Programming Guide)

Począwszy od C# 7.0, C# obsługuje *funkcje lokalne*. Funkcje lokalne są metody prywatne typu, które są osadzone w innym elemencie członkowskim. One może być wywołana tylko z ich nadrzędnego elementu członkowskiego. Funkcje lokalne może być zadeklarowana w i wywoływane z:

- Metody, szczególnie metody iteratorów i metod asynchronicznych
- Konstruktorów
- Metod dostępu do właściwości
- Metod dostępu zdarzeń
- Metody anonimowe
- Wyrażenia lambda
- Finalizatory
- Inne funkcje lokalne

Jednak funkcje lokalne nie można deklarować wewnątrz elementu członkowskiego z wyrażeniem w treści.

> [!NOTE]
> W niektórych przypadkach można użyć wyrażenia lambda do implementacji funkcji również są obsługiwane przez funkcję lokalnego. Dla porównania, zobacz [funkcje lokalne w porównaniu do wyrażenia Lambda](../../local-functions-vs-lambdas.md).

Funkcje lokalne upewnij celem zwykłego kodu. Kto czyta kodu możesz zobaczyć, że metoda nie jest wywoływane z wyjątkiem przez zawierającego metodę. W przypadku projektów zespołowych, one również spowodować, że inny deweloper może je przez pomyłkę wywołać metodę bezpośrednio z innego miejsca w klasie lub strukturze.
 
## <a name="local-function-syntax"></a>Składnia funkcji lokalnej

Funkcja lokalna jest zdefiniowany jako metodę zagnieżdżone wewnątrz nadrzędnego elementu członkowskiego. Jego definicja ma następującą składnię:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Można użyć funkcji lokalnych [async](../../language-reference/keywords/async.md) i [niebezpieczne](../../language-reference/keywords/unsafe.md) modyfikatorów. 

Należy pamiętać, że wszystkie zmienne lokalne, które są zdefiniowane w nadrzędnego elementu członkowskiego, łącznie z jego parametrów metody są dostępne w funkcji lokalnej. 

W przeciwieństwie do definicji metody definicja funkcji lokalnej nie może zawierać następujące elementy:

- Modyfikator dostępu składowej. Ponieważ wszystkie funkcje lokalne są prywatne, łącznie z modyfikatora dostępu, takich jak `private` — słowo kluczowe, generuje błąd kompilatora CS0106, "modyfikator"private"jest nieprawidłowy dla tego elementu."
 
- [Statyczne](../../language-reference/keywords/static.md) — słowo kluczowe. W tym `static` — słowo kluczowe generuje błąd kompilatora CS0106, "modyfikator"static"jest nieprawidłowy dla tego elementu."

Ponadto atrybuty nie można zastosować do funkcji lokalnej lub jego parametry i parametry typu. 
 
W poniższym przykładzie zdefiniowano funkcji lokalnej o nazwie `AppendPathSeparator` jest oznaczony jako prywatny metodę o nazwie `GetText`:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Funkcje lokalne i wyjątki

Jest jednym z przydatnych funkcji funkcje lokalne, czy ich zezwalają na wyjątki, aby od razu powierzchni. Dla metody iteratorów wyjątki są udostępniane tylko wtedy, gdy są wyliczane zwracanej sekwencji, a nie w przypadku, gdy są pobierane iteratora. Do metod asynchronicznych wyjątki zgłaszane w metodzie asynchronicznej są przestrzegane, gdy zwracane zadanie jest oczekiwane. 

W poniższym przykładzie zdefiniowano `OddSequence` metodę, która wylicza nieparzystej liczby z zakresu od określonego zakresu. Ponieważ przekazuje liczbę większą niż 100 do `OddSequence` metody modułu wyliczającego, metoda zgłasza <xref:System.ArgumentOutOfRangeException>. Dane wyjściowe z przykładu pokazują, wyjątek wydobywa informacje dotyczące tylko wtedy, gdy iteracji numery, a nie w przypadku, gdy pobieranie modułu wyliczającego.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Zamiast tego może zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iteratora, zwracając iteratora, z funkcją lokalną, w poniższym przykładzie pokazano.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funkcje lokalne może służyć w podobny sposób, aby obsłużyć wyjątki poza operację asynchroniczną. Zazwyczaj wyjątki zgłaszane w metodzie asynchronicznej wymagają badania wewnętrznych wyjątków z <xref:System.AggregateException>. Funkcje lokalne zezwalają na kodzie w celu szybkiego kończenia działania i Zezwalaj na wyjątek zarówno wygenerowany i zaobserwowanie synchronicznie.

W poniższym przykładzie użyto metody asynchronicznej o nazwie `GetMultipleAsync` wstrzymać określoną liczbę sekund i zwracają wartość, która jest wielokrotnością losowe tę liczbę sekund. Maksymalne opóźnienie to 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5. Jak pokazano na poniższym przykładzie, wyjątek, który jest zgłaszany, gdy wartość 6 jest przekazywany do `GetMultipleAsync` metody jest opakowana w <xref:System.AggregateException> po `GetMultipleAsync` metoda rozpoczyna wykonywanie.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Ile My mieliśmy z metody iteratora, możemy refaktoryzować kod z tego przykładu w celu sprawdzenia poprawności przed wywołaniem metody asynchronicznej. Jako dane wyjściowe w poniższym przykładzie przedstawiono <xref:System.ArgumentOutOfRangeException> nie jest ujęty w <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Zobacz też

- [Metody](methods.md)
