---
title: 'Porady: użycie bloków finally'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708835"
---
# <a name="how-to-use-finally-blocks"></a>Jak używać bloków finally

Gdy wystąpi wyjątek, wykonywanie zostaje zatrzymane i kontrola zostanie udzielona odpowiedniej procedurze obsługi wyjątków. Często oznacza to, że wiersze kodu, które należy wykonać, są pomijane. Niektóre Oczyszczanie zasobów, takie jak zamykanie pliku, należy wykonać nawet wtedy, gdy zostanie zgłoszony wyjątek. W tym celu można użyć bloku `finally`. Blok `finally` jest zawsze wykonywany, niezależnie od tego, czy wystąpił wyjątek.

Poniższy przykład kodu używa bloku `try`/`catch` do przechwytywania <xref:System.ArgumentOutOfRangeException>. Metoda `Main` tworzy dwie tablice i próbuje skopiować jeden do drugiego. Akcja generuje <xref:System.ArgumentOutOfRangeException> i błąd jest zapisywana w konsoli. Blok `finally` jest wykonywany niezależnie od wyniku akcji kopiowania.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
