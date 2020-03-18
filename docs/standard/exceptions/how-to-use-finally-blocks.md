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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708835"
---
# <a name="how-to-use-finally-blocks"></a>Jak używać wreszcie bloków

W przypadku wystąpienia wyjątku, wykonywanie zatrzymuje się i kontroli jest podana do obsługi wyjątków odpowiednie. Często oznacza to, że wiersze kodu, które mają być wykonywane są pomijane. Niektóre oczyszczania zasobów, takich jak zamknięcie pliku, musi być wykonane, nawet jeśli wyjątek. Aby to zrobić, można `finally` użyć bloku. Blok `finally` zawsze jest wykonywany, niezależnie od tego, czy wyjątek jest zgłaszany.

Poniższy przykład kodu `try` / `catch` używa bloku <xref:System.ArgumentOutOfRangeException>do połowu . Metoda `Main` tworzy dwie tablice i próbuje skopiować jedną do drugiej. Akcja generuje i <xref:System.ArgumentOutOfRangeException> błąd jest zapisywany w konsoli. Blok `finally` jest wykonywany niezależnie od wyniku akcji kopiowania.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
