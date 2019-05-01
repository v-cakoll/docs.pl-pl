---
title: Tworzenie ról aplikacji w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: f836fd239eca30d0a1f4a667cddc844446d1d951
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878023"
---
# <a name="creating-application-roles-in-sql-server"></a>Tworzenie ról aplikacji w programie SQL Server
Role aplikacji umożliwiają przypisywanie uprawnień do aplikacji zamiast roli bazy danych lub użytkownika. Użytkowników można połączenia z bazą danych, Aktywuj rolę aplikacji i przyjęto założenie, uprawnienia nadane aplikacji. Uprawnienia przyznane roli aplikacji pozostają w mocy przez czas trwania połączenia.  
  
> [!IMPORTANT]
>  Role aplikacji zostaną aktywowane, gdy aplikacja kliencka dostarcza nazwę roli aplikacji i hasło w parametrach połączenia. Stanowią one luki w zabezpieczeniach w aplikacji dwuwarstwowej ponieważ hasła muszą być przechowywane na komputerze klienckim. W trójwarstwowej aplikacji można przechowywać hasło, tak aby nie są dostępne przez użytkowników aplikacji.  
  
## <a name="application-role-features"></a>Funkcje roli aplikacji  
 Role aplikacji mają następujące funkcje:  
  
- W przeciwieństwie do ról bazy danych z ról aplikacji zawiera żadnych elementów członkowskich.  
  
- Role aplikacji są aktywowane, jeśli aplikacja dostarcza nazwę roli aplikacji i hasło, aby `sp_setapprole` systemowej procedury składowanej.  
  
- Hasło musi być przechowywane na komputerze klienckim i dostarczane w czasie wykonywania. do roli aplikacji nie można aktywować z wewnątrz programu SQL Server.  
  
- Hasło nie jest zaszyfrowany. Hasło parametr jest przechowywany jako jednokierunkowego skrótu.  
  
- Po uaktywnieniu uprawnienia, które zakupione w ramach roli aplikacji obowiązywać przez czas trwania połączenia.  
  
- Rola aplikacji dziedziczy uprawnienia przyznawane rolom `public` roli.  
  
- Jeśli członek `sysadmin` stałej roli serwera aktywuje roli aplikacji, kontekst zabezpieczeń przełącza się do tej roli aplikacji na czas trwania połączenia.  
  
- Jeśli tworzysz `guest` konta w bazie danych, która ma rolę aplikacji, nie musisz utworzyć konto użytkownika bazy danych dla ról aplikacji ani danych logowania, które ją wywołują. Role aplikacji można uzyskać dostęp do innej bazy danych tylko wtedy, gdy `guest` konto istnieje w drugiej bazy danych  
  
- Wbudowane funkcje, które zwracają nazwy logowania, takie jak SYSTEM_USER, zwraca nazwę logowania, która wywołała roli aplikacji. Wbudowane funkcje, które zwracają nazwy użytkownika bazy danych zwraca nazwę roli aplikacji.  
  
### <a name="the-principle-of-least-privilege"></a>Zasadę najmniejszych uprawnień  
 Role aplikacji może być przyznany tylko wymagane uprawnienia, w przypadku, gdy hasło zostanie naruszone. Uprawnienia do `public` roli powinny zostać odwołane w dowolnej bazie danych przy użyciu roli aplikacji. Wyłącz `guest` konto w dowolnej bazie danych nie ma obiektów wywołujących, roli aplikacji z dostępem do.  
  
### <a name="application-role-enhancements"></a>Udoskonalenia ról aplikacji  
 Kontekst wykonywania można przełączyć oryginalnego obiektu wywołującego, po aktywowaniu roli aplikacji, usuwając konieczność, aby wyłączyć buforowanie połączeń. `sp_setapprole` Procedura ma nową opcję, która tworzy plik cookie, który zawiera informacje o kontekście o obiekcie wywołującym. Możesz przywrócić sesję przez wywołanie metody `sp_unsetapprole` procedury, podając mu pliku cookie.  
  
## <a name="application-role-alternatives"></a>Alternatywy ról aplikacji  
 Role aplikacji są zależne od bezpieczeństwa hasła, który przedstawia potencjalne luki w zabezpieczeniach. Hasła mogą być udostępniane przez osadzona w kodzie aplikacji lub zapisywane na dysku.  
  
 Warto wziąć pod uwagę następujących alternatyw.  
  
- Za pomocą EXECUTE AS do przełączania kontekstu użyj instrukcji z jej klauzul bez przywracania i za pomocą plików COOKIE. Można utworzyć konto użytkownika w bazie danych, która nie jest zamapowany na nazwę logowania. Następnie przypisz uprawnienia tego konta. Przy użyciu wykonania zgodnie z użytkownikiem bez nazwy logowania jest bezpieczniejsza, ponieważ jest on oparty na uprawnieniach, nie opartego na hasłach. Aby uzyskać więcej informacji, zobacz [dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Utwórz procedury przechowywane za pomocą certyfikatów, przyznać dostęp tylko do wykonywania procedur. Aby uzyskać więcej informacji, zobacz [podpisywania procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Role aplikacji](/sql/relational-databases/security/authentication-access/application-roles)|Opisuje sposób tworzenia i używania ról aplikacji w programie SQL Server 2008.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
