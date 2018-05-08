---
title: 'Porady: umożliwia przechwytywanie wyjątków w bloku Try-Catch'
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
ms.openlocfilehash: b169353752f6e6483a056cdc9dd8c3227b9ebeb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Przechwytywanie wyjątków przy użyciu bloku try/catch

Umieść fragmentów kodu, który może zgłaszać wyjątki w `try` bloku i umieść kod, który obsługuje wyjątki w `catch` bloku. `catch` Blok jest serię instrukcji rozpoczynające się od słowa kluczowego `catch`, a następnie typ wyjątku i akcji do wykonania.

Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch dopuszczalnych wyjątków. `Main` Metoda zawiera `try` zablokować z <xref:System.IO.StreamReader> instrukcji, która otwiera plik danych o nazwie `data.txt` i zapisuje ciąg z pliku. Po `try` blok `catch` bloku, który przechwytuje wszystkie wyjątki, będącą wynikiem `try` bloku.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Środowisko uruchomieniowe języka wspólnego przechwytuje wyjątki, które nie są objęte bloku catch. W zależności od sposobu skonfigurowania środowiska uruchomieniowego zostanie wyświetlone okno dialogowe debugowania, program zatrzymuje wykonywanie i pojawi się okno dialogowe z informacji o wyjątkach lub błąd jest drukowany stderr.

> [!NOTE] 
> Prawie każdego wiersza kodu może spowodować wyjątek, szczególnie wyjątki, które są generowane przez środowisko uruchomieniowe języka wspólnego, takich jak <xref:System.OutOfMemoryException>. Większość aplikacji, nie trzeba uwzględniać z następującymi wyjątkami, ale należy zwrócić uwagę tej możliwości podczas zapisywania bibliotek, które mają być używane przez innych użytkowników. Sugestie o tym, kiedy można ustawić kodu w bloku Try, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)
