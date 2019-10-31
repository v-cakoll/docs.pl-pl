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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139732"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych

Ten przykład pokazuje, jak zrównoleglanie operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece zadań równoległych. Trzy operacje są wykonywane na udostępnionym źródle danych. Ponieważ żadna z operacji nie modyfikuje źródła, można wykonać ją równolegle w prosty sposób.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Należy pamiętać, że w przypadku <xref:System.Threading.Tasks.Parallel.Invoke%2A>można po prostu przedstawić, które akcje mają być uruchamiane współbieżnie, a środowisko uruchomieniowe obsługuje wszystkie szczegóły planowania wątków, w tym skalowanie automatycznie do liczby rdzeni na komputerze hosta.

Ten przykład parallelizes operacje, a nie dane. Alternatywnie można zrównoleglanie zapytania LINQ przy użyciu PLINQ i uruchamiać zapytania sekwencyjnie. Alternatywnie można zrównoleglanie dane przy użyciu PLINQ. Kolejną opcją jest zrównoleglanie zarówno zapytania, jak i zadania. Chociaż wynikowe obciążenie może obniżyć wydajność na komputerach hostów z stosunkowo kilkoma procesorami, znacznie lepiej jest skalować komputery z wieloma procesorami.

## <a name="compile-the-code"></a>Kompiluj kod

Skopiuj i wklej cały przykład do projektu Microsoft Visual Studio i naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
