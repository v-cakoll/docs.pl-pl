---
title: Tworzenie ról aplikacji w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: e7060e1b171ee1791b9986250fe6f2050ec77acd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961166"
---
# <a name="creating-application-roles-in-sql-server"></a>Tworzenie ról aplikacji w programie SQL Server
Role aplikacji umożliwiają przypisywanie uprawnień do aplikacji zamiast roli lub użytkownika bazy danych. Użytkownicy mogą łączyć się z bazą danych, aktywować rolę aplikacji i przypuszczać uprawnienia przyznane aplikacji. Uprawnienia przyznane roli aplikacji są obowiązujące na czas trwania połączenia.  
  
> [!IMPORTANT]
> Role aplikacji są aktywowane, gdy aplikacja kliencka poda nazwę roli aplikacji i hasło w parametrach połączenia. W aplikacji dwuwarstwowej występują luki w zabezpieczeniach, ponieważ hasło musi być przechowywane na komputerze klienckim. W aplikacji trójwarstwowej można przechowywać hasło, aby nie było dostępne dla użytkowników aplikacji.  
  
## <a name="application-role-features"></a>Funkcje roli aplikacji  
 Role aplikacji mają następujące funkcje:  
  
- W przeciwieństwie do ról bazy danych role aplikacji nie zawierają żadnych członków.  
  
- Role aplikacji są aktywowane, gdy aplikacja dostarcza nazwę roli aplikacji i hasło do `sp_setapprole` procedury składowanej system.  
  
- Hasło musi być przechowywane na komputerze klienckim i udostępniane w czasie wykonywania; nie można uaktywnić roli aplikacji z wnętrza SQL Server.  
  
- Hasło nie jest zaszyfrowane. Hasło parametru jest przechowywane jako skrót jednokierunkowy.  
  
- Po aktywowaniu uprawnienia pozyskane przez rolę aplikacji pozostają w mocy na czas trwania połączenia.  
  
- Rola aplikacji dziedziczy uprawnienia przyznane do `public` roli.  
  
- Jeśli członek `sysadmin` stałej roli serwera aktywuje rolę aplikacji, kontekst zabezpieczeń przełączy się do tej roli aplikacji na czas trwania połączenia.  
  
- Jeśli utworzysz `guest` konto w bazie danych, która ma rolę aplikacji, nie musisz tworzyć konta użytkownika bazy danych dla roli aplikacji lub dla żadnego z nich, które go wywołują. Role aplikacji mogą bezpośrednio uzyskiwać dostęp do innej bazy danych `guest` tylko wtedy, gdy konto istnieje w drugiej bazie danych  
  
- Wbudowane funkcje, które zwracają nazwy logowania, takie jak SYSTEM_USER, zwracają nazwę logowania, która wywołała rolę aplikacji. Wbudowane funkcje, które zwracają nazwy użytkowników bazy danych zwracają nazwę roli aplikacji.  
  
### <a name="the-principle-of-least-privilege"></a>Zasada najniższych uprawnień  
 Role aplikacji powinny mieć przyznane tylko wymagane uprawnienia w przypadku naruszenia zabezpieczeń hasła. Uprawnienia do `public` roli należy odwołać w dowolnej bazie danych przy użyciu roli aplikacji. `guest` Wyłącz konto w dowolnej bazie danych, której nie chcesz, aby wywołujący rolę aplikacji mieli dostęp do programu.  
  
### <a name="application-role-enhancements"></a>Udoskonalenia roli aplikacji  
 Kontekst wykonywania można przełączyć z powrotem do oryginalnego obiektu wywołującego po aktywowaniu roli aplikacji, usuwając konieczność wyłączenia puli połączeń. `sp_setapprole` Procedura zawiera nową opcję, która tworzy plik cookie, który zawiera informacje kontekstowe dotyczące obiektu wywołującego. Możesz przywrócić sesję, wywołując `sp_unsetapprole` procedurę, przekazując plik cookie.  
  
## <a name="application-role-alternatives"></a>Alternatywy ról aplikacji  
 Role aplikacji są zależne od zabezpieczeń hasła, co stanowi potencjalną lukę w zabezpieczeniach. Hasła mogą być uwidaczniane przez osadzanie w kodzie aplikacji lub zapisane na dysku.  
  
 Warto rozważyć następujące alternatywy.  
  
- Użyj przełączania kontekstu z instrukcją EXECUTE AS z klauzulami NO Revert i WITH COOKIE. Możesz utworzyć konto użytkownika w bazie danych, która nie jest zamapowana na nazwę logowania. Następnie można przypisać uprawnienia do tego konta. Używanie polecenia EXECUTE AS z użytkownikiem bez hasła jest bezpieczniejsze, ponieważ jest to oparte na uprawnieniach, a nie oparte na haśle. Aby uzyskać więcej informacji, zobacz [Dostosowywanie uprawnień przy użyciu personifikacji w SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Podpisz procedury składowane z certyfikatami, przyznając tylko uprawnienia do wykonywania procedur. Aby uzyskać więcej informacji, zobacz Podpisywanie [procedur składowanych w SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Role aplikacji](/sql/relational-databases/security/authentication-access/application-roles)|Opisuje sposób tworzenia i używania ról aplikacji w SQL Server 2008.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
