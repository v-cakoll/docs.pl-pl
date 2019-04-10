---
title: Obsługa SqlClient dla wysokiej dostępności, odzyskiwania po awarii
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 40054378319b81113dcb8f40cb82a8b1d02fc594
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307618"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Obsługa SqlClient dla wysokiej dostępności, odzyskiwania po awarii
W tym temacie omówiono Obsługa SqlClient (dodano w [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]) o wysokiej dostępności, odzyskiwania po awarii — zawsze włączonych grup dostępności.  Funkcja zawsze włączonych grup dostępności zostało dodane do programu SQL Server 2012. Aby uzyskać więcej informacji na temat zawsze włączonych grup dostępności zobacz dokumentację SQL Server — książki Online.  
  
 Teraz możesz określić dla odbiornika grupy dostępności (wysokiej dostępności, odzyskiwania po awarii) grupy dostępności (grupy dostępności) lub SQL Server 2012 wystąpienia klastra trybu Failover we właściwości połączenia. Jeśli aplikacja SqlClient jest połączona z bazą danych AlwaysOn w trybie Failover, oryginalne połączenie zostało przerwane i aplikacji, należy otworzyć nowe połączenie do kontynuowania pracy po przełączeniu w tryb failover.  
  
 Jeśli łączysz nie odbiornika grupy dostępności lub wystąpienia klastra trybu Failover programu SQL Server 2012 i wieloma adresami IP są skojarzone z nazwą hosta, SqlClient iteracji sekwencyjnie przez wszystkie adresy IP skojarzone z wpisem DNS. To może zająć dużo czasu, jeśli pierwszy adres IP zwrócony przez serwer DNS nie jest powiązany z dowolnej karty interfejsu sieciowego (NIC). Podczas nawiązywania połączenia z odbiornikiem grupy dostępności lub wystąpienia klastra trybu Failover programu SQL Server 2012, Klient SQL próbuje nawiązać połączenia z adresami IP wszystkich równolegle i jeśli próba połączenia zakończy się powodzeniem, sterownik zostanie odrzucić wszystkie oczekujące połączenie próby.  
  
> [!NOTE]
>  Zwiększenie limitu czasu połączenia i implementowanie logikę ponawiania próby połączenia zwiększy prawdopodobieństwo, że aplikacja połączy się z grupy dostępności. Ponadto ponieważ połączenia może zakończyć się niepowodzeniem z powodu przejścia w tryb failover, należy zaimplementować logikę ponawiania prób połączenia, ponawianie próby połączenia zakończone niepowodzeniem dopóki ponownie nawiązuje połączenie.  
  
 Następujące właściwości zostały dodane do SqlClient w [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]:  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 Programowe można zmodyfikować te słowa kluczowe parametrów połączenia przy użyciu:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  Ustawienie `MultiSubnetFailover` do `true` nie jest wymagane w przypadku [!INCLUDE[net_v461](../../../../../includes/net-v461-md.md)] lub nowszy.
  
## <a name="connecting-with-multisubnetfailover"></a>Connecting With MultiSubnetFailover  
 Zawsze określać `MultiSubnetFailover=True` podczas nawiązywania połączenia z odbiornikiem grupy dostępności programu SQL Server 2012 lub wystąpienia klastra trybu Failover programu SQL Server 2012. `MultiSubnetFailover` Umożliwia szybsze trybu failover dla wszystkich grup dostępności i wystąpienia klastra trybu Failover programu SQL Server 2012 i będzie znacznie skrócić czas pracy awaryjnej dla topologii AlwaysOn pojedynczych i wielu podsieci. Podczas pracy awaryjnej wiele podsieci klient podejmie próbę połączenia równolegle. Podczas pracy awaryjnej podsieci agresywnie ponowi próbę połączenia TCP.  
  
 `MultiSubnetFailover` Właściwości połączenia oznacza, że aplikacja jest wdrażana w grupie dostępności lub wystąpienia klastra trybu Failover programu SQL Server 2012 i SqlClient podejmie próbę połączenia z bazą danych na podstawowe wystąpienie programu SQL Server, podejmując próbę Połącz z adresami IP. Gdy `MultiSubnetFailover=True` jest określona dla połączeń klienta ponawia próby połączeń TCP szybciej niż interwały retransmisji TCP domyślny system operacyjny. Umożliwia to szybsze ponownego łączenia po włączeniu trybu failover grupy dostępności AlwaysOn lub wystąpienia klastra trybu Failover funkcji AlwaysOn oraz dotyczy zarówno subnet jednym i wielu grup dostępności i wystąpienia klastra trybu Failover.  
  
 Aby uzyskać więcej informacji na temat słów kluczowych z parametrów połączenia w SqlClient zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Określanie `MultiSubnetFailover=True` podczas nawiązywania połączenia z coś innego niż odbiornika grupy dostępności lub wystąpienia klastra trybu Failover programu SQL Server 2012 może spowodować negatywny wpływ na wydajność, a nie jest obsługiwane.  
  
 Aby połączyć się z serwerem w grupie dostępności lub wystąpienia klastra trybu Failover programu SQL Server 2012, użyj następujących wytycznych:  
  
-   Użyj `MultiSubnetFailover` właściwości połączenia podczas nawiązywania połączenia z jednej podsieci lub wiele podsieci; poprawi wydajność ich obu.  
  
-   Aby połączyć z grupy dostępności, należy określić odbiornika grupy dostępności grupy dostępności jako serwera w ciągu połączenia.  
  
-   Łączenie z serwerem SQL skojarzone z więcej niż 64 adresami IP wystąpienia spowoduje, że błąd połączenia.  
  
