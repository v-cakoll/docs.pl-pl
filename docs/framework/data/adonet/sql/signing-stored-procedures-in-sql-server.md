---
title: Rejestrowanie procedur składowanych w programie SQL Server
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: da7b21d725d301006288245c940e4367c3ce8568
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606825"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Rejestrowanie procedur składowanych w programie SQL Server
 Podpis cyfrowy jest szyfrowane przy użyciu klucza prywatnego osoby podpisującej podsumowanie danych. Klucza prywatnego gwarantuje, że podpis cyfrowy jest unikatowe dla jego elementów nośnych lub właściciela. Możesz zarejestrować procedury składowane, funkcje (z wyjątkiem funkcji z wartościami przechowywanymi w tabeli śródwierszowych), wyzwalacze i zestawów.  
  
 Możesz zarejestrować procedury składowanej za pomocą certyfikatu bądź klucza asymetrycznego. To jest przeznaczona dla scenariuszy, gdy uprawnienia nie może być dziedziczona przez tworzenie łańcucha własności lub łańcucha własności jest uszkodzony, takich jak dynamiczny język SQL. Następnie można utworzyć użytkownika mapowanego na certyfikat udzielanie uprawnień użytkownika do obiektów, które procedury składowanej musi uzyskać dostęp do certyfikatu.  

 Możesz można również utworzyć identyfikator logowania mapowany na ten sam certyfikat, a następnie przyznać wszelkich niezbędnych uprawnień na poziomie serwera do tej nazwy logowania lub Dodaj logowanie do co najmniej jednej z ról stałej. Służy to umożliwienie `TRUSTWORTHY` bazy danych ustawienie dla scenariuszy, w których są wymagane uprawnienia na wyższym poziomie.  
  
 Podczas wykonywania procedury składowanej uprawnienia użytkownika certyfikatu i/lub logowania programu SQL Server łączy się z udostępnianych przez obiekt wywołujący. W odróżnieniu od `EXECUTE AS` klauzuli nie zmienia kontekst wykonywania procedury. Wbudowane funkcje tej zwrotu nazwy logowania i nazwy użytkowników zwrócić nazwę obiektu wywołującego, a nie nazwa użytkownika certyfikatu.  
  
## <a name="creating-certificates"></a>Tworzenie certyfikatów  
 Podczas rejestrowania procedury składowanej przy użyciu certyfikatu lub klucza asymetrycznego, podsumowanie danych składające się z zaszyfrowanego skrótu kod procedury składowanej, wraz z execute-jako użytkownik, jest tworzony przy użyciu klucza prywatnego. W czasie wykonywania szyfrowanie danych jest odszyfrowywany przy użyciu klucza publicznego i porównywana z wartością skrótu procedury składowanej. Zmiana execute — jak użytkownik unieważnia wartość skrótu, tak aby nie jest już zgodny podpis cyfrowy. Modyfikacja procedury składowanej porzuca podpis całkowicie, co uniemożliwia osobą, która nie ma dostępu do klucza prywatnego z zmiany kodu procedury składowanej. W obu przypadkach musisz ponownie podpisać procedury po każdej zmianie kodu lub execute-jako użytkownik.  
  
 Istnieją dwie czynności związane z rejestracją modułu:  
  
1.  Utwórz certyfikat za pomocą instrukcji języka Transact-SQL `CREATE CERTIFICATE [certificateName]` instrukcji. Ta instrukcja oferuje kilka opcji do ustawiania datę początkową i końcową i hasła. Data wygaśnięcia domyślną jest jeden rok.  
  
1.  Utwórz procedurę za pomocą certyfikatu za pomocą języka Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` instrukcji.  

Gdy moduł został podpisany, jeden lub więcej podmiotów zabezpieczeń należy utworzyć w celu przechowywania dodatkowe uprawnienia, które powinny być skojarzone z certyfikatem.  

Jeśli moduł wymaga dodatkowych uprawnień na poziomie bazy danych:  
  
1.  Utwórz użytkownika bazy danych, skojarzone z tym certyfikatem, za pomocą instrukcji języka Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` instrukcji. Ten użytkownik istnieje tylko w bazie danych i nie jest skojarzony z logowaniem, chyba, że nazwa logowania została również utworzona na podstawie tego samego certyfikatu.  
  
1.  Przyznaj użytkownikowi certyfikatu wymagane uprawnienia na poziomie bazy danych.  
  
Jeśli moduł wymaga dodatkowych uprawnień na poziomie serwera:  
  
1.  Skopiuj certyfikat `master` bazy danych.  
 
1.  Utwórz dane logowania skojarzonego z tym certyfikatem, za pomocą instrukcji języka Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` instrukcji.  
  
1.  Przyznaj logowania certyfikatu wymagane uprawnienia na poziomie serwera.  
  
> [!NOTE]  
>  Certyfikat nie może udzielać uprawnień użytkownika, który miał odwołano przy użyciu instrukcji DENY uprawnienia. ODMÓW zawsze ma pierwszeństwo przed udzielanie, uniemożliwiając dziedziczy uprawnienia przyznane użytkownikowi certyfikatu przez obiekt wywołujący.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Moduł podpisywania](https://go.microsoft.com/fwlink/?LinkId=98590) w SQL Server — książki Online|W tym artykule opisano moduł podpisywania, zapewniając przykładowy scenariusz i linki do powiązanych tematów języka Transact-SQL.|  
|[Rejestrowanie procedur składowanych z certyfikatem](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) w SQL Server — książki Online|Zawiera samouczek dla procedury składowanej przy użyciu certyfikatu podpisywania.|  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
