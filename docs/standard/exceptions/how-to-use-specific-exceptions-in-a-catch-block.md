---
title: "Porady: użycie określonych wyjątków w bloku CATCH"
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
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
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
