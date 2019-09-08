---
title: Udzielanie uprawnień na poziomie wiersza w programie SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: df5fcb4a6c73e12bec2ab17501fdfb02cf672324
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782355"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Udzielanie uprawnień na poziomie wiersza w programie SQL Server

W niektórych scenariuszach istnieje wymóg, aby kontrolować dostęp do danych na bardziej szczegółowym poziomie niż to, co po prostu przyznanie, odwoływanie lub odmowa uprawnień. Na przykład aplikacja szpitalnej bazy danych może wymagać, aby indywidualni Lekarze mogli uzyskiwać dostęp do informacji związanych tylko z ich pacjentami. Podobne wymagania istnieją w wielu środowiskach, takich jak aplikacje finansowe, prawne, rządowe i wojskowe. Aby rozwiązać te scenariusze, SQL Server 2016 zapewnia funkcję [zabezpieczeń na poziomie wiersza](/sql/relational-databases/security/row-level-security) , która upraszcza i scentralizowana logiki dostępu na poziomie wiersza w zasadach zabezpieczeń. W przypadku wcześniejszych wersji SQL Server można osiągnąć podobną funkcjonalność przy użyciu widoków, aby przyjąć filtrowanie na poziomie wiersza.

## <a name="implementing-row-level-filtering"></a>Implementowanie filtrowania na poziomie wierszy

Filtrowanie na poziomie wiersza jest używane w przypadku aplikacji przechowujących informacje w pojedynczej tabeli, jak w powyższym przykładzie szpital. Aby zaimplementować filtrowanie na poziomie wierszy każdy wiersz ma kolumnę definiującą parametr odróżniający, taki jak nazwa użytkownika, etykieta lub inny identyfikator. Tworzysz zasady zabezpieczeń lub widok w tabeli, który filtruje wiersze, do których użytkownik może uzyskać dostęp. Następnie utworzysz sparametryzowane procedury składowane, które kontrolują typy zapytań, które użytkownik może wykonywać.

W poniższym przykładzie opisano sposób konfigurowania filtrowania na poziomie wierszy na podstawie nazwy użytkownika lub logowania:

- Utwórz tabelę, dodając do niej kolumnę.

- Włącz filtrowanie na poziomie wierszy:

  - Jeśli używasz SQL Server 2016 lub nowszej lub [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), Utwórz zasady zabezpieczeń, które dodają predykat w tabeli, ograniczając wiersze zwracane do tych, które pasują do bieżącego użytkownika bazy danych (za pomocą wbudowanej funkcji CURRENT_USER ()) lub Bieżąca nazwa logowania (przy użyciu wbudowanej funkcji SUSER_SNAME ()):

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

  - Jeśli używasz wersji SQL Server wcześniejszej niż 2016, możesz uzyskać podobną funkcjonalność przy użyciu widoku:

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- Utwórz procedury składowane, aby wybierać, wstawiać, aktualizować i usuwać dane. Jeśli filtrowanie zostało wprowadzone przez zasady zabezpieczeń, procedury składowane powinny wykonać te operacje bezpośrednio w tabeli podstawowej; w przeciwnym razie, jeśli Filtrowanie jest wykonywane przez widok, procedury składowane powinny w zamian działać względem widoku. Zasady zabezpieczeń lub widok automatycznie filtrują wiersze zwrócone lub zmodyfikowane przez zapytania użytkowników, a procedura składowana zapewnia trudniejszą granicę zabezpieczeń, aby uniemożliwić użytkownikom bezpośredni dostęp do zapytań, które mogą wywnioskować istnienie filtrowanych danych.

- W przypadku procedur składowanych, które wstawiają dane, Przechwyć nazwę użytkownika przy użyciu tej samej funkcji, która jest określona w zasadach zabezpieczeń lub widoku, i Wstaw tę wartość do kolumny UserName.

- Odrzuć wszystkie uprawnienia w tabelach (i widokach, jeśli ma to zastosowanie `public` ) do roli. Użytkownicy nie będą mogli dziedziczyć uprawnień z innych ról bazy danych, ponieważ predykat filtru jest oparty na nazwach użytkowników lub nazw logowania, a nie na rolach.

- Przyznaj wykonywanie na procedurach składowanych do ról bazy danych. Użytkownicy mogą uzyskiwać dostęp tylko do danych za pomocą dostarczonych procedur składowanych.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia na poziomie wiersza](/sql/relational-databases/security/row-level-security)
- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
