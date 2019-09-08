---
title: Połączenie kontekstu
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 26578d0c6a5e4553e57673561f94090b9a1fd1a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791514"
---
# <a name="the-context-connection"></a>Połączenie kontekstu
Problem z wewnętrznym dostępem do danych jest dość typowym scenariuszem. Oznacza to, że chcesz uzyskać dostęp do tego samego serwera, na którym jest wykonywana procedura składowana środowiska uruchomieniowego języka wspólnego (CLR). Jedną z opcji jest utworzenie połączenia przy użyciu <xref:System.Data.SqlClient.SqlConnection>programu, określenie parametrów połączenia wskazujących na serwer lokalny, a następnie otwarcie połączenia. Wymaga to określenia poświadczeń do logowania. Połączenie znajduje się w innej sesji bazy danych niż procedura składowana lub funkcja, która może mieć różne `SET` opcje, jest w oddzielnym transakcjach, nie widzi tabel tymczasowych i tak dalej. Jeśli zarządzana procedura składowana lub kod funkcji jest wykonywany w procesie SQL Server, jest to spowodowane tym, że ktoś połączony z tym serwerem i wykonał instrukcję SQL, aby ją wywołać. Prawdopodobnie chcesz, aby procedura składowana lub funkcja była wykonywana w kontekście tego połączenia, wraz z jego transakcjami `SET` , opcjami i tak dalej. Jest to nazywane połączeniem kontekstu.  
  
 Połączenie kontekstu umożliwia wykonywanie instrukcji języka Transact-SQL w tym samym kontekście, w którym kod został wywołany w pierwszym miejscu. Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **Książka SQL Server online**  
  
1. [Połączenie kontekstu](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../ado-net-overview.md)
