---
title: Serwer i role bazy danych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: c7fdac92c2d980669a3cc3bf67119bdbb42509a4
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091815"
---
# <a name="server-and-database-roles-in-sql-server"></a>Serwer i role bazy danych w programie SQL Server
Wszystkie wersje programu SQL Server przy użyciu opartej na rolach zabezpieczeń, dzięki czemu można przypisać uprawnienia do roli lub grupy użytkowników, a nie do poszczególnych użytkowników. Stałej i ról stałej bazy danych mają stały zestaw uprawnień przypisanych do nich.  
  
## <a name="fixed-server-roles"></a>Role serwera stałej  
 Stałej role mają stały zestaw uprawnień i zakres całego serwera. Są one przeznaczone do użytku w administrowanie serwerem programu SQL Server i nie można zmienić uprawnienia przypisane do nich. Logowania można przypisać do ról stałej bez konta użytkownika w bazie danych.  
  
> [!IMPORTANT]
>  `sysadmin` Stałej roli serwera obejmuje wszystkie inne role i ma nieograniczonego zakresu uprawnień. Nie należy dodawać podmiotów zabezpieczeń do tej roli, chyba że są wysoce zaufanym. `sysadmin` Członkowie roli są nieodwołalnej uprawnienia administracyjne na wszystkich zasobów i serwera bazy danych.  
  
 Dodawanie użytkowników do ról stałej, zachować ostrożność. Na przykład `bulkadmin` rola pozwala użytkownikom wstawić zawartość dowolnego pliku lokalnego do tabeli, które mogłyby zagrozić integralności danych. Zobacz dokumentację SQL Server — książki Online szczegółowy wykaz stałej role i uprawnienia.  
  
## <a name="fixed-database-roles"></a>Ustalone role bazy danych  
 Ról stałej bazy danych mają wstępnie zdefiniowany zestaw uprawnień, które są przeznaczone do umożliwiają łatwe zarządzanie grupy uprawnień. Elementy członkowskie `db_owner` roli mogą wykonywać wszystkie działania konfiguracji i konserwacji na bazie danych.  
  
 Aby uzyskać więcej informacji na temat programu SQL Server, wstępnie zdefiniowanych ról, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Ról na poziomie serwera](/sql/relational-databases/security/authentication-access/server-level-roles)|W tym artykule opisano stałej ról i uprawnień skojarzonych z nimi w programie SQL Server.|  
|[Ról na poziomie bazy danych](/sql/relational-databases/security/authentication-access/database-level-roles)|Opis ról stałej bazy danych i uprawnień skojarzonych z nimi|  
  
## <a name="database-roles-and-users"></a>Role bazy danych i użytkowników  
 Nazwy logowania muszą być zamapowane do kont użytkowników bazy danych w celu pracy z obiektami bazy danych. Bazy danych można następnie można dodać użytkowników do ról bazy danych, dziedziczenie żadnych zestawów uprawnień skojarzonych z tymi rolami. Mogą być przyznawane wszystkie uprawnienia.  
  
 Należy również rozważyć `public` roli `dbo` konta użytkownika i `guest` konta podczas projektowania zabezpieczeń dla aplikacji.  
  
### <a name="the-public-role"></a>Roli publicznej  
 `public` Roli znajduje się w każdej bazie danych, która obejmuje systemowych baz danych. Nie można usunąć, i nie można dodać lub usunąć użytkowników z niego. Uprawnienia przyznane `public` roli są dziedziczone przez wszystkich użytkowników i ról, ponieważ należą one do `public` roli domyślnie. Udziel `public` tylko uprawnienia, aby wszyscy użytkownicy mają.  
  
### <a name="the-dbo-user-account"></a>Właściciela konta użytkownika  
 `dbo`, Lub właściciel bazy danych, to konto użytkownika, który ma też dorozumianych uprawnienia do wykonywania wszystkich działań w bazie danych. Elementy członkowskie `sysadmin` stałej roli serwera są automatycznie mapowane na `dbo`.  
  
> [!NOTE]
>  `dbo` jest także nazwa schematu, zgodnie z opisem w [własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 `dbo` Konto użytkownika jest często mylić z `db_owner` stałej roli bazy danych. Zakres `db_owner` jest bazą danych; zakres `sysadmin` jest całego serwera. Członkostwo w grupie `db_owner` rola przyznaje `dbo` uprawnienia użytkownika.  
  
### <a name="the-guest-user-account"></a>Konto użytkownika gościa  
 Po użytkownik został uwierzytelniony i mogą logować się do wystąpienia programu SQL Server, oddzielne konto użytkownika musi istnieć w każdej bazie danych, użytkownik będzie musiał uzyskać dostęp. Wymagania konta użytkownika w każdej bazie danych uniemożliwia użytkownikom łączenie się z wystąpieniem programu SQL Server i uzyskiwania dostępu do wszystkich baz danych na serwerze. Istnienie `guest` konta użytkownika w bazie danych zmierzone to wymaganie, umożliwiając logowania bez dostępu do bazy danych konta użytkownika bazy danych.  
  
 `guest` Konto jest kontem wbudowanego we wszystkich wersjach programu SQL Server. Domyślnie jest wyłączona w nowych baz danych. Jeśli jest włączone, można to wyłączyć odwołując jego uprawnienia CONNECT przez wykonanie instrukcji języka Transact-SQL ODWOŁAĆ POŁĄCZYĆ z GOŚCIA.  
  
> [!IMPORTANT]
>  Unikaj używania `guest` konta; wszystkie nazwy logowania bez uprawnień do bazy danych uzyskać uprawnienia bazy danych do tego konta. Jeśli musisz użyć `guest` konto, przyznać jej minimalny poziom uprawnień.  
  
 Aby uzyskać więcej informacji na temat nazw logowania, użytkownicy i role programu SQL Server zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Rozpoczęcie korzystania z uprawnień aparatu bazy danych](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Zawiera łącza do tematów opisujących podmiotów zabezpieczeń, ról, poświadczenia, obiektów zabezpieczanych i uprawnienia.|  
|[Podmiotów zabezpieczeń](/sql/relational-databases/security/authentication-access/principals-database-engine)|W tym artykule opisano podmiotów zabezpieczeń i zawiera łącza do tematów, które opisują role serwera i bazy danych.|  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
