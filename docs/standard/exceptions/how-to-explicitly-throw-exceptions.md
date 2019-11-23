---
title: 'Porady: jawne zgłaszanie wyjątków'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a71cefc0a6483dbbe6513a64d8111a07a2e5af42
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696743"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak jawnie zgłosić wyjątki

Wyjątek można jawnie zgłosić przy użyciu C# [`throw`](../../csharp/language-reference/keywords/throw.md) lub instrukcji Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) . Przechwycony wyjątek można również zgłosić ponownie, używając instrukcji `throw`. Dobrym sposobem kodowania jest dodanie informacji do wyjątku, który został ponownie wygenerowany, aby uzyskać więcej informacji podczas debugowania.

Poniższy przykład kodu używa bloku `try`/`catch`, aby przechwycić możliwe <xref:System.IO.FileNotFoundException>. Następujący blok `try` jest blokiem `catch`, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli plik danych nie zostanie znaleziony. Następną instrukcją jest instrukcja `throw`, która zgłasza nowy <xref:System.IO.FileNotFoundException> i dodaje do wyjątku informacje tekstowe.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
