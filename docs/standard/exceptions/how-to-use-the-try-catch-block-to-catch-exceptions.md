---
title: 'Porady: Użyj bloku Try / Catch do przechwytywania wyjątków'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185207"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak przechwytywać wyjątki za pomocą bloku try/catch

Umieszczenie fragmentów kodu, który może zgłaszać wyjątki w `try` bloku i umieść kod, który obsługuje wyjątki w `catch` bloku. `catch` Blok jest szereg instrukcji rozpoczynające się od słowa kluczowego `catch`, a następnie typ wyjątku i akcję do wykonania.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch możliwym wyjątkiem. `Main` Metoda zawiera `try` blokowania z <xref:System.IO.StreamReader> instrukcję, która otwiera plik danych o nazwie `data.txt` i zapisuje ciąg z pliku. Następujące `try` blok `catch` blok, który przechwytuje wszystkie wyjątki, które powstały na skutek `try` bloku.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Środowisko uruchomieniowe języka wspólnego przechwytuje wyjątki, które nie są przechwytywane przez blok catch. W zależności od sposobu skonfigurowania środowiska uruchomieniowego pojawi się okno dialogowe debugowania, program zatrzymuje wykonywanie i pojawia się okno dialogowe z informacjami o wyjątek lub błąd jest drukowany stderr.

> [!NOTE] 
> Prawie w każdym wierszu kodu może spowodować wyjątek, szczególnie te wyjątki, które są generowane przez środowisko uruchomieniowe języka wspólnego, takich jak <xref:System.OutOfMemoryException>. Większość aplikacji nie ma do czynienia z uwzględnieniem poniższych wyjątków, ale należy pamiętać o to martwić, podczas zapisywania biblioteki ma być używany przez inne osoby. Aby uzyskać sugestie, kiedy należy ustawić możesz pisać kod w bloku Try, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
