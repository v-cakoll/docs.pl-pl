---
title: Włączanie dostępu między bazami danych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 70b4b7b55311bfc5dba1b537a603e0d15d7f3d9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229670"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Włączanie dostępu między bazami danych w programie SQL Server
Tworzenie łańcucha własności między bazami danych występuje, gdy procedura w jednej bazie danych jest zależna od obiektów w innej bazie danych. Łańcucha własności między bazami danych działa w taki sam sposób jak łańcucha własności, w ramach pojedynczej bazy danych, z tą różnicą, że łańcucha własności nieprzerwany wymaga, że wszyscy właściciele obiektu są mapowane do tego samego konta logowania. Jeśli obiekt źródłowy w źródłowej bazie danych i obiektów docelowych w docelowych baz danych są własnością tego samego konta logowania, programu SQL Server nie sprawdza uprawnienia do obiektów docelowych.  
  
## <a name="off-by-default"></a>Funkcja domyślnie wyłączona  
 Własność łańcucha w bazach danych jest domyślnie wyłączona. Firma Microsoft zaleca wyłączenie łańcucha własności między bazami danych, ponieważ prezentuje następujące niebezpieczeństwa:  
  
-   Właściciele i członkowie bazy danych `db_ddladmin` lub `db_owners` ról bazy danych można tworzyć obiekty, które są własnością innych użytkowników. Te obiekty mogą potencjalnie kierować obiektów w innych bazach danych. Oznacza to, że jeśli włączysz tworzenie łańcucha własności między bazami danych, należy pełnego zaufania, tych użytkowników, danych we wszystkich bazach danych.  
  
-   Użytkownicy mający uprawnienie Tworzenie bazy danych można tworzyć nowe bazy danych i dołączanie istniejących baz danych. Jeśli włączono tworzenie łańcucha własności między bazami danych tych użytkowników może uzyskać dostęp do obiektów w innych bazach danych, które mogą nie mieć uprawnień z bazy danych nowo utworzone lub dołączone, które tworzą.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Włączanie łańcucha własności między bazami danych  
 Tworzenie łańcucha własności między bazami danych należy włączyć tylko w środowiskach, w którym można w pełni zaufane wysoce uprzywilejowanych użytkowników. Można skonfigurować podczas instalacji dla wszystkich baz danych lub selektywnie dla określonych baz danych przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] polecenia `sp_configure` i `ALTER DATABASE`.  
  
 Aby selektywnie skonfigurować tworzenie łańcucha własności między bazami danych, użyj `sp_configure` wyłączenia serwera. Następnie użyj polecenia ALTER DATABASE za pomocą zestawu ON DB_CHAINING do skonfigurowania własności między bazami danych, tworzenie łańcucha tylko bazy danych, które tego wymagają.  
  
 Poniższy przykład powoduje włączenie łańcucha własności między bazami danych, dla wszystkich baz danych:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Poniższy przykład powoduje włączenie łańcucha własności między bazami danych, do konkretnych baz danych:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dynamiczny język SQL  
 Tworzenie łańcucha własności między bazami danych nie działa w przypadku których dynamicznie utworzoną instrukcje SQL są wykonywane, chyba że ten sam użytkownik istnieje w obu bazach danych. Można obejść to w programie SQL Server, tworząc procedury przechowywanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywania procedury przy użyciu certyfikatu, który znajduje się w obu bazach danych. To zapewnia użytkownikom dostęp do zasobów bazy danych używane przez tę procedurę, bez nadawania im dostępu do bazy danych lub uprawnienia.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Rozszerzanie personifikacji bazy danych przy użyciu EXECUTE AS](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) i [obejmujące wiele własności DB łańcucha opcji](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).|Artykuły zawierają instrukcje dotyczące konfigurowania własności między bazami danych z łańcucha dla wystąpienia programu SQL Server.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
