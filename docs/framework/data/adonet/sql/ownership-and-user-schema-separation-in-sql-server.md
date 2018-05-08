---
title: Własność i oddzielenie użytkowników schematu w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 69d0c0dee6141b80908c8cdc36dfe21ff318f423
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Własność i oddzielenie użytkowników schematu w programie SQL Server
Kluczową ideą zabezpieczeń programu SQL Server jest właściciele obiektów uprawnień do administrowania nimi. Nie można usunąć uprawnień od właściciela obiektu i nie można usunąć użytkowników z bazy danych, jeśli są właścicielami obiektów w nim.  
  
## <a name="user-schema-separation"></a>Oddzielanie schematów użytkownika  
 Oddzielanie schematów użytkownika pozwala na większą elastyczność w zarządzaniu uprawnienia obiektu bazy danych. A *schematu* jest nazwane kontener dla obiektów bazy danych, dzięki czemu można do obiektów grup w oddzielnych przestrzeni nazw. Na przykład przykładową bazę danych AdventureWorks zawiera schematów produkcji, sprzedaży i brzmi HumanResources.  
  
 Czteroczęściową nazewnictwa składnia odwoływania się do obiektów Określa nazwę schematu.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Właściciele schematu i uprawnień  
 Schematy może należeć do dowolnej podmiotem zabezpieczeń bazy danych, a jeden podmiot zabezpieczeń może mieć wiele schematów. Reguły zabezpieczeń można stosować do schematu, które są dziedziczone przez wszystkie obiekty w schemacie. Po skonfigurowaniu uprawnień dostępu do schematu te uprawnienia są automatycznie stosowane jako nowe obiekty zostaną dodane do schematu. Użytkownicy mogą być przypisani schemat domyślny i wielu użytkowników bazy danych może współużytkować ten sam schemat.  
  
 Domyślnie gdy deweloperom tworzenie obiektów w schemacie, obiekty są własnością podmiotu zabezpieczeń, który jest właścicielem schematu nie dewelopera. Można przenieść własności obiektu z autoryzacji języka Transact-SQL ALTER. Schemat może również zawierać obiekty, które należą do różnych użytkowników i bardziej szczegółowego uprawnień niż te, które są przypisane do schematu, chociaż nie jest to zalecane, ponieważ do zarządzania uprawnieniami jest dodawany złożoności. Obiekty można przenosić między schematów i własność schematu mogą być przekazywane między podmiotów zabezpieczeń. Bazy danych użytkowników można było porzucić bez wpływu na schematów.  
  
### <a name="built-in-schemas"></a>Schematy wbudowane  
 Program SQL Server jest dostarczany z dziesięć wstępnie zdefiniowanych schematów, takich samych nazwach wbudowaną bazą danych użytkowników i ról. Istnieją one głównie dla zgodności z poprzednimi wersjami. Można usunąć schematów, które mają takie same nazwy co w przypadku ról stałej bazy danych, jeśli nie ma potrzeby. Nie można usunąć następujących schematów:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Jeśli upuść je z modelu bazy danych zostanie nie pojawią się one w nowych baz danych.  
  
> [!NOTE]
>  `sys` i `INFORMATION_SCHEMA` schematy są zastrzeżone dla obiektów systemowych. Nie można utworzyć obiektów w tych schematów i nie można porzucić.  
  
#### <a name="the-dbo-schema"></a>Dbo schematu  
 `dbo` Schemat jest domyślny schemat dla nowo utworzonej bazy danych. `dbo` Schematu jest własnością `dbo` konta użytkownika. Domyślnie użytkownicy utworzone za pomocą polecenia Utwórz użytkownika języka Transact-SQL mają `dbo` jako ich schemat domyślny.  
  
 Użytkownicy, którzy mają przypisaną `dbo` schematu nie dziedziczy uprawnień z `dbo` konta użytkownika. Brak uprawnień są dziedziczone z schematu przez użytkowników. Schemat uprawnienia są dziedziczone przez obiekty bazy danych zawartych w schemacie.  
  
> [!NOTE]
>  Po obiektów bazy danych odwołuje się przy użyciu nazwy jednej części, domyślny schemat użytkownika najpierw sprawdza, programu SQL Server. Jeśli obiekt nie zostaną znalezione, SQL Server wygląda dalej w `dbo` schematu. Jeśli obiekt nie znajduje się w `dbo` schematu, zwracany jest błąd.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na własność obiektu i schematów zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Schemat użytkownika separacji](http://msdn.microsoft.com/library/ms190387.aspx) w dokumentacji SQL Server Books Online|Opisuje zmiany wprowadzone przez oddzielenie schemat użytkownika. Obejmuje nowe zachowanie, jego wpływ na własność, widoków wykazu i uprawnień.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
