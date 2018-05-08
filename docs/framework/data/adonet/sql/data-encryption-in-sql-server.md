---
title: Szyfrowanie danych w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 9e2924dc9f2f2954f6690ad5009c4143d1b9a44f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-encryption-in-sql-server"></a>Szyfrowanie danych w programie SQL Server
SQL Server udostępnia funkcje do szyfrowania i odszyfrowywania danych przy użyciu certyfikatu, klucza asymetrycznego lub klucza symetrycznego. Zarządza wszystkich tych w magazynie certyfikatu wewnętrznego. Magazyn używa szyfrowania hierarchii, która zabezpiecza certyfikatów i kluczy na jednym poziomie z warstwą wyżej w hierarchii. Ten obszar funkcji programu SQL Server jest nazywany magazynu klucz tajny.  
  
 Najszybszym tryb szyfrowania obsługiwane przez funkcje szyfrowania jest klucza szyfrowania symetrycznego. Ten tryb jest odpowiednia do obsługi dużych ilości danych. Klucze symetryczne mogą być szyfrowane przez certyfikaty, hasła lub innych kluczy symetrycznych.  
  
## <a name="keys-and-algorithms"></a>Kluczy i algorytmów  
 SQL Server obsługuje kilka algorytmy szyfrowania klucza symetrycznego, w tym DES, Triple DES, RC2, RC4, 128-bitowego szyfrowania RC4, DESX, AES 128-bitowego, 192-bitowego szyfrowania AES i AES 256 bitów. Algorytmy są implementowane za pomocą interfejsu API szyfrowania systemu Windows.  
  
 W zakresie połączenia z bazą danych programu SQL Server może przechowywać wiele kluczy symetrycznych Otwórz. Otworzyć klucza jest pobierana z magazynu i jest dostępny do odszyfrowania danych. Gdy element danych jest odszyfrowywany, jest niepotrzebna do określenia klucza symetrycznego do użycia. Każdy zaszyfrowaną wartość zawiera klucz identyfikator (klucz identyfikator GUID) używany do szyfrowania klucza. Aparat odpowiada strumień bajtów zaszyfrowanego można otworzyć klucza symetrycznego, jeśli klucz jest poprawny odszyfrowaniu i jest otwarty. Ten klucz jest następnie umożliwia wykonują odszyfrowywania i zwracają dane. Jeśli klucz jest poprawny, nie jest otwarty, zwracana jest wartość NULL.  
  
 Na przykład pokazujący sposób pracy z zaszyfrowanych danych w bazie danych, zobacz [porady: szyfrowanie kolumny danych](http://go.microsoft.com/fwlink/?LinkID=128559) w dokumentacji SQL Server — książki Online.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji dotyczących szyfrowania danych zobacz następujące zasoby.  
  
|||  
|-|-|  
|[SQL Server szyfrowania](http://msdn.microsoft.com/library/bb510663.aspx) w dokumentacji SQL Server Books Online|Zawiera omówienie szyfrowania w służyć SQL. Ten temat zawiera linki do dodatkowych tematów i w jaki sposób — do firmy.|  
|[Szyfrowanie hierarchii](http://msdn.microsoft.com/library/ms189586.aspx) i [— tematy porad szyfrowania](http://msdn.microsoft.com/library/aa337557.aspx) w dokumentacji SQL Server Books Online|Zawiera omówienie szyfrowania w programie SQL Server. Ten temat zawiera linki do dodatkowych tematów i w jaki sposób — do firmy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
