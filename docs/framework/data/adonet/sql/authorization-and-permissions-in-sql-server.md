---
title: Autoryzacja i uprawnienia w programie SQL Server
description: Dowiedz się, jak jawnie przyznać uprawnienia do tworzenia obiektów bazy danych, które są dostępne dla użytkowników w SQL Server z ADO.NET.
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: eb01e29b36da5e1793b9176301a968a42115d19c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286536"
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autoryzacja i uprawnienia w programie SQL Server
Podczas tworzenia obiektów bazy danych należy jawnie udzielić uprawnień, aby były dostępne dla użytkowników. Każdy zabezpieczany obiekt ma uprawnienia, które mogą zostać przyznane podmiotowi zabezpieczeń przy użyciu instrukcji uprawnień.  
  
## <a name="the-principle-of-least-privilege"></a>Zasada najniższych uprawnień  
 Opracowywanie aplikacji przy użyciu podejścia z najniższymi uprawnieniami konta użytkownika (LUA) to ważna część obrony, szczegółowej strategii dotyczącej liczników zagrożeń zabezpieczeń. Podejście LUA gwarantuje, że użytkownicy będą przestrzegać zasad najniższych uprawnień i zawsze logować się z ograniczonymi kontami użytkowników. Zadania administracyjne są rozbite przy użyciu stałych ról serwera, a korzystanie z `sysadmin` stałej roli serwera jest poważnie ograniczone.  
  
 Zawsze stosuj zasadę najniższych uprawnień podczas udzielania uprawnień użytkownikom bazy danych. Przyznaj użytkownikowi lub roli minimalne uprawnienia wymagane do wykonania danego zadania.  
  
> [!IMPORTANT]
> Opracowywanie i testowanie aplikacji przy użyciu podejścia LUA powoduje dodanie stopnia trudności w procesie opracowywania. Łatwiej jest tworzyć obiekty i pisać kod podczas logowania jako administrator systemu lub właściciel bazy danych niż przy użyciu konta LUA. Aplikacje korzystające z wysoce uprzywilejowanego konta mogą jednak zasłaniać wpływ ograniczonej funkcjonalności w przypadku próby uruchomienia aplikacji wymagającej podwyższonego poziomu uprawnień w celu poprawnego działania. Przyznawanie nadmiernych uprawnień użytkownikom w celu ponownego uzyskania utraconych funkcji może spowodować, że aplikacja będzie narażona na ataki. Projektowanie, opracowywanie i testowanie aplikacji zalogowanej przy użyciu konta LUA wymusza podejście do planowania zabezpieczeń, które eliminuje nieprzyjemne nieprzyjemny i Temptation, aby udzielić podwyższonych uprawnień jako szybkiej poprawki. Możesz użyć SQL Server logowania do testowania, nawet jeśli aplikacja jest przeznaczona do wdrożenia przy użyciu uwierzytelniania systemu Windows.  
  
## <a name="role-based-permissions"></a>Uprawnienia oparte na rolach  
 Przyznanie uprawnień rolom, a nie użytkownikom, upraszcza administrację zabezpieczeniami. Zestawy uprawnień przypisane do ról są dziedziczone przez wszystkich członków roli. Łatwiej jest dodawać i usuwać użytkowników z roli niż w przypadku ponownego tworzenia oddzielnych zestawów uprawnień dla poszczególnych użytkowników. Role mogą być zagnieżdżane; jednak zbyt wiele poziomów zagnieżdżenia może obniżyć wydajność. Możesz również dodać użytkowników do stałych ról bazy danych, aby uprościć przypisywanie uprawnień.  
  
 Można udzielić uprawnień na poziomie schematu. Użytkownicy automatycznie dziedziczą uprawnienia do wszystkich nowych obiektów utworzonych w schemacie. nie trzeba przyznawać uprawnień w miarę tworzenia nowych obiektów.  
  
## <a name="permissions-through-procedural-code"></a>Uprawnienia poprzez kod proceduralny  
 Hermetyzowanie dostępu do danych za poorednictwem modułów, takich jak procedury składowane i funkcje zdefiniowane przez użytkownika, zapewnia dodatkową warstwę ochrony aplikacji. Można uniemożliwić użytkownikom bezpośrednią współpracę z obiektami bazy danych przez przyznanie uprawnień tylko do procedur składowanych lub funkcji przy odmowie uprawnień do obiektów bazowych, takich jak tabele. SQL Server osiąga to przez tworzenie łańcucha własności.  
  
