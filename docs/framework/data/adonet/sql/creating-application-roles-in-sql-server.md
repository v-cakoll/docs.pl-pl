---
title: "Tworzenie ról aplikacji w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7808f2e60902eeb2fce0ac53010e329e4252a24e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-application-roles-in-sql-server"></a>Tworzenie ról aplikacji w programie SQL Server
Role aplikacji umożliwiają przypisywanie uprawnień do aplikacji zamiast roli bazy danych lub użytkownika. Użytkownicy mogą połączenia z bazą danych, aktywować rolę aplikacji i założono uprawnienia do aplikacji. Uprawnienia przyznane roli aplikacji pozostają w mocy przez czas trwania połączenia.  
  
> [!IMPORTANT]
>  Role aplikacji jest aktywowany, gdy aplikacja kliencka dostarcza nazwę roli aplikacji i hasła w parametrach połączenia. Luki w zabezpieczeniach one obecne w dwuwarstwowej aplikacji, ponieważ hasło muszą być przechowywane na komputerze klienckim. W aplikacji trójwarstwowej mogą przechowywać hasło, dzięki czemu są niedostępne przez użytkowników aplikacji.  
  
## <a name="application-role-features"></a>Funkcje roli aplikacji  
 Role aplikacji mają następujące funkcje:  
  
-   W przeciwieństwie do ról bazy danych Role aplikacji zawierać żadnych członków.  
  
-   Role aplikacji jest aktywowany, gdy aplikacja zawiera nazwę roli aplikacji i hasła w celu `sp_setapprole` procedury składowanej systemu.  
  
-   Hasła muszą być przechowywane na komputerze klienckim i dostarczony w czasie wykonywania. roli aplikacji nie można aktywować z wewnątrz programu SQL Server.  
  
-   Hasło nie jest zaszyfrowany. Parametr hasła jest przechowywana jako jednokierunkowego skrótu.  
  
-   Po uaktywnieniu uprawnienia zakupione w ramach roli aplikacji będą obowiązywać przez czas trwania połączenia.  
  
-   Rola aplikacji dziedziczy uprawnienia przyznane `public` roli.  
  
-   Jeśli element członkowski z `sysadmin` stałej roli serwera aktywuje roli aplikacji, kontekst zabezpieczeń zmienia się do tej roli aplikacji w czasie trwania połączenia.  
  
-   W przypadku utworzenia `guest` konta w bazie danych, w których ma rolę aplikacji, nie trzeba utworzyć konto użytkownika bazy danych dla roli aplikacji ani nazwy logowania, które wywołują go. Role aplikacji można uzyskać dostęp do innej bazy danych tylko wtedy, gdy `guest` konto istnieje w drugiej bazy danych  
  
-   Wbudowane funkcje, które zwracają nazwy logowania, takie jak SYSTEM_USER, zwraca nazwę logowania, która wywołała roli aplikacji. Wbudowane funkcje, które zwracają nazwy użytkownika bazy danych zwraca nazwę roli aplikacji.  
  
### <a name="the-principle-of-least-privilege"></a>Zasadą najniższych uprawnień  
 Role aplikacji może być przyznany tylko wymagane uprawnienia, w przypadku złamania hasła. Uprawnienia do `public` roli powinny zostać odwołane w dowolnej bazy danych przy użyciu roli aplikacji. Wyłącz `guest` konta w dowolnej bazy danych nie ma obiektów wywołujących roli aplikacji ma mieć dostęp.  
  
### <a name="application-role-enhancements"></a>Ulepszenia roli aplikacji  
 Kontekst wykonywania można przełączyć do oryginalnego obiektu wywołującego po uaktywnieniu roli aplikacji, aby wyłączyć buforowanie połączeń jest potrzebna. `sp_setapprole` Procedura ma nową opcję, która tworzy plik cookie, który zawiera informacje o kontekście o elemencie wywołującym. Możesz przywrócić sesji przez wywołanie metody `sp_unsetapprole` procedury przekazanie jej przez plik cookie.  
  
## <a name="application-role-alternatives"></a>Alternatywy roli aplikacji  
 Role aplikacji są zależne od bezpieczeństwa hasła, który przedstawia potencjalnej luki w zabezpieczeniach. Hasła może być udostępniany przez osadzona w kodzie aplikacji lub zapisywane na dysku.  
  
 Warto wziąć pod uwagę następujące alternatyw.  
  
-   Przełączenie EXECUTE AS kontekstu użyj instrukcji z jego klauzule nie PRZYWRÓCIĆ i z plików COOKIE. Można utworzyć konto użytkownika w bazie danych, który nie jest zamapowany na nazwę logowania. Następnie można przypisać uprawnienia do tego konta. Przy użyciu wykonania zgodnie z użytkownikiem bez nazwy logowania jest bezpieczniejsza, ponieważ jest na podstawie uprawnień, nie opartego na hasłach. Aby uzyskać więcej informacji, zobacz [Dostosowywanie uprawnieniami personifikacja w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Utwórz procedury składowane za pomocą certyfikatów, udzielanie tylko uprawnienia do wykonania procedury. Aby uzyskać więcej informacji, zobacz [podpisywania procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Role aplikacji](http://msdn.microsoft.com/library/ms190998.aspx) w dokumentacji SQL Server Books Online|Opisuje sposób tworzenia i używania ról aplikacji w programie SQL Server 2008.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
