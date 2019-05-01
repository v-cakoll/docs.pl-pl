---
title: Udzielanie uprawnień na poziomie wiersza w programie SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 891b5114551c5784b11504f2463525087125131f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033907"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Udzielanie uprawnień na poziomie wiersza w programie SQL Server

W niektórych scenariuszach istnieje wymóg do kontrolowania dostępu do danych na bardziej szczegółowym poziomie niż zapewnia jakie po prostu udzielanie, odwoływanie lub odmawianie uprawnień. Na przykład szpitali aplikacji bazy danych może wymagać poszczególnych lekarzy ograniczona do uzyskiwania dostępu do informacji dotyczących tylko pacjentów. Istnieją podobne wymagania w wielu środowiskach, w tym Finanse, prawo, instytucji rządowych i wojskowe aplikacji. Aby ułatwić obsługę tych scenariuszy, programu SQL Server 2016 zapewnia [zabezpieczenia na poziomie wiersza](/sql/relational-databases/security/row-level-security) funkcja, która upraszcza i umożliwia scentralizowanie logiki dostępu na poziomie wiersza w zasadach zabezpieczeń. We wcześniejszych wersjach programu SQL Server podobne funkcje można osiągnąć przy użyciu widoków wprowadzenie filtrowanie na poziomie wiersza.

## <a name="implementing-row-level-filtering"></a>Implementowanie filtrowanie na poziomie wiersza

Filtrowanie na poziomie wiersza jest używana do przechowywania informacji w jednej tabeli podobnie jak w powyższym przykładzie szpitali aplikacji. Aby zaimplementować filtrowanie każdy wiersz na poziomie wiersza ma kolumny, która ma parametr różnicujący, takie jak nazwa użytkownika, etykietę lub inny identyfikator. Można tworzyć zasady zabezpieczeń lub widoku w tabeli i filtrować wiersze, których użytkownik ma dostęp. Następnie można utworzyć sparametryzowany procedur składowanych, które kontrolę typów zapytań, które użytkownik może uruchomić.

Poniższy przykład zawiera opis sposobu konfigurowania, filtrowanie na podstawie nazwy użytkownika lub logowania na poziomie wiersza:

- Utwórz tabelę, dodając kolumny do przechowywania nazwy.

- Włącz filtrowanie na poziomie wiersza:

  - Jeśli używasz programu SQL Server 2016 lub nowszym, lub [usługi Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), utworzyć zasady zabezpieczeń, który dodaje predykatu w tabeli wiersze ograniczenie zwrócone do tych, które pasują do jednego bieżącego użytkownika bazy danych (za pomocą CURRENT_USER() wbudowana funkcja) lub bieżąca nazwa logowania (przy użyciu wbudowanej funkcji SUSER_SNAME()):

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - Jeśli używasz wersji programu SQL Server przed 2016, można osiągnąć podobne funkcje przy użyciu widoku:

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- Tworzenie procedur składowanych, aby wybrać, wstawianie, aktualizowanie i usuwanie danych. Jeśli filtrowanie jest wprowadzany przez zasady zabezpieczeń, procedur składowanych powinien wykonywać te operacje, w tabeli podstawowej bezpośrednio; w przeciwnym razie Jeśli filtrowanie jest wprowadzany przez widok, procedur składowanych należy zamiast tego działać widoku. Zasady zabezpieczeń lub widoku automatycznie spowoduje odfiltrowanie wierszy zwrócony lub modyfikowane przez zapytania użytkowników i procedury składowanej zapewni trudniejsze granicy zabezpieczeń uniemożliwić użytkownikom przy użyciu zapytania bezpośredniego dostępu do poprawnego działania zapytania, które może wywnioskować istnienie odfiltrowane dane.

- Dla procedur składowanych, które wstawiają dane przechwytywania nazwę użytkownika przy użyciu tej samej funkcji, które są określone w zasadach zabezpieczeń lub w widoku, a następnie wstaw tę wartość w kolumnie Nazwa użytkownika.

- Odmowa uprawnień wszystkie tabele (i widoki, jeśli ma to zastosowanie) do `public` roli. Użytkownicy nie będą mogli dziedziczą uprawnienia z innych ról bazy danych, ponieważ predykatu filtru opartego na użytkownika lub nazwy logowania, nie na rolach.

- Udziel wykonać na procedurach przechowywanych do ról bazy danych. Użytkownicy mogą tylko dostęp do danych przy użyciu przechowywanych procedur.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia na poziomie wiersza](/sql/relational-databases/security/row-level-security)
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
