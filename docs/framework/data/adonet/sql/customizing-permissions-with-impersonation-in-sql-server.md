---
title: Dostosowywanie uprawnień personifikacji w programie SQL Server
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 52e11bd983a8c9155d90659834df03dea6449a8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961121"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Dostosowywanie uprawnień personifikacji w programie SQL Server
Wiele aplikacji korzysta z procedur składowanych w celu uzyskania dostępu do danych, opierając się na łańcuchu własności, aby ograniczyć dostęp do tabel podstawowych. Można przyznać uprawnienia wykonywania w procedurach składowanych, odwoływaniu lub odmowie uprawnień do tabel podstawowych. SQL Server nie sprawdza uprawnień obiektu wywołującego, jeśli procedura składowana i tabele mają tego samego właściciela. Jednak tworzenie łańcucha własności nie działa, jeśli obiekty mają różnych właścicieli lub w przypadku dynamicznego języka SQL.  
  
 W procedurze składowanej można użyć klauzuli EXECUTE AS, gdy obiekt wywołujący nie ma uprawnień do obiektów bazy danych, do których się odwołuje. Efekt klauzuli EXECUTE AS polega na tym, że kontekst wykonywania jest przełączany do użytkownika serwera proxy. Wszystkie kody, a także wszystkie wywołania zagnieżdżonych procedur składowanych lub wyzwalaczy są wykonywane w kontekście zabezpieczeń użytkownika serwera proxy. Kontekst wykonywania jest przywracany do oryginalnego obiektu wywołującego dopiero po wykonaniu procedury lub po wydaniu instrukcji przywracania.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Przełączanie kontekstu za pomocą instrukcji EXECUTE AS  
 Instrukcja EXECUTE AS języka Transact-SQL umożliwia przełączenie kontekstu wykonywania instrukcji przez personifikację innego identyfikatora logowania lub użytkownika bazy danych. Jest to przydatna technika testowania zapytań i procedur jako inny użytkownik.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Użytkownik musi mieć uprawnienia PERSONIFIKACJi w przypadku personifikowanej nazwy logowania lub użytkownika. To uprawnienie jest implikowane `sysadmin` dla wszystkich baz danych i `db_owner` członków roli w bazach danych, których są właścicielami.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Przyznawanie uprawnień za pomocą klauzuli EXECUTE AS  
 Można użyć klauzuli EXECUTE AS w nagłówku definicji procedury składowanej, wyzwalacza lub funkcji zdefiniowanej przez użytkownika (z wyjątkiem wbudowanych funkcji zwracających tabele). Powoduje to wykonanie procedury w kontekście nazwy użytkownika lub słowa kluczowego określonego w klauzuli EXECUTE AS. W bazie danych, która nie jest zamapowana na nazwę logowania, można utworzyć użytkownika proxy, przyznając mu tylko niezbędne uprawnienia do obiektów, do których uzyskuje się dostęp za pomocą tej procedury. Tylko użytkownik serwera proxy określony w klauzuli EXECUTE AS musi mieć uprawnienia do wszystkich obiektów, do których uzyskuje dostęp ten moduł.  
  
> [!NOTE]
> Niektóre akcje, takie jak TRUNCATE TABLE, nie mają uprawnień do udzielenia. Przez uwzględnienie instrukcji w ramach procedury i określenie użytkownika serwera proxy, który ma uprawnienia ALTER TABLE, można przyciągnąć uprawnienia do obcinania tabeli do obiektów wywołujących, którzy mają tylko uprawnienia do wykonywania w tej procedurze.  
  
 Kontekst określony w klauzuli EXECUTE AS jest prawidłowy dla czasu trwania procedury, w tym zagnieżdżone procedury i wyzwalacze. Kontekst odwraca do obiektu wywołującego po zakończeniu wykonywania lub wygenerowaniu instrukcji przywracania.  
  
 W procedurze należy wykonać trzy kroki, korzystając z klauzuli EXECUTE AS.  
  
1. Utwórz użytkownika serwera proxy w bazie danych, która nie jest zamapowana na nazwę logowania. Nie jest to wymagane, ale ułatwia zarządzanie uprawnieniami.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. Przyznaj użytkownikowi proxy niezbędne uprawnienia.  
  
2. Dodaj klauzulę EXECUTE AS do procedury składowanej lub funkcji zdefiniowanej przez użytkownika.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
> Aplikacje wymagające inspekcji mogą zostać przerwane, ponieważ oryginalny kontekst zabezpieczeń obiektu wywołującego nie jest zachowywany. Wbudowane funkcje, które zwracają tożsamość bieżącego użytkownika, takie jak SESSION_USER, USER lub nazwa_użytkownika, zwracają użytkownika skojarzonego z klauzulą EXECUTE AS, a nie z oryginalnym obiektem wywołującym.  
  
### <a name="using-execute-as-with-revert"></a>Używanie polecenia EXECUTE AS z opcją Revert  
 Możesz użyć instrukcji przywracania Transact-SQL, aby przywrócić pierwotny kontekst wykonania.  
  
 Opcjonalna klauzula bez przywracania pliku cookie = @variableName, umożliwia przełączenie kontekstu wykonywania z powrotem do obiektu wywołującego, @variableName Jeśli zmienna zawiera poprawną wartość. Pozwala to na przełączenie kontekstu wykonywania z powrotem do obiektu wywołującego w środowiskach, w których jest używane pule połączeń. Ponieważ wartość @variableName jest znana tylko obiektowi wywołującemu instrukcji EXECUTE AS, obiekt wywołujący może zagwarantować, że kontekst wykonywania nie może zostać zmieniony przez użytkownika końcowego, który wywoła aplikację. Gdy połączenie jest zamknięte, zostanie zwrócone do puli. Aby uzyskać więcej informacji na temat puli połączeń w programie ADO.NET, zobacz SQL Servering pooling [(ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Określanie kontekstu wykonywania  
 Oprócz określania użytkownika można również użyć słowa kluczowego EXECUTE jako z dowolnym z następujących słów kluczowych.  
  
- OBIEKT WYWOŁUJĄCY. Wykonywanie jako obiekt wywołujący jest wartością domyślną; Jeśli żadna inna opcja nie zostanie określona, procedura jest wykonywana w kontekście zabezpieczeń obiektu wywołującego.  
  
- WŁAOCICIELA. Wykonywanie jako właściciel wykonuje procedurę w kontekście właściciela procedury. Jeśli procedura jest tworzona w schemacie `dbo` lub właścicielu bazy danych, procedura zostanie wykonana z nieograniczonymi uprawnieniami.  
  
- SELF. Wykonywanie jako samodziałanie w kontekście zabezpieczeń twórcy procedury składowanej. Jest to równoważne wykonywaniu przez określonego użytkownika, gdzie określony użytkownik jest osobą tworzącą lub zmieniającą procedurę.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
