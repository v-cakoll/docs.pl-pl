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
ms.openlocfilehash: a1a8658999f08d295e76afc9df6ec8acd146abe2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863229"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak jawne zgłaszanie wyjątków

Można jawnie zgłosić wyjątek za pomocą `throw` instrukcji. Może również zgłosić wyjątek zgłoszony ponownie, używając `throw` instrukcji. Jest dobrą praktyką, aby dodać informacje do wyjątek, który jest zgłoszony ponownie, aby dostarczyć dodatkowych informacji podczas debugowania kodu.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch możliwe <xref:System.IO.FileNotFoundException>. Następujące `try` blok `catch` blok, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli nie można odnaleźć pliku danych. Następna instrukcja znajduje się `throw` instrukcji generującej nową <xref:System.IO.FileNotFoundException> i dodaje informacje tekstowe do wyjątku.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
