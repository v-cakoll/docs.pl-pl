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
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453016"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Porady: obsługa wyjątków w pętlach równoległych
I <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia nie mają żadnego specjalnego mechanizmu do obsługi wyjątków, które mogą być generowane. W związku z tym `for` przypominają `foreach` one`For` regularne `For Each` i pętle ( i w visual basic); nieobsługiwany wyjątek powoduje, że pętla kończy się natychmiast po zakończeniu wszystkich aktualnie uruchomionych iteracji.
  
 Po dodaniu własnej logiki obsługi wyjątków do pętli równoległych, należy obsługiwać przypadek, w którym podobne wyjątki mogą być generowane na wiele wątków jednocześnie, a przypadek, w którym wyjątek w jednym wątku powoduje, że inny wyjątek ma zostać wygenerowany w innym Wątku. Obie sprawy można obsługiwać, zawijając <xref:System.AggregateException?displayProperty=nameWithType>wszystkie wyjątki z pętli w pliku . W poniższym przykładzie przedstawiono jedno możliwe podejście.  
  
> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który został pokazany w poniższym przykładzie. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wszystkie wyjątki są przechwycone, a następnie zawinięte w który <xref:System.AggregateException?displayProperty=nameWithType> jest generowany. Obiekt wywołujący może zdecydować, które wyjątki do obsługi.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
