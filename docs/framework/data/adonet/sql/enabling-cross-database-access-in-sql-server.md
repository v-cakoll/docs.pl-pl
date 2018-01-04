---
title: "Włączanie dostępu między bazami danych w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 56de7da4c0883c9fe209a221c36457ef8b617a18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Włączanie dostępu między bazami danych w programie SQL Server
Łańcucha między bazami danych własność występuje, gdy procedura w jednej bazie danych jest zależna od obiektów w innej bazie danych. Łańcuch własności między bazami danych działa w taki sam sposób jak własność łańcucha w ramach pojedynczej bazy danych, z tą różnicą, że łańcucha własności nieprzerwany wymaga, aby wszystkich właścicieli obiektów są mapowane do tego samego konta logowania. Jeśli obiekt źródłowy w źródłowej bazy danych i obiektów docelowych w z docelowymi bazami danych są własnością tego samego konta logowania, programu SQL Server nie sprawdza uprawnienia do obiektów docelowych.  
  
## <a name="off-by-default"></a>Domyślnie wyłączone  
 Własność łańcucha między bazami danych jest domyślnie wyłączona. Firma Microsoft zaleca wyłączenie łańcucha własności między bazami danych, ponieważ ujawnia on należy do następujących zagrożenia bezpieczeństwa:  
  
-   Bazy danych właścicieli i członkowie `db_ddladmin` lub `db_owners` ról bazy danych można tworzyć obiektów, które są własnością innych użytkowników. Te obiekty potencjalnie może kierować obiektów w innych bazach danych. Oznacza to, że po włączeniu procesu tworzenia łańcucha między bazami danych własności musi pełnego zaufania, tych użytkowników z danymi w wszystkie bazy danych.  
  
-   Użytkownicy mający uprawnienie CREATE DATABASE można tworzyć nowych baz danych i dołączać istniejącej bazy danych. Jeśli włączono tworzenie łańcucha między bazami danych własność tych użytkowników są dostępne obiektów w innych bazach danych, które mogą nie mieć uprawnień nowo utworzony lub dołączone baz danych, które tworzą.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Włączanie łańcucha własności między bazami danych  
 Tworzenie łańcucha między bazami danych własność powinna być włączona tylko w środowiskach, w którym można w pełni zaufane uprawnieniach użytkowników. Można skonfigurować podczas instalacji dla wszystkich baz danych lub selektywnie dla baz danych przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] polecenia `sp_configure` i `ALTER DATABASE`.  
  
 Aby selektywnie skonfigurować tworzenie łańcucha własności między bazami danych, użyj `sp_configure` jej wyłączenia serwera. Następnie za pomocą polecenia ALTER DATABASE USTAWIĆ ON DB_CHAINING skonfigurować tworzenie łańcucha tylko baz danych, które tego wymagają własności między bazami danych.  
  
 Poniższy przykład powoduje włączenie łańcucha między bazami danych własności dla wszystkich baz danych:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Poniższy przykład powoduje włączenie łańcucha między bazami danych własności dla baz danych:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dynamiczne SQL  
 Tworzenie łańcucha własności między bazami danych nie działa w przypadku, gdy utworzony dynamicznie instrukcji SQL są wykonywane, chyba że ten sam użytkownik istnieje w obu bazach danych. Można obejść to w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] , tworząc procedury przechowywanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywania procedury przy użyciu certyfikatu, który istnieje w obu bazach danych. To umożliwia użytkownikom dostęp do zasobów bazy danych używane przez procedurę bez przyznawania im dostępu do bazy danych lub uprawnieniami.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Rozszerzanie personifikacji bazy danych przy użyciu EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) i [Cross własność DB łańcucha opcja](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online.|Tematach opisano, jak skonfigurować tworzenie łańcucha między bazami danych własność wystąpienia [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
