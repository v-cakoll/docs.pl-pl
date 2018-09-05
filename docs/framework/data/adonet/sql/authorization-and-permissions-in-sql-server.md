---
title: Autoryzacja i uprawnienia w programie SQL Server
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: bdf5112e3f0e2cada4885b0b66adf248f0ffe808
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661937"
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autoryzacja i uprawnienia w programie SQL Server
Podczas tworzenia obiektów bazy danych, należy jawnie udzielić uprawnień, aby udostępnić je użytkownikom. Każdy obiekt zabezpieczany ma uprawnienia, które mogą być przyznane podmiot zabezpieczeń za pomocą instrukcji uprawnień.  
  
## <a name="the-principle-of-least-privilege"></a>Zasadę najmniejszych uprawnień  
 Projektowanie aplikacji przy użyciu podejścia użytkownika najmniej uprzywilejowane konto (LUA) stanowi ważną część strategii obronienia, szczegółowe przeciwdziałanie zagrożenia bezpieczeństwa. Podejście LUA temu, postępuj zgodnie z zasadą najniższych uprawnień użytkowników i zawsze Zaloguj się przy użyciu kont z ograniczonymi uprawnieniami. Zadania administracyjne są rozbite przy użyciu ról stałej i użytkowania `sysadmin` stałej roli serwera jest znacznie ograniczone.  
  
 Zawsze postępuj zgodnie z zasadą najniższych uprawnień, podczas nadawania uprawnień do bazy danych użytkowników. Przyznaj najniższe uprawnienia niezbędne do użytkownika lub roli do wykonywania danego zadania.  
  
> [!IMPORTANT]
>  Tworzenie i testowanie aplikacji przy użyciu podejścia LUA dodaje stopień trudności z procesu opracowywania. Jest to łatwiejsze do tworzenia obiektów i napisać kod, gdy są zalogowani jako właściciel bazy danych lub administratorem systemu, niż konto LUA. Jednak tworzenie aplikacji przy użyciu konta o wysokim poziomie uprawnień można zaciemniania wpływu o ograniczonej funkcjonalności, gdy najniższych uprawnieniach użytkownicy próbują uruchomić aplikację, która wymaga podniesionych uprawnień, aby działać poprawnie. Udzielanie uprawnień nadmiernego użytkownikom, aby ponownie pobrać utraty funkcji można pozostawić aplikację na ataki. Projektowanie, tworzenie i testowanie aplikacji przy użyciu konta LUA wymusza wolą podejście do planowania zabezpieczeń, które eliminuje nieprzyjemnych niespodzianek i możliwość przesłania do udzielania podwyższonego poziomu uprawnień jako szybkiej poprawki. Identyfikator logowania programu SQL Server można użyć do testowania, nawet jeśli Twoja aplikacja jest przeznaczona do wdrożenia przy użyciu uwierzytelniania Windows.  
  
## <a name="role-based-permissions"></a>Uprawnienia opartej na rolach  
 Udzielanie uprawnień do ról, a nie do użytkowników upraszcza administrowanie zabezpieczeniami. Zestawy uprawnień, które są przypisane do ról są dziedziczone przez wszystkie elementy członkowskie roli. Łatwiej dodawać i usuwać użytkowników z roli, niż jest to, aby ponownie utworzyć oddzielne uprawnienia ustawia dla poszczególnych użytkowników. Role mogą być zagnieżdżone; jednak zbyt wiele poziomów zagnieżdżenia może obniżyć wydajność. Możesz również dodać użytkowników do ról stałej bazy danych, aby uprościć przypisywanie uprawnień.  
  
 Można przyznać uprawnienia na poziomie schematu. Użytkownicy automatycznie dziedziczą uprawnienia na wszystkich nowych obiektów utworzonych w schemacie; nie musisz udzielić uprawnień w miarę tworzenia nowych obiektów.  
  
## <a name="permissions-through-procedural-code"></a>Uprawnienia za pomocą kod proceduralny  
 Zawieranie dostęp do danych za pośrednictwem modułów, takie jak procedur przechowywanych i funkcji zdefiniowanych przez użytkownika zapewnia dodatkową warstwę ochrony wokół aplikacji. Aby uniemożliwić użytkownikom bezpośrednie interakcje z obiektów bazy danych, przyznając uprawnienia tylko do procedur przechowywanych i funkcji podczas odmawianie uprawnień do obiektów podstawowych, takich jak tabele. Program SQL Server osiąga to za pomocą łańcucha własności.  
  
