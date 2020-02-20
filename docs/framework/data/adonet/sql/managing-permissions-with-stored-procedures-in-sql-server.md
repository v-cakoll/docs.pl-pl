---
title: Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 85383c46dd029db825d24d2f67d2dbda00f3bc95
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452386"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server
Jedną z metod tworzenia wielu wierszy obrony bazy danych jest zaimplementowanie całego dostępu do danych za pomocą procedur składowanych lub funkcji zdefiniowanych przez użytkownika. Wszystkie uprawnienia do obiektów bazowych, takie jak tabele, są odwoływane lub odrzucane. Dzięki temu powstaje obwód zabezpieczeń wokół obiektów danych i baz danych.  
  
## <a name="stored-procedure-benefits"></a>Korzyści z procedury składowanej  
 Procedury składowane mają następujące zalety:  
  
- Reguły logiki danych i biznesowe mogą być hermetyzowane, dzięki czemu użytkownicy mogą uzyskiwać dostęp do danych i obiektów tylko w taki sposób, że deweloperzy i administratorzy baz danych mają.  
  
- Sparametryzowane procedury składowane, które sprawdzają, czy wszystkie dane wejściowe użytkownika mogą być używane do zapamiętania ataków iniekcji SQL. Jeśli używasz dynamicznego języka SQL, pamiętaj, aby Sparametryzuj polecenia, i nigdy nie dodawaj wartości parametrów bezpośrednio do ciągu zapytania.  
  
- Zapytania ad hoc i modyfikacje danych mogą być niedozwolone. Zapobiega to złośliwemu lub przypadkowemu zniszczeniu danych lub wykonywaniu zapytań, które ograniczają wydajność na serwerze lub w sieci.  
  
- Błędy mogą być obsługiwane w kodzie procedury bez przekazywania ich bezpośrednio do aplikacji klienckich. Zapobiega to zwracaniu komunikatów o błędach, które mogą pomóc w ataku typu badanie. Rejestruj błędy i obsługuj je na serwerze.  
  
- Procedury składowane można napisać raz i uzyskać do nich dostęp przez wiele aplikacji.  
  
- Aplikacje klienckie nie muszą wiedzieć niczego o podstawowych strukturach danych. Kod procedury składowanej można zmienić bez konieczności wprowadzania zmian w aplikacjach klienckich, o ile zmiany nie wpływają na listy parametrów lub zwracane typy danych.  
  
- Procedury składowane mogą zmniejszyć ruch sieciowy przez połączenie wielu operacji w jedno wywołanie procedury.  
  
## <a name="stored-procedure-execution"></a>Wykonywanie procedury składowanej  
 Procedury składowane wykorzystują tworzenie łańcucha własności, aby zapewnić dostęp do danych, dzięki czemu użytkownicy nie muszą mieć jawnego uprawnienia dostępu do obiektów bazy danych. Łańcuch własności istnieje, gdy obiekty, które uzyskują dostęp do siebie nawzajem, są własnością tego samego użytkownika. Na przykład procedura składowana może wywołać inne procedury składowane lub procedura składowana może uzyskać dostęp do wielu tabel. Jeśli wszystkie obiekty w łańcuchu wykonywania mają tego samego właściciela, SQL Server sprawdza tylko uprawnienie EXECUTE dla obiektu wywołującego, a nie uprawnienia obiektu wywołującego na innych obiektach. W związku z tym należy przyznać tylko uprawnienia do wykonywania w procedurach składowanych; Możesz odwołać lub odrzucić wszystkie uprawnienia do tabel źródłowych.  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 Zwykłe pisanie procedur składowanych jest niewystarczające, aby odpowiednio zabezpieczyć aplikację. Należy również wziąć pod uwagę następujące potencjalne luki w zabezpieczeniach.  
  
- Przyznaj uprawnienia do wykonywania w procedurach składowanych dla ról bazy danych, które mają mieć możliwość uzyskiwania dostępu do danych.  
  
- Odwołaj lub Odmów wszystkich uprawnień do odpowiednich tabel dla wszystkich ról i użytkowników w bazie danych, w tym roli `public`. Wszyscy użytkownicy dziedziczą uprawnienia od publicznego. W związku z tym odmowa uprawnień do `public` oznacza, że tylko właściciele i członkowie `sysadmin` mają dostęp; Wszyscy inni użytkownicy nie będą mogli dziedziczyć uprawnień z członkostwa w innych rolach.  
  
- Nie należy dodawać użytkowników ani ról do ról `sysadmin` ani `db_owner`. Administratorzy systemu i właściciele baz danych mogą uzyskać dostęp do wszystkich obiektów bazy danych.  
  
- Wyłącz konto `guest`. Uniemożliwi to anonimowym użytkownikom łączenie się z bazą danych. Konto gościa jest domyślnie wyłączone w nowych bazach danych.  
  
- Zaimplementuj obsługę błędów i Rejestruj błędy.  
  
- Utwórz sparametryzowane procedury składowane, które weryfikują wszystkie dane wejściowe użytkownika. Traktuj wszystkie dane wprowadzane przez użytkownika jako niezaufane.  
  
- Unikaj dynamicznego SQL, chyba że jest to absolutnie konieczne. Funkcja cudzysłowu Transact-SQL Quote () służy do ograniczania wartości ciągu i ucieczki dowolnego wystąpienia ogranicznika w ciągu wejściowym.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Więcej informacji zawierają poniższe zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Procedury składowane](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) i [iniekcja kodu SQL](/sql/relational-databases/security/sql-injection)|Artykuły opisują sposób tworzenia procedur składowanych i sposobu działania iniekcji języka SQL.|  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Rejestrowanie procedur składowanych w programie SQL Server](signing-stored-procedures-in-sql-server.md)
- [Dostosowywanie uprawnień personifikacji w programie SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../modifying-data-with-stored-procedures.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
