---
title: Własność i oddzielenie schematu użytkownika w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: adeed5ff4961a33d8f7d330941a5680f11a88b96
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694805"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Własność i oddzielenie schematu użytkownika w programie SQL Server
Podstawowa koncepcja zabezpieczeń programu SQL Server jest właściciele obiektów uprawnień do administrowania nimi. Nie można usunąć uprawnień od właściciela obiektu, a nie można usunąć użytkowników z bazy danych, jeśli ich właścicielem obiektów w nim.  
  
## <a name="user-schema-separation"></a>Oddzielenie schematu użytkownika  
 Oddzielenie schematu użytkownika umożliwia większą elastyczność w zakresie zarządzania uprawnień obiektu bazy danych. A *schematu* to kontener o nazwie obiekty bazy danych, który umożliwia przeprowadzenie obiekty grupy do oddzielnych przestrzeni nazw. Na przykład przykładowej bazy danych AdventureWorks zawiera schematy dla produkcji, sprzedaży i kadry.  
  
 Czteroczęściową Składnia nazwy do odwoływania się do obiektów określa nazwy schematu.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Właściciele schematu i uprawnienia  
 Schematy może być własnością dowolnego podmiotu zabezpieczeń bazy danych i pojedynczej jednostki może mieć wiele schematów. Zasady zabezpieczeń można zastosować do schematu, które są dziedziczone przez wszystkie obiekty w schemacie. Po skonfigurowaniu uprawnień dostępu do schematu te uprawnienia są stosowane automatycznie, gdy nowe obiekty są dodawane do schematu. Użytkownikom można przypisać domyślny schemat i wielu użytkowników bazy danych może współużytkować ten sam schemat.  
  
 Domyślnie gdy deweloperom tworzenie obiektów w schemacie, obiekty są własnością podmiotu zabezpieczeń, który jest właścicielem schematu, a nie dla deweloperów. Za pomocą instrukcji ALTER autoryzacji Transact-SQL można przenieść własności obiektu. Schemat może również zawierać obiektów, które należą do różnych użytkowników i korzystają z bardziej szczegółowych uprawnień niż te, które są przypisane do schematu, chociaż nie jest to zalecane, ponieważ dodaje złożoności do zarządzania uprawnieniami. Obiekty można przenosić między schematów i własność schematu mogą być przekazywane między podmiotów zabezpieczeń. Użytkownicy bazy danych można porzucić bez wywierania wpływu na schematach.  
  
### <a name="built-in-schemas"></a>Wbudowane schematów  
 Program SQL Server jest dostarczany z dziesięciu wstępnie zdefiniowanych schematów, które mają takie same nazwy użytkowników wbudowaną bazą danych i ról. Istnieją one głównie dla zgodności z poprzednimi wersjami. Mogą porzucić schematów, które mają takie same nazwy ról stałej bazy danych, jeśli nie potrzebujesz. Nie można usunąć następujących schematów:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Jeśli usuniesz je z modelu bazy danych, nie pojawią się one w nowych baz danych.  
  
> [!NOTE]
>  `sys` i `INFORMATION_SCHEMA` schematy są zarezerwowane dla obiektów systemu. Nie można utworzyć obiektów te schematy i nie można porzucić.  
  
#### <a name="the-dbo-schema"></a>Dbo schematu  
 `dbo` Schemat jest domyślny schemat dla nowo utworzoną bazę danych. `dbo` Schematu jest własnością `dbo` konta użytkownika. Domyślnie użytkownicy utworzeni za pomocą polecenia Utwórz użytkownika języka Transact-SQL mają `dbo` jako jego domyślny schemat.  
  
 Użytkownicy, którzy mają przypisaną `dbo` schematu nie dziedziczą uprawnienia `dbo` konta użytkownika. Nie uprawnienia są dziedziczone w schemacie przez użytkowników. Schemat uprawnienia są dziedziczone przez obiekty bazy danych zawartych w schemacie.  
  
> [!NOTE]
>  Gdy przy użyciu nazwy jedną część odwołują się obiekty bazy danych, SQL Server najpierw przeszukuje domyślny schemat użytkownika. Jeśli obiekt nie zostaną znalezione, programu SQL Server wygląda przyszłość `dbo` schematu. Jeśli obiekt nie znajduje się w `dbo` schematu, zwracany jest błąd.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji o własności obiektu i schematów zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Oddzielenie schematu użytkownika](https://msdn.microsoft.com/library/ms190387.aspx) w SQL Server — książki Online|Opis zmian wprowadzonych przez oddzielenie schematu użytkownika. Obejmuje nowe zachowanie, ich wpływu na własność, widoków wykazu i uprawnienia.|  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
