---
title: "Porady: obsługa wyjątków w zapytaniu PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 209e0c1bf89f231d03647ae4351279bfdb172e68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Porady: obsługa wyjątków w zapytaniu PLINQ
Pierwszym przykładzie w tym temacie przedstawiono sposób obsługi <xref:System.AggregateException?displayProperty=nameWithType> który mógł zostać zgłoszony w zapytaniu PLINQ podczas wykonywania. Drugi przykład przedstawia sposób możliwie, do której zostanie wyjątek put bloków try-catch w obrębie obiektów delegowanych. W ten sposób można je catch natychmiast wystąpić i być może kontynuować wykonywania zapytania. Jest wywoływane, gdy wyjątki mogą bąbelkowy się wstecz do łącząca wątku, możliwe zapytania mogą nadal przetwarzania niektórych elementów po wyjątku jest.  
  
 W niektórych przypadkach po PLINQ powraca do wykonywania sekwencyjnego, i wystąpi wyjątek, wyjątek może być propagowane bezpośrednio i nie są ujęte w <xref:System.AggregateException>. Ponadto <xref:System.Threading.ThreadAbortException>s zawsze są propagowane bezpośrednio.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" programu Visual Studio będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest niegroźne. Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
>   
>  W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak put bloków try-catch wokół kod, który wykonuje zapytanie, aby wykryć wszelkie <xref:System.AggregateException?displayProperty=nameWithType>, które są zgłaszane.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 W tym przykładzie zapytanie nie może kontynuować po wyjątku. W czasie przechwycony wyjątek w kodzie aplikacji PLINQ ma już przestał wykonywać zapytanie na wszystkie wątki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wprowadzić bloku try-catch w pełnomocnika, aby umożliwić catch wyjątku i kontynuować wykonywanie zapytania.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować i uruchomić te przykłady, skopiuj je do przykład próbka danych PLINQ i wywołać metodę z głównym.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Nie przechwytuj wyjątków, jeśli nie wiadomo, jak obsługiwać go tak, aby nie spowodować uszkodzenie stanu programu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.ParallelEnumerable>  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
