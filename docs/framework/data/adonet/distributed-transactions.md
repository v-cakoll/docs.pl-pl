---
title: Transakcje rozproszone
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: f5ed99928534dc31832ac0baf1bb1bfa7e83ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956756"
---
# <a name="distributed-transactions"></a>Transakcje rozproszone
Transakcja to zestaw powiązanych zadań zakończonych powodzeniem (zatwierdzanie) lub niepowodzenie (przerwanie) jako jednostki, między innymi. *Transakcja rozproszona* to transakcja, która ma wpływ na kilka zasobów. Aby transakcja rozproszona została zatwierdzona, wszyscy uczestnicy muszą zagwarantować, że jakakolwiek zmiana danych będzie trwała. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli nawet pojedynczy uczestnik nie wykona tej gwarancji, cała transakcja zakończy się niepowodzeniem, a wszelkie zmiany danych w zakresie transakcji zostaną wycofane.  
  
> [!NOTE]
> Wyjątek zostanie wygenerowany, jeśli zostanie podjęta próba zatwierdzenia lub wycofania transakcji, jeśli `DataReader` zostanie ona uruchomiona, gdy transakcja jest aktywna.  
  
## <a name="working-with-systemtransactions"></a>Praca z System. Transactions  
 W .NET Framework transakcje rozproszone są zarządzane za pomocą interfejsu API w <xref:System.Transactions> przestrzeni nazw. <xref:System.Transactions> Interfejs API przekaże obsługę transakcji rozproszonych do monitora transakcji, takiego jak Microsoft Distributed Transaction Coordinator (MS DTC), gdy jest używanych wiele menedżerów zasobów trwałych. Aby uzyskać więcej informacji, zobacz temat [podstawy transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 W ADO.NET 2,0 wprowadzono obsługę rejestrowania w transakcji rozproszonej przy użyciu `EnlistTransaction` metody, która powoduje zarejestrowanie połączenia <xref:System.Transactions.Transaction> w wystąpieniu. W poprzednich wersjach ADO.NET jawna Rejestracja w transakcjach rozproszonych została wykonana `EnlistDistributedTransaction` przy użyciu metody połączenia, aby zarejestrować połączenie <xref:System.EnterpriseServices.ITransaction> w wystąpieniu, które jest obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. Aby uzyskać więcej informacji na temat transakcji usług przedsiębiorstwa, zobacz Współdziałanie [z usługami przedsiębiorstwa i transakcjami modelu COM+](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 W przypadku korzystania <xref:System.Transactions> z transakcji z dostawcą .NET Framework dla SQL Server z bazą danych SQL Server zostanie użyta <xref:System.Transactions.Transaction> wartość uproszczona. Transakcja może zostać następnie podwyższona do pełnej transakcji rozproszonej w razie potrzeby. Aby uzyskać więcej informacji, zobacz temat [integracja z usługą system. Transactions z SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
> Maksymalna liczba transakcji rozproszonych, w których jednocześnie może uczestniczyć baza danych Oracle, jest domyślnie ustawiona na 10. Po dziesiątej transakcji po nawiązaniu połączenia z bazą danych Oracle zostanie zgłoszony wyjątek. Firma Oracle nie obsługuje `DDL` transakcji rozproszonej.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Automatyczne rejestrowanie w transakcji rozproszonej  
 Automatyczna rejestracja jest domyślnym (i preferowanym) sposobem integrowania połączeń ADO.NET z `System.Transactions`usługą. Obiekt połączenia zostanie automatycznie zarejestrowany w istniejącej transakcji rozproszonej, jeśli ustali, że transakcja jest aktywna, co `System.Transaction` oznacza, że `Transaction.Current` nie ma wartości null. Automatyczne rejestracje transakcji odbywa się po otwarciu połączenia. Nie nastąpi to nawet wtedy, gdy polecenie jest wykonywane wewnątrz zakresu transakcji. Funkcję autorejestracji można wyłączyć w istniejących transakcjach, `Enlist=false` określając jako parametr parametrów połączenia <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>dla parametru lub `OLE DB Services=-7` parametry połączenia dla elementu <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji o parametrach parametrów połączenia Oracle i ODBC <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> , <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>Zobacz i.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Ręczne rejestrowanie w transakcji rozproszonej  
 Jeśli funkcja autorejestracji jest wyłączona lub konieczne jest zarejestrowanie transakcji, która została uruchomiona po otwarciu połączenia, można zarejestrować się w istniejącej transakcji rozproszonej przy użyciu `EnlistTransaction` metody <xref:System.Data.Common.DbConnection> obiektu dla dostawcy, z którym pracujesz. się. Rejestracja w istniejącej transakcji rozproszonej zapewnia, że jeśli transakcja zostanie zatwierdzona lub wycofana, modyfikacje wprowadzone przez kod w źródle danych zostaną zatwierdzone lub wycofane.  
  
 Rejestrowanie w transakcjach rozproszonych jest szczególnie stosowane podczas puli obiektów firmowych. Jeśli obiekt biznesowy jest w puli z otwartym połączeniem, automatyczne rejestrację transakcji odbywa się tylko wtedy, gdy to połączenie jest otwarte. Jeśli wiele transakcji jest wykonywanych przy użyciu obiektu biznesowego w puli, otwarte połączenie dla tego obiektu nie zostanie automatycznie zarejestrowane w nowo zainicjowanych transakcjach. W takim przypadku można wyłączyć automatyczne rejestrowanie transakcji dla połączenia i zarejestrować połączenie w transakcjach za pomocą programu `EnlistTransaction`.  
  
 `EnlistTransaction`przyjmuje pojedynczy argument typu <xref:System.Transactions.Transaction> , który jest odwołaniem do istniejącej transakcji. Po wywołaniu `EnlistTransaction` metody połączenia wszystkie modyfikacje wprowadzone w źródle danych przy użyciu połączenia są uwzględniane w transakcji. Przekazanie wartości null umożliwia odrejestrowanie połączenia z bieżącej rejestracji transakcji rozproszonej. Należy pamiętać, że połączenie musi zostać otwarte przed `EnlistTransaction`wywołaniem.  
  
> [!NOTE]
> Gdy połączenie zostanie jawnie zarejestrowane w transakcji, nie można go wyrejestrować lub zarejestrować w innej transakcji do momentu zakończenia pierwszej transakcji.  
  
> [!CAUTION]
>  `EnlistTransaction`zgłasza wyjątek, jeśli połączenie już rozpoczęło transakcję przy użyciu <xref:System.Data.Common.DbConnection.BeginTransaction%2A> metody połączenia. Jeśli jednak transakcja jest transakcją lokalną uruchomioną w źródle danych (na przykład w przypadku wykonywania instrukcji BEGIN TRANSACTION jawnie używającej <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` program wycofa transakcję lokalną i zarejestrowany w istniejącej dystrybucji transakcja zgodnie z żądaniem. Nie otrzymasz powiadomienia, że lokalna transakcja została wycofana, i musi zarządzać wszelkimi lokalnymi transakcjami, <xref:System.Data.Common.DbConnection.BeginTransaction%2A>które nie zostały rozpoczęte przy użyciu. Jeśli używasz dostawca danych .NET Framework dla SQL Server (`SqlClient`) z SQL Server, próba zarejestrowania spowoduje zgłoszenie wyjątku. Wszystkie inne przypadki nie zostaną wykryte.  
  
## <a name="promotable-transactions-in-sql-server"></a>Promocja transakcji w SQL Server  
 SQL Server obsługuje operacje promocji, w których lokalna transakcja uproszczona może zostać automatycznie podwyższona do transakcji rozproszonej tylko wtedy, gdy jest to wymagane. Transakcja promocji nie wywołuje dodanego nakładu transakcji rozproszonej, chyba że jest wymagane dodatkowe obciążenie. Aby uzyskać więcej informacji i przykład kodu, zobacz [System. Transactions Integration with SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Konfigurowanie transakcji rozproszonych  
 Może być konieczne włączenie usługi MS DTC przez sieć w celu korzystania z transakcji rozproszonych. Jeśli Zapora systemu Windows jest włączona, należy zezwolić usłudze MS DTC na korzystanie z sieci lub otworzyć port usługi MS DTC.  
  
## <a name="see-also"></a>Zobacz także

- [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
