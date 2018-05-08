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
ms.openlocfilehash: 4eeb70c10d71a7c96136039342bcdcc7bc8ece20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak jawne zgłaszanie wyjątków

Można jawne zgłaszanie wyjątków za pomocą `throw` instrukcji. Można również zgłosić wyjątek zgłoszony ponownie, używając `throw` instrukcji. Jest dobrym rozwiązaniem, aby dodać informacje do wyjątek, który jest zgłoszony ponownie o podanie dodatkowych informacji podczas debugowania kodu.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch potencjalnie <xref:System.IO.FileNotFoundException>. Po `try` blok `catch` bloku, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli nie znaleziono pliku danych. Następna instrukcja jest `throw` instrukcji, która zwraca nową <xref:System.IO.FileNotFoundException> i dodaje informacje tekstowe wyjątek.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)
