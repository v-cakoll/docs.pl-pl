---
title: Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 5357bb4ad82f5fe9a70f15a540aba355e847ad71
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857917"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server
Iniekcja SQL to proces, za pomocą której złośliwy użytkownik wprowadza instrukcje języka Transact-SQL zamiast prawidłowych danych wejściowych. Jeśli dane wejściowe jest przekazywana bezpośrednio do serwera bez sprawdzania poprawności i aplikacja wykonuje przypadkowo wprowadzonego kodu ataku ma możliwość uszkodzenia lub zniszczenia danych.  
  
 Każda procedura tworząca instrukcje SQL powinna zostać przejrzana pod dla iniekcją, ponieważ oprogramowanie SQL Server wykonuje wszystkie otrzymane nieprawidłową składnię zapytania, które. Nawet sparametryzowane danych może być manipulowane przez wykwalifikowanych i określone osoby atakującej. Jeśli używasz dynamiczny język SQL, pamiętaj zdefiniować parametry poleceń, a nigdy nie dołączaj parametru wartości bezpośrednio do ciągu zapytania.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomia ataku polegającego na iniekcji SQL  
 Proces iniekcji działa dzięki przedwcześnie ciąg tekstowy i dodanie nowego polecenia. Ponieważ polecenie wstawiono mogą mieć dodatkowe ciągi, dołączone do niego, zanim zostanie on wykonany, malefactor kończy wprowadzony ciąg przy użyciu znacznika komentarza "--". Kolejne tekst jest ignorowany w czasie wykonywania. Wiele poleceń można wstawiać przy użyciu średnika (;) ogranicznik.  
  
 Tak długo, jak wprowadzonego kodu SQL jest poprawny składniowo, modyfikowaniu nie można wykryć programowo. W związku z tym należy sprawdzić, wszystkie dane wejściowe użytkownika i dokładnie przeglądu kodu, który wykonuje polecenia SQL zbudowany na serwerze, którego używasz. Nigdy nie łączyć dane wejściowe użytkownika nie zostanie zweryfikowana. Łączenie ciągów jest podstawowym punktem wejścia dla uruchomienie skryptu.  
  
 Poniżej przedstawiono kilka przydatnych wskazówek:  
  
-   Nigdy nie twórz instrukcji języka Transact-SQL bezpośrednio w danych wejściowych użytkownika; Używanie procedur składowanych, aby sprawdzić poprawność danych wejściowych użytkownika.  
  
-   Weryfikowanie danych wejściowych użytkownika, testując typu, długość, formatu i zakresu. Funkcja języka Transact-SQL QUOTENAME() jako znak ucieczki dla nazwy systemu lub funkcja REPLACE() jako znak ucieczki dla dowolnego znaku w ciągu.  
  
-   W przypadku każdej warstwy aplikacji, należy zaimplementować wiele warstw sprawdzania poprawności.  
  
-   Przetestuj rozmiar i typ danych wejściowych i wymuszanie limitów odpowiednie. Może to pomóc uniknąć przepełnienia buforu zamierzone.  
  
-   Testowanie zawartości zmiennych ciągu i akceptuje tylko oczekiwanej wartości. Odrzuć wpisy, które zawierają dane binarne, sekwencje ucieczki i znaki komentarza.  
  
-   Podczas pracy z dokumentami XML Sprawdź poprawność wszystkich danych ze schematem, zgodnie z ich wprowadzenia.  
  
-   W środowiskach wielopoziomowe wszystkie dane powinny zostać uwierzytelnionym i móc dopuszczenie do zaufanej strefy.  
  
-   Nie akceptuje następujące ciągi z plik, który można skonstruować nazwy pól: AUX, CLOCK$, COM1 do COM8, CON, konfiguracji$, LPT1 do LPT8, NUL i PRN.  
  
-   Użyj <xref:System.Data.SqlClient.SqlParameter> obiektów za pomocą procedur składowanych i polecenia w celu udostępnienia weryfikacji typ sprawdzania i długości.  
  
-   Użyj <xref:System.Text.RegularExpressions.Regex> wyrażeń w kodzie klienta, aby filtrować nieprawidłowe znaki.  
  
## <a name="dynamic-sql-strategies"></a>Strategie dynamiczny język SQL  
 Wykonywanie dynamicznie utworzony instrukcji języka SQL w swojej podziały kod proceduralny łańcucha własności, powodując programu SQL Server w celu sprawdzenia uprawnień obiektu wywołującego względem obiektów, w której uzyskuje dostęp przez dynamiczny język SQL.  
  
 Program SQL Server ma metody do udzielania użytkownikom dostępu do danych przy użyciu procedury składowane i funkcje zdefiniowane przez użytkownika, które są wykonywane dynamiczny język SQL.  
  
-   Korzystanie z personifikacji z języka Transact-SQL AS wykonywanie klauzuli, zgodnie z opisem w [dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Podpisywanie za pomocą certyfikatów, procedury składowane, zgodnie z opisem w [podpisywania procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>WYKONAJ AS  
 WYKONAJ jako zastępuje klauzuli uprawnień obiektu wywołującego za pomocą użytkownika określonego w EXECUTE AS klauzuli. Zagnieżdżone procedur składowanych i wyzwalaczy należy wykonać w kontekście zabezpieczeń użytkownika serwera proxy. Może to spowodować awarię aplikacji, które polegają na zabezpieczenia na poziomie wiersza lub wymagają przeprowadzania inspekcji. Niektóre funkcje, które zwracają tożsamości użytkownika zwracają użytkownika określonego w EXECUTE AS klauzuli, nie oryginalny obiekt wywołujący. Kontekst wykonywania zostanie przywrócona do oryginalnego obiektu wywołującego dopiero po wykonanie procedury lub po wygenerowaniu instrukcji REVERT.  
  
### <a name="certificate-signing"></a>Podpisywanie certyfikatu  
 Podczas wykonywania procedury składowanej, który został podpisany za pomocą certyfikatu, uprawnienia przyznane użytkownikowi certyfikatu są scalane z udostępnianych przez obiekt wywołujący. Kontekst wykonywania pozostają bez zmian; certyfikat użytkownika nie spersonifikować obiektu wywołującego. Rejestrowanie procedur składowanych wymaga podjęcia kilku czynności do wykonania. Każdorazowo, gdy procedura jest modyfikowany, musi być ponownie podpisany.  
  
### <a name="cross-database-access"></a>Krzyżowe dostępu do bazy danych  
 Tworzenie łańcucha własności między bazami danych nie działa w przypadkach, w których są wykonywane dynamicznie utworzoną instrukcji języka SQL. Można obejść to w programie SQL Server, tworząc procedury przechowywanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywania procedury przy użyciu certyfikatu, który znajduje się w obu bazach danych. To zapewnia użytkownikom dostęp do zasobów bazy danych używane przez tę procedurę, bez nadawania im dostępu do bazy danych lub uprawnienia.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Procedury składowane](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) i [wstrzyknięcie kodu SQL](/sql/relational-databases/security/sql-injection) w SQL Server — książki Online|Tematy opisują sposób tworzenia procedury składowane i jak działa wstrzyknięcie kodu SQL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
