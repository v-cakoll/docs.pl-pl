---
title: 'Porady: jawne zgłaszanie wyjątków'
description: Dowiedz się, jak zgłosić wyjątek jawnie w programie .NET przy użyciu instrukcji throw języka C# lub instrukcji Visual Basic throw.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 2dd939f9edd58ba91ea74df5d6930087849f0560
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662787"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak jawnie zgłosić wyjątki

Wyjątek można jawnie zgłosić przy użyciu języka C# [`throw`](../../csharp/language-reference/keywords/throw.md) lub [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) instrukcji Visual Basic. Można również zgłosić przechwycony wyjątek ponownie, używając `throw` instrukcji. Dobrym sposobem kodowania jest dodanie informacji do wyjątku, który został ponownie wygenerowany, aby uzyskać więcej informacji podczas debugowania.

Poniższy przykład kodu używa bloku, `try` / `catch` Aby przechwycić możliwe <xref:System.IO.FileNotFoundException> . Po `try` bloku jest `catch` blok, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli plik danych nie zostanie znaleziony. Następna instrukcja to `throw` instrukcja, która zgłasza nowe <xref:System.IO.FileNotFoundException> i dodaje do wyjątku informacje tekstowe.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
