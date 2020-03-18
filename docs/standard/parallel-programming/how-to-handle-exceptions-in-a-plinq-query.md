---
title: 'Porady: obsługa wyjątków w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 3645f5dc470ef53710aa7f4c78c60431fb27ecfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123090"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Porady: obsługa wyjątków w zapytaniu PLINQ

Pierwszy przykład w tym temacie pokazuje, jak <xref:System.AggregateException?displayProperty=nameWithType> obsługiwać, które mogą być generowane z kwerendy PLINQ podczas wykonywania. Drugi przykład pokazuje, jak umieścić try-catch bloki w delegatów, jak najbliżej, gdzie wyjątek zostanie wygenerowany. W ten sposób można je złapać, gdy tylko wystąpią i ewentualnie kontynuować wykonywanie zapytań. Gdy wyjątki mogą bąbelkować z powrotem do wątku łączącego, jest możliwe, że kwerenda może kontynuować przetwarzanie niektórych elementów po wyłączeniu wyjątku.

W niektórych przypadkach, gdy PLINQ wraca do wykonania sekwencyjnego i występuje wyjątek, wyjątek może <xref:System.AggregateException>być propagowane bezpośrednio i nie zawinięte w . Ponadto <xref:System.Threading.ThreadAbortException>s są zawsze propagowane bezpośrednio.

> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, program Visual Studio zostanie przerwany w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.
>
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak umieścić try-catch bloki wokół <xref:System.AggregateException?displayProperty=nameWithType>kodu, który wykonuje kwerendę do połowu wszystkich s, które są generowane.

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

W tym przykładzie kwerenda nie może kontynuować po wyjątek wyjątek. Do czasu kodu aplikacji przechwytuje wyjątek, PLINQ już zatrzymał kwerendę we wszystkich wątkach.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak umieścić blok try-catch w pełnomocnika, aby umożliwić przechwycać wyjątek i kontynuować wykonywanie kwerendy.

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu próbki danych PLINQ i wywołaj metodę z Main.

## <a name="robust-programming"></a>Niezawodne programowanie

Nie łapiesz wyjątku, chyba że wiesz, jak go obsługiwać, aby nie uszkodzić stanu programu.

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
