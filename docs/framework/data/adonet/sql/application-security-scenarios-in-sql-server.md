---
title: "Scenariusze zabezpieczeń aplikacji w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6207bc570dd8182b351a945a36d5f80c14a8dd4c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="application-security-scenarios-in-sql-server"></a>Scenariusze zabezpieczeń aplikacji w programie SQL Server
Nie istnieje jeden sposób poprawne do tworzenia bezpiecznego aplikacji klienckiej programu SQL Server. Każda aplikacja jest unikatowa w jego wymagania, środowisko wdrażania i użytkowników. Aplikacja, która jest bezpieczny okres, po początkowym wdrożeniu może stać się mniej bezpieczne wraz z upływem czasu. Nie można przewidzieć z dowolnym dokładność, jakie zagrożenia mogą pojawić się w przyszłości.  
  
 SQL Server jako produkt, powstał przez wiele wersji w celu uwzględnienia najnowszych funkcji zabezpieczeń, które umożliwiają deweloperom tworzenie aplikacji w bezpiecznej bazie danych. Jednak zabezpieczeń nie są dostępne w polu; wymaga to ciągłe monitorowanie i aktualizowanie.  
  
## <a name="common-threats"></a>Typowe zagrożenia  
 Deweloperzy muszą zrozumieć zagrożenia bezpieczeństwa, narzędzi dostarczonych do licznika oraz jak uniknąć luk w zabezpieczeniach sam. Zabezpieczeń najlepiej można traktować jako łańcuch, gdzie przerwy w dowolnym łączu jeden obniża siły całości. Poniższa lista zawiera niektóre typowe zagrożenia bezpieczeństwa, które opisano szczegółowo w tematach w tej sekcji.  
  
### <a name="sql-injection"></a>Iniekcja kodu SQL  
 Iniekcja kodu SQL to proces, za pomocą którego złośliwy użytkownik wprowadza instrukcji języka Transact-SQL zamiast prawidłowe wartości wejściowe. Dane wejściowe jest przekazywany bezpośrednio do serwera bez sprawdzania poprawności i aplikacja wykonuje przypadkowo wprowadzony kod, ataku może potencjalnie uszkodzić lub spowodować utratę danych. Można zablokować programu SQL Server iniekcji atakom przy użyciu procedur składowanych i sparametryzowanych poleceń, unikając dynamiczne SQL i ograniczanie uprawnień do wszystkich użytkowników.  
  
### <a name="elevation-of-privilege"></a>Podniesienie uprawnień  
 Atakom powodującym podniesienie uprawnień wystąpić, gdy użytkownik jest w stanie założono konto zaufanych, takich jak właściciel lub administrator z uprawnieniami. Zawsze uruchamiane w ramach konta użytkownika uprzywilejowanego najmniej i przypisać tylko odpowiednie uprawnienia. Unikaj przy użyciu administracyjne lub właściciela konta do wykonywania kodu. Ogranicza to czas uszkodzeń, które mogą wystąpić, jeśli atak zakończy się pomyślnie. Podczas wykonywania zadań, które wymagają dodatkowych uprawnień, należy użyć procedury podpisywania lub personifikacji tylko na czas trwania zadania. Możesz zarejestrować procedur składowanych z certyfikatami lub należy używać personifikacji tymczasowo przypisać uprawnienia.  
  
### <a name="probing-and-intelligent-observation"></a>Sondowania i inteligentnych obserwacji  
 Atak sondowania można użyć komunikaty o błędach generowanych przez aplikację do wyszukiwania luk w zabezpieczeniach. Implementowanie obsługi błędów w wszystkich procedurach kod, aby zapobiec programu SQL Server informacje o błędach zwracanych do użytkownika końcowego.  
  
### <a name="authentication"></a>Uwierzytelnianie  
 Atak iniekcji ciągu połączenia może wystąpić, gdy przy użyciu logowania do programu SQL Server, jeśli parametry połączenia oparte na danych wejściowych użytkownika jest tworzony w czasie wykonywania. Jeśli parametry połączenia nie jest zaznaczone dla par prawidłową — słowo kluczowe, osoba atakująca wstawić dodatkowych znaków potencjalnie uzyskiwania dostępu do danych poufnych lub innych zasobów na serwerze. Gdy jest to możliwe, należy używać uwierzytelniania systemu Windows. Jeśli musisz użyć logowania do programu SQL Server, użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder> do tworzenia i sprawdzanie poprawności ciągów połączenia w czasie wykonywania.  
  
### <a name="passwords"></a>Hasła  
 Wiele ataków się powieść, ponieważ intruz mógł uzyskać lub odgadnąć hasło dla użytkownika uprzywilejowanego. Hasła są pierwszą linię obrony przed intruzami, więc ustawienie silnego hasła jest niezbędne do zabezpieczenia systemu. Utwórz i wymuszać zasady haseł dla uwierzytelniania w trybie mieszanym.  
  
 Zawsze należy przypisać silne hasło, aby `sa` konta, nawet w przypadku korzystania z uwierzytelniania systemu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Informacje dotyczące używania procedur składowanych do zarządzania uprawnieniami i kontroli dostępu do danych. Korzystanie z procedur składowanych jest efektywny sposób reagowania na zagrożenia bezpieczeństwa wiele.  
  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Opisuje metody zapisywania bezpiecznego dynamiczne SQL przy użyciu procedur składowanych.  
  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Opisuje sposób procedurę składowaną z certyfikatem, aby umożliwić użytkownikom pracę z danymi, które nie mają bezpośredniego dostępu do podpisania. Dzięki temu procedur składowanych do wykonywania operacji, które obiekt wywołujący nie ma uprawnień do wykonania bezpośrednio.  
  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Informacje dotyczące używania EXECUTE AS klauzuli personifikować innego użytkownika. Personifikacja przełącza kontekst wykonywania wywołujący dla określonego użytkownika.  
  
 [Udzielanie uprawnień na poziomie wiersza w programie SQL Server](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Opisuje sposób nadawania uprawnień na poziomie wiersza do ograniczenia dostępu do danych.  
  
 [Tworzenie ról aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Zawiera opis funkcji i funkcji ról aplikacji.  
  
 [Włączanie dostępu między bazami danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Opisuje sposób włączania dostępu do bazy danych między bez narażenia zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
