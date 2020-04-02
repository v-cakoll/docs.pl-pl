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
ms.openlocfilehash: 7189c478e132a41971a364b833f0fabda6ff84d4
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588397"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych

W tym przykładzie pokazano, <xref:System.Threading.Tasks.Parallel.Invoke%2A> jak zrównoleglić operacje przy użyciu biblioteki równoległej zadania. Trzy operacje są wykonywane na udostępnionym źródle danych. Ponieważ żadna z operacji modyfikuje źródło, mogą być wykonywane równolegle w prosty sposób.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Należy zauważyć, że za pomocą <xref:System.Threading.Tasks.Parallel.Invoke%2A>programu , wystarczy wyrazić, które akcje mają być uruchamiane jednocześnie, a środowisko wykonawcze obsługuje wszystkie szczegóły planowania wątków, w tym automatyczne skalowanie do liczby rdzeni na komputerze-hoście.

W tym przykładzie równoległości operacji, a nie danych. Jako podejście alternatywne można zrównoleglić zapytania LINQ przy użyciu PLINQ i uruchamiać kwerendy sekwencyjnie. Alternatywnie można zrównoleglić dane przy użyciu PLINQ. Inną opcją jest zrównoleglić zarówno kwerendy, jak i zadania. Mimo że wynikowe obciążenie może obniżyć wydajność na komputerach-hostach ze stosunkowo nielicznymi procesorami, znacznie lepiej skalowałoby się na komputerach z wieloma procesorami.

## <a name="compile-the-code"></a>Skompiluj kod

Skopiuj i wklej cały przykład do projektu programu Microsoft Visual Studio i naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
