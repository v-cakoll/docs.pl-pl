---
title: "Zarządzanie uprawnieniami w procedurach składowanych w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 38bdc4d41e4b42f2dccaf059d84f6b8b45967ff5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Zarządzanie uprawnieniami w procedurach składowanych w programie SQL Server
Jedną z metod tworzenia wielu linii obrony wokół bazy danych jest wdrożenie wszystkich dostęp do danych za pomocą procedury składowanej lub funkcji zdefiniowanej przez użytkownika. Odwoływanie lub odmówić wszystkich uprawnień do obiektów podstawowych, takich jak tabele i przyznać uprawnienia EXECUTE procedur składowanych. Spowoduje to skutecznie utworzenie obwodu zabezpieczeń wokół obiektów danych i bazy danych.  
  
## <a name="stored-procedure-benefits"></a>Procedura składowana korzyści  
 Procedury składowane są następujące korzyści:  
  
-   Reguły logiki i business danych można hermetyzowany, dzięki czemu użytkownicy mogą uzyskiwać dostęp do danych i obiektów tylko w sposób, w którym mają deweloperom i administratorom bazy danych.  
  
-   Sparametryzowane procedur składowanych, sprawdzania poprawności wszystkich danych wejściowych użytkownika można zablokować ataki. Użycie dynamicznych SQL, należy koniecznie parametryzacja poleceń i nigdy nie dołączaj parametru wartości bezpośrednio do ciągu zapytania.  
  
-   Ad hoc modyfikacji zapytań i danych mogą niedozwolone. Zapobiega to użytkownikom złośliwe lub przypadkowo niszczenie danych lub wykonywanie zapytań, które obniżają wydajność na serwerze lub w sieci.  
  
-   Błędy mogą być obsługiwane w kodzie procedury bez przekazywany bezpośrednio do aplikacji klienckich. Zapobiega to komunikaty o błędach zwracanych, która może pomóc w sondowania ataku. Rejestrowanie błędów i obsługiwać je na serwerze.  
  
-   Procedury składowane można raz zapisany i dostęp do wielu aplikacji.  
  
-   Aplikacje klienta nie muszą mieć żadnych informacji na temat podstawowej struktury danych. Procedura składowana kodu można zmienić bez konieczności wprowadzania zmian w aplikacjach klienckich, tak długo, jak zmiany nie wpływają na listy parametrów lub zwracane typy danych.  
  
-   Procedury składowane można zmniejszenie ruchu w sieci, łącząc wiele operacji na jednym wywoływania.  
  
## <a name="stored-procedure-execution"></a>Wykonywanie procedury składowanej  
 Przechowywane procedury Wykorzystaj własność łańcucha w celu zapewnienia dostępu do danych, dzięki czemu użytkownicy nie muszą mieć jawne uprawnienia dostępu do obiektów bazy danych. Łańcuch własność występuje, gdy obiekty, które uzyskują dostęp do siebie sekwencyjnie własnością tego samego użytkownika. Na przykład wywołać procedurę składowaną innych procedur składowanych lub procedury składowanej mogą uzyskiwać dostęp do wielu tabel. Jeśli wszystkie obiekty w łańcuchu wykonanie tego samego właściciela, a następnie programu SQL Server tylko sprawdza uprawnienia EXECUTE dla obiekt wywołujący, nie wywołującego uprawnienia do innych obiektów. W związku z tym należy przyznać uprawnienia tylko wykonywania na procedury składowane; można odwołać lub odrzucać wszystkie uprawnienia w tabeli.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Po prostu Pisanie procedur składowanych nie wystarcza do odpowiednio zabezpieczania aplikacji. Należy również rozważyć następujące potencjalnych luk w zabezpieczeniach.  
  
-   Udziel uprawnienia do wykonania na procedury składowane dla ról bazy danych, które chcesz mieć możliwość uzyskania dostępu do danych.  
  
-   Odwoływanie lub odrzucać wszystkie uprawnienia do tabeli dla wszystkich ról i użytkowników w bazie danych, w tym `public` roli. Wszyscy użytkownicy dziedziczą uprawnienia z publicznej. W związku z tym odmawiania uprawnień do `public` oznacza tylko właściciele i `sysadmin` członkowie mają dostęp; wszyscy inni użytkownicy będą mogli dziedziczą uprawnienia z członkostwa w innych ról.  
  
-   Nie należy dodawać użytkowników i ról do `sysadmin` lub `db_owner` ról. Administratorzy systemu i właścicielom bazy danych mają dostęp do wszystkich obiektów bazy danych.  
  
-   Wyłącz `guest` konta. Uniemożliwi to użytkownicy anonimowi łączenia z bazą danych. Konta gościa jest domyślnie wyłączona w nowych baz danych.  
  
-   Implementuje błąd obsługi i dziennik błędów.  
  
-   Utworzyć sparametryzowany procedur składowanych, sprawdzania poprawności wszystkich danych wejściowych użytkownika. Traktuj wszystkie dane wejściowe użytkownika jako niezaufane.  
  
-   Uniknąć dynamiczne SQL, chyba że bezwzględnie konieczne. Użyj funkcji QUOTENAME() języka Transact-SQL, aby ograniczyć wartość ciągu i uniknięcie wszelkich wystąpieniu ogranicznika w ciągu wejściowym.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Procedury składowane](http://msdn.microsoft.com/library/ms190782.aspx) i [iniekcja kodu SQL](http://go.microsoft.com/fwlink/?LinkId=98234) w dokumentacji SQL Server Books Online|Tematach opisano sposób tworzenia procedury składowane i jak działa iniekcja kodu SQL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
