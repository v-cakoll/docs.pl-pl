---
title: Śledzenie danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: df49fc7a5f7c437132a4dc24ed7f18492d9e7647
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583783"
---
# <a name="data-tracing-in-adonet"></a>Śledzenie danych w ADO.NET

ADO.NET funkcji funkcja śledzenia danych wbudowane, który jest obsługiwany przez dostawcę danych .NET dla programu SQL Server, Oracle, OLE DB i ODBC, a także ADO.NET <xref:System.Data.DataSet>i protokoły sieciowe programu SQL Server.

Śledzenie danych dostęp do interfejsu API może pomóc w diagnozowaniu następujące problemy:

- Niezgodność schematów między program kliencki a bazą danych.

- Baza danych niedostępność lub biblioteka problemów z siecią.

- Niepoprawne SQL czy ciężko kodowanego generowanych przez aplikację.

- Niepoprawne logikę programistyczną.

- Problemów wynikających z interakcji między wieloma składnikami ADO.NET lub między ADO.NET i własnych składników.

Aby zapewnić obsługę śledzenia różne technologie, śledzenia jest rozszerzalny, więc deweloper śledzenia problemu na dowolnym poziomie stosu aplikacji. Chociaż śledzenia nie jest to funkcja przeznaczona tylko do ADO.NET, dostawców firmy Microsoft zalet uogólnionego śledzenie i Instrumentacja interfejsów API.

Aby uzyskać więcej informacji na temat i konfigurowanie zarządzanych śledzenia w ADO.NET, zobacz [dostęp do danych śledzenia](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Uzyskiwanie dostępu do informacji diagnostycznych w dzienniku zdarzeń rozszerzonych

W .NET Framework Data Provider for SQL Server, dostępu do danych śledzenia ([śledzenie dostępu do danych](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) został zaktualizowany, aby ułatwić ułatwia korelowanie zdarzeń klienta z informacje diagnostyczne, takie jak błędy połączenia z łączność serwera cyklicznego buforu i aplikacji informacje o wydajności w dzienniku zdarzeń rozszerzonych. Aby uzyskać informacje o odczytywaniu dziennika zdarzeń rozszerzonych, zobacz [dane sesji zdarzeń widoku](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

W przypadku operacji połączenia ADO.NET wyśle klientowi identyfikator połączenia. Jeśli połączenie nie powiedzie się, możesz uzyskać dostęp bufor cykliczny łączności ([rozwiązywania problemów z łącznością w programie SQL Server 2008 buforem pierścienia łączności](https://go.microsoft.com/fwlink/?LinkId=207752)) i Znajdź `ClientConnectionID` pola, a następnie uzyskaj informacje diagnostyczne o Błąd połączenia. Identyfikatory połączenia klienta są rejestrowane w bufor cykliczny, tylko wtedy, gdy wystąpi błąd. (Jeśli połączenie nie powiedzie się przed wysłaniem identyfikatora pakietu, identyfikator połączenia klienta nie będą generowane.) Identyfikator połączenia klienta jest 16-bajtowy identyfikator GUID. Połączenia klienta można także znaleźć IDENTYFIKATORA w danych wyjściowych docelowej rozszerzonych zdarzeń, jeśli `client_connection_id` akcja zostanie dodany do zdarzenia w sesji zdarzeń rozszerzonych. Można włączyć śledzenie dostępu do danych i uruchom ponownie polecenie połączenia i obserwować `ClientConnectionID` pole Śledzenie dostępu do danych, jeśli potrzebujesz dodatkowej pomocy diagnostycznych sterownika klienta.

Klienta można uzyskać Identyfikatora połączenia programowo przy użyciu `SqlConnection.ClientConnectionID` właściwości.

`ClientConnectionID` Jest dostępna dla <xref:System.Data.SqlClient.SqlConnection> obiekt, który pomyślnie nawiąże połączenie. Jeśli próba połączenia zakończy się niepowodzeniem, `ClientConnectionID` mogą być dostępne za pośrednictwem `SqlException.ToString`.

ADO.NET wysyła również identyfikator działania właściwe dla wątków. Jeśli sesje są uruchamiane z włączoną opcją TRACK_CAUSALITY, identyfikator działania są przechwytywane w sesji zdarzeń rozszerzonych. Problemy z wydajnością z aktywnym połączeniem, możesz uzyskać identyfikator działania od śledzenie dostępu do danych klienta (`ActivityID` pole) i zlokalizuj identyfikator działania w danych wyjściowych zdarzeń rozszerzonych. Identyfikator działania w ramach zdarzeń rozszerzonych jest 16-bajtowy identyfikator GUID (nie taka sama jak identyfikator GUID dla Identyfikatora połączenia klienta) dołączany wraz z liczbą sekwencji czwartego bajtu. Numer sekwencyjny reprezentuje kolejność żądania w wątku i wskazuje względną kolejność usługi batch oraz instrukcje RPC dla wątku. `ActivityID` Obecnie opcjonalnie jest wysyłana dla instrukcji przetwarzania wsadowego SQL i żądania RPC, gdy jest włączone śledzenie dostępu do danych i 18 bitu dostępu do danych, śledzenie konfiguracji w programie word jest włączona.

Oto przykład, który używa [!INCLUDE[tsql](../../../../includes/tsql-md.md)] można uruchomić sesji zdarzeń rozszerzonych, będą przechowywane w bufor cykliczny, która zarejestruje identyfikator działania wysłane przez klienta na operacje RPC i usługi batch.

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

- [Śledzenie sieci w programie .NET Framework](../../../../docs/framework/network-programming/network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
