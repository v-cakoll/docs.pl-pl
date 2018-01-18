---
title: "Obsługa SqlClient wysokiej dostępności, odzyskiwania po awarii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d2a444440af9dfaa2b084a55db9348fa48df7b54
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Obsługa SqlClient wysokiej dostępności, odzyskiwania po awarii
W tym temacie omówiono SqlClient pomocy technicznej (dodany w [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]) wysokiej dostępności, odzyskiwania po awarii — zawsze włączonych grup dostępności.  Funkcja zawsze włączonych grup dostępności zostało dodane do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012. Aby uzyskać więcej informacji na temat zawsze włączonych grup dostępności, zobacz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online.  
  
 Możesz teraz określić odbiornika grupy dostępności programu (wysokiej dostępności, odzyskiwania po awarii) grupy dostępności (grupy dostępności) lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 wystąpienia klastra trybu Failover we właściwości połączenia. Jeśli aplikacja SqlClient jest podłączony do bazy danych programu AlwaysOn awaryjnie, oryginalne połączenie zostanie przerwane i aplikacji, należy otworzyć nowe połączenie, aby kontynuować pracę po przejściu w tryb failover.  
  
 Jeśli nie łączysz się odbiornik grupy dostępności lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 wystąpienia klastra trybu Failover, a jeśli wiele adresów IP skojarzonych z nazwą hosta, SqlClient sekwencyjnie iteracji przez wszystkie adresy IP skojarzone z wpisu DNS. To może zająć dużo czasu, jeśli pierwszy adres IP zwrócony przez serwer DNS nie jest powiązany z dowolnej karty interfejsu sieciowego (NIC). Podczas nawiązywania połączenia odbiornika grupy dostępności lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 wystąpienia klastra trybu Failover, SqlClient podejmuje próbę nawiązania połączenia dla wszystkich adresów IP równolegle i jeśli próba połączenia zakończy się powodzeniem, sterownik spowoduje odrzucenie wszystkich oczekujących połączeń prób.  
  
> [!NOTE]
>  Zwiększenie limitu czasu połączenia i wykonania logiki ponawiania próby połączenia zwiększy prawdopodobieństwo, że aplikacja będzie łączyć się z grupy dostępności. Ponadto ponieważ połączenie może zakończyć się niepowodzeniem z powodu pracy awaryjnej, należy zaimplementować logiki ponawiania próby połączenia, ponawianie próby połączenia nie powiodło się, dopóki ponownie nawiązuje połączenie.  
  
 Następujące właściwości połączenia zostały dodane do SqlClient w [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]:  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 Te słowa kluczowe parametrów połączenia z można modyfikować programowo:  
  
1.  <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2.  <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  
  
