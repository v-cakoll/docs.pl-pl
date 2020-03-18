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
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708865"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak jawnie zgłaszać wyjątki

Jawnie można zgłosić wyjątek przy [`throw`](../../csharp/language-reference/keywords/throw.md) użyciu c# [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) lub Visual Basic instrukcji. Można również zgłosić przechwyconego wyjątku ponownie przy użyciu `throw` instrukcji. Dobrą praktyką kodowania jest dodawanie informacji do wyjątku, który jest ponownie generowany, aby zapewnić więcej informacji podczas debugowania.

Poniższy przykład kodu `try` / `catch` używa bloku do <xref:System.IO.FileNotFoundException>połowu możliwe . Po `try` bloku jest `catch` blok, <xref:System.IO.FileNotFoundException> który przechwytuje i zapisuje wiadomość do konsoli, jeśli plik danych nie zostanie znaleziony. Następna instrukcja `throw` jest instrukcja, <xref:System.IO.FileNotFoundException> która zgłasza nowy i dodaje informacje tekstowe do wyjątku.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
