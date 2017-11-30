---
title: "Porady: użycie bloków finally"
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
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b303582a62f211091b1ebee0e88cf380da8b03d9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-finally-blocks"></a>Jak użycie bloków finally

Po wystąpieniu wyjątku, zatrzymuje wykonywanie i kontroli podano do obsługi odpowiednich wyjątków. Często oznacza to, że wiersze kodu, który może być wykonywane są pomijane. Porządkowanie zasobów, np. zamknięcie pliku, należy wykonać, nawet jeśli jest zgłaszany wyjątek. Aby to zrobić, można użyć `finally` bloku. A `finally` bloku zawsze wykonywana, niezależnie od tego, czy jest zgłaszany wyjątek.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>. `Main` Metoda tworzy dwie tablice i próbuje skopiować je do innych. Akcja generuje <xref:System.ArgumentOutOfRangeException> i jest on zapisywany do konsoli. `finally` Bloku wykonuje niezależnie od wyniku akcji kopiowania.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)   
