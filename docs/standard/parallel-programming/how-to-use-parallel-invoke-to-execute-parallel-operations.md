---
title: 'Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0192e12c86b21eb126293bbd220e093b334768b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46695371"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych

W tym przykładzie pokazano, jak zrównoleglić operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece zadań równoległych. Trzy operacje są wykonywane na udostępnione źródło danych. Ponieważ żadne operacje modyfikuje źródła, mogą być wykonywane równolegle w prosty sposób.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Należy pamiętać, że za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A>, po prostu express akcje, które mają być uruchamiane równolegle i środowisko wykonawcze obsługuje wszystkie wątku planowania szczegółów, takich jak automatyczne skalowanie do liczby rdzeni na komputerze-hoście.

W tym przykładzie parallelizes operacji, a nie dane. Jako alternatywne podejście możesz zrównoleglenia zapytania w LINQ za pomocą PLINQ i uruchamiać je sekwencyjnie. Alternatywnie można zrównoleglić danych przy użyciu PLINQ. Innym rozwiązaniem jest równoległe przetwarzanie zapytań i zadań. Mimo że wynikowy obciążenie może zmniejszyć wydajność na komputerach hostów stosunkowo niewielką liczbą procesorów, go czy skalowanie znacznie lepsze na komputerach z procesorami wielordzeniowymi, wiele.

## <a name="compile-the-code"></a>Skompilować kod

Skopiuj i Wklej cały przykład w projekcie programu Microsoft Visual Studio i naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
