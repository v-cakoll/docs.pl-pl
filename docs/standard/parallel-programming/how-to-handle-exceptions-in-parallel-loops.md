---
title: 'Porady: obsługa wyjątków w pętlach równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf311ad2b79e615f5c3097686035e7bbfbc49c9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185142"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Porady: obsługa wyjątków w pętlach równoległych
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia nie mają żadnych specjalnych mechanizm obsługi wyjątków, które może zostać wygenerowany. W związku z tym przypominają zwykłe `for` i `foreach` pętli (`For` i `For Each` w języku Visual Basic); wystąpił nieobsługiwany wyjątek powoduje pętlę, można od razu zakończyć.  
  
 Po dodaniu własną logiką obsługi wyjątków, równoległe pętli, obsłużyć przypadek, w którym podobne wyjątków może być wyrzucanych na wiele wątków jednocześnie, a także przypadek, w którym wyjątek zgłoszony w jednym wątku powoduje zgłoszenie wyjątku inny od innego Wątek. Może obsługiwać obu przypadkach dzięki zawijaniu wszystkie wyjątki z pętli w <xref:System.AggregateException?displayProperty=nameWithType>. Poniższy przykład przedstawia jedno z możliwych podejść.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest nieszkodliwe. Naciśnij klawisz F5, aby nadal z niego i sprawdzić sposób obsługi wyjątków, przedstawionej w poniższym przykładzie. Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wszystkie wyjątki są przechwytywane i następnie otoczona <xref:System.AggregateException?displayProperty=nameWithType> której zgłaszany. Obiekt wywołujący można zdecydować, której wyjątki, aby obsłużyć.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
