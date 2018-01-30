---
title: "Rejestrowanie procedur składowanych w programie SQL Server"
ms.custom: 
ms.date: 01/05/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 15771cc214ee17bc2c98bab2423013483d1355f1
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a>Rejestrowanie procedur składowanych w programie SQL Server
 Podpis cyfrowy jest szyfrowane dane zaszyfrowane przy użyciu klucza prywatnego osoby podpisującej. Klucza prywatnego gwarantuje, że podpis cyfrowy jest unikatowa dla jego elementów nośnych lub właściciela. Możesz utworzyć procedur składowanych, funkcje (z wyjątkiem funkcji śródwierszowych przechowywanymi w tabeli), wyzwalacze i zestawów.  
  
 Możesz zarejestrować procedury składowanej z certyfikatu lub klucza asymetrycznego. To jest przeznaczona dla scenariuszy, gdy uprawnienia nie może być dziedziczona za pośrednictwem łańcucha własność lub łańcuch własności został przerwany, takich jak SQL dynamicznych. Następnie można utworzyć użytkownika mapowanego na certyfikat, udzielanie uprawnień użytkownika na obiekty, które procedury składowanej musi mieć dostęp do certyfikatu.  

 Możesz również utworzyć identyfikator logowania mapowany na ten sam certyfikat i przypisz wszelkie niezbędne uprawnienia poziomu serwera do tego logowania lub Dodaj logowanie do co najmniej jednej z ról serwera. Służy to nie włączaj `TRUSTWORTHY` bazy danych ustawienie w scenariuszach, w których wymagane są uprawnienia na wyższym poziomie.  
  
 Podczas wykonywania procedury składowanej uprawnienia użytkownika certyfikatu i/lub logowania programu SQL Server łączy się z tymi obiektu wywołującego. W odróżnieniu od `EXECUTE AS` klauzuli nie zmienia kontekstu wykonywania procedury. Danych logowania tego zwracany funkcji wbudowanych i nazwy użytkownika zwrócił nazwę obiektu wywołującego, a nie nazwa użytkownika certyfikatu.  
  
## <a name="creating-certificates"></a>Tworzenie certyfikatów  
 Podczas rejestrowania certyfikatu lub klucza asymetrycznego, szyfrowanie danych, składające się z zaszyfrowanego skrótu kodu procedury składowanej, oraz wykonywanie procedury składowanej — jako użytkownik, jest tworzony przy użyciu klucza prywatnego. W czasie wykonywania szyfrowanie danych jest odszyfrować za pomocą klucza publicznego i porównania z wartością skrótu procedury składowanej. Zmiana execute-jako wartość skrótu unieważnienia użytkownika tak, aby podpisu cyfrowego nie jest już zgodny. Modyfikacja procedury składowanej porzuca podpis całkowicie, co uniemożliwia osobie, która nie ma dostępu do klucza prywatnego z zmiana kodu procedury składowanej. W obu przypadkach należy ponownie podpisać procedury każdej zmianie kodu lub wykonaj — jako użytkownik.  
  
 Istnieją dwie czynności związane z moduł podpisywania:  
  
1.  Utwórz certyfikat przy użyciu języka Transact-SQL `CREATE CERTIFICATE [certificateName]` instrukcji. Ta instrukcja ma kilka opcji do ustawiania datę początkową i końcową i hasła. Domyślne Data wygaśnięcia jest jeden rok.  
  
1.  Procedury należy podpisać certyfikat przy użyciu języka Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` instrukcji.  

Podpisany modułu podmiotów zabezpieczeń co najmniej jeden musi zostać utworzona w celu przechowywania dodatkowe uprawnienia, które powinny być skojarzone z certyfikatem.  

Jeśli moduł wymaga dodatkowych uprawnień na poziomie bazy danych:  
  
1.  Utwórz użytkownika bazy danych skojarzony z tym certyfikatem przy użyciu języka Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` instrukcji. Ten użytkownik istnieje w bazie danych tylko i nie jest skojarzony z logowaniem, chyba że identyfikator logowania została także utworzona na podstawie tego samego certyfikatu.  
  
1.  Przyznaj użytkownikowi certyfikatów wymaganych uprawnień poziom bazy danych.  
  
Jeśli moduł wymaga dodatkowych uprawnień na poziomie serwera:  
  
1.  Skopiuj certyfikat do `master` bazy danych.  
 
1.  Utwórz dane logowania skojarzonego z tym certyfikatem przy użyciu języka Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` instrukcji.  
  
1.  Przyznaj logowania certyfikatu wymagane uprawnienia na poziomie serwera.  
  
> [!NOTE]  
>  Certyfikat nie może przyznać uprawnienia użytkownika, który miał odwołany za pomocą instrukcji ODMÓW uprawnień. ODMÓW zawsze ma pierwszeństwo przed GRANT, uniemożliwia dziedziczy uprawnienia przyznane użytkownikowi certyfikatu przez obiekt wywołujący.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Moduł podpisywania](http://go.microsoft.com/fwlink/?LinkId=98590) w dokumentacji SQL Server Books Online|W tym artykule opisano moduł podpisywania, zapewniając przykładowy scenariusz i linki do powiązanych tematów języka Transact-SQL.|  
|[Procedury składowane za pomocą certyfikatu podpisywania](http://msdn.microsoft.com/library/bb283630.aspx) w dokumentacji SQL Server Books Online|Zawiera samouczek do procedury składowanej przy użyciu certyfikatu podpisywania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
