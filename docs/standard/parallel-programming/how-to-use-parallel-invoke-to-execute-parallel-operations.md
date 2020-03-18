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
ms.openlocfilehash: 665490601cad9ccd7881042aed576b95bbc07115
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139732"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych

W tym przykładzie pokazano, jak <xref:System.Threading.Tasks.Parallel.Invoke%2A> równoległych operacji przy użyciu w bibliotece równoległej zadania. Trzy operacje są wykonywane na udostępnionym źródle danych. Ponieważ żadna z operacji modyfikuje źródło, mogą być wykonywane równolegle w prosty sposób.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Należy zauważyć, że za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A>programu , po prostu wyrazić, które akcje chcesz uruchomić jednocześnie, a czas wykonywania obsługuje wszystkie szczegóły planowania wątków, w tym skalowanie automatycznie do liczby rdzeni na komputerze-hoście.

W tym przykładzie równoległości operacji, a nie danych. Jako alternatywne podejście, można równoległych zapytań LINQ przy użyciu PLINQ i uruchamiać zapytania sekwencyjnie. Alternatywnie można zrównoleglić dane przy użyciu PLINQ. Inną opcją jest zrównolegliwość zarówno zapytań, jak i zadań. Mimo że wynikające z tego obciążenie może obniżyć wydajność na komputerach hosta z stosunkowo niewielką liczbą procesorów, znacznie lepiej skalowałoby się na komputerach z wieloma procesorami.

## <a name="compile-the-code"></a>Skompiluj kod

Skopiuj i wklej cały przykład do projektu programu Microsoft Visual Studio i naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
