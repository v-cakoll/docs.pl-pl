---
title: Autoryzacja i uprawnienia w programie SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d476b3fc3cce1bcb283f740f734ae285e55e192
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autoryzacja i uprawnienia w programie SQL Server
Podczas tworzenia obiektów bazy danych musi jawnie udzielić uprawnień, aby udostępnić je użytkownikom. Co zabezpieczanego obiektu ma uprawnienia, które mogą być przyznane uprawnienia instrukcje using podmiot zabezpieczeń.  
  
## <a name="the-principle-of-least-privilege"></a>Zasadą najniższych uprawnień  
 Opracowywanie aplikacji przy użyciu podejścia użytkownika najmniej uprzywilejowane konta (LUA) jest ważną częścią strategii obrony, szczegółowe przeciwdziałanie zagrożenia bezpieczeństwa. Podejście LUA temu postępuj zgodnie z zasadą najniższych uprawnień użytkowników i zawsze zalogować się z kontami użytkownika standardowego. Zadania administracyjne są podzielone przy użyciu ról serwera, a także korzystanie z `sysadmin` stałej roli serwera jest znacznie ograniczone.  
  
 Należy zawsze wykonać zasadą najniższych uprawnień podczas udzielania uprawnień użytkownikom bazy danych. Przyznaj minimalne uprawnienia wymagane do użytkownika lub roli do wykonania danego zadania.  
  
> [!IMPORTANT]
>  Tworzenie i testowanie aplikacji przy użyciu podejścia LUA dodaje stopień trudności do procesu tworzenia. Możliwe jest łatwiejsze tworzenie obiektów i pisania kodu, zaloguj się jako administratora systemu lub właściciela bazy danych nie jest używa konta LUA. Jednak opracowywanie aplikacji przy użyciu wysoko uprzywilejowane konto można zasłaniają wpływ ograniczonej funkcjonalności, gdy użytkownicy najniższych uprawnieniach próba uruchomienia aplikacji, która wymaga uprawnień z podwyższonym poziomem uprawnień, aby działać poprawnie. Udzielanie uprawnień nadmiernego użytkownikom, aby ponownie pozyskać funkcji utracone pozostawić aplikacji narażony na ataki. Projektowanie, tworzenie i testowanie aplikacji zalogowany przy użyciu konta LUA wymusza wolą podejście do planowania zabezpieczeń, która eliminuje nieprzyjemny niespodzianki i możliwość przesłania przyznanie podniesionych uprawnień jako szybkiej poprawki. Logowania programu SQL Server można użyć do testowania, nawet jeśli aplikacja jest przeznaczona do wdrożenia przy użyciu uwierzytelniania systemu Windows.  
  
## <a name="role-based-permissions"></a>Uprawnienia oparte na rolach  
 Udzielanie uprawnień do ról, a nie do użytkowników upraszcza administrowania zabezpieczeniami. Zestawy uprawnień, które są przypisane do ról są dziedziczone przez wszystkie elementy członkowskie roli. Łatwiej dodawać i usuwać użytkowników z roli, niż jest to, aby ponownie utworzyć oddzielne uprawnienia ustawia dla poszczególnych użytkowników. Role mogą być zagnieżdżane; zbyt wiele poziomów zagnieżdżenia może jednak zmniejszyć wydajność. Można również dodać użytkowników do ról upraszcza przypisywanie uprawnień stałej bazy danych.  
  
 Można przyznać uprawnień na poziomie schematu. Użytkownicy automatycznie dziedziczą uprawnienia do wszystkich nowych obiektów tworzonych w schemacie; nie trzeba udzielić uprawnień w miarę tworzenia nowych obiektów.  
  
## <a name="permissions-through-procedural-code"></a>Uprawnienia za pomocą procedur kodu  
 Zawieranie dostęp do danych za pośrednictwem modułów, takich jak procedury składowane i funkcje zdefiniowane przez użytkownika zapewnia dodatkową warstwę ochrony wokół aplikacji. Aby uniemożliwić użytkownikom bezpośrednio interakcji z obiektami bazy danych przez udzielanie uprawnień tylko do procedury składowanej lub funkcji odrzuca uprawnień do obiektów podstawowych, takich jak tabele. SQL Server osiąga to, własność łańcucha.  
  
