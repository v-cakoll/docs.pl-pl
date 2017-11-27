---
title: "Serwer i ról bazy danych w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0bcb42e018f5e62179924634bfa49fcbfc4c7d16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="server-and-database-roles-in-sql-server"></a>Serwer i ról bazy danych w programie SQL Server
Wszystkie wersje programu SQL Server, użyj opartej na rolach zabezpieczeń, dzięki czemu można przypisać uprawnienia do roli lub grupy użytkowników, a nie dla poszczególnych użytkowników. Stały server i bazy danych mają ustalony zbiór przypisane im uprawnienia.  
  
## <a name="fixed-server-roles"></a>Role serwera  
 Role serwera stałej ma ustalony zbiór uprawnień i zakres całego serwera. Są one przeznaczone do użytku podczas administrowania programu SQL Server i nie można zmienić uprawnienia przypisane do nich. Logowania można przypisać do ról serwera bez konieczności konto użytkownika w bazie danych.  
  
> [!IMPORTANT]
>  `sysadmin` Stałej roli serwera obejmuje wszystkie inne role i ma nieograniczonego zakresu. Nie należy dodawać podmiotów zabezpieczeń do tej roli, chyba że są wysoce zaufanych. `sysadmin`Członkowie roli mają nieodwołalną uprawnienia administracyjne na wszystkich baz danych serwera i zasobów.  
  
 Dodawanie użytkowników do ról serwera, zachować ostrożność. Na przykład `bulkadmin` roli umożliwia użytkownikom Wstaw zawartość z dowolnego pliku lokalnego do tabeli, które mogłyby zagrozić integralności danych. Zobacz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online, aby uzyskać pełną listę ról serwera i uprawnienia.  
  
## <a name="fixed-database-roles"></a>Stałe role bazy danych  
 Stałe role bazy danych zostały wstępnie zdefiniowany zestaw uprawnień, które są zaprojektowane, aby umożliwić łatwe zarządzanie grupy uprawnień. Elementy członkowskie `db_owner` rola może wykonać wszystkie czynności dotyczące konfiguracji i konserwacji na bazie danych.  
  
 Aby uzyskać więcej informacji o programie SQL Server wstępnie zdefiniowanych ról, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Role na poziomie serwera](http://msdn.microsoft.com/library/ms188659.aspx) i [uprawnienia ról serwera](http://msdn.microsoft.com/library/ms175892.aspx) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online|W tym artykule opisano role serwera i uprawnienia skojarzone z nimi w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
|[Role bazy danych na poziomie](http://msdn.microsoft.com/library/ms189121.aspx) i [uprawnienia bazy danych](http://msdn.microsoft.com/library/ms189612.aspx) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online|Opisuje bazy danych i skojarzone z nimi uprawnienia|  
  
## <a name="database-roles-and-users"></a>Role bazy danych i użytkowników  
 Nazwy logowania muszą być zamapowane do kont użytkowników bazy danych do pracy z obiektami bazy danych. Bazy danych można następnie można dodać użytkowników do ról bazy danych dziedziczy wszystkie zestawy uprawnień skojarzonych z tymi rolami. Mogą być przyznawane wszystkie uprawnienia.  
  
 Należy również rozważyć `public` roli, `dbo` konta użytkownika i `guest` konta podczas projektowania zabezpieczeń aplikacji.  
  
### <a name="the-public-role"></a>W roli publicznej  
 `public` Roli znajduje się w każdej bazie danych obejmuje systemowych baz danych. Nie można porzucić i nie można dodawać ani usuwać użytkowników. Uprawnienia przyznane `public` roli są dziedziczone przez wszystkich użytkowników i ról, ponieważ należą do `public` roli domyślnie. Udziel `public` tylko uprawnienia mają wszyscy użytkownicy mają korzystać.  
  
### <a name="the-dbo-user-account"></a>Konto użytkownika dbo  
 `dbo`, Lub bazy danych właściciela, to konto użytkownika, który ma niejawnego uprawnienia do wykonywania wszystkich działań w bazie danych. Elementy członkowskie `sysadmin` stałej roli serwera są automatycznie mapowane na `dbo`.  
  
> [!NOTE]
>  `dbo`jest także nazwa schematu, zgodnie z opisem w [własności i oddzielenie użytkowników schematu w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 `dbo` Konto użytkownika jest często pomylić z `db_owner` stałej roli bazy danych. Zakres `db_owner` jest bazą danych; zakres `sysadmin` jest całego serwera. Członkostwo w grupie `db_owner` rola przyznaje `dbo` uprawnienia użytkownika.  
  
### <a name="the-guest-user-account"></a>Konto użytkownika gościa  
 Po ukończeniu uwierzytelniony użytkownik i mogą logować się do wystąpienia programu SQL Server, oddzielne konto użytkownika musi istnieć w każdej bazie danych, użytkownik będzie musiał uzyskać dostęp. Wymagającą konta użytkownika w każdej bazie danych uniemożliwia użytkownikom łączenie się z wystąpieniem programu SQL Server oraz uzyskiwanie dostępu do wszystkich baz danych na serwerze. Istnienie `guest` konta użytkownika w bazie danych obejścia tego wymagania, zezwalając logowania bez dostępu do bazy danych konta użytkownika bazy danych.  
  
 `guest` Konto jest kontem wbudowanego we wszystkich wersjach programu SQL Server. Domyślnie jest wyłączona w nowych baz danych. Jeśli jest włączone, można ją wyłączyć za odwoływanie jego uprawnienia CONNECT przez wykonywania instrukcji języka Transact-SQL ODWOŁAĆ POŁĄCZ z GOŚCIA.  
  
> [!IMPORTANT]
>  Unikaj używania `guest` konta; Synch bez uprawnień do bazy danych uzyskać uprawnienia bazy danych do tego konta. Jeśli musisz użyć `guest` konto, przyznać jej minimalne uprawnienia.  
  
 Aby uzyskać więcej informacji dotyczących logowania, użytkownicy i role programu SQL Server zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Tożsamości i kontroli dostępu](http://msdn.microsoft.com/library/bb510418.aspx) w dokumentacji SQL Server Books Online|Zawiera linki do tematów opisujących podmiotów zabezpieczeń, ról, poświadczenia, zabezpieczanych obiektów i uprawnienia.|  
|[Podmioty zabezpieczeń](http://msdn.microsoft.com/library/ms181127.aspx) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online|Zawiera opis głównych i zawiera linki do tematów opisujących ról serwera i bazy danych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Uwierzytelnianie programu SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Własność i oddzielenie użytkowników schematu w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
