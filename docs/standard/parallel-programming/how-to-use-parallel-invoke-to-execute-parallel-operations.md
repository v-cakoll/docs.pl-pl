---
title: 'Instrukcje: Wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 2b353fb8cb5e04ee4cab6b49f55539ecb40fab4f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290801"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Instrukcje: Wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke

Ten przykład pokazuje, jak zrównoleglanie operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece zadań równoległych. Trzy operacje są wykonywane na udostępnionym źródle danych. Operacje mogą być wykonywane równolegle w prosty sposób, ponieważ żaden z nich nie modyfikuje źródła.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Za pomocą programu <xref:System.Threading.Tasks.Parallel.Invoke%2A> można po prostu przedstawić, które akcje mają być uruchamiane współbieżnie, a środowisko uruchomieniowe obsługuje wszystkie szczegóły dotyczące planowania wątków, w tym skalowanie automatycznie do liczby rdzeni na komputerze hosta.

Ten przykład parallelizes operacje, a nie dane. Alternatywnie można zrównoleglanie zapytania LINQ przy użyciu PLINQ i uruchamiać zapytania sekwencyjnie. Alternatywnie można zrównoleglanie dane przy użyciu PLINQ. Kolejną opcją jest zrównoleglanie zarówno zapytania, jak i zadania. Chociaż wynikowe obciążenie może obniżyć wydajność na komputerach hostów z stosunkowo kilkoma procesorami, lepiej skalować je na komputerach z wieloma procesorami.

## <a name="compile-the-code"></a>Kompiluj kod

Skopiuj i wklej cały przykład do projektu Microsoft Visual Studio i naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](index.md)
- [Instrukcje: Anulowanie zadania i jego elementów podrzędnych](how-to-cancel-a-task-and-its-children.md)
- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
