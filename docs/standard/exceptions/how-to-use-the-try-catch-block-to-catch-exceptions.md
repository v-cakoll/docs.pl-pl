---
title: 'Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków'
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
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708469"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak używać bloku try/catch do wychwytywania wyjątków

Umieść wszelkie instrukcje kodu, które mogą `try` podnieść lub zgłosić wyjątek w bloku i umieścić instrukcje `catch` używane `try` do obsługi wyjątku lub wyjątków w jednym lub więcej bloków poniżej bloku. Każdy `catch` blok zawiera typ wyjątku i może zawierać dodatkowe instrukcje potrzebne do obsługi tego typu wyjątku.

W poniższym przykładzie <xref:System.IO.StreamReader> otwiera plik o nazwie *data.txt* i pobiera wiersz z pliku. Ponieważ kod może zgłosić jeden z trzech wyjątków, `try` jest umieszczony w bloku. Trzy `catch` bloki złapać wyjątki i obsługiwać je, wyświetlając wyniki do konsoli.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Common Language Runtime (CLR) przechwytuje wyjątki nie obsługiwane przez `catch` bloki. Jeśli wyjątek zostanie przechwycony przez clr, jeden z następujących wyników może wystąpić w zależności od konfiguracji CLR:

- Pojawi się okno dialogowe **Debugowania.**
- Program zatrzymuje wykonywanie i pojawia się okno dialogowe z informacjami o wyjątku.
- Błąd jest drukowany do [standardowego strumienia wyjściowego błędu](xref:System.Console.Error).

> [!NOTE]
> Większość kodu może zgłosić wyjątek, a <xref:System.OutOfMemoryException>niektóre wyjątki, takie jak , mogą być generowane przez clr się w dowolnym momencie. Chociaż aplikacje nie są wymagane do radzenia sobie z tymi wyjątkami, należy pamiętać o możliwości podczas pisania bibliotek, które mają być używane przez inne osoby. Aby uzyskać sugestie dotyczące ustawiania `try` kodu w bloku, zobacz [Najważniejsze wskazówki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
- [Obsługa błędów we/wy w .NET](../io/handling-io-errors.md)
