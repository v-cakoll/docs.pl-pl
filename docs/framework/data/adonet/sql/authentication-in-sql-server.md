---
title: Uwierzytelnianie programu SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c462b7c2e888ed0f6394435e0de2131e26dbef08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="authentication-in-sql-server"></a>Uwierzytelnianie programu SQL Server
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]obsługuje dwa tryby uwierzytelniania, tryb uwierzytelniania systemu Windows i w trybie mieszanym.  
  
-   Uwierzytelnianie systemu Windows jest ustawieniem domyślnym i jest często określany jako zintegrowane zabezpieczenia ponieważ to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] model zabezpieczeń jest ściśle zintegrowany z systemem Windows. Określonych kont użytkowników i grup systemu Windows są zaufane logować się do programu SQL Server. Nie masz użytkowników systemu Windows, którzy już zostali uwierzytelnieni do prezentowania dodatkowych poświadczeń.  
  
-   Tryb mieszany obsługuje uwierzytelniania zarówno przez system Windows i przez [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Pary nazwy i hasła użytkowników są obsługiwane w ramach [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Firma Microsoft zaleca używanie uwierzytelniania systemu Windows, gdy jest to możliwe. Uwierzytelnianie systemu Windows używa szereg zaszyfrowane wiadomości do uwierzytelniania użytkowników w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Gdy [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logowania są używane, [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nazwy logowania i hasła są przekazywane w sieci, dzięki czemu ich mniej bezpieczne.  
  
 Z uwierzytelnianiem systemu Windows użytkownicy są już zalogowany do systemu Windows i nie trzeba zalogować się oddzielnie do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Następujące `SqlConnection.ConnectionString` Określa uwierzytelnianie systemu Windows bez konieczności wprowadzania nazwy użytkownika ani hasła.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Logowania różnią się od użytkowników baz danych. Nazwy logowania lub grupy systemu Windows musi być zamapowany do bazy danych użytkowników lub ról w oddzielnych operacji. Następnie przydziel uprawnienia dla użytkowników lub ról, dostęp do obiektów bazy danych.  
  
## <a name="authentication-scenarios"></a>Scenariusze uwierzytelniania  
 Uwierzytelnianie systemu Windows jest zwykle najlepszym rozwiązaniem w następujących sytuacjach:  
  
-   Jest kontrolerem domeny.  
  
-   Aplikacji i bazy danych znajdują się na tym samym komputerze.  
  
-   W przypadku korzystania z wystąpienia [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express lub LocalDB.  
  
 Logowania do programu SQL Server są często używane w następujących sytuacjach:  
  
-   Jeśli masz grupy roboczej.  
  
-   Łączenie użytkowników z innej, niezaufanej domeny.  
  
-   Aplikacje internetowe, takich jak [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Określanie uwierzytelniania systemu Windows nie wyłączać [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logowania. Użyj polecenia ALTER LOGIN Wyłącz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, aby wyłączyć uprawnieniach [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logowania.  
  
## <a name="login-types"></a>Typy logowania  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]obsługuje trzy typy logowania:  
  
-   Lokalne konto użytkownika systemu Windows lub konto domeny zaufanej. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]zależy od systemu Windows do uwierzytelniania kont użytkowników systemu Windows.  
  
-   Grupy systemu Windows. Udzielanie dostępu do grupy systemu Windows daje dostęp do wszystkich logowania użytkownika do systemu Windows, które są elementami członkowskimi grupy.  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]dane logowania. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]przechowuje nazwę użytkownika i wyznaczania wartości skrótu hasła w bazie danych master, przy użyciu metody uwierzytelniania wewnętrznego, aby sprawdzić prób logowania.  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]udostępnia logowania utworzone na podstawie certyfikaty lub klucze asymetryczne, które są używane tylko w przypadku podpisywania kodu. Nie można nawiązać połączenia [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="mixed-mode-authentication"></a>Uwierzytelnianie w trybie mieszanym  
 Jeśli należy użyć uwierzytelniania w trybie mieszanym, należy utworzyć [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logowania, które są przechowywane w programie SQL Server. Następnie trzeba podawać [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nazwę użytkownika i hasło w czasie wykonywania.  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Instaluje z [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logowania o nazwie `sa` (skrót od "administrator systemu"). Przypisz silne hasło, aby `sa` logowania i nie używaj `sa` logowania w aplikacji. `sa` Logowania mapowany na `sysadmin` stałej roli serwera, mającej nieodwołalną poświadczeń administracyjnych na całego serwera. Nie ma żadnych limitów w celu potencjalne szkody, jeśli osoba atakująca uzyska dostęp administrator systemu. Wszystkie elementy członkowskie systemu Windows `BUILTIN\Administrators` grupy (grupy administratorów lokalnych) są elementami członkowskimi `sysadmin` roli domyślnie, ale można ją usunąć z tej roli.  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]zawiera mechanizmy zasad haseł systemu Windows [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logowania, gdy jest uruchomiony na [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] lub nowszy. Zasady złożoności haseł są przeznaczone do ograniczanie ataków siłowych przez odpowiednie zwiększenie liczby możliwych haseł. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]można stosować te same zasady złożoności i wygaśnięcia używane w [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] do hasła używane wewnątrz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Łączenie ciągów połączenia z danych wejściowych użytkownika może sprawić, że użytkownik narażony na atak iniekcji ciągu połączenia. Użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podmioty zabezpieczeń](http://msdn.microsoft.com/library/bb543165.aspx) w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online|W tym artykule opisano logowania i innych podmiotów zabezpieczeń w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Nawiązywanie połączenia ze źródłem danych](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Parametry połączeń](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
