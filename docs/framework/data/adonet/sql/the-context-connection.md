---
title: Połączenie kontekstu
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: e237bb53c699fd4bf051876a378c31b73a038502
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451814"
---
# <a name="the-context-connection"></a>Połączenie kontekstu
Problem z wewnętrznym dostępem do danych jest dość typowym scenariuszem. Oznacza to, że chcesz uzyskać dostęp do tego samego serwera, na którym jest wykonywana procedura składowana środowiska uruchomieniowego języka wspólnego (CLR). Jedną z opcji jest utworzenie połączenia przy użyciu <xref:System.Data.SqlClient.SqlConnection>, określenie parametrów połączenia wskazujących na serwer lokalny, a następnie otwarcie połączenia. Wymaga to określenia poświadczeń do logowania. Połączenie znajduje się w innej sesji bazy danych niż procedura składowana lub funkcja. może ona mieć różne `SET` opcje, w oddzielnym transakcjach, nie widzi tabel tymczasowych i tak dalej. Jeśli zarządzana procedura składowana lub kod funkcji jest wykonywany w procesie SQL Server, jest to spowodowane tym, że ktoś połączony z tym serwerem i wykonał instrukcję SQL, aby ją wywołać. Prawdopodobnie chcesz, aby procedura składowana lub funkcja była wykonywana w kontekście tego połączenia, wraz z jego transakcjami, `SET` opcjami i tak dalej. Jest to nazywane połączeniem kontekstu.  
  
 Połączenie kontekstu umożliwia wykonywanie instrukcji języka Transact-SQL w tym samym kontekście, w którym kod został wywołany w pierwszym miejscu. Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **SQL Server documentation (Dokumentacja programu SQL Server)**  
  
1. [Połączenie kontekstu](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie ADO.NET](../ado-net-overview.md)
