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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160160"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Jak używać określonych wyjątków w bloku catch

Ogólnie rzecz biorąc, dobrym sposobem programowania jest przechwycenie określonego typu wyjątku zamiast używania podstawowej instrukcji `catch`.

Gdy wystąpi wyjątek, zostanie przekazany stos, a każdy blok catch otrzymuje szansę na jego obsługę. Kolejność instrukcji catch jest ważna. Umieść bloki catch skierowane do określonych wyjątków przed ogólnym blokiem catch wyjątku lub kompilator może wydać błąd. Odpowiedni blok catch jest określany przez dopasowanie typu wyjątku do nazwy wyjątku określonego w bloku catch. Jeśli nie ma określonego bloku catch, wyjątek jest przechwytywany przez ogólny blok catch, jeśli taki istnieje.

Poniższy przykład kodu używa bloku `try`/`catch` do przechwytywania <xref:System.InvalidCastException>. Przykład tworzy klasę o nazwie `Employee` z pojedynczą właściwością na poziomie pracownika (`Emlevel`). Metoda `PromoteEmployee`, przyjmuje obiekt i zwiększa poziom pracownika. <xref:System.InvalidCastException> występuje, gdy wystąpienie <xref:System.DateTime> zostanie przesłane do metody `PromoteEmployee`.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
