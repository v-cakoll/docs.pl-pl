---
title: Uwierzytelnianie programu SQL Server
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: f2d290d22d27c43cf7fb3250bf7898e8260dce2b
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472390"
---
# <a name="authentication-in-sql-server"></a>Uwierzytelnianie programu SQL Server
SQL Server obsługuje dwa tryby uwierzytelniania, tryb uwierzytelniania systemu Windows i w trybie mieszanym.  
  
-   Uwierzytelnianie systemu Windows jest ustawieniem domyślnym i jest często określany jako zintegrowanych zabezpieczeń, ponieważ ten model zabezpieczeń programu SQL Server jest ściśle zintegrowany z systemem Windows. Określonych kont użytkowników i grup systemu Windows są zaufane logować się do programu SQL Server. Nie masz użytkowników systemu Windows, którzy już zostali uwierzytelnieni do prezentowania dodatkowych poświadczeń.  
  
-   Tryb mieszany obsługuje uwierzytelnianie zarówno przez system Windows i program SQL Server. Pary nazwy i hasła użytkowników są obsługiwane w programie SQL Server.  
  
> [!IMPORTANT]
>  Firma Microsoft zaleca używanie uwierzytelniania systemu Windows, gdy jest to możliwe. Uwierzytelnianie systemu Windows używa szereg zaszyfrowane wiadomości do uwierzytelniania użytkowników w programie SQL Server. Podczas logowania do programu SQL Server są używane, nazwy logowania programu SQL Server i hasła szyfrowane są przekazywane w sieci, dzięki czemu ich mniej bezpieczne.  
  
 Z uwierzytelnianiem systemu Windows użytkownicy są już zalogowany do systemu Windows i nie trzeba oddzielnie logowania do programu SQL Server. Następujące `SqlConnection.ConnectionString` Określa uwierzytelnianie systemu Windows bez konieczności wprowadzania nazwy użytkownika ani hasła.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Logowania różnią się od użytkowników baz danych. Nazwy logowania lub grupy systemu Windows musi być zamapowany do bazy danych użytkowników lub ról w oddzielnych operacji. Następnie przydziel uprawnienia dla użytkowników lub ról, dostęp do obiektów bazy danych.  
  
## <a name="authentication-scenarios"></a>Scenariusze uwierzytelniania  
 Uwierzytelnianie systemu Windows jest zwykle najlepszym rozwiązaniem w następujących sytuacjach:  
  
-   Jest kontrolerem domeny.  
  
-   Aplikacji i bazy danych znajdują się na tym samym komputerze.  
  
-   Używasz wystąpienia programu SQL Server Express lub LocalDB.  
  
 Logowania do programu SQL Server są często używane w następujących sytuacjach:  
  
-   Jeśli masz grupy roboczej.  
  
-   Łączenie użytkowników z innej, niezaufanej domeny.  
  
-   Aplikacje internetowe, takich jak [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Określanie uwierzytelniania systemu Windows nie wyłączać logowania do programu SQL Server. Użyj polecenia ALTER LOGIN Wyłącz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, aby wyłączyć uprawnieniach logowania programu SQL Server.  
  
## <a name="login-types"></a>Typy logowania  
 SQL Server obsługuje trzy typy logowania:  
  
-   Lokalne konto użytkownika systemu Windows lub konto domeny zaufanej. Program SQL Server korzysta z systemu Windows do uwierzytelniania kont użytkowników systemu Windows.  
  
-   Grupy systemu Windows. Udzielanie dostępu do grupy systemu Windows daje dostęp do wszystkich logowania użytkownika do systemu Windows, które są elementami członkowskimi grupy.  
  
-   Logowanie do serwera SQL. Program SQL Server przechowuje zarówno nazwa użytkownika oraz skrót hasła w bazie danych master, przy użyciu metody uwierzytelniania wewnętrznego, aby sprawdzić prób logowania.  
  
> [!NOTE]
>  Program SQL Server stanowi logowania utworzone na podstawie certyfikaty lub klucze asymetryczne, które są używane tylko w przypadku podpisywania kodu. Ich nie można nawiązać połączenia z programem SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Uwierzytelnianie w trybie mieszanym  
 Jeśli należy użyć uwierzytelniania w trybie mieszanym, należy utworzyć logowania do programu SQL Server, które są przechowywane w programie SQL Server. Następnie należy podać nazwę użytkownika serwera SQL i hasło w czasie wykonywania.  
  
> [!IMPORTANT]
>  Instaluje program SQL Server z danych logowania SQL Server o nazwie `sa` (skrót od "administrator systemu"). Przypisz silne hasło, aby `sa` logowania i nie używaj `sa` logowania w aplikacji. `sa` Logowania mapowany na `sysadmin` stałej roli serwera, mającej nieodwołalną poświadczeń administracyjnych na całego serwera. Nie ma żadnych limitów w celu potencjalne szkody, jeśli osoba atakująca uzyska dostęp administrator systemu. Wszystkie elementy członkowskie systemu Windows `BUILTIN\Administrators` grupy (grupy administratorów lokalnych) są elementami członkowskimi `sysadmin` roli domyślnie, ale można ją usunąć z tej roli.  
  
 Program SQL Server stanowi mechanizmów zasad haseł systemu Windows dla logowania do programu SQL Server uruchomionej [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] lub nowszy. Zasady złożoności haseł są przeznaczone do ograniczanie ataków siłowych przez odpowiednie zwiększenie liczby możliwych haseł. SQL Server można zastosować te same zasady złożoności i wygaśnięcia używane w [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] do hasła używane w programie SQL Server.  
  
> [!IMPORTANT]
>  Łączenie ciągów połączenia z danych wejściowych użytkownika może sprawić, że użytkownik narażony na atak iniekcji ciągu połączenia. Użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podmioty zabezpieczeń](http://msdn.microsoft.com/library/bb543165.aspx) w dokumentacji SQL Server Books Online|Opisuje logowania i innych podmiotów zabezpieczeń w programie SQL Server.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Nawiązywanie połączenia ze źródłem danych](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
