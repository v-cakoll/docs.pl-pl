---
title: Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: d16a6609603cfb83fc6523606cc7ec9e7bfd8dba
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912068"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server
Jedną z metod tworzenia wielu wierszy obrony wokół bazy danych jest do wdrożenia dostępu do wszystkich danych przy użyciu procedur składowanych i funkcji zdefiniowanych przez użytkownika. Odwoływanie lub odmówić uprawnień wszystkich podstawowych obiektów, takich jak tabele i Udziel uprawnień wykonywanie procedur składowanych. Spowoduje to skutecznie utworzenie obwodu zabezpieczeń wokół obiektów danych i bazy danych.  
  
## <a name="stored-procedure-benefits"></a>Procedura składowana korzyści  
 Procedury składowane zapewnia następujące korzyści:  
  
-   Można hermetyzować reguł biznesowych i logiki danych, dzięki czemu użytkownicy mogą uzyskiwać dostęp do danych i obiektów tylko w sposób, który ma deweloperów i administratorów baz danych.  
  
-   Sparametryzowanej procedury składowane, które sprawdzają poprawność wszystkich danych wejściowych użytkownika może służyć do udaremnić ataki przez wstrzyknięcie kodu SQL. Jeśli używasz dynamiczny język SQL, pamiętaj zdefiniować parametry poleceń, a nigdy nie dołączaj parametru wartości bezpośrednio do ciągu zapytania.  
  
-   Może być niedozwolona ad-hoc modyfikacji zapytania i danych. Uniemożliwia to użytkownikom złośliwie przypadkowo zniszczenie danych lub wykonywaniem zapytań, które obniżają wydajność na serwerze lub w sieci.  
  
-   Błędy mogą być obsługiwane w kodzie procedury nie został przekazany bezpośrednio do aplikacji klienckich. Zapobiega to komunikaty o błędach zwracanych, które może pomóc w badania ataków. Rejestrowanie błędów i obsługiwać je na serwerze.  
  
-   Procedury składowane można zapisywane jeden raz i używane przez wiele aplikacji.  
  
-   Aplikacje klienckie nie trzeba nic wiedzieć o podstawowej struktury danych. Procedura składowana kod, można zmienić bez konieczności wprowadzania zmian w aplikacjach klienckich, tak długo, jak zmiany nie wpływają na listy parametrów lub zwracane typy danych.  
  
-   Procedury składowane można zmniejszyć ruch sieciowy, łącząc wiele operacji do wywołania jednej procedury.  
  
## <a name="stored-procedure-execution"></a>Wykonywanie procedury składowanej  
 Przechowywane procedury Wykorzystaj własności łańcucha zapewnienie dostępu do danych, dzięki czemu użytkownicy nie muszą mieć jawne uprawnienia do dostępu do obiektów bazy danych. Łańcucha własności istnieje, gdy obiektów mających dostęp do sekwencyjnego sobą należą do tego samego użytkownika. Na przykład wywołać procedurę składowaną innych procedur składowanych lub procedury składowanej mogą uzyskiwać dostęp do wielu tabel. Jeśli wszystkie obiekty w łańcuchu wykonywania mają tego samego właściciela, a następnie programu SQL Server sprawdza tylko uprawnień wykonywanie do obiektu wywołującego, nie uprawnienia obiektu wywołującego od innych obiektów. W związku z tym należy udzielić tylko uprawnienia wykonywania na procedurach przechowywanych; można odwołać lub odmówić wszystkie uprawnienia wobec tabel podstawowych.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Po prostu pisania procedur składowanych nie jest wystarczająco dużo, aby odpowiednio zabezpieczenia aplikacji. Należy również rozważyć następujące potencjalnych luk w zabezpieczeniach.  
  
-   Udziel uprawnień wykonywanie procedur składowanych do ról bazy danych, które chcesz mieć możliwość dostępu do danych.  
  
-   Odwoływanie lub Odrzuć wszystkie uprawnienia w tabelach dla wszystkich ról i użytkowników w bazie danych, w tym `public` roli. Wszyscy użytkownicy dziedziczą uprawnienia z publicznej. W związku z tym odmawia uprawnienia do `public` oznacza, że tylko właściciele i `sysadmin` członkowie mają dostęp; wszyscy inni użytkownicy będą mogli dziedziczą uprawnienia z członkostwa w innych ról.  
  
-   Nie należy dodawać użytkowników lub ról, aby `sysadmin` lub `db_owner` ról. Administratorzy systemu i właścicieli bazy danych można uzyskać dostęp do wszystkich obiektów bazy danych.  
  
-   Wyłącz `guest` konta. Uniemożliwi to użytkownicy anonimowi połączenie z bazą danych. Konto gościa jest domyślnie wyłączona, w nowych baz danych.  
  
-   Implementowanie błędu dziennika i obsługi błędów.  
  
-   Utwórz sparametryzowanej procedury składowane, które sprawdzają poprawność wszystkich danych wejściowych użytkownika. Wszystkie dane wejściowe użytkownika należy traktować jako niezaufane.  
  
-   Należy unikać dynamiczny język SQL, chyba że jest to absolutnie konieczne. Funkcja QUOTENAME() języka Transact-SQL do ograniczania wartości ciągu i wprowadzić dowolne wystąpienie ogranicznika w ciągu wejściowym.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Procedury składowane](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) i [wstrzyknięcie kodu SQL](http://go.microsoft.com/fwlink/?LinkId=98234) w SQL Server — książki Online|Tematy opisują sposób tworzenia procedury składowane i jak działa wstrzyknięcie kodu SQL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](http://go.microsoft.com/fwlink/?LinkId=217917)
