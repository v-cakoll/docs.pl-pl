---
title: Uwierzytelnianie w programie SQL Server
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 09f7825fd6b4f852b24142ea297c078bd8a1e221
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040268"
---
# <a name="authentication-in-sql-server"></a>Uwierzytelnianie w programie SQL Server
SQL Server obsługuje dwa tryby uwierzytelniania, tryb uwierzytelniania systemu Windows i tryb mieszany.  
  
- Uwierzytelnianie systemu Windows jest ustawieniem domyślnym i jest często określane jako zabezpieczenia zintegrowane, ponieważ ten SQL Server model zabezpieczeń jest ściśle zintegrowany z systemem Windows. Określone konta użytkowników i grup systemu Windows są zaufane, aby zalogować się do SQL Server. Użytkownicy systemu Windows, którzy zostali już uwierzytelnieni, nie muszą przedstawić dodatkowych poświadczeń.  
  
- Tryb mieszany obsługuje uwierzytelnianie zarówno w systemie Windows, jak i przez SQL Server. Pary nazwa użytkownika i hasło są utrzymywane w SQL Server.  
  
> [!IMPORTANT]
> Zalecamy używanie uwierzytelniania systemu Windows wszędzie tam, gdzie to możliwe. Uwierzytelnianie systemu Windows korzysta z serii zaszyfrowanych komunikatów do uwierzytelniania użytkowników w SQL Server. Gdy są używane SQL Server logowania, nazwy logowania SQL Server i szyfrowane hasła są przesyłane przez sieć, co sprawia, że są one mniej bezpieczne.  
  
 W przypadku uwierzytelniania systemu Windows użytkownicy są już zalogowani do systemu Windows i nie muszą logować się oddzielnie do SQL Server. Poniższe `SqlConnection.ConnectionString` określają uwierzytelnianie systemu Windows bez konieczności podawania nazwy użytkownika lub hasła.  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> Nazwy logowania różnią się od użytkowników bazy danych. Musisz zamapować nazwy logowania lub grupy systemu Windows na użytkowników lub role bazy danych w osobnej operacji. Następnie Udziel uprawnień użytkownikom lub rolom dostępu do obiektów bazy danych.  
  
## <a name="authentication-scenarios"></a>Scenariusze uwierzytelniania  
 Uwierzytelnianie systemu Windows jest zazwyczaj najlepszym wyborem w następujących sytuacjach:  
  
- Istnieje kontroler domeny.  
  
- Aplikacja i baza danych znajdują się na tym samym komputerze.  
  
- Używasz wystąpienia SQL Server Express lub LocalDB.  
  
 Identyfikatory logowania SQL Server często są używane w następujących sytuacjach:  
  
- Jeśli masz grupę roboczą.  
  
- Użytkownicy łączą się z różnych domen niezaufanych.  
  
- Aplikacje internetowe, takie jak ASP.NET.  
  
> [!NOTE]
> Określenie uwierzytelniania systemu Windows nie powoduje wyłączenia logowania SQL Server. Użyj instrukcji ALTER LOGIN DISABLE Transact-SQL, aby wyłączyć logowanie o wysokim poziomie uprawnień SQL Server.  
  
## <a name="login-types"></a>Typy logowania  
 SQL Server obsługuje trzy typy logowań:  
  
- Lokalne konto użytkownika systemu Windows lub zaufane konto domeny. SQL Server opiera się na systemie Windows do uwierzytelniania kont użytkowników systemu Windows.  
  
- Grupa systemu Windows. Przyznanie dostępu do grupy systemu Windows umożliwia dostęp do wszystkich logowań użytkowników systemu Windows, które są członkami tej grupy.  
  
- SQL Server logowania. SQL Server przechowuje zarówno nazwę użytkownika, jak i skrót hasła w bazie danych Master, przy użyciu wewnętrznych metod uwierzytelniania do weryfikowania prób logowania.  
  
> [!NOTE]
> SQL Server udostępnia nazwy logowania utworzone na podstawie certyfikatów lub kluczy asymetrycznych, które są używane tylko do podpisywania kodu. Nie można ich używać do nawiązywania połączenia z SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Uwierzytelnianie w trybie mieszanym  
 Jeśli konieczne jest użycie uwierzytelniania w trybie mieszanym, należy utworzyć SQL Server nazwy logowania, które są przechowywane w SQL Server. Następnie należy podać nazwę użytkownika SQL Server i hasło w czasie wykonywania.  
  
> [!IMPORTANT]
> SQL Server instalowany przy użyciu SQL Server logowania o nazwie `sa` (skrót "administrator systemu"). Przypisz silne hasło do `sa` logowania i nie używaj `sa` logowania w aplikacji. `sa` logowania są mapowane na stałą rolę serwera `sysadmin`, która ma nieodwołalne poświadczenia administracyjne na całym serwerze. Jeśli osoba atakująca uzyska dostęp jako administrator systemu, nie ma żadnych ograniczeń dotyczących potencjalnego uszkodzenia. Wszyscy członkowie grupy `BUILTIN\Administrators` systemu Windows (grupy administratorów lokalnych) są domyślnie członkami roli `sysadmin`, ale można ją usunąć z tej roli.  
  
 SQL Server zapewnia mechanizmy zasad haseł systemu Windows dla SQL Server logowania, gdy jest uruchomiona w [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] lub nowszych wersjach. Zasady złożoności haseł zaprojektowano w celu powstrzymania ataków na ataki przez zwiększenie liczby możliwych haseł. SQL Server mogą zastosować te same zasady złożoności i wygasania używane w [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] do haseł używanych wewnątrz SQL Server.  
  
> [!IMPORTANT]
> Łączenie parametrów połączenia z danymi wejściowymi użytkownika może spowodować zagrożenie dla ataku polegającego na iniekcji parametrów połączenia. Użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, aby utworzyć składniowo prawidłowe parametry połączenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [konstruktory parametrów połączenia](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podmiotów](/sql/relational-databases/security/authentication-access/principals-database-engine)|Opisuje nazwy logowania i inne podmioty zabezpieczeń w SQL Server.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Nawiązywanie połączenia ze źródłem danych](../connecting-to-a-data-source.md)
- [Parametry połączeń](../connection-strings.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
