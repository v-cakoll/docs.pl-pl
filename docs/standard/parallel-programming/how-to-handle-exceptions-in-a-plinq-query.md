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
ms.openlocfilehash: 5ccddfb01d6b173900dfffc465292c7812626ddc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587984"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Porady: obsługa wyjątków w zapytaniu PLINQ

Pierwszy przykład w tym temacie pokazuje, jak <xref:System.AggregateException?displayProperty=nameWithType> obsługiwać, które mogą być generowane z kwerendy PLINQ podczas wykonywania. W drugim przykładzie pokazano, jak umieścić try-catch bloków w delegatów, jak najbliżej, gdzie zostanie zgłoszony wyjątek. W ten sposób można je złapać, jak tylko wystąpią i ewentualnie kontynuować wykonywanie kwerendy. Gdy wyjątki są dozwolone do bańki z powrotem do wątku łączącego, a następnie jest możliwe, że kwerenda może kontynuować przetwarzanie niektórych elementów po wyjątek jest wywoływany.

W niektórych przypadkach, gdy PLINQ powraca do wykonywania sekwencyjnego i występuje wyjątek, wyjątek <xref:System.AggregateException>może być propagowany bezpośrednio, a nie zawinięty w . Ponadto <xref:System.Threading.ThreadAbortException>s są zawsze propagowane bezpośrednio.

> [!NOTE]
> Gdy "Tylko mój kod" jest włączona, Visual Studio zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z napisem "wyjątek nie obsługiwany przez kod użytkownika". Ten błąd jest łagodny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, które jest pokazane w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu w programie Visual Studio, po prostu wyczyść pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.
>
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak umieścić try-catch bloków wokół <xref:System.AggregateException?displayProperty=nameWithType>kodu, który wykonuje kwerendę, aby złapać wszelkie s, które są generowane.

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

W tym przykładzie kwerenda nie może kontynuować po zarzuceniu wyjątku. Do czasu, gdy kod aplikacji łapie wyjątek, PLINQ już zatrzymał kwerendę na wszystkie wątki.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak umieścić blok try-catch w delegata, aby umożliwić przechwyt wyjątek i kontynuować wykonywanie kwerendy.

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu przykładu danych PLINQ i wywołaj metodę z main.

## <a name="robust-programming"></a>Niezawodne programowanie

Nie należy przechwytywać wyjątek, chyba że wiesz, jak go obsłużyć, tak aby nie uszkodzić stan programu.

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
