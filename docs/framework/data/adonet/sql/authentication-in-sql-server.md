---
title: Uwierzytelnianie w programie SQL Server
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 0172259446724e0be85bd7ca2d15cf299db04e27
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613105"
---
# <a name="authentication-in-sql-server"></a>Uwierzytelnianie w programie SQL Server
SQL Server obsługuje dwa tryby uwierzytelniania, tryb uwierzytelniania Windows i w trybie mieszanym.  
  
-   Uwierzytelnianie Windows jest ustawieniem domyślnym i jest często określane jako zabezpieczenia zintegrowane ponieważ ten model zabezpieczeń programu SQL Server jest ściśle zintegrowany z programem Windows. Określone konta użytkowników i grup Windows są zaufane do logowania do programu SQL Server. Windows użytkowników, którzy już zostali uwierzytelnieni jest konieczne przedstawić dodatkowych poświadczeń.  
  
-   Tryb mieszany obsługuje uwierzytelnianie za pomocą zarówno Windows, jak i przez program SQL Server. Pary nazwy i hasła użytkowników są przechowywane w programie SQL Server.  
  
> [!IMPORTANT]
>  Zaleca się korzystania z uwierzytelniania Windows wszędzie tam, gdzie to możliwe. Uwierzytelnianie Windows przy użyciu szeregu szyfrowanych komunikatów do uwierzytelniania użytkowników w programie SQL Server. Podczas logowania do programu SQL Server są używane, nazwy logowania programu SQL Server i zaszyfrowane hasła są przekazywane za pośrednictwem sieci, co sprawia, że są ich mniej bezpieczna opcja.  
  
 Przy użyciu uwierzytelniania Windows użytkowników jest już zalogowany na Windows i nie musisz oddzielnie Zaloguj się do programu SQL Server. Następujące `SqlConnection.ConnectionString` Określa uwierzytelnianie Windows bez konieczności użytkowników o podanie nazwy użytkownika ani hasła.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Identyfikatory logowania różnią się od użytkowników bazy danych. Nazwy logowania lub grup Windows musi być mapowane do bazy danych użytkowników lub ról w oddzielnych operacji. Następnie przydziel uprawnienia dla użytkowników lub ról, dostęp do obiektów bazy danych.  
  
## <a name="authentication-scenarios"></a>Scenariusze uwierzytelniania  
 Uwierzytelnianie Windows jest zwykle najlepszym wyborem w następujących sytuacjach:  
  
-   Jest kontrolerem domeny.  
  
-   Aplikacji i bazy danych znajdują się na tym samym komputerze.  
  
-   Używasz wystąpienia programu SQL Server Express lub LocalDB.  
  
 Logowania do programu SQL Server są często używane w następujących sytuacjach:  
  
-   Jeśli masz grupy roboczej.  
  
-   Łączenie użytkowników z innej, niezaufanej domeny.  
  
-   Aplikacje internetowe, takie jak [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Określanie uwierzytelniania Windows nie wyłączać logowania programu SQL Server. Użyj polecenia ALTER LOGIN Wyłącz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcję, aby wyłączyć logowania programu SQL Server w uprawnieniach.  
  
## <a name="login-types"></a>Typy logowania  
 Program SQL Server obsługuje trzy typy danych logowania:  
  
-   Lokalne konto użytkownika Windows lub konto domeny zaufanej. Program SQL Server opiera się na Windows do uwierzytelniania kont użytkowników Windows.  
  
-   Grupa Windows. Udzielanie dostępu do grupy Windows udziela dostępu do wszystkich logowań użytkowników Windows, które są członkami grupy.  
  
-   Dane logowania programu SQL Server. SQL Server przechowuje nazwy użytkownika i wartość skrótu hasła w bazie danych master przy użyciu metody uwierzytelniania wewnętrznego, aby sprawdzić prób logowania.  
  
> [!NOTE]
>  SQL Server udostępnia logowania utworzone na podstawie certyfikaty lub klucze asymetryczne, które są używane tylko w przypadku podpisywania kodu. One nie można nawiązać połączenia z programem SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Uwierzytelnianie w trybie mieszanym  
 Jeśli musisz użyć uwierzytelniania w trybie mieszanym, należy utworzyć nazwy logowania programu SQL Server, które są przechowywane w programie SQL Server. Następnie musisz podać nazwę użytkownika programu SQL Server i hasło w czasie wykonywania.  
  
> [!IMPORTANT]
>  Program SQL Server instaluje się za pomocą identyfikatora logowania programu SQL Server o nazwie `sa` (skrót od "administrator systemu"). Przypisz silne hasło, aby `sa` logowania i nie używaj `sa` logowania w aplikacji. `sa` Identyfikator logowania mapowany na `sysadmin` stałej roli serwera, mającej nieodwołalnej poświadczeń administracyjnych na całego serwera. Nie ma ograniczeń na potencjalne szkody jeśli atakujący uzyska dostęp jako administrator systemu. Wszyscy członkowie Windows `BUILTIN\Administrators` (grupy administratora lokalnego) są elementami członkowskimi `sysadmin` roli domyślnie, ale można je usunąć z tej roli.  
  
 Program SQL Server zapewnia Windows mechanizmy zasad haseł logowania do programu SQL Server, gdy jest uruchomiona na [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] lub nowszy. Zasady dotyczące złożoności haseł są przeznaczone do sądowym ataków siłowych, zwiększając liczbę możliwych haseł. Program SQL Server można zastosować te same zasady złożoności i wygaśnięcia używana w [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to haseł używanych w programie SQL Server.  
  
> [!IMPORTANT]
>  Łączenie ciągów połączenia z danych wejściowych użytkownika może sprawić, że użytkownik narażony na atak iniekcji ciąg połączenia. Użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder> do tworzenia parametrów połączenia nieprawidłową składnię w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Konstruktorzy parametrów połączeń](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podmiotów zabezpieczeń](/sql/relational-databases/security/authentication-access/principals-database-engine)|W tym artykule opisano identyfikatory logowania i inne podmioty zabezpieczeń w programie SQL Server.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Nawiązywanie połączenia ze źródłem danych](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