-   Zachowanie aplikacji, która używa `MultiSubnetFailover` właściwości połączenia nie ma wpływu na podstawie typu uwierzytelniania: Uwierzytelnianie programu SQL Server, uwierzytelnianie Kerberos lub uwierzytelniania Windows.  
  
-   Zwiększ wartość `Connect Timeout` do uwzględnienia czasu pracy awaryjnej i zmniejszyć próby połączenia w aplikacji.  
  
-   Transakcje rozproszone nie są obsługiwane.  
  
 Jeśli routing tylko do odczytu nie jest włączone, nawiązywania połączenia z lokalizacji pomocniczej repliki zakończy się niepowodzeniem w następujących sytuacjach:  
  
1. Jeśli lokalizacja replika pomocnicza nie jest skonfigurowany do akceptowania połączeń.  
  
2. Jeśli aplikacja używa `ApplicationIntent=ReadWrite` (omówionych poniżej) oraz lokalizacji replika pomocnicza jest skonfigurowana dla dostępu tylko do odczytu.  
  
 <xref:System.Data.SqlClient.SqlDependency> nie jest obsługiwana w trybie tylko do odczytu replikach pomocniczych.  
  
 Połączenie zakończy się niepowodzeniem, jeśli replika podstawowa jest skonfigurowany do odrzucania obciążeń tylko do odczytu i parametry połączenia zawierają `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Uaktualnianie do użycia wielu podsieci klastrów funkcji dublowania baz danych  
 Błąd połączenia (<xref:System.ArgumentException>) wystąpi `MultiSubnetFailover` i `Failover Partner` połączenia słowa kluczowe są obecne w parametrach połączenia lub jeśli `MultiSubnetFailover=True` i protokołu innego niż TCP jest używany. Błąd (<xref:System.Data.SqlClient.SqlException>) również wystąpić, jeśli `MultiSubnetFailover` jest używany i programu SQL Server zwraca odpowiedź partnera pracy awaryjnej wskazujący, że jest częścią pary dublowania bazy danych.  
  
 Jeśli zaktualizujesz aplikację SqlClient obecnie używa funkcji dublowania baz danych w scenariuszu wiele podsieci, należy usunąć `Failover Partner` właściwości połączenia i zastąp go wartością `MultiSubnetFailover` równa `True` i zastąp nazwę serwera w Parametry połączenia przy użyciu odbiornika grupy dostępności. Jeśli korzysta z parametrów połączenia `Failover Partner` i `MultiSubnetFailover=True`, sterownik spowoduje wygenerowanie błędu. Jednakże jeśli używa parametrów połączenia `Failover Partner` i `MultiSubnetFailover=False` (lub `ApplicationIntent=ReadWrite`), aplikacja będzie używać funkcji dublowania baz danych.  
  
 Sterownik zwróci błąd, jeśli funkcja dublowania bazy danych jest używana na podstawowej bazy danych w grupy dostępności, a `MultiSubnetFailover=True` jest używany w parametrach połączenia, który nawiązuje połączenie z podstawowej bazy danych zamiast na odbiornik grupy dostępności.  
  
## <a name="specifying-application-intent"></a>Określanie przeznaczenia aplikacji  
 Gdy `ApplicationIntent=ReadOnly`, klient żąda obciążenia odczytu podczas nawiązywania połączenia z bazą danych z włączoną funkcją AlwaysOn. Serwer będzie wymuszać zamiar w trakcie połączenia i podczas instrukcja USE bazy danych, ale tylko do zawsze włączone bazy danych.  
  
 `ApplicationIntent` — Słowo kluczowe nie działa dla starszej wersji, tylko do odczytu bazy danych.  
  
 Bazę danych można zezwolić lub nie zezwalaj na obciążeniami odczytu w docelowej bazie danych zawsze włączonych. (Jest to zrobić za pomocą `ALLOW_CONNECTIONS` klauzuli `PRIMARY_ROLE` i `SECONDARY_ROLE`[!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji.)  
  
 `ApplicationIntent` Słowo kluczowe jest używane, aby umożliwić routing tylko do odczytu.  
  
## <a name="read-only-routing"></a>Routing tylko do odczytu  
 Routing tylko do odczytu jest funkcją, która może zapewnić dostępność odczytu jedyną repliką bazy danych. Aby włączyć routing tylko do odczytu:  
  
1. Musisz połączyć się odbiornik grupy dostępności zawsze włączonej grupy dostępności.  
  
2. `ApplicationIntent` Słowo kluczowe parametrów połączenia musi być równa `ReadOnly`.  
  
3. Grupa dostępności musi być skonfigurowany przez administratora bazy danych, aby umożliwić routing tylko do odczytu.  
  
 Istnieje możliwość, że wiele połączeń przy użyciu routingu tylko do odczytu nie wszystkie będą łączyć z tej samej repliki tylko do odczytu. Zmiany w synchronizacji bazy danych lub zmiany w konfiguracji routingu serwera może powodować połączeń klientów z różnych replik tylko do odczytu. Aby upewnić się, że wszystkie żądania tylko do odczytu połączyć się z tym samym repliki tylko do odczytu, nie przekazuj odbiornik grupy dostępności do `Data Source` słowo kluczowe parametrów połączenia. Zamiast tego należy określić nazwę wystąpienia tylko do odczytu.  
  
 Routing tylko do odczytu może trwać dłużej niż łączenie do podstawowej, ponieważ odczytu tylko routing najpierw łączy się podstawowym, a następnie szuka najlepsze dostępne pomocniczego do odczytu. W związku z tym należy zwiększyć swoje limit czasu logowania.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Serwera SQL i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
