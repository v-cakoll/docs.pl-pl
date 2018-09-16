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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40b98e01d6c34fb01a1f508f2ea52309f2f7938b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668765"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Porady: obsługa wyjątków w zapytaniu PLINQ
Pierwszy przykład w tym temacie przedstawiono sposób obsługi <xref:System.AggregateException?displayProperty=nameWithType> , mogą być generowane w wyniku zapytania PLINQ, podczas wykonywania. Drugi przykład pokazuje, jak umieścić bloków try-catch w obrębie delegatów, w jak najbardziej zbliżony do której zostanie zgłoszony wyjątek. W ten sposób możesz przechwytywać je jak najszybciej występują i ewentualnie kontynuować wykonywanie zapytania. Kiedy wyjątki mogą się pojawiać z powrotem w sąsiednim wątku, jest możliwe, że zapytanie może w dalszym ciągu przetwarzać niektóre elementy po wyjątku jest zgłaszany.  
  
 W niektórych przypadkach PLINQ powraca do wykonywania sekwencyjnego, gdy wystąpi wyjątek, wyjątek może być propagowane bezpośrednio i nie zostały opakowane w <xref:System.AggregateException>. Ponadto <xref:System.Threading.ThreadAbortException>s zawsze są propagowane bezpośrednio.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" Visual Studio będzie przerwania w wierszu, który zgłasza wyjątek i wyświetlać komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest nieszkodliwe. Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
>   
>  W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak umieścić bloków try-catch wokół kodu, który wykonuje zapytanie, aby przechwytywać wszystkie <xref:System.AggregateException?displayProperty=nameWithType>s, które są zgłaszane.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 W tym przykładzie zapytanie nie może kontynuować po wyrzuceniu wyjątku. Według czasu, w kodzie aplikacji przechwytuje wyjątek PLINQ została już zatrzymana zapytanie we wszystkich wątkach.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak umieścić bloku try / catch w delegacie, aby umożliwić przechwytywać wyjątek, a następnie kontynuuj wykonywanie zapytania.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu próbka danych PLINQ i wywołać metodę z Main.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Nie przechwytuj wyjątek, chyba że wiesz, jak je obsłużyć, dzięki czemu nie spowodują uszkodzenia stanu programu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>  
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
