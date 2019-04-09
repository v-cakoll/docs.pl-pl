---
title: Scenariusze zabezpieczeń aplikacji w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 96c9f48cbf2e2ade2ff1688573a83fd86d613f2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130165"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scenariusze zabezpieczeń aplikacji w programie SQL Server
Nie ma żadnych pojedynczy prawidłowy sposób do tworzenia bezpiecznych aplikacji klienckiej programu SQL Server. Każda aplikacja jest unikatowa w jej wymagań, wdrożenia środowiska i populacji użytkowników. Aplikacja, która jest względnie bezpieczne, po początkowym wdrożeniu mogą stać się mniej bezpieczna opcja wraz z upływem czasu. Nie jest możliwe do przewidzenia o dowolnym dokładności, jakie zagrożenia mogą pojawić się w przyszłości.  
  
 SQL Server jest produktem powstał przez wiele wersji w celu włączenia najnowszych funkcji zabezpieczeń, które umożliwiają deweloperom tworzenie aplikacji działających w bezpiecznej bazie danych. Jednak zabezpieczeń nie są dostępne w polu; wymaga to ciągłe monitorowanie i aktualizowanie.  
  
## <a name="common-threats"></a>Typowych zagrożeń  
 Deweloperzy muszą poznać zagrożenia bezpieczeństwa, narzędzi dostępnych do licznika i sposobu uniknięcia luk w zabezpieczeniach samodzielnie sprowokowane. Zabezpieczeń można najlepiej traktować jako łańcuch, gdzie podział w dowolnym jedno łącze obniża siłę całego. Poniższa lista zawiera niektóre typowe zagrożenia bezpieczeństwa, które zostały omówione bardziej szczegółowo w tematach w tej sekcji.  
  
### <a name="sql-injection"></a>Wstrzyknięcie kodu SQL  
 Iniekcja SQL to proces, za pomocą której złośliwy użytkownik wprowadza instrukcje języka Transact-SQL zamiast prawidłowych danych wejściowych. Jeśli dane wejściowe jest przekazywana bezpośrednio do serwera bez sprawdzania poprawności i aplikacja wykonuje przypadkowo wprowadzonego kodu ataku ma możliwość uszkodzenia lub zniszczenia danych. Można zablokować programu SQL Server iniekcji ataków przy użyciu procedur składowanych i sparametryzowanych poleceń, unikanie dynamiczny język SQL i ograniczanie uprawnień do wszystkich użytkowników.  
  
### <a name="elevation-of-privilege"></a>Podniesienie uprawnień  
 Atakom powodującym podniesienie uprawnień wystąpić, gdy użytkownik będzie mógł z nich przejmować uprawnienia konto zaufane, takich jak właściciel lub administrator. Zawsze działać w ramach kont użytkowników najmniej uprzywilejowane i przypisywać tylko wymagane uprawnienia. Należy unikać przy użyciu administracyjne lub właściciela konta umożliwiającego wykonywanie kodu. To ogranicza ryzyko uszkodzeń spowodowanych przez może wystąpić, jeśli atak zakończy się pomyślnie. Podczas wykonywania zadań, które wymagają dodatkowych uprawnień, należy użyć procedury podpisywania lub personifikacji tylko za czas trwania zadania. Można utworzyć procedury przechowywane za pomocą certyfikatów lub tymczasowo Przypisz uprawnienia za pomocą personifikacji.  
  
### <a name="probing-and-intelligent-observation"></a>Obserwowanie badania i inteligentnych  
 Badania ataków można użyć komunikaty o błędach generowane przez aplikację do wyszukania luk w zabezpieczeniach. Implementowanie obsługi błędów w kod proceduralny wszystkie, aby uniemożliwić programu SQL Server błąd informacji zwracanych dla użytkownika końcowego.  
  
### <a name="authentication"></a>Uwierzytelnianie  
 Ataku polegającego na iniekcji ciąg połączenia może wystąpić, gdy za pomocą logowania programu SQL Server, jeśli parametry połączenia oparte na danych wejściowych użytkownika jest tworzony w czasie wykonywania. Jeśli ciąg połączenia nie jest zaznaczone dla par prawidłowe — słowo kluczowe, osoba atakująca wstawić dodatkowe znaki potencjalnie uzyskiwania dostępu do danych poufnych lub innych zasobów na serwerze. Uwierzytelnianie Windows wszędzie tam, gdzie to możliwe. Jeśli musisz użyć identyfikatorów logowania programu SQL Server, należy użyć <xref:System.Data.SqlClient.SqlConnectionStringBuilder> do tworzenia i sprawdzanie poprawności ciągów połączeń w czasie wykonywania.  
  
### <a name="passwords"></a>Hasła  
 Wiele ataków się powieść, ponieważ intruz był w stanie uzyskać lub odgadnięcia hasła dla użytkownika uprzywilejowanego. Hasła są pierwszą linię obrony przed intruzami, dzięki czemu ustawienie silnego hasła jest niezbędne do zabezpieczenia systemu. Tworzenie i wymuszanie zasad haseł dla uwierzytelniania w trybie mieszanym.  
  
 Zawsze należy przypisać silne hasło, aby `sa` konta, nawet w przypadku korzystania z uwierzytelniania Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 W tym artykule opisano, jak zarządzać uprawnieniami i kontrolować dostęp do danych za pomocą procedur składowanych. Korzystanie z procedur składowanych jest efektywny sposób reagowania na zagrożenia bezpieczeństwa wiele.  
  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Opisano techniki pisanie bezpiecznego dynamicznego kodu SQL przy użyciu procedur składowanych.  
  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 W tym artykule opisano sposób rejestrowania procedury składowanej przy użyciu certyfikatu, aby umożliwić użytkownikom pracę z danymi, które nie mają bezpośredniego dostępu do. Dzięki temu procedur składowanych do wykonywania operacji, które obiekt wywołujący nie ma uprawnień do wykonania bezpośrednio.  
  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Opisuje sposób używania EXECUTE AS klauzuli personifikować innego użytkownika. Personifikacja przełącza kontekst wykonania od elementu wywołującego dla określonego użytkownika.  
  
 [Udzielanie uprawnień na poziomie wiersza w programie SQL Server](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Opisuje sposób implementacji uprawnienia na poziomie wiersza do ograniczania dostępu do danych.  
  
 [Tworzenie ról aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 W tym artykule opisano funkcje i możliwości ról aplikacji.  
  
 [Włączanie dostępu między bazami danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Opisuje sposób włączania dostępu między bazami danych bez narażenia zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
