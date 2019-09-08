---
title: Włączanie dostępu między bazami danych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: f69a405a562bfae3bc283f2b3166812046be868e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794182"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Włączanie dostępu między bazami danych w programie SQL Server
Tworzenie łańcucha własności między bazami danych odbywa się, gdy procedura w jednej bazie danych zależy od obiektów w innej bazie danych. Łańcuch własności między bazami danych działa w taki sam sposób jak w przypadku łańcucha własności w pojedynczej bazie danych, z tą różnicą, że nieuszkodzony łańcuch własności wymaga, aby wszyscy właściciele obiektów były zamapowane na to samo konto logowania. Jeśli obiekt źródłowy w źródłowej bazie danych i obiekty docelowe w docelowych bazach danych są własnością tego samego konta logowania, SQL Server nie sprawdza uprawnień do obiektów docelowych.  
  
## <a name="off-by-default"></a>Domyślnie wyłączone  
 Łańcuch własności między bazami danych jest domyślnie wyłączony. Firma Microsoft zaleca wyłączenie łańcucha własności między bazami danych, ponieważ ujawnia on następujące zagrożenia bezpieczeństwa:  
  
- Właściciele bazy danych i członkowie `db_ddladmin` `db_owners` lub role bazy danych mogą tworzyć obiekty należące do innych użytkowników. Obiekty te mogą być obiektami docelowymi w innych bazach danych. Oznacza to, że w przypadku włączenia łańcucha własności między bazami danych należy w pełni ufać tym użytkownikom z danymi we wszystkich bazach danych.  
  
- Użytkownicy z uprawnieniem Tworzenie bazy danych mogą tworzyć nowe bazy danych i dołączać istniejące bazy danych. W przypadku włączenia tworzenia łańcucha własności między bazami danych użytkownicy mogą uzyskać dostęp do obiektów w innych bazach danych, które mogą nie mieć uprawnień w nowo utworzonych lub dołączonych bazach danych.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Włączanie łańcucha własności między bazami danych  
 Tworzenie łańcucha własności między bazami danych powinno być włączone tylko w środowiskach, w których można w pełni ufać użytkownikom o wysokim poziomie uprawnień. Można ją skonfigurować podczas instalacji dla wszystkich baz danych lub selektywnie dla określonych baz danych przy użyciu poleceń `sp_configure` języka Transact-SQL i `ALTER DATABASE`programu.  
  
 Aby selektywnie konfigurować tworzenie łańcucha własności między bazami danych `sp_configure` , użyj, aby wyłączyć go dla serwera. Następnie użyj polecenia ALTER DATABASE z USTAWIENIEm DB_CHAINING ON, aby skonfigurować tworzenie łańcucha własności między bazami danych tylko dla baz danych, które tego wymagają.  
  
 Poniższy przykład włącza tworzenie łańcucha własności między bazami danych dla wszystkich baz danych:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Poniższy przykład włącza łańcuch własności między bazami danych dla określonych baz danych:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dynamiczny SQL  
 Tworzenie łańcucha własności między bazami danych nie działa w przypadkach, w których są wykonywane dynamiczne instrukcje SQL, chyba że ten sam użytkownik istnieje w obu bazach danych. Można obejść ten krok w SQL Server przez utworzenie procedury składowanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywanie procedury z certyfikatem, który istnieje w obu bazach danych. Zapewnia to użytkownikom dostęp do zasobów bazy danych używanych przez procedurę bez udzielania im dostępu do bazy danych lub uprawnień.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Rozszerzanie personifikacji bazy danych za pomocą opcji wykonaj jako](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) i przetworzenie [łańcucha własności dla wielu baz](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option)danych.|W artykule opisano sposób konfigurowania łańcucha własności między bazami danych dla wystąpienia SQL Server.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Rejestrowanie procedur składowanych w programie SQL Server](signing-stored-procedures-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
