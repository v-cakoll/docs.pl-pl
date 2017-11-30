---
title: "Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych"
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
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a51f180a394c1baa2ecb0620279ea15c62e1edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych
W tym przykładzie pokazano, jak parallelize operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece równoległych zadań. Trzy operacje są wykonywane na udostępnione źródło danych. Ponieważ żadna z operacji modyfikuje źródło, mogą być wykonywane równolegle w sposób proste.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Należy pamiętać, że z <xref:System.Threading.Tasks.Parallel.Invoke%2A>, po prostu express akcje, które chcesz uruchamiać jednocześnie i środowiska uruchomieniowego obsługuje wszystkie wątku planowania szczegółów, takich jak automatycznie skalować liczbę rdzeni na komputerze hosta.  
  
 W tym przykładzie parallelizes operacji, a nie dane. Jako alternatywne podejście możesz parallelize zapytań LINQ za pomocą PLINQ i zapytania są wykonywane sekwencyjnie. Alternatywnie można parallelize danych przy użyciu PLINQ. Innym rozwiązaniem jest parallelize zarówno zapytania i zadania. Mimo że powstałe w ten sposób obciążenie może zmniejszyć wydajność na komputerach hostów mają względnie mało procesory, go będzie skalować znacznie poprawia na komputerach z wielu procesorów.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Skopiuj i Wklej cały przykład do projektu Microsoft Visual Studio 2010 i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 [Porady: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
