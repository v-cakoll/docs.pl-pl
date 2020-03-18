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
ms.openlocfilehash: 48b450e579263876725f96e0adfc4c16aac1d869
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160160"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Jak używać określonych wyjątków w bloku catch

Ogólnie rzecz biorąc jest dobrą praktyką programowania, aby przechwycić określony `catch` typ wyjątku, a nie użyć podstawowej instrukcji.

Po wystąpieniu wyjątku jest przekazywana do stosu i każdy blok catch ma możliwość obsługi go. Kolejność instrukcji połowowych jest ważna. Umieść catch bloki przeznaczone do określonych wyjątków przed ogólnym bloku catch wyjątku lub kompilator może wystawiać błąd. Właściwy blok catch jest określana przez dopasowanie typu wyjątku do nazwy wyjątku określonego w bloku catch. Jeśli nie ma żadnego określonego bloku catch, wyjątek jest przechwycone przez ogólny blok catch, jeśli istnieje.

Poniższy przykład kodu `try` / `catch` używa bloku <xref:System.InvalidCastException>do połowu . Przykład tworzy klasę `Employee` o nazwie z jednej`Emlevel`właściwości, poziom pracownika ( ). Metoda , `PromoteEmployee`przyjmuje obiekt i zwiększa poziom pracownika. Występuje, <xref:System.InvalidCastException> gdy <xref:System.DateTime> wystąpienie jest `PromoteEmployee` przekazywane do metody.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
