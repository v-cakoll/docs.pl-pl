---
title: "Porady: jawne zgłaszanie wyjątków"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a>Jak jawne zgłaszanie wyjątków

Można jawne zgłaszanie wyjątków za pomocą `throw` instrukcji. Można również zgłosić wyjątek zgłoszony ponownie, używając `throw` instrukcji. Jest dobrym rozwiązaniem, aby dodać informacje do wyjątek, który jest zgłoszony ponownie o podanie dodatkowych informacji podczas debugowania kodu.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch potencjalnie <xref:System.IO.FileNotFoundException>. Po `try` blok `catch` bloku, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli nie znaleziono pliku danych. Następna instrukcja jest `throw` instrukcji, która zwraca nową <xref:System.IO.FileNotFoundException> i dodaje informacje tekstowe wyjątek.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)