## <a name="connecting-with-multisubnetfailover"></a>Łączenie z MultiSubnetFailover  
 Określ zawsze `MultiSubnetFailover=True` podczas nawiązywania połączenia [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] odbiornika grupy dostępności 2012 lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia klastra trybu Failover 2012. `MultiSubnetFailover`Włącza przyspieszyć tryb failover dla wszystkich grup dostępności i wystąpienia klastra trybu Failover w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 i znacznie zmniejsza czas pracy awaryjnej dla pojedynczych i wielu podsieci topologie AlwaysOn. Podczas pracy awaryjnej wielu podsieci klient podejmie próbę połączenia równolegle. Podczas pracy awaryjnej podsieci agresywnie ponowi próbę połączenia TCP.  
  
 `MultiSubnetFailover` Połączenia właściwość wskazuje, że aplikacja jest wdrażany w grupie dostępności lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia klastra trybu Failover 2012 i SqlClient podejmie próbę połączenia z bazą danych na serwerze podstawowym [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia przez próby nawiązania połączenia z adresami IP. Gdy `MultiSubnetFailover=True` jest określony dla połączenia, klient ponawia próby połączenia TCP szybciej niż przy użyciu protokołu TCP retransmisji systemu operacyjnego domyślne. Umożliwia szybsze ponowne nawiązanie połączenia po trybu failover grupy dostępności funkcji AlwaysOn lub zawsze włączone wystąpienia klastra trybu Failover i dotyczy zarówno subnet jednym i wielu grup dostępności i wystąpienia klastra trybu Failover.  
  
 Aby uzyskać więcej informacji na temat słowa kluczowe parametrów połączenia w SqlClient zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Określanie `MultiSubnetFailover=True` podczas nawiązywania połączenia z inną niż odbiornika grupy dostępności lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia klastra trybu Failover 2012 może spowodować negatywny wpływ na wydajność i nie jest obsługiwany.  
  
 Skorzystaj z poniższych wskazówek, aby połączyć się z serwerem w grupie dostępności lub [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia klastra trybu Failover 2012:  
  
-   Użyj `MultiSubnetFailover` właściwości połączenia podczas łączenia się z jednej podsieci lub wielu podsieci; poprawi wydajność ich obu.  
  
-   Aby połączyć się z grupy dostępności, określ odbiornika grupy dostępności grupy dostępności jako serwer w ciągu połączenia.  
  
-   Łączenie z [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia skonfigurowano więcej niż 64 adresy IP spowoduje błąd połączenia.  
  
-   Zachowanie aplikacji, która używa `MultiSubnetFailover` właściwość connection nie ma wpływu na podstawie typu uwierzytelniania: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] uwierzytelniania, uwierzytelnianie Kerberos lub uwierzytelnianie systemu Windows.  
  
-   Zwiększ wartość `Connect Timeout` przyjmować czas pracy awaryjnej i zmniejsza aplikacji połączenia ponownych prób.  
  
-   Transakcje rozproszone nie są obsługiwane.  
  
 Jeśli routingu tylko do odczytu nie jest włączone, połączenie z lokalizacją replika pomocnicza nie powiedzie się w następujących sytuacjach:  
  
1.  Jeśli lokalizacji replika pomocnicza nie jest skonfigurowany do akceptowania połączeń.  
  
2.  Jeśli aplikacja używa `ApplicationIntent=ReadWrite` (opisanych poniżej) i lokalizacja replika pomocnicza jest skonfigurowana dla dostępu tylko do odczytu.  
  
 <xref:System.Data.SqlClient.SqlDependency>nie jest obsługiwane w trybie tylko do odczytu replikach pomocniczych.  
  
 Połączenia zakończy się niepowodzeniem, jeśli replika podstawowa jest skonfigurowany do odrzucania obciążeń tylko do odczytu i parametry połączenia zawierają `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Uaktualnianie do użycia wielu podsieci klastrów z dublowania bazy danych  
 Błąd połączenia (<xref:System.ArgumentException>) zostanie przeprowadzona, jeśli `MultiSubnetFailover` i `Failover Partner` słowa kluczowe połączenia znajdują się w ciągu połączenia, lub jeśli `MultiSubnetFailover=True` i protokołu innego niż TCP jest używany. Wystąpił błąd (<xref:System.Data.SqlClient.SqlException>) również wystąpić, jeśli `MultiSubnetFailover` jest używany i [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] zwraca odpowiedź partnera pracy awaryjnej wskazujący, że jest częścią pary dublowania bazy danych.  
  
 W przypadku uaktualniania aplikacji SqlClient który aktualnie używa funkcji dublowania baz danych na potrzeby scenariusza wielu podsieci, należy usunąć `Failover Partner` właściwości połączenia i zastąpić go ciągiem `MultiSubnetFailover` ustawioną `True` i zastąp nazwę serwera w Parametry połączenia z odbiornika grupy dostępności. Jeśli parametry połączenia używane `Failover Partner` i `MultiSubnetFailover=True`, sterownik zostanie wygenerowany błąd. Jednak jeśli parametry połączenia używane `Failover Partner` i `MultiSubnetFailover=False` (lub `ApplicationIntent=ReadWrite`), aplikacja będzie używać funkcji dublowania baz danych.  
  
 Sterownik zwróci błąd, jeśli funkcja dublowania bazy danych jest używany w podstawowej bazy danych w grupy dostępności, a `MultiSubnetFailover=True` jest używany w parametrach połączenia, w którym łączy się z podstawowej bazy danych zamiast do odbiornika grupy dostępności.  
  
## <a name="specifying-application-intent"></a>Określanie przeznaczenia aplikacji  
 Gdy `ApplicationIntent=ReadOnly`, klient żąda odczytu obciążenie podczas łączenia się z bazą danych z włączoną funkcją AlwaysOn. Serwer będzie wymuszać zamiar w czasie połączenia i podczas użycie instrukcji bazy danych, ale tylko do zawsze włączone bazy danych.  
  
 `ApplicationIntent` — Słowo kluczowe nie działa z bazami danych starszy, tylko do odczytu.  
  
 Bazy danych można Zezwalaj lub nie zezwalaj odczytu obciążenie w docelowej bazie danych AlwaysOn. (Jest to zrobić za pomocą `ALLOW_CONNECTIONS` klauzuli `PRIMARY_ROLE` i `SECONDARY_ROLE` [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji.)  
  
 `ApplicationIntent` Słowo kluczowe jest używane, aby włączyć routing tylko do odczytu.  
  
## <a name="read-only-routing"></a>Tylko do odczytu routingu  
 Tylko do odczytu routing jest funkcją, która może zapewnić dostępność odczytu tylko repliki bazy danych. Aby włączyć routing tylko do odczytu:  
  
1.  Należy nawiązać odbiornik grupy dostępności zawsze włączonej grupy dostępności.  
  
2.  `ApplicationIntent` Słowo kluczowe parametrów połączenia musi mieć ustawioną `ReadOnly`.  
  
3.  Grupa dostępności musi być skonfigurowany przez administratora bazy danych, aby włączyć routing tylko do odczytu.  
  
 Istnieje możliwość, że wiele połączeń przy użyciu routingu tylko do odczytu nie wszystkie będą łączyć się sam repliki tylko do odczytu. Zmiany w synchronizacji bazy danych lub zmiany w konfiguracji routingu serwera może spowodować połączeń klientów z innej repliki tylko do odczytu. Aby upewnić się, że wszystkie żądania tylko do odczytu połączyć się z tej samej repliki tylko do odczytu, nie przekazuj odbiornika grupy dostępności, aby `Data Source` słowo kluczowe parametrów połączenia. Zamiast tego należy określić nazwę wystąpienia tylko do odczytu.  
  
 Tylko do odczytu routingu może trwać dłużej niż łączenie z serwera podstawowego, ponieważ odczytu tylko routing pierwszy raz łączy się serwerem podstawowym, a następnie szuka najlepiej dostępne dodatkowego do odczytu. W związku z tym należy zwiększyć limit czasu użytkownika logowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Serwera SQL i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
