---
title: 'Instrukcje: używanie bloku try-catch do przechwytywania wyjątków'
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eaa389f461e70aae41f2e09437fd725a3bcefa5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696718"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak przechwytywać wyjątki przy użyciu bloku try/catch

Umieść wszystkie instrukcje Code, które mogą podnieść lub zgłosić wyjątek w bloku `try` i umieścić instrukcje używane do obsługi wyjątku lub wyjątków w co najmniej jednym bloku `catch` poniżej bloku `try`. Każdy blok `catch` zawiera typ wyjątku i może zawierać dodatkowe instrukcje, które są konieczne do obsłużenia tego typu wyjątku.

W poniższym przykładzie <xref:System.IO.StreamReader> otwiera plik o nazwie *Data. txt* i pobiera wiersz z pliku. Ponieważ kod może zgłosić którykolwiek z trzech wyjątków, zostanie umieszczony w bloku `try`. Trzy `catch` bloków przechwytują wyjątki i obsługują je, wyświetlając wyniki w konsoli.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Aparat plików wykonywalnych języka wspólnego (CLR) przechwytuje wyjątki, które nie są obsługiwane przez bloki `catch`. W przypadku przechwyconego wyjątku przez środowisko CLR może wystąpić jeden z następujących wyników w zależności od konfiguracji środowiska CLR:

- Zostanie wyświetlone okno dialogowe **debugowanie** .
- Program przerywa wykonywanie i pojawia się okno dialogowe z informacjami o wyjątku.
- Wystąpił błąd podczas drukowania [strumienia wyjściowego błędu standardowego](xref:System.Console.Error).

> [!NOTE]
> Większość kodu może zgłosić wyjątek, a niektóre wyjątki, takie jak <xref:System.OutOfMemoryException>, mogą być zgłaszane przez samo środowisko CLR w dowolnym momencie. Chociaż aplikacje nie są wymagane do obsługi tych wyjątków, należy pamiętać o możliwości, gdy pisanie bibliotek ma być używane przez inne osoby. Aby uzyskać sugestie dotyczące sposobu ustawiania kodu w bloku `try`, zobacz [najlepsze rozwiązania dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
- [Obsługa błędów we/wy w programie .NET](../io/handling-io-errors.md)
