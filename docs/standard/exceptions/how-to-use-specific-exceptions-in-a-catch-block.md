---
title: 'Instrukcje: Użycie określonych wyjątków w bloku CATCH'
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
ms.openlocfilehash: 3da35dae374018f0695f79022e83ad397e98cb88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970888"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Jak używać określonych wyjątków w bloku catch

Ogólnie rzecz biorąc, jest dobrą praktyką catch konkretny typ wyjątku, zamiast używać podstawowego programowania `catch` instrukcji.

Po wystąpieniu wyjątku jest przekazywany górę stosu, a każdy blok catch jest możliwość go obsłużyć. Kolejność instrukcji catch jest ważna. Umieść bloki catch przeznaczone dla określonych wyjątków, przed blokiem catch ogólny wyjątek lub kompilator może wydać błąd. Blok catch właściwej jest określany przez dopasowanie typu wyjątku do nazwy wystąpienia wyjątku określonego w bloku catch. W przypadku nie blok catch określonych wyjątek zostaje przechwycony przez ogólnego bloku catch, jeśli taka istnieje.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.InvalidCastException>. Przykładowa aplikacja tworzy klasę o nazwie `Employee` z tylko jedną właściwość poziom pracownika (`Emlevel`). Metoda `PromoteEmployee`, przyjmuje obiekt i zwiększa poziom pracownika. <xref:System.InvalidCastException> Występuje, gdy <xref:System.DateTime> wystąpienia jest przekazywany do `PromoteEmployee` metody.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
