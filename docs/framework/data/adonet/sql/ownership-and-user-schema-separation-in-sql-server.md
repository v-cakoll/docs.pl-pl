---
title: Własność i oddzielenie schematu użytkownika w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 520772acc5edd812f64c61cc7fdda9db3441c87c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961109"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Własność i oddzielenie schematu użytkownika w programie SQL Server
Podstawową koncepcją SQL Server zabezpieczeń jest to, że właściciele obiektów mają nieodwołalne uprawnienia do administrowania nimi. Nie można usunąć uprawnień z właściciela obiektu i nie można upuścić użytkowników z bazy danych, jeśli są one właścicielami obiektów.  
  
## <a name="user-schema-separation"></a>Oddzielanie schematu użytkownika  
 Separacja schematów użytkownika umożliwia większą elastyczność zarządzania uprawnieniami obiektu bazy danych. *Schemat* to nazwany kontener dla obiektów bazy danych, który umożliwia grupowanie obiektów w oddzielne przestrzenie nazw. Przykładowa baza danych AdventureWorks zawiera schematy dla produkcji, sprzedaży i HumanResources.  
  
 Składnia nazewnictwa czterech części dla odwoływania się do obiektów określa nazwę schematu.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Właściciele i uprawnienia schematu  
 Schematy mogą należeć do każdego podmiotu zabezpieczeń bazy danych, a jeden podmiot zabezpieczeń może być właścicielem wielu schematów. Reguły zabezpieczeń można stosować do schematu, które są dziedziczone przez wszystkie obiekty w schemacie. Po skonfigurowaniu uprawnień dostępu dla schematu te uprawnienia są automatycznie stosowane w miarę dodawania nowych obiektów do schematu. Użytkownikom można przypisać domyślny schemat, a wielu użytkowników bazy danych może współużytkować ten sam schemat.  
  
 Domyślnie, gdy deweloperzy tworzą obiekty w schemacie, obiekty są własnością podmiotu zabezpieczeń, który jest właścicielem schematu, a nie deweloperem. Własność obiektu można przenieść za pomocą instrukcji języka Transact-SQL ALTER AUTHORIZATION. Schemat może również zawierać obiekty należące do różnych użytkowników i mieć bardziej szczegółowe uprawnienia niż te przypisane do schematu, chociaż nie jest to zalecane, ponieważ zwiększa się złożoność zarządzania uprawnieniami. Obiekty mogą być przenoszone między schematami, a własność schematu można przenosić między podmiotami zabezpieczeń. Użytkowników bazy danych można porzucić bez wpływu na schematy.  
  
### <a name="built-in-schemas"></a>Schematy wbudowane  
 SQL Server jest dostarczany z dziesięcioma wstępnie zdefiniowanymi schematami, które mają takie same nazwy, jak wbudowanej użytkownika i role bazy danych. Istnieją one głównie w celu zapewnienia zgodności z poprzednimi wersjami. Można upuścić schematy mające takie same nazwy jak stałe role bazy danych, jeśli nie są potrzebne. Nie można porzucić następujących schematów:  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 Jeśli porzucisz je z bazy danych modelu, nie będą one wyświetlane w nowych bazach danych.  
  
> [!NOTE]
> Schematy `sys` i`INFORMATION_SCHEMA` są zarezerwowane dla obiektów systemowych. Nie można tworzyć obiektów w tych schematach i nie można ich upuścić.  
  
#### <a name="the-dbo-schema"></a>Schemat dbo  
 `dbo` Schemat jest domyślnym schematem nowo utworzonej bazy danych. Schemat jest własnością `dbo` konta użytkownika. `dbo` Domyślnie użytkownicy utworzeni za pomocą polecenia Create User Transact-SQL mają `dbo` jako domyślny schemat.  
  
 Użytkownicy, którym przypisano schemat, `dbo` nie dziedziczą uprawnień `dbo` konta użytkownika. Żadne uprawnienia nie są dziedziczone przez użytkowników ze schematu; uprawnienia schematu są dziedziczone przez obiekty bazy danych zawarte w schemacie.  
  
> [!NOTE]
> Gdy odwoływanie się do obiektów bazy danych przy użyciu jednoczęściowej nazwy, SQL Server najpierw szuka domyślnego schematu użytkownika. Jeśli obiekt nie zostanie tam znaleziony, SQL Server będzie wyglądał dalej w `dbo` schemacie. Jeśli obiekt nie znajduje się w `dbo` schemacie, zwracany jest błąd.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji o własności i schematach obiektów, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Oddzielanie schematu użytkownika](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|Opisuje zmiany wprowadzone przez separację w schemacie użytkownika. Obejmuje nowe zachowanie, jego wpływ na własność, widoki katalogów i uprawnienia.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
