---
title: 'Porady: użycie określonych wyjątków w bloku CATCH'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 424db46c879974a9859637f9a2a5dfcd4494a3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Jak używać określonych wyjątków w bloku catch

Ogólnie rzecz biorąc, jest dobrym rozwiązaniem catch konkretny typ wyjątku, zamiast używać podstawowego programowania `catch` instrukcji.

Po wystąpieniu wyjątku, są przekazywane w górę stosu, a każdy blok catch jest możliwość jego obsługa. Kolejność instrukcji catch jest ważna. Umieść bloki catch przeznaczone dla określonych wyjątków przed blok catch wyjątku ogólne lub kompilator może wydać wystąpił błąd. Blok catch właściwe jest określany przez dopasowanie typ wyjątku, aby nazwa określona w bloku catch wyjątku. Jeśli nie ma żadnych bloku catch określonych, wyjątek zostanie przechwycony przez blok catch ogólne, jeśli taka istnieje.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.InvalidCastException>. Przykład tworzy klasę o nazwie `Employee` z tylko jedną właściwość poziom pracownika (`Emlevel`). W metodzie `PromoteEmployee`, obiekt i zwiększa poziom pracownika. <xref:System.InvalidCastException> Występuje, gdy <xref:System.DateTime> wystąpienia są przekazywane do `PromoteEmployee` metody.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)
