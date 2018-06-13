---
title: Udzielanie uprawnień na poziomie wiersza w programie SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 5f777b47c9b2f92c40fec01b4ff0c35fc28dbd89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361309"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Udzielanie uprawnień na poziomie wiersza w programie SQL Server
W niektórych scenariuszach jest wymagane do kontrolowania dostępu do danych na bardziej szczegółowym poziomie niż zapewnia jakie po prostu udzielanie, odwoływanie lub odmawianie uprawnień. Na przykład szpital Twoich aplikacji bazy danych mogą wymagać poszczególnych lekarzy ograniczona do uzyskiwania dostępu do informacji dotyczących tylko ich pacjentów. Podobne wymagania istnieje w wielu środowiskach, w tym finance, prawa dla instytucji rządowych i godzina aplikacji. Aby pomóc w pokonywaniu tych scenariuszy, SQL Server 2016 zapewnia [zabezpieczenia na poziomie wiersza](https://msdn.microsoft.com/library/dn765131.aspx) funkcja, która upraszcza i centralizuje logiki dostęp na poziomie wiersza w zasadach zabezpieczeń. W przypadku wcześniejszych wersji programu SQL Server podobne funkcje można osiągnąć za pomocą widoków wprowadzenie filtrowanie na poziomie wiersza.  
  
## <a name="implementing-row-level-filtering"></a>Implementowanie filtrowanie na poziomie wiersza  
 Filtrowanie na poziomie wiersza jest używany do przechowywania informacji w jednej tabeli podobnie jak w powyższym przykładzie szpital Twoich aplikacji. Aby zaimplementować filtrowania każdy wiersz na poziomie wiersza ma kolumny, która definiuje różnego parametrów, takich jak nazwa użytkownika, etykiety lub innego identyfikatora. Można tworzyć zasady zabezpieczeń lub widok w tabeli, które filtry wierszy, na które użytkownik ma dostęp. Następnie można utworzyć sparametryzowany procedur składowanych, które kontrolują typy zapytań, które użytkownik może uruchomić.  
  
 Na poniższym przykładzie opisano, jak skonfigurować filtrowanie na podstawie nazwy użytkownika lub nazwy logowania na poziomie wiersza:  
  
-   Utwórz tabelę, dodać kolumnę do przechowywania nazwy.  
  
-   Włącz filtrowanie na poziomie wiersza:  
  
    -   Jeśli używasz programu SQL Server 2016 lub nowszego, lub [bazy danych SQL Azure](https://docs.microsoft.com/azure/sql-database/), tworzenie zasad zabezpieczeń, który dodaje predykatu w tabeli wiersze ograniczenie zwrócone do tych, które pasuje do żadnej bieżącego użytkownika bazy danych (przy użyciu CURRENT_USER() wbudowana funkcja) lub bieżąca nazwa logowania (przy użyciu wbudowanych funkcji SUSER_SNAME()):  
  
        ```tsql  
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
  
    -   Jeśli używasz wersji programu SQL Server przed 2016, można uzyskać podobne funkcje przy użyciu widoku:  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   Utwórz procedury składowane można wybrać, wstawiania, aktualizowania i usuwania danych. Jeśli filtrowanie jest wprowadzany przy użyciu zasad zabezpieczeń, procedur składowanych należy wykonać te operacje w tabeli podstawowej bezpośrednio; w przeciwnym razie Jeśli filtrowanie jest wdrożonych przez widok, procedur składowanych zamiast tego powinien działać w widoku. Zasady zabezpieczeń lub widok automatycznie filtrów wierszy zwrócony lub zmodyfikowane przez użytkownika zapytania i procedury składowanej zapewni przeszkodę granicy zabezpieczeń, aby uniemożliwić użytkownikom z dostępem do zapytania bezpośredniego pomyślnie uruchamiania zapytań, które można wywnioskować istnienie odfiltrowane dane.  
  
-   Procedury składowanej wstawiania danych nazwę użytkownika przy użyciu tej samej funkcji określonej w zasadach zabezpieczeń lub Widok przechwytywania i Wstaw tę wartość w kolumnie nazwy użytkownika.  
  
-   Odmów wszystkie uprawnienia w tabelach (i widoków, jeśli ma to zastosowanie) do `public` roli. Użytkownicy nie będą mogli dziedziczą uprawnienia z innych ról bazy danych, ponieważ predykatu filtru opartego na użytkownika lub nazwy logowania, a nie w odniesieniu do ról.  
  
-   Udziel wykonać na procedury składowane do ról bazy danych. Użytkownicy mogą tylko uzyskiwać dostęp do danych przechowywanych procedur.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|||  
|-|-|  
|[Implementowanie zabezpieczeń na poziomie wierszy i komórek w niejawnych baz danych przy użyciu programu SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) w witrynie TechCenter programu SQL Server.|Informacje dotyczące używania zabezpieczeń na poziomie wierszy i komórek, aby spełnić wymagania dotyczące zabezpieczeń niejawnych bazy danych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia na poziomie wiersza](https://msdn.microsoft.com/library/dn765131.aspx)  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
