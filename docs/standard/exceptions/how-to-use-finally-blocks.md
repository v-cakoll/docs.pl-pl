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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 213ab53c68a37ac0ba5f337a1d6fc32bfe6f8989
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883682"
---
# <a name="how-to-use-finally-blocks"></a>Jak użycie bloków finally

Gdy wystąpi wyjątek, zatrzymuje wykonywanie i kontrola otrzymuje do obsługi odpowiednich wyjątków. Często oznacza to, że są pomijane wiersze kodu, których oczekujesz, że do wykonania. Niektóre czyszczenie zasobów, takich jak zamykania pliku musi odbywać się nawet wtedy, gdy wyjątek jest zgłaszany. Aby to zrobić, można użyć `finally` bloku. A `finally` blok zawsze jest wykonywany, niezależnie od tego, czy wyjątek jest zgłaszany.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>. `Main` Metoda tworzy dwie tablice i próbuje skopiować jednego do drugiego. Akcja generuje <xref:System.ArgumentOutOfRangeException> i jest on zapisywany w konsoli. `finally` Blok jest wykonywany niezależnie od tego, w wyniku akcji kopiowania.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
