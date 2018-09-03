---
title: Transakcje rozproszone
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: 1f45f572b4336e52f7eee224ec80d9b7f423f991
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486330"
---
# <a name="distributed-transactions"></a>Transakcje rozproszone
Transakcja jest zestaw powiązanych zadań, który zakończy się powodzeniem (zatwierdzenie) albo kończy się niepowodzeniem (przerwanie) jako jednostki, między innymi. A *transakcja rozproszona* jest transakcji, która ma wpływ na kilka zasobów. Dla rozproszonych można zatwierdzić transakcji wszyscy uczestnicy należy zagwarantować, że wszelkie zmiany danych będą trwałe. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli pojedynczego uczestnika nie powiedzie się gwarancji, cała transakcja nie powiedzie się, a wszelkie zmiany danych w zakresie transakcji zostaną przywrócone.  
  
> [!NOTE]
>  Jeśli spróbujesz przekazać ani wycofać transakcji, jeśli zostanie zgłoszony wyjątek `DataReader` została uruchomiona, gdy transakcja jest aktywny.  
  
## <a name="working-with-systemtransactions"></a>Praca z System.Transactions  
 W .NET Framework, transakcje rozproszone są zarządzane za pośrednictwem interfejsu API w <xref:System.Transactions> przestrzeni nazw. <xref:System.Transactions> API oddeleguje transakcji rozproszonej, obsługa monitorowania transakcji, takich jak Microsoft Distributed Transaction Coordinator (MS DTC), w przypadku wielu menedżerów zasobów trwałe związane. Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET w wersji 2.0 wprowadzono obsługę rejestrowanie w transakcji rozproszonych za pomocą `EnlistTransaction` metody, która pozyskuje połączenia w <xref:System.Transactions.Transaction> wystąpienia. W poprzednich wersjach programu ADO.NET, wykonano jawnej rejestracji transakcji rozproszonych za pomocą `EnlistDistributedTransaction` metody połączenia, aby zarejestrować połączenie w <xref:System.EnterpriseServices.ITransaction> wystąpienia, która jest obsługiwana w przypadku zapewnienia zgodności. Aby uzyskać więcej informacji na temat transakcji korporacyjnych usług, zobacz [współdziałanie z usługami przedsiębiorstwa i transakcjami COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Korzystając z <xref:System.Transactions> transakcji przy użyciu dostawcy programu .NET Framework dla programu SQL Server względem bazy danych programu SQL Server, lekkie <xref:System.Transactions.Transaction> automatycznie będą używane. Transakcja może być następnie podwyższony do pełnego transakcji rozproszonych na zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
>  Maksymalna liczba transakcji rozproszonych, które bazy danych Oracle mogą uczestniczyć w tym samym czasie jest ustawiony na 10 domyślnie. Po 10 transakcji po podłączeniu do bazy danych Oracle jest zgłaszany wyjątek. Oracle nie obsługuje `DDL` wewnątrz transakcji rozproszonej.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Automatyczne rejestrowanie w transakcji rozproszonych  
 Automatyczne umieszczanie jest ustawieniem domyślnym (i preferowana) sposób integrowania połączenia ADO.NET z `System.Transactions`. Obiekt połączenia będą automatycznie zarejestrować się w istniejącej transakcji rozproszonych, gdy ustali, że transakcja jest aktywny, która w `System.Transaction` warunki, oznacza to, że `Transaction.Current` nie ma wartości null. Rejestracja automatyczna transakcja występuje, gdy połączenie jest otwarte. Go nie nastąpi po tym nawet, jeśli polecenie jest wykonywane wewnątrz zakresu transakcji. Funkcja automatycznego rejestracji w istniejących transakcji można wyłączyć, określając `Enlist=false` jako parametr ciągu połączenia dla <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, lub `OLE DB Services=-7` jako parametr ciągu połączenia dla <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji na temat bazy danych Oracle i ODBC parametry połączenia, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> i <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Ręczne rejestrowanie w transakcji rozproszonych  
 Jeśli trzeba zarejestrować transakcji, która została uruchomiona po otwarto połączenie automatycznej rejestracji jest wyłączona, można zarejestrować się w istniejącej transakcji rozproszonych za pomocą `EnlistTransaction` metody <xref:System.Data.Common.DbConnection> obiektu dla dostawcy, w którym pracujesz za pomocą. Rejestrowanie w istniejącej transakcji rozproszonych zapewnia, że jeśli transakcja jest przekazana lub wycofana, zmiany dokonane przez kod w źródle danych będą się przekazana lub wycofana także.  
  
 Rejestrowanie w transakcji rozproszonych jest szczególnie przydatny, gdy buforowanie obiektów biznesowych. Jeśli obiektem biznesowym w puli za pomocą otwartego połączenia, rejestracji automatycznej transakcji występuje tylko po otwarciu tego połączenia. Jeśli wiele transakcji są wykonywane przy użyciu obiektu biznesowego pulpitów, otwartego połączenia dla tego obiektu zostanie nie automatycznie zarejestrować się w nowo inicjowane transakcji. W takim przypadku można wyłączyć rejestracji automatycznej transakcji dla połączenia i zarejestrować połączenie w transakcji za pomocą `EnlistTransaction`.  
  
 `EnlistTransaction` przyjmuje pojedynczy argument typu <xref:System.Transactions.Transaction> to znaczy odwołanie do istniejącej transakcji. Po wywołaniu tego połączenia `EnlistTransaction` metody, wszelkich zmian wprowadzonych w źródła danych przy użyciu połączenia znajdują się w transakcji. Przekazywanie wartości null unenlists połączenie z jego bieżącej rejestracji transakcji rozproszonej. Należy pamiętać, że można otworzyć połączenia przed wywołaniem `EnlistTransaction`.  
  
> [!NOTE]
>  Gdy połączenie jest jawnie zarejestrowana w transakcji, nie może być niezaznaczone zobowiązaniom lub zobowiązaniom w innej transakcji aż do zakończenia pierwszej transakcji.  
  
> [!CAUTION]
>  `EnlistTransaction` zgłasza wyjątek, jeśli połączenie już się rozpoczęło transakcji za pomocą połączenia <xref:System.Data.Common.DbConnection.BeginTransaction%2A> metody. Jednak jeśli transakcja jest transakcji lokalnej rozpoczęło się o źródle danych (na przykład wykonywania instrukcji BEGIN TRANSACTION, w sposób jawny przy użyciu <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` będzie wycofać transakcji lokalnej i zarejestrować w istniejących rozproszonych transakcji, zgodnie z żądaniem. Nie będą otrzymywali Zwróć uwagę, że lokalne transakcja została wycofana, a musi zarządzać wszystkie transakcje lokalne Nierozpoczęte przy użyciu <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. Jeśli używasz dostawcy danych .NET Framework dla programu SQL Server (`SqlClient`) z programem SQL Server, próba zarejestrować spowoduje zgłoszenie wyjątku. Wszystkich innych przypadkach zaczną niewykryte.  
  
## <a name="promotable-transactions-in-sql-server"></a>Awansowanie transakcji w programie SQL Server  
 SQL Server obsługuje awansowanie transakcji, w których uproszczone transakcji lokalnej może być automatycznie podwyższony do transakcji rozproszonych tylko wtedy, gdy jest to wymagane. Awansowanie transakcji nie jest wywoływany dodano obciążenie z transakcji rozproszonych, chyba że dodany obciążenie jest wymagana. Aby uzyskać więcej informacji i przykładowy kod, zobacz [integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Konfigurowanie transakcje rozproszone  
 Może być konieczne Włączanie MS DTC za pośrednictwem sieci, aby można było używać transakcji rozproszonych. Jeśli masz Windows włączona zapora, musisz zezwolić na usługę MS DTC, aby używała sieci ani nie otwieraj portu MS DTC.  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
