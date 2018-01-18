---
title: "Rejestrowanie procedur składowanych w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3f1ed66ed7caf2272ca27097dc9a838bec7d0ae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a>Rejestrowanie procedur składowanych w programie SQL Server
Możesz zarejestrować procedury składowanej z certyfikatu lub klucza asymetrycznego. To jest przeznaczona dla scenariuszy, gdy uprawnienia nie może być dziedziczona za pośrednictwem łańcucha własność lub łańcuch własności został przerwany, takich jak SQL dynamicznych. Następnie można utworzyć użytkownika mapowanego na certyfikat, udzielanie uprawnień użytkownika na obiekty, które procedury składowanej musi mieć dostęp do certyfikatu.  
  
 Podczas wykonywania procedury składowanej SQL Server łączy z uprawnieniami użytkownika certyfikatu z właściwościami obiektu wywołującego. W przeciwieństwie do wykonania jako klauzuli nie zmienia kontekstu wykonywania procedury. Danych logowania tego zwracany funkcji wbudowanych i nazwy użytkownika zwrócił nazwę obiektu wywołującego, a nie nazwa użytkownika certyfikatu.  
  
 Podpis cyfrowy jest szyfrowane dane zaszyfrowane przy użyciu klucza prywatnego osoby podpisującej. Klucza prywatnego gwarantuje, że podpis cyfrowy jest unikatowa dla jego elementów nośnych lub właściciela. Możesz zarejestrować wyzwalaczy, funkcji lub procedury składowane.  
  
> [!NOTE]
>  W bazie danych master można udzielić uprawnienia na poziomie serwera, można utworzyć certyfikatu.  
  
## <a name="creating-certificates"></a>Tworzenie certyfikatów  
 Po zarejestrowaniu procedury składowanej przy użyciu certyfikatu szyfrowanie danych, składające się z zaszyfrowanego skrótu kodu procedury składowanej jest tworzony przy użyciu klucza prywatnego. W czasie wykonywania szyfrowanie danych jest odszyfrować za pomocą klucza publicznego i porównania z wartością skrótu procedury składowanej. Modyfikacja procedury składowanej unieważnia wartość skrótu, tak, aby podpisu cyfrowego nie jest już zgodne. Zapobiega to osobie, która nie ma dostępu do klucza prywatnego z zmiana kodu procedury składowanej. W związku z tym należy ponownie podpisać procedury go po każdej zmianie.  
  
 Istnieją cztery kroki związane z moduł podpisywania:  
  
1.  Utwórz certyfikat przy użyciu języka Transact-SQL `CREATE CERTIFICATE [certificateName]` instrukcji. Ta instrukcja ma kilka opcji do ustawiania datę początkową i końcową i hasła. Domyślne Data wygaśnięcia jest rok  
  
2.  Utwórz użytkownika bazy danych skojarzony z tym certyfikatem przy użyciu języka Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` instrukcji. Ten użytkownik istnieje w bazie danych tylko i nie są skojarzone z logowaniem.  
  
3.  Przyznaj użytkownikowi certyfikatów wymaganych uprawnień do obiektów bazy danych.  
  
> [!NOTE]
>  Certyfikat nie może przyznać uprawnienia użytkownika, który miał odwołany za pomocą instrukcji ODMÓW uprawnień. ODMÓW zawsze ma pierwszeństwo przed GRANT, uniemożliwia dziedziczy uprawnienia przyznane użytkownikowi certyfikatu przez obiekt wywołujący.  
  
1.  Procedury należy podpisać certyfikat przy użyciu języka Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` instrukcji.  
  
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
