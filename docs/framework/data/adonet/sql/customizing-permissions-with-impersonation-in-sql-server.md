---
title: Dostosowywanie uprawnień personifikacji w programie SQL Server
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 182eadecbd5330f06fc1cd45d2c768b570f12bf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596972"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Dostosowywanie uprawnień personifikacji w programie SQL Server
Wiele aplikacji używa procedur składowanych na dostęp do danych, opierając się na łańcucha własności, aby ograniczyć dostęp do tabel podstawowych. Można przyznać uprawnień wykonywanie procedur składowanych, odwoływanie lub odmówienia uprawnień do tabel podstawowych. SQL Server nie sprawdza uprawnienia obiektu wywołującego, jeśli procedura składowana i tabele mają tego samego właściciela. Jednak tworzenie łańcucha własności nie działa w przypadku obiektów mieć różnych właścicieli lub w przypadku dynamiczny język SQL.  
  
 Możesz użyć EXECUTE AS klauzuli w procedurze składowanej, gdy obiekt wywołujący nie ma uprawnień do obiektów bazy danych. Efekt EXECUTE AS — klauzula jest kontekst wykonywania przestaje być wyświetlony dla użytkownika serwera proxy. Cały kod, jak również wszelkie wywołania zagnieżdżonych procedury składowane i wyzwalacze, jest wykonywany w kontekście zabezpieczeń użytkownika serwera proxy. Kontekst wykonywania zostanie przywrócona do oryginalnego obiektu wywołującego dopiero po wykonanie procedury lub po wygenerowaniu instrukcji REVERT.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Za pomocą EXECUTE AS do przełączania kontekstu — instrukcja  
 Instrukcja pozwala na przełączanie kontekstu wykonania instrukcji przez personifikacja innego użytkownika logowania lub bazy danych WYKONAJ AS języka Transact-SQL. To jest przydatną techniką do testowania zapytań i procedur jako inny użytkownik.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Musi mieć uprawnienia PERSONIFIKUJ logowania lub użytkownika, którego możesz podszyć się pod. To uprawnienie jest implikowane dla `sysadmin` dla wszystkich baz danych, a `db_owner` członkowie roli w bazach danych, które są właścicielami.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Udzielanie uprawnień za pomocą EXECUTE AS — klauzula  
 Możesz użyć EXECUTE AS klauzuli w nagłówku definicji procedury składowanej, wyzwalacza lub funkcji zdefiniowanej przez użytkownika (z wyjątkiem funkcji śródwierszowych wartościami przechowywanymi w tabeli). Powoduje to, że procedury są wykonywane w kontekście nazwy użytkownika lub określone w EXECUTE AS — słowo kluczowe klauzuli. W bazie danych, która nie jest zamapowany na nazwę logowania, udzielanie go tylko wymagane uprawnienia do obiektów, którego procedura uzyskuje, można utworzyć użytkownika serwera proxy. Dostęp do wszystkich obiektów wskazane w poleceniu EXECUTE klauzuli musi mieć uprawnienia tylko użytkownika serwera proxy przez moduł.  
  
> [!NOTE]
>  Niektóre akcje, takie jak TRUNCATE TABLE nie masz uprawnień przydzielenia. Dołączanie instrukcji w procedurze, a następnie określając użytkownika serwera proxy, który ma uprawnienia ALTER TABLE, można rozszerzyć uprawnienia, aby obciąć tabeli dla kodu wywołującego, którzy mają tylko uprawnień wykonywanie procedury.  
  
 Kontekst wskazane w poleceniu EXECUTE klauzula jest ważny przez czas trwania procedury, w tym zagnieżdżone procedury składowane i wyzwalacze. Kontekst powraca do obiektu wywołującego, po zakończeniu wykonywania lub wystawiono instrukcji REVERT.  
  
 Istnieją trzy kroki związane ze stosowaniem EXECUTE AS klauzuli w procedurze.  
  
1.  Utwórz użytkownika serwera proxy w bazie danych, która nie jest zamapowany na nazwę logowania. Nie jest to wymagane, ale pomaga związane z zarządzaniem uprawnieniami.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  Przyznaj użytkownikowi proxy wystarczających uprawnień.  
  
2.  Dodaj EXECUTE AS klauzuli, która procedura składowana lub funkcja zdefiniowana przez użytkownika.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Aplikacje, które wymagają inspekcji może przerwać, ponieważ nie jest zachowywana oryginalna kontekstu zabezpieczeń obiektu wywołującego. Wbudowane funkcje, które zwracają tożsamość bieżącego użytkownika, takie jak SESSION_USER, użytkownika lub nazwa_użytkownika, zwraca użytkownika skojarzonego z EXECUTE AS klauzuli, nie oryginalny obiekt wywołujący.  
  
### <a name="using-execute-as-with-revert"></a>EXECUTE AS przy użyciu operacji przywracania  
 Aby powrócić do oryginalnego kontekstu wykonywania, można użyć instrukcji języka Transact-SQL PRZYWRÓCIĆ.  
  
 Opcjonalna klauzula z nie PRZYWRÓCENIE pliku COOKIE = @variableName, umożliwia przełączenia kontekstu wykonania obiektu wywołującego, jeśli @variableName zmienna zawiera poprawną wartość. Pozwala na przełączanie kontekstu wykonania obiektu wywołującego w środowiskach, w których buforowanie połączeń jest używany. Ponieważ wartość @variableName jest znane tylko do obiektu wywołującego EXECUTE AS instrukcji, obiekt wywołujący może zagwarantować, że kontekst wykonywania nie można zmienić przez użytkownika końcowego, który wywołuje aplikację. Gdy połączenie jest zamknięte, wartość jest zwracana do puli. Aby uzyskać więcej informacji na temat połączenia buforowanie w ADO.NET, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Określając Kontekst wykonywania  
 Oprócz określenia użytkownika, można również użyć EXECUTE AS z dowolnymi z następujących słów kluczowych.  
  
-   OBIEKT WYWOŁUJĄCY. Trwa wykonywanie jako obiekt WYWOŁUJĄCY jest wartością domyślną; Jeśli żadna inna opcja jest określona, następnie procedura jest wykonywana w kontekście zabezpieczeń obiektu wywołującego.  
  
-   WŁAŚCICIEL. Trwa wykonywanie jako właściciel wykonuje procedurę w kontekście właściciel. Jeśli procedura jest tworzona w schemacie własnością `dbo` lub procedura właściciel bazy danych będzie wykonywane z nieograniczonymi uprawnieniami.  
  
-   SELF. Trwa wykonywanie jako samodzielna wykonywany w kontekście zabezpieczeń Twórcy procedury składowanej. Jest to równoważne Trwa wykonywanie jako określony użytkownik w przypadku, gdy określony użytkownik to osoba, utworzenie lub modyfikacja procedury.  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
