---
title: Funkcje lokalne (C# przewodnik programowania w języku)
ms.date: 06/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac18aa57f443f28f55779ff9c92a5349b9b39fd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="local-functions-c-programming-guide"></a>Funkcje lokalne (C# przewodnik programowania w języku)

Począwszy od C# 7.0, C# obsługuje *funkcje lokalne*. Funkcje lokalne są prywatnych metod typu, które są zagnieżdżone w innym elemencie członkowskim. Mogą one można wywołać tylko z ich zawierającego element członkowski. Funkcje lokalne może być zadeklarowana w i wywoływać z:

- Metody szczególnie metody iteracyjne i metod asynchronicznych
- Konstruktorów
- Metod dostępu do właściwości
- Metod dostępu zdarzeń
- Metody anonimowe
- Wyrażenia lambda
- Finalizatory
- Inne funkcje lokalne

Jednak funkcje lokalne nie może być deklarowane w zabudowanych wyrażenie elementu członkowskiego.

> [!NOTE]
> W niektórych przypadkach wyrażenia lambda służy do implementowania również obsługiwane przez funkcję lokalnego. Porównanie, zobacz [funkcje lokalne w porównaniu do wyrażenia Lambda](../../local-functions-vs-lambdas.md).

Funkcje lokalne należy celem wyczyść kodu. Odczytywanie programowanie można stwierdzić, że każdy użytkownik metoda nie jest można wywołać z wyjątkiem przez metodę zawierającego. Dla projektów zespołowych one również uniemożliwić innym deweloperowi przez pomyłkę Wywołaj metodę bezpośrednio w innym miejscu w klasie lub stuct.
 
## <a name="local-function-syntax"></a>Składnia funkcji lokalnej

Funkcja lokalna jest zdefiniowany jako metodę zagnieżdżone wewnątrz zawierającego element członkowski. Jego definicja ma następującą składnię:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Można użyć funkcji lokalnej [async](../../language-reference/keywords/async.md) i [niebezpieczne](../../language-reference/keywords/unsafe.md) modyfikatorów. 

Należy pamiętać, że wszystkie zmienne lokalne, zdefiniowane w zawierającym elementu członkowskiego, w tym jego parametrów metody są dostępne w funkcji lokalnej. 

W odróżnieniu od definicję metody definicji funkcji lokalnego nie może zawierać następujące elementy:

- Modyfikator dostępu elementu członkowskiego. Ponieważ wszystkie funkcje lokalne są prywatne, łącznie z modyfikatora dostępu, takich jak `private` — słowo kluczowe, generuje błąd kompilatora CS0106 "modyfikator"private"jest nieprawidłowy dla tego elementu."
 
- [Statycznych](../../language-reference/keywords/static.md) — słowo kluczowe. W tym `static` — słowo kluczowe generuje błąd kompilatora CS0106, "modyfikator"static"jest nieprawidłowy dla tego elementu."

Ponadto atrybuty nie można zastosować do funkcji lokalnej lub jego parametrów i parametry typu. 
 
W poniższym przykładzie zdefiniowano lokalnym funkcji o nazwie `AppendPathSeparator` jest oznaczony jako prywatny metodę o nazwie `GetText`:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Funkcje lokalne i wyjątków

Jednym z przydatnych funkcji funkcje lokalne jest czy umożliwiają one wyjątki, aby natychmiast powierzchni. Dla metody Iteratory wyjątki są udostępniane tylko wtedy, gdy zwrócony sekwencji jest wyliczone i nie w przypadku, gdy są pobierane iteratora. Dla metody asynchroniczne wszelkie wyjątki zgłaszane w metodzie asynchronicznej są przestrzegane, gdy zadanie zwracane jest oczekiwane. 

W poniższym przykładzie zdefiniowano `OddSequence` metodę, która wylicza nieparzystej liczby z zakresu określonego zakresu. Ponieważ przekazaniem liczbą większą od 100 do `OddSequence` metoda modułu wyliczającego, metoda zgłasza <xref:System.ArgumentOutOfRangeException>. Jak pokazano na dane wyjściowe z przykładu, wyjątek powierzchni tylko wtedy, gdy iteracyjne numery, a nie w przypadku, gdy pobieranie modułu wyliczającego.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Zamiast tego można zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iteratora zwracając iteratora z funkcji lokalnej, jak w poniższym przykładzie przedstawiono.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funkcje lokalne można w sposób podobny do obsługi wyjątków poza operację asynchroniczną. Zwykle wyjątki zgłaszane w metodzie asynchronicznej wymagają, że należy zbadać wyjątków wewnętrznych z <xref:System.AggregateException>. Zezwalaj na funkcje lokalne swój kod, aby szybko zakończyć się niepowodzeniem i umożliwić wyjątku zarówno zgłoszony i obserwowanych synchronicznie.

W poniższym przykładzie użyto metody asynchronicznej o nazwie `GetMultipleAsync` wstrzymać określoną liczbę sekund i zwracać wartość, która jest wielokrotnością losowe podanej liczby sekund. Maksymalne opóźnienie to 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5. Jak pokazano na poniższym przykładzie, wyjątek zgłaszany, gdy wartość 6 jest przekazywana do `GetMultipleAsync` metody jest ujęte w <xref:System.AggregateException> po `GetMultipleAsync` metody rozpoczyna się wykonanie.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Jak robiliśmy z metody iteracyjne, firma Microsoft zrefaktoryzuj kod w tym przykładzie do sprawdzania poprawności przed wywołaniem metody asynchronicznej. Jako dane wyjściowe w poniższym przykładzie przedstawiono <xref:System.ArgumentOutOfRangeException> nie jest ujęte w < x:System.AggregateException >.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Zobacz także
[Metody](methods.md)
