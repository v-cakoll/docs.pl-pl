---
title: Transakcje rozproszone
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: 7792a719a73ca5183d57bcecc5d346153d824570
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="distributed-transactions"></a>Transakcje rozproszone
Transakcja jest zestaw powiązanych zadań, który zakończy się powodzeniem (zatwierdzania) albo nie powiedzie się (przerwanie) jako jednostki, między innymi. A *transakcja rozproszona* transakcji, które ma wpływ na kilku zasobów. Transakcji rozproszonych można przekazać wszystkich uczestników musi zapewniać każda zmiana danych będą trwałe. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli jednego uczestnika nie powiedzie się gwarancji, cała transakcja nie powiedzie się i wycofać zmiany wprowadzone w danych w zakresie transakcji.  
  
> [!NOTE]
>  Zostanie wygenerowany wyjątek przy próbie przekazać ani wycofać transakcji, jeśli `DataReader` została uruchomiona, gdy transakcja jest aktywna.  
  
## <a name="working-with-systemtransactions"></a>Praca z System.Transactions  
 W programie .NET Framework, transakcje rozproszone są zarządzane za pośrednictwem interfejsu API w <xref:System.Transactions> przestrzeni nazw. <xref:System.Transactions> Interfejsu API będzie delegowane Obsługa monitorowania transakcji, takich jak Microsoft Distributed Transaction Coordinator (MS DTC) podczas obejmuje wiele menedżerowie zasobów trwałe transakcji rozproszonej. Aby uzyskać więcej informacji, zobacz [podstawy transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET 2.0 wprowadzono obsługę rejestracji w transakcji rozproszonej przy użyciu `EnlistTransaction` metodę, która współdziała z połączenia w <xref:System.Transactions.Transaction> wystąpienia. W poprzednich wersjach programu ADO.NET, wykonano jawnej rejestracji w transakcji rozproszonych za pomocą `EnlistDistributedTransaction` metodę połączenia można zarejestrować połączenie w <xref:System.EnterpriseServices.ITransaction> wystąpienia, która jest obsługiwana w przypadku zapewnienia zgodności. Aby uzyskać więcej informacji na transakcje usług dla przedsiębiorstw, zobacz [współdziałanie z usługami przedsiębiorstwa i transakcje COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Korzystając z <xref:System.Transactions> transakcji z dostawcy programu .NET Framework dla programu SQL Server w bazie danych programu SQL Server, lekkie <xref:System.Transactions.Transaction> automatycznie będą używane. Następnie można można podwyższyć poziomu transakcji do pełnego transakcji rozproszonej na zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [System.Transactions integracji z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
>  Maksymalna liczba transakcji rozproszonych, które bazy danych programu Oracle mogą uczestniczyć w tym samym czasie jest ustawiony na 10 domyślnie. Po 10 transakcji podczas połączenia z bazą danych Oracle, jest zgłaszany wyjątek. Oracle nie obsługuje `DDL` wewnątrz transakcji rozproszonej.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Automatyczne rejestrowanie transakcji rozproszonej  
 Automatyczne umieszczanie jest ustawieniem domyślnym (i preferowany) sposób integrowania połączenia ADO.NET z `System.Transactions`. Obiekt połączenia zostanie automatycznie zarejestrować się w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna, która w `System.Transaction` warunki, oznacza, że `Transaction.Current` nie ma wartości null. Automatyczne transakcji rejestracji występuje po otwarciu połączenia. Go nie nastąpi po wykonaniu tej nawet, jeśli polecenie jest wykonywane w zakresie transakcji. Auto rejestracji w istniejącej transakcji można wyłączyć, określając `Enlist=false` jako parametr ciągu połączenia dla <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, lub `OLE DB Services=-7` jako parametr ciągu połączenia dla <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji na parametry ciągu połączenia Oracle i ODBC, zobacz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> i <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Ręczne rejestrowanie transakcji rozproszonej  
 Jeśli automatycznej rejestracji jest wyłączona lub musisz zarejestrować transakcji, która została uruchomiona po połączenie zostało otwarte, można zarejestrować się w istniejących przy użyciu transakcji rozproszonej `EnlistTransaction` metody <xref:System.Data.Common.DbConnection> obiektu dla dostawcy pracy z. Rejestrowanie w istniejącej transakcji rozproszonych zapewnia, że w przypadku transakcji jest zatwierdzona lub wycofana, zmiany dokonane przez kod w źródle danych zatwierdzona lub wycofana również.  
  
 Rejestrowanie w transakcjach rozproszonych jest szczególnie przydatny, gdy buforowanie obiektów biznesowych. Jeśli z otwartego połączenia w puli jest obiekt biznesowy, transakcji automatycznej rejestracji występuje tylko po otwarciu tego połączenia. Jeśli wiele transakcji są wykonywane przy użyciu obiektu biznesowego puli, otwartego połączenia dla tego obiektu zostanie nie automatycznie zarejestrować nowo inicjowane transakcji. W takim przypadku można wyłączyć automatyczne transakcji rejestracji dla połączenia i zarejestrować połączenie w transakcji za pomocą `EnlistTransaction`.  
  
 `EnlistTransaction` pobiera jeden argument typu <xref:System.Transactions.Transaction> oznacza to odwołanie do istniejącej transakcji. Po wywołaniu metody połączenia `EnlistTransaction` — metoda, wszystkie zmiany wprowadzone w źródła danych przy użyciu połączenia znajdują się w transakcji. Przekazana wartość null unenlists połączenie z jego bieżącym rejestracji transakcji rozproszonej. Należy pamiętać, że można otworzyć połączenia przed wywołaniem `EnlistTransaction`.  
  
> [!NOTE]
>  Gdy połączenie jest jawnie zarejestrowana w transakcji, nie może być usunięcie zarejestrowane lub zarejestrowane w innej transakcji zakończenie pierwszej transakcji.  
  
> [!CAUTION]
>  `EnlistTransaction` zgłasza wyjątek, jeśli połączenie zostało już uruchomione transakcji za pomocą połączenia <xref:System.Data.Common.DbConnection.BeginTransaction%2A> metody. Jednak jeśli transakcja jest transakcji lokalnej rozpoczęty o godzinie źródło danych (na przykład wykonywania instrukcji BEGIN TRANSACTION, jawnie za pomocą <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` będzie wycofać transakcji lokalnej i zarejestrować w istniejących rozproszonych Transakcja zgodnie z żądaniem. Nie będą otrzymywali Zwróć uwagę, że lokalne transakcja została wycofana i należy zarządzać wszystkich transakcji lokalnej nie uruchomiony przy użyciu <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. Jeśli używasz dostawcy danych programu .NET Framework dla programu SQL Server (`SqlClient`) z programem SQL Server, próba zarejestrować spowoduje zgłoszenie wyjątku. Wszystkich innych przypadkach będzie zostać wykryte.  
  
## <a name="promotable-transactions-in-sql-server"></a>Awansowanie transakcji w programie SQL Server  
 SQL Server obsługuje awansowanie transakcji, w których lekkich transakcji lokalnej może być automatycznie podwyższony do transakcji rozproszonej tylko wtedy, gdy jest to wymagane. Awansowanie transakcji nie jest wywoływany dodany narzutów transakcji rozproszonej, chyba że dodany jest wymagana. Aby uzyskać więcej informacji i przykładowy kod, zobacz [System.Transactions integracji z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Konfigurowanie transakcji rozproszonych  
 Należy włączyć MS DTC za pośrednictwem sieci, aby można było używać transakcji rozproszonych. Jeśli systemu Windows jest włączona zapora, należy zezwolić na użycie sieci lub Otwórz port MS DTC usługi MS DTC.  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
