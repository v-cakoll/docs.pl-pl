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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970862"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Jak przechwytywać wyjątki za pomocą bloku try/catch

Umieść wszystkie instrukcje kodu, które mogą zgłosić lub zgłosić wyjątek w `try` bloku i instrukcje miejsce używane do obsługi wyjątków lub wyjątków w co najmniej jeden `catch` poniższych bloków `try` bloku. Każdy `catch` blok zawiera typ wyjątku i może zawierać dodatkowe instrukcje niezbędne do obsługi tego typu wyjątku.

W poniższym przykładzie <xref:System.IO.StreamReader> otwiera plik o nazwie *data.txt* i pobiera wiersz z pliku. Ponieważ kod może zgłosić żadnego z trzema wyjątkami, jest umieszczany w `try` bloku. Trzy `catch` bloków rejestrować wyjątki i je obsłużyć, wyświetlając wyniki do konsoli.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Środowisko uruchomieniowe języka wspólnego (CLR) przechwytuje wyjątki, które nie są obsługiwane przez `catch` bloków. Jeśli wyjątek zostaje przechwycony przez środowisko CLR, może wystąpić jeden z następujących wyników w zależności od konfiguracji środowiska CLR:

- A **debugowania** pojawi się okno dialogowe.
- Program zatrzymuje wykonywanie i pojawi się okno dialogowe, za pomocą informacji o wyjątku.
- Błąd do drukowania do [błędu standardowego strumienia wyjściowego](xref:System.Console.Error).

> [!NOTE]
> Większość kodu może zgłosić wyjątek, a niektóre wyjątki, takie jak <xref:System.OutOfMemoryException>, mogą być generowane przez środowisko CLR, sama w dowolnym momencie. Gdy aplikacje nie są wymagane do czynienia z uwzględnieniem poniższych wyjątków, należy pamiętać o możliwości podczas zapisywania biblioteki ma być używany przez inne osoby. Sugestie, gdy można ustawić kodu w `try` blokowania, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Wyjątki](index.md)  
[Obsługa błędów operacji We/Wy na platformie .NET](../io/handling-io-errors.md)
