---
title: Śledzenie danych
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 2b2a33739619ba09e56d4cc9ce99c51423678918
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980226"
---
# <a name="data-tracing-in-adonet"></a>Śledzenie danych w ADO.NET

Funkcja ADO.NET wbudowane funkcje śledzenia danych obsługiwane przez dostawców danych platformy .NET dla SQL Server, Oracle, OLE DB i ODBC, a także <xref:System.Data.DataSet>ADO.NET i SQL Server protokoły sieciowe.

Wywołania interfejsu API uzyskiwania dostępu do danych śledzenia mogą pomóc zdiagnozować następujące problemy:

- Niezgodność schematu między programem klienckim a bazą danych.

- Problemy z niedostępnością lub biblioteką sieciową bazy danych.

- Nieprawidłowo zakodowane lub wygenerowane przez aplikację.

- Nieprawidłowa logika programowania.

- Problemy wynikłe z interakcji między wieloma składnikami ADO.NET lub między ADO.NET i własnymi składnikami.

Aby zapewnić obsługę różnych technologii śledzenia, śledzenie jest rozszerzalne, dzięki czemu deweloper może śledzić problem na dowolnym poziomie stosu aplikacji. Chociaż śledzenie nie jest funkcją ADO.NET, dostawcy firmy Microsoft wykorzystują uogólnione interfejsy API śledzenia i instrumentacji.

Aby uzyskać więcej informacji na temat ustawiania i konfigurowania zarządzanego śledzenia w programie ADO.NET, zobacz [Śledzenie dostępu do danych](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Uzyskiwanie dostępu do informacji diagnostycznych w dzienniku zdarzeń rozszerzonych

W .NET Framework Dostawca danych na potrzeby SQL Server funkcja śledzenia dostępu do danych ([Śledzenie dostępu do danych](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) została zaktualizowana w celu ułatwienia skorelowania zdarzeń klienta z informacjami diagnostycznymi, takimi jak błędy połączeń, z buforu i informacji o wydajności aplikacji serwera w dzienniku zdarzeń rozszerzonych. Informacje dotyczące odczytywania dziennika zdarzeń rozszerzonych znajdują się w temacie [Wyświetlanie danych sesji zdarzeń](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

W przypadku operacji połączenia ADO.NET wyśle identyfikator połączenia klienta. Jeśli połączenie nie powiedzie się, można uzyskać dostęp do buforu pierścienia łączności ([Rozwiązywanie problemów z łącznością w SQL Server 2008 z buforem pierścieni łączności](https://docs.microsoft.com/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)) i znaleźć pole `ClientConnectionID` i uzyskać informacje diagnostyczne dotyczące błędu połączenia. Identyfikatory połączeń klientów są rejestrowane w buforze pierścieni tylko w przypadku wystąpienia błędu. (Jeśli połączenie nie powiedzie się przed wysłaniem pakietu przed zalogowaniem, identyfikator połączenia klienta nie zostanie wygenerowany). Identyfikator połączenia klienta jest 16-bajtowym identyfikatorem GUID. Identyfikator połączenia klienta można również znaleźć w danych wyjściowych obiektów docelowych zdarzeń rozszerzonych, jeśli akcja `client_connection_id` zostanie dodana do zdarzeń w sesji zdarzeń rozszerzonych. Można włączyć śledzenie dostępu do danych i ponownie uruchomić polecenie połączenia i obserwować pole `ClientConnectionID` w śladie dostępu do danych, jeśli potrzebujesz dalszej pomocy diagnostycznej sterownika klienta.

Identyfikator połączenia klienta można uzyskać programowo przy użyciu właściwości `SqlConnection.ClientConnectionID`.

`ClientConnectionID` jest dostępny dla obiektu <xref:System.Data.SqlClient.SqlConnection>, który pomyślnie nawiąże połączenie. Jeśli próba połączenia nie powiedzie się, `ClientConnectionID` może być dostępna za pośrednictwem `SqlException.ToString`.

ADO.NET wysyła także identyfikator działania specyficzny dla wątku. Identyfikator działania jest przechwytywany w sesji zdarzeń rozszerzonych, jeśli sesje są uruchamiane z włączoną opcją TRACK_CAUSALITY. W przypadku problemów z wydajnością z aktywnym połączeniem można uzyskać identyfikator działania z poziomu śledzenia dostępu do danych klienta (`ActivityID` pole), a następnie zlokalizować identyfikator działania w danych wyjściowych zdarzeń rozszerzonych. Identyfikator działania w zdarzeniach rozszerzonych to 16-bajtowy identyfikator GUID (nie taki sam jak identyfikator GUID identyfikatora połączenia klienta) dołączony przy użyciu numeru sekwencyjnego z czterema bajtami. Numer sekwencyjny reprezentuje kolejność żądania w wątku i wskazuje względne porządkowanie instrukcji Batch i RPC dla wątku. `ActivityID` jest obecnie opcjonalnie wysyłane do instrukcji SQL Batch i żądań RPC, gdy włączone jest śledzenie dostępu do danych, a bit 18 w konfiguracji śledzenia dostępu do danych jest włączony.

Poniżej znajduje się przykład, który używa języka Transact-SQL do uruchamiania sesji zdarzeń rozszerzonych, która będzie przechowywana w buforze pierścieni i rejestrowania identyfikatora działania wysyłanego z klienta w ramach wywołań RPC i operacji wsadowych.

```sql
create event session MySession on server
add event connectivity_ring_buffer_recorded,
add event sql_statement_starting (action (client_connection_id)),
add event sql_statement_completed (action (client_connection_id)),
add event rpc_starting (action (client_connection_id)),
add event rpc_completed (action (client_connection_id))
add target ring_buffer with (track_causality=on)
```

## <a name="see-also"></a>Zobacz także

- [Śledzenie sieci w programie .NET Framework](../../network-programming/network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Omówienie ADO.NET](ado-net-overview.md)
