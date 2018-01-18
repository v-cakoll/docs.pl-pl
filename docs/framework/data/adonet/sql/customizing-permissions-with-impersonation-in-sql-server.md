---
title: Dostosowywanie uprawnieniami personifikacja w programie SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7175542d8a9441d9f0d3eeb05acc67cf12d6a270
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Dostosowywanie uprawnieniami personifikacja w programie SQL Server
Wiele aplikacji korzysta procedur składowanych dostępu do danych polegania na własność łańcucha, aby ograniczyć dostęp do tabel podstawowych. Można przyznać uprawnienia EXECUTE procedur składowanych, odwoływanie lub nie zezwalających na uprawnienia do tabel podstawowych. SQL Server nie sprawdza uprawnienia obiektu wywołującego, jeśli procedura składowana i tabele mieć tego samego właściciela. Jednak łańcucha własności nie działa obiektów mieć różnych właścicieli lub w przypadku dynamicznego SQL.  
  
 EXECUTE AS można użyć klauzuli w procedurze składowanej, gdy obiekt wywołujący nie ma uprawnień do obiektów bazy danych. Efekt EXECUTE AS klauzula jest, że przełączania kontekstu wykonywania dla użytkownika serwera proxy. Cały kod, a także wszystkie wywołania zagnieżdżonych procedur składowanych lub wyzwalaczy, jest wykonywany w kontekście zabezpieczeń użytkownika serwera proxy. Kontekst wykonywania zostanie przywrócony do oryginalnego obiektu wywołującego tylko po wykonaniu procedury lub po wygenerowaniu instrukcji REVERT.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Kontekst przełączenie EXECUTE AS — instrukcja  
 Języka Transact-SQL AS wykonania instrukcji umożliwia przełączanie kontekstu wykonywania instrukcji przez personifikowanie innego użytkownika logowania lub bazy danych. Jest to przydatne technika testowanie zapytań i procedur jako inny użytkownik.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Musi mieć uprawnienia IMPERSONATE logowania lub użytkownika, które są personifikacji. To uprawnienie jest domniemane dla `sysadmin` dla wszystkich baz danych, i `db_owner` członków roli w bazach danych, które są właścicielami.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Udzielanie uprawnień z EXECUTE AS — klauzula  
 EXECUTE AS można użyć klauzuli w nagłówku definicji procedury przechowywanej, wyzwalacza lub funkcji zdefiniowanej przez użytkownika (z wyjątkiem funkcji śródwierszowych przechowywanymi w tabeli). Powoduje to procedurę można wykonać w kontekście nazwa użytkownika lub słowa kluczowego, określonego w EXECUTE AS klauzuli. Utwórz użytkownika serwera proxy w bazie danych, która nie jest zamapowany na nazwę logowania udzielanie go tylko wymagane uprawnienia na obiekty używane przez procedurę. Dostęp do wszystkich obiektów tylko użytkownika serwera proxy, określony w poleceniu EXECUTE jako klauzuli musi mieć uprawnienia przez moduł.  
  
> [!NOTE]
>  Niektóre akcje, takie jak TRUNCATE TABLE nie masz uprawnień możliwy. Dołączanie instrukcji w procedurze i określając użytkownika serwera proxy, który ma uprawnienia ALTER TABLE, można rozszerzyć uprawnienia do obcięcia tabeli dla kodu wywołującego, którzy mają tylko uprawnienia EXECUTE w procedurze.  
  
 Kontekst określony w poleceniu EXECUTE jako klauzula jest ważny przez czas trwania procedury, w tym zagnieżdżonych procedury i wyzwalaczy. Kontekst wraca do wywołującego po zakończeniu wykonywania lub wystawienia instrukcji REVERT.  
  
 Istnieją trzy kroki związane ze stosowaniem EXECUTE AS klauzuli w procedurze.  
  
1.  Utwórz użytkownika serwera proxy w bazie danych, który nie jest zamapowany na nazwę logowania. Nie jest to wymagane, ale pomaga podczas zarządzania uprawnieniami.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  Przyznaj uprawnienia użytkownika serwera proxy.  
  
2.  Dodaj EXECUTE AS klauzuli do procedury składowanej lub funkcji zdefiniowanej przez użytkownika.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Aplikacje, które wymagają inspekcji mogą być dzielone, ponieważ nie jest zachowywana oryginalna kontekstu zabezpieczeń wywołującego. Wbudowane funkcje, które zwracają tożsamości bieżącego użytkownika, takie jak SESSION_USER, użytkownika lub nazwa_użytkownika, zwraca użytkownika skojarzonego z EXECUTE AS klauzuli, nie oryginalny obiekt wywołujący.  
  
### <a name="using-execute-as-with-revert"></a>Używanie EXECUTE AS z przywracania  
 Instrukcji języka Transact-SQL PRZYWRÓCIĆ umożliwia przywrócenie oryginalnego kontekstu wykonywania.  
  
 Opcjonalna klauzula, z nie PRZYWRÓCENIE pliku COOKIE = @variableName, umożliwia przełączenie kontekstu wykonywania powrotem do wywołującego, jeśli @variableName zmienna zawiera poprawną wartość. Dzięki temu można przełączyć się do obiektu wywołującego w środowiskach, w którym jest używane buforowanie połączenia kontekstu wykonywania. Ponieważ wartość @variableName jest znany tylko do wywołującego EXECUTE AS instrukcji, wywołujący może zagwarantować, że nie można zmienić kontekstu wykonywania przez użytkownika końcowego, który wywołuje aplikację. Gdy połączenie jest zamknięte, jest zwracana do puli. Aby uzyskać więcej informacji na temat połączenia buforowanie w ADO.NET, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Określanie kontekstu wykonywania  
 Oprócz określenia użytkownika, można również używać EXECUTE AS z żadnego z następujących słów kluczowych.  
  
-   OBIEKT WYWOŁUJĄCY. Wykonywanie jako obiekt WYWOŁUJĄCY jest domyślnie; Jeśli zostanie określona żadna inna opcja, następnie procedura jest wykonywana w kontekście zabezpieczeń obiektu wywołującego.  
  
-   OWNER. W kontekście właściciela procedury wykonywania jako właściciela wykonuje procedurę. Jeśli procedura jest tworzona w schemacie własnością `dbo` lub właściciela bazy danych z nieograniczonych uprawnień wykona procedurę.  
  
-   SELF. Wykonywanie jako SELF wykonywane w kontekście zabezpieczeń Twórcy procedury składowanej. Jest to równoważne wykonywania jako dla określonego użytkownika, jeśli określony użytkownik jest osoba, utworzenie lub modyfikacja procedury.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Przełączanie kontekstu](http://msdn.microsoft.com/library/ms188268.aspx) w dokumentacji SQL Server Books Online|Zawiera łącza do tematów opisujących sposób użycia EXECUTE AS klauzuli.|  
|[Tworzenie zestawów uprawnień niestandardowych za pomocą EXECUTE AS](http://msdn.microsoft.com/library/ms190384.aspx) i [przy użyciu EXECUTE AS w modułach](http://msdn.microsoft.com/library/ms178106.aspx) w dokumentacji SQL Server Books Online|Tematy opisują sposób użycia EXECUTE AS klauzuli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
