---
title: Serwer i role bazy danych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: f3e31aa67bfbaa541d8d1eb5b8b61dfd28182c72
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791779"
---
# <a name="server-and-database-roles-in-sql-server"></a>Serwer i role bazy danych w programie SQL Server
Wszystkie wersje SQL Server korzystają z zabezpieczeń opartych na rolach, które umożliwiają przypisywanie uprawnień do roli lub grupy użytkowników, a nie do poszczególnych użytkowników. Stałe role serwera i stałych baz danych mają przypisane do nich stały zestaw uprawnień.  
  
## <a name="fixed-server-roles"></a>Stałe role serwera  
 Stałe role serwera mają stały zestaw uprawnień i zakres całego serwera. Są one przeznaczone do użytku w administrowaniu SQL Server i nie można zmienić przypisanych do nich uprawnień. Nazwy logowania można przypisywać do stałych ról serwera bez konieczności używania konta użytkownika w bazie danych.  
  
> [!IMPORTANT]
> `sysadmin` Stała rola serwera obejmuje wszystkie pozostałe role i ma nieograniczony zakres. Nie należy dodawać podmiotów zabezpieczeń do tej roli, chyba że są one wysoce zaufane. `sysadmin`Członkowie roli mają nieodwołalne uprawnienia administracyjne do wszystkich baz danych i zasobów serwera.  
  
 Być wybiórcze w przypadku dodawania użytkowników do stałych ról serwera. Na przykład `bulkadmin` rola umożliwia użytkownikom wstawianie zawartości dowolnego pliku lokalnego do tabeli, co może zagrozić integralności danych. Zobacz dokumentację SQL Server Books Online, aby uzyskać pełną listę stałych ról i uprawnień serwera.  
  
## <a name="fixed-database-roles"></a>Stałe role bazy danych  
 Stałe role bazy danych mają wstępnie zdefiniowany zestaw uprawnień, które zostały zaprojektowane tak, aby umożliwić łatwe zarządzanie grupami uprawnień. `db_owner` Członkowie roli mogą wykonywać wszystkie działania związane z konfiguracją i konserwacją w bazie danych.  
  
 Aby uzyskać więcej informacji na temat SQL Server wstępnie zdefiniowanych ról, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Role na poziomie serwera](/sql/relational-databases/security/authentication-access/server-level-roles)|Zawiera opis stałych ról serwera i skojarzonych z nimi uprawnień w SQL Server.|  
|[Role na poziomie bazy danych](/sql/relational-databases/security/authentication-access/database-level-roles)|Opisuje stałe role bazy danych i skojarzone z nimi uprawnienia|  
  
## <a name="database-roles-and-users"></a>Role bazy danych i użytkownicy  
 Aby można było korzystać z obiektów bazy danych, nazwy logowania muszą być mapowane na konta użytkowników bazy danych. Użytkowników bazy danych można następnie dodać do ról bazy danych, dziedziczących wszystkie zestawy uprawnień skojarzone z tymi rolami. Wszystkie uprawnienia można udzielić.  
  
 Podczas projektowania zabezpieczeń aplikacji należy `public` również wziąć pod `dbo` uwagę rolę, konto `guest` użytkownika i konto.  
  
### <a name="the-public-role"></a>Rola publiczna  
 `public` Rola jest zawarta w każdej bazie danych, która obejmuje systemowe bazy danych. Nie można go porzucić i nie można dodawać ani usuwać użytkowników. Uprawnienia przyznane `public` roli są dziedziczone przez wszystkich innych użytkowników i ról, ponieważ należą `public` do roli domyślnie. Przyznaj `public` tylko uprawnienia, które mają mieć wszyscy użytkownicy.  
  
### <a name="the-dbo-user-account"></a>Konto użytkownika dbo  
 `dbo`Właścicielem bazy danych jest konto użytkownika, które ma implikowane uprawnienia do wykonywania wszystkich działań w bazie danych. Członkowie stałej roli serwera są automatycznie zamapowane na `dbo`. `sysadmin`  
  
> [!NOTE]
> `dbo`jest również nazwą schematu, zgodnie z opisem w sekcji [własność i separacja w schemacie użytkownika w SQL Server](ownership-and-user-schema-separation-in-sql-server.md).  
  
 Konto użytkownika jest często mylone `db_owner` ze stałą rolą bazy danych. `dbo` Zakresem `db_owner` jest baza danych; `sysadmin` zakresem jest cały serwer. Członkostwo w `db_owner` roli nie `dbo` przyznaje uprawnień użytkownika.  
  
### <a name="the-guest-user-account"></a>Konto użytkownika-gościa  
 Gdy użytkownik zostanie uwierzytelniony i będzie mógł zalogować się do wystąpienia SQL Server, do każdej bazy danych musi istnieć osobne konto użytkownika, do którego użytkownik ma dostęp. Wymaganie konta użytkownika w każdej bazie danych uniemożliwia użytkownikom nawiązywanie połączenia z wystąpieniem SQL Server i uzyskiwanie dostępu do wszystkich baz danych na serwerze. Istnienie `guest` konta użytkownika w bazie danych spowoduje obejście tego wymagania przez zezwolenie na logowanie bez konta użytkownika bazy danych w celu uzyskania dostępu do bazy danych.  
  
 To `guest` konto jest wbudowane we wszystkich wersjach SQL Server. Domyślnie jest on wyłączony w nowych bazach danych. Jeśli ta funkcja jest włączona, można ją wyłączyć przez odwołanie się do jej uprawnienia Połącz przez wykonanie instrukcji ODWOŁYWANia połączenia języka Transact-SQL z poziomu GOŚCIa.  
  
> [!IMPORTANT]
> Unikaj korzystania `guest` z konta; wszystkie identyfikatory logowania bez własnych uprawnień bazy danych uzyskują uprawnienia bazy danych przyznane dla tego konta. Jeśli musisz użyć `guest` konta, udziel im minimalnych uprawnień.  
  
 Aby uzyskać więcej informacji na temat SQL Server logowania, użytkowników i ról, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Wprowadzenie z uprawnieniami aparatu bazy danych](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Zawiera łącza do tematów opisujących podmioty zabezpieczeń, role, poświadczenia, zabezpieczenia i uprawnienia.|  
|[Podmiotów](/sql/relational-databases/security/authentication-access/principals-database-engine)|Opisuje podmioty zabezpieczeń i zawiera linki do tematów, które opisują role serwera i bazy danych.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Uwierzytelnianie w programie SQL Server](authentication-in-sql-server.md)
- [Własność i oddzielenie schematu użytkownika w programie SQL Server](ownership-and-user-schema-separation-in-sql-server.md)
- [Autoryzacja i uprawnienia w programie SQL Server](authorization-and-permissions-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