## <a name="permission-statements"></a>Instrukcje uprawnień  
 Trzy instrukcji języka Transact-SQL w uprawnienia są opisane w poniższej tabeli.  
  
|Instrukcja uprawnień|Opis|  
|--------------------------|-----------------|  
|UDZIEL|Udziela uprawnienia.|  
|ODWOŁYWANIE|Odwołuje uprawnienia. Jest to domyślny stan nowego obiektu. Uprawnienie odwołany od użytkownika lub roli nadal mogą być dziedziczone z innych grup lub ról, którym przypisano podmiot zabezpieczeń.|  
|ODMÓW|ODMÓW odwołuje uprawnienia tak, aby nie może być dziedziczona. Odmowa ma pierwszeństwo przed wszystkie uprawnienia, z wyjątkiem ODMÓW nie ma zastosowania do obiektu właścicieli i członkowie `sysadmin`. Odmowa uprawnień do obiektu do `public` roli jest zabroniony wszystkich użytkowników i ról z wyjątkiem właścicieli obiektów i `sysadmin` elementów członkowskich.|  
  
-   Instrukcja GRANT można przypisać uprawnienia do grupy lub roli, które mogą być dziedziczone przez użytkowników bazy danych. Jednak instrukcji odmowa ma pierwszeństwo przed wszystkie inne instrukcje uprawnień. W związku z tym odmówiono uprawnienia użytkownika nie może dziedziczyć po jego innej roli.  
  
> [!NOTE]
>  Elementy członkowskie `sysadmin` właścicieli roli i obiekt serwera nie może być odmówiono uprawnień.  
  
## <a name="ownership-chains"></a>Łańcuchy własności  
 SQL Server zapewnia, że tylko podmiotów zabezpieczeń, którym przyznano uprawnienia można dostęp do obiektów. W przypadku wielu obiektów bazy danych, dostęp do siebie, sekwencja jest określany jako łańcucha. Gdy program SQL Server jest przechodzenie łączy w łańcuchu, oblicza uprawnienia inaczej niż po jego zostały dostęp do każdego elementu oddzielnie. Gdy obiekt jest dostępny za pośrednictwem łańcucha, SQL Server najpierw porównuje właściciela obiektu do właściciela obiektu wywołującego (poprzedniej konsolidacji w łańcuchu). Jeśli oba obiekty mają tego samego właściciela, uprawnienia przywoływanego obiektu nie są sprawdzane. Zawsze, gdy obiekt uzyskuje dostęp do innego obiektu, który ma innego właściciela, łańcuch własności został przerwany, a program SQL Server musi sprawdzić kontekstu zabezpieczeń obiektu wywołującego.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Kod procedury i łańcucha własności  
 Załóżmy, że użytkownik otrzymuje uprawnienia do wykonywania dotyczące procedury przechowywanej, która wybiera danych z tabeli. Jeśli procedura składowana i tabeli mają tego samego właściciela, użytkownik nie musi mieć wszystkie uprawnienia w tabeli i może nawet odmówiono uprawnień. Jednak jeśli procedura i tabela mieć różnych właścicieli, SQL Server musi sprawdzać uprawnienia użytkownika w tabeli przed zezwoleniem na dostęp do danych.  
  
> [!NOTE]
>  Tworzenie łańcuchów własność nie ma zastosowania w przypadku dynamicznych instrukcji SQL. Wywoływanie procedury, która wykonuje instrukcję SQL, wywołujący musi mieć uprawnienia na tabel, pozostawiając aplikacji narażone na atak iniekcja kodu SQL. Program SQL Server stanowi nowych mechanizmów, takich jak personifikacji i podpisywania modułów za pomocą certyfikatów, które nie wymagają przyznawanie uprawnień do tabel. Mogą one również używane w procedurach składowanych CLR.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Uprawnienia](http://msdn.microsoft.com/library/ms191291.aspx) w dokumentacji SQL Server Books Online|Zawiera tematy opisujące hierarchii uprawnień, widoków wykazu i uprawnienia stałe role serwera i bazy danych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
