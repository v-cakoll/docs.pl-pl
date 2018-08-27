---
title: Szyfrowanie danych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: d662f04cb54e12abfc481487cb5172f63edf0316
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932747"
---
# <a name="data-encryption-in-sql-server"></a>Szyfrowanie danych w programie SQL Server
Program SQL Server udostępnia funkcje do szyfrowania i odszyfrowywania danych za pomocą certyfikatu, klucza asymetrycznego lub klucza symetrycznego. Zarządza wszystkie wymienione w magazynie certyfikatu wewnętrznego. Magazyn używa hierarchii szyfrowania, który zabezpiecza certyfikatów i kluczy na jednym poziomie z użyciem warstwy nad nim w hierarchii. Ten obszar funkcji programu SQL Server, nosi nazwę wpisu tajnego magazynu.  
  
 Najszybszy tryb szyfrowania obsługiwane przez funkcje szyfrowania jest szyfrowania klucza symetrycznego. Ten tryb jest odpowiednia do obsługi dużych ilości danych. Klucze symetryczne mogą być szyfrowane, certyfikaty, hasła lub inne klucze symetryczne.  
  
## <a name="keys-and-algorithms"></a>Kluczy i algorytmów  
 SQL Server obsługuje wielu algorytmów szyfrowania symetrycznego klucza, w tym DES, Triple DES, RC2, RC4, 128-bitowego szyfrowania RC4, DESX, 128-bitowego szyfrowania AES, 192-bitowego szyfrowania AES i szyfrowania AES 256-bitowego. Te algorytmy są implementowane przy użyciu interfejsu API szyfrowania Windows.  
  
 W zakresie połączenia z bazą danych programu SQL Server można obsługiwać wielu Otwórz klucze symetryczne. Otworzyć klucza są pobierane z magazynu i jest dostępny do odszyfrowania danych. Gdy element danych zostanie odszyfrowany, nie ma potrzeby określić klucz symetryczny do użycia. Każda wartość zaszyfrowanych zawiera klucz identyfikator (klucz identyfikator GUID) klucz używany do szyfrowania. Aparat dopasowuje strumień bajtów zaszyfrowane, można otworzyć klucza symetrycznego, jeśli poprawny klucz odszyfrowaniu i jest otwarty. Ten klucz jest następnie używany do wykonywania odszyfrowywania i zwrócić dane. Jeśli poprawny klucz nie jest otwarty, zwracana jest wartość NULL.  
  
 Na przykład, który pokazuje, jak pracować z zaszyfrowanych danych w bazie danych, zobacz [szyfrowanie kolumny danych](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na temat szyfrowania danych zobacz następujące zasoby.  
  
|Zasób|Opis|  
|-|-|  
|[Szyfrowanie serwera SQL](/sql/relational-databases/security/encryption/sql-server-encryption)|Omówienie szyfrowania w programie SQL Server. Ten temat zawiera łącza do dodatkowych artykułów.|  
|[Szyfrowanie hierarchii](/sql/relational-databases/security/encryption/encryption-hierarchy)|Omówienie szyfrowania w programie SQL Server. Ten temat zawiera łącza do dodatkowych artykułów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](http://go.microsoft.com/fwlink/?LinkId=217917)