## <a name="permission-statements"></a>Instrukcje uprawnień  
 Trzy instrukcje języka Transact-SQL w uprawnienia są opisane w poniższej tabeli.  
  
|Uprawnienia — instrukcja|Opis|  
|--------------------------|-----------------|  
|PRZYDZIAŁ|Udziela uprawnienia.|  
|ODWOŁYWANIE|Odwołuje uprawnienia. Jest to domyślny stan nowego obiektu. Uprawnienie odwołane dla użytkownika lub rolę nadal może być dziedziczona z innych grup lub ról, którym przypisano podmiot zabezpieczeń.|  
|ODMÓW|ODMÓW odwołuje uprawnienia, tak aby nie może być dziedziczona. Odmowa ma pierwszeństwo przed wszystkie uprawnienia, z wyjątkiem ODMÓW nie ma zastosowania do obiektów właściciele i członkowie `sysadmin`. Odmowa uprawnień do obiektu do `public` roli jest możliwy wszyscy użytkownicy i role z wyjątkiem właścicieli obiektów i `sysadmin` elementów członkowskich.|  
  
-   Wykonywanie instrukcji GRANT można przypisać uprawnienia do grupy lub roli, które mogą być dziedziczone przez użytkowników bazy danych. Jednak instrukcji DENY ma pierwszeństwo przed wszystkie inne instrukcje uprawnień. W związku z tym, użytkownik, który odmówiono uprawnień nie może dziedziczyć po jego innej roli.  
  
> [!NOTE]
>  Elementy członkowskie `sysadmin` stałej roli i obiekt właścicieli nie odmówiono uprawnień.  
  
## <a name="ownership-chains"></a>Łańcuchy własności  
 Program SQL Server gwarantuje, że tylko jednostek, które zostały udzielone uprawnienia dostępu do obiektów. Gdy wielu obiektów bazy danych uzyskują dostęp do siebie nawzajem, kolejność jest określana jako łańcuch. Gdy program SQL Server jest kierowany łącza w łańcuchu, ocenia uprawnień inaczej niż po jego zostały uzyskiwania dostępu do każdego elementu oddzielnie. Gdy obiekt jest dostępny za pośrednictwem łańcuch, programu SQL Server najpierw porównuje właściciela obiektu do właściciela obiekt wywołujący (poprzedniej konsolidacji w łańcuchu). Jeśli oba obiekty mają tego samego właściciela, uprawnienia do przywoływanego obiektu nie są sprawdzane. Zawsze, gdy obiekt uzyskuje dostęp do innego obiektu, który ma innego właściciela, łańcucha własności jest uszkodzona i programu SQL Server, należy zaznaczyć kontekstu zabezpieczeń obiektu wywołującego.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Kod proceduralny działań i tworzenie łańcuchów własności  
 Załóżmy, że użytkownik otrzymuje uprawnienia do wykonywania dotyczące procedury przechowywanej, która wybiera dane z tabeli. Jeśli procedura składowana i tabeli mają tego samego właściciela, użytkownik nie musi mieć wszystkie uprawnienia w tabeli i może nawet odmówiono uprawnień. Jednak jeśli procedura składowana a tabelą mieć różnych właścicieli, programu SQL Server należy sprawdzić uprawnienia użytkownika w tabeli przed zezwoleniem na dostęp do danych.  
  
> [!NOTE]
>  Tworzenie łańcucha własności nie ma zastosowania w przypadku dynamicznych instrukcji SQL. Aby wywołać procedurę, która wykonuje instrukcję SQL, obiekt wywołujący musi mieć uprawnienia na tabelach źródłowych, narażając aplikacji do ataku polegającego na iniekcji SQL. SQL Server udostępnia nowe mechanizmy, takie jak personifikacji i podpisywania modułów za pomocą certyfikatów, które nie wymagają przyznawanie uprawnień do tabel podstawowych. Mogą one także używane przy użyciu procedur składowanych CLR.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Uprawnienia](/sql/relational-databases/security/permissions-database-engine)|Zawiera tematy, zawierająca opis uprawnienia hierarchii, widoków wykazu i uprawnienia stałe role serwera i bazy danych.|
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