## <a name="permission-statements"></a>Instrukcje dotyczące uprawnień  
 W poniższej tabeli opisano trzy instrukcje dotyczące uprawnień języka Transact-SQL.  
  
|Oświadczenie dotyczące uprawnień|Opis|  
|--------------------------|-----------------|  
|DAWAĆ|Przyznaje uprawnienia.|  
|ODWOŁANIA|Odwołuje uprawnienie. Jest to domyślny stan nowego obiektu. Uprawnienie odwołane od użytkownika lub roli można nadal dziedziczyć z innych grup lub ról, do których jest przypisany podmiot zabezpieczeń.|  
|DENY|Odmów unieważnia uprawnienia, aby nie można było dziedziczyć. Odmów ma pierwszeństwo przed wszystkimi uprawnieniami, z wyjątkiem Odmów nie ma zastosowania do właścicieli obiektów lub członków `sysadmin` . Jeśli odmówisz uprawnień do obiektu do `public` roli, odmówiono wszystkim użytkownikom i rolom, z wyjątkiem właścicieli obiektów i `sysadmin` członków.|  
  
- Instrukcja GRANT może przypisywać uprawnienia do grupy lub roli, które mogą być dziedziczone przez użytkowników bazy danych. Jednakże instrukcja DENY ma pierwszeństwo przed wszystkimi innymi instrukcjami uprawnień. W związku z tym użytkownik, który odmówił uprawnienia, nie może dziedziczyć go z innej roli.  
  
> [!NOTE]
> Członkom `sysadmin` stałej roli serwera i właścicieli obiektów nie można odmówić uprawnień.  
  
## <a name="ownership-chains"></a>Łańcuchy własności  
 SQL Server zapewnia, że tylko podmioty zabezpieczeń, którym udzielono uprawnień, mogą uzyskiwać dostęp do obiektów. Gdy wiele obiektów bazy danych uzyskuje dostęp nawzajem, sekwencja jest znana jako łańcuch. Gdy SQL Server przechodzą linki w łańcuchu, szacuje uprawnienia inaczej niż w przypadku uzyskiwania dostępu do poszczególnych elementów osobno. Gdy dostęp do obiektu odbywa się za pomocą łańcucha, SQL Server najpierw porównuje właściciela obiektu z właścicielem obiektu wywołującego (poprzedni link w łańcuchu). Jeśli oba obiekty mają tego samego właściciela, uprawnienia do obiektu, do którego się odwoływano, nie są sprawdzane. Za każdym razem, gdy obiekt uzyskuje dostęp do innego obiektu, który ma innego właściciela, łańcuch własności jest przerwany i SQL Server musi sprawdzić kontekst zabezpieczeń obiektu wywołującego.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Kod proceduralny i tworzenie łańcucha własności  
 Załóżmy, że użytkownik ma przyznane uprawnienia do wykonywania w procedurze składowanej, która wybiera dane z tabeli. Jeśli procedura składowana i tabela mają tego samego właściciela, użytkownik nie musi mieć uprawnień do tabeli i może nawet odmówić uprawnień. Jeśli jednak procedura składowana i tabela mają różnych właścicieli, SQL Server musi sprawdzić uprawnienia użytkownika w tabeli przed zezwoleniem na dostęp do danych.  
  
> [!NOTE]
> Tworzenie łańcucha własności nie ma zastosowania w przypadku dynamicznych instrukcji SQL. Aby wywołać procedurę, która wykonuje instrukcję SQL, obiekt wywołujący musi mieć przyznane uprawnienia do odpowiednich tabel, pozostawiając aplikacji narażonych na ataki z iniekcją SQL. SQL Server udostępnia nowe mechanizmy, takie jak personifikacja i moduły podpisywania z certyfikatami, które nie wymagają przyznawania uprawnień w tabelach bazowych. Mogą one być również używane z procedurami składowanymi CLR.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Więcej informacji zawierają poniższe zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Uprawnienia](/sql/relational-databases/security/permissions-database-engine)|Zawiera tematy opisujące hierarchię uprawnień, widoki wykazu i uprawnienia stałych ról serwera i bazy danych.|
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Uwierzytelnianie w programie SQL Server](authentication-in-sql-server.md)
- [Serwer i role bazy danych w programie SQL Server](server-and-database-roles-in-sql-server.md)
- [Własność i oddzielenie schematu użytkownika w programie SQL Server](ownership-and-user-schema-separation-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
