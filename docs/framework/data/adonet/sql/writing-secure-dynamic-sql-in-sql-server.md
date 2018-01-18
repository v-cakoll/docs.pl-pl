---
title: Zapisywanie Secure dynamiczne SQL w programie SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 41c396bf2101e54adb1608f938c702ff7663cb1d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Zapisywanie Secure dynamiczne SQL w programie SQL Server
Iniekcja kodu SQL to proces, za pomocą którego złośliwy użytkownik wprowadza instrukcji języka Transact-SQL zamiast prawidłowe wartości wejściowe. Dane wejściowe jest przekazywany bezpośrednio do serwera bez sprawdzania poprawności i aplikacja wykonuje przypadkowo wprowadzony kod, ataku może potencjalnie uszkodzić lub spowodować utratę danych.  
  
 Każda procedura tworzy instrukcji SQL powinny być weryfikowane luk iniekcji, ponieważ program SQL Server wykona wszystkie nieprawidłową składnię zapytania, które otrzymuje. Nawet sparametryzowane danych może manipulować wykwalifikowanych i określone osoby atakującej. Użycie dynamicznych SQL, należy koniecznie parametryzacja poleceń i nigdy nie dołączaj parametru wartości bezpośrednio do ciągu zapytania.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomia ataku polegającego na iniekcji SQL  
 Proces iniekcji odbywa się przez przedwczesne zakończenie ciągu tekstowego i dołączenie nowe polecenie. Ponieważ wstawionego polecenia może posiadać dodatkowe dołączone do niego przed jego wykonaniem, malefactor kończy wprowadzony ciąg z znacznika komentarza "--". Kolejne tekst jest ignorowany w czasie wykonywania. Wiele poleceń można wstawiać przy użyciu średnika (;) ogranicznika.  
  
 Wprowadzony kod SQL jest poprawna składniowo, manipulowanie nie można wykryć programowo. W związku z tym należy sprawdzić wszystkie dane wejściowe użytkownika i dokładnie przeglądu kodu, który wykonuje skonstruowane polecenia SQL na serwerze, którego używasz. Nigdy nie łączyć danych wejściowych użytkownika, który nie jest weryfikowany. Łączenie ciągów to podstawowy punkt wejścia dla uruchomienie skryptu.  
  
 Poniżej przedstawiono wskazówki pomocne:  
  
-   Nigdy nie kompilacji instrukcji języka Transact-SQL bezpośrednio z danych wejściowych użytkownika; Użyj procedur składowanych do sprawdzania poprawności danych wprowadzonych przez użytkownika.  
  
-   Sprawdzanie poprawności danych wejściowych użytkownika za testowanie typu, długość formatu i zakresu. Funkcja języka Transact-SQL QUOTENAME() ucieczki nazwy systemu lub funkcji REPLACE() ucieczki dowolny znak w ciągu.  
  
-   Wdrożenie wielu warstw weryfikacji w każdej warstwy aplikacji.  
  
-   Typ danych i rozmiar danych wejściowych testu i wymuszać odpowiednie limity. Może to zapobiec przekroczenia zamierzonego buforu.  
  
-   Testowanie zawartości zmiennych ciągu i akceptuje tylko oczekiwanych wartości. Odrzuć wpisów, które zawierają dane binarne, unikowe i znaki komentarza.  
  
-   Podczas pracy z dokumentami XML wprowadzanemu należy zweryfikować wszystkie dane ze schematem.  
  
-   W środowiskach wielowarstwowych wszystkie dane powinny być weryfikowane przed wprowadzenia do zaufanej strefy.  
  
-   Nie akceptuj następujących ciągów w polach z plik, który można skonstruować nazwy: AUX, CLOCK$, COM1 do COM8, CON, CONFIG$, LPT1 do LPT8, NUL i PRN.  
  
-   Użyj <xref:System.Data.SqlClient.SqlParameter> obiektów z procedur składowanych i polecenia w celu udostępnienia weryfikacji sprawdzanie i długość typu.  
  
-   Użyj <xref:System.Text.RegularExpressions.Regex> wyrażenia w kodu klienta, aby filtrować nieprawidłowe znaki.  
  
## <a name="dynamic-sql-strategies"></a>Strategie dynamiczne SQL  
 Wykonywania dynamicznie utworzyć instrukcji SQL w Twojej podziały kod procedury łańcucha własności, powodując programu SQL Server sprawdzić uprawnienia obiektu wywołującego względem obiektów uzyskiwany przez dynamiczne SQL.  
  
 Program SQL Server ma metody umożliwić użytkownikom dostęp do danych za pomocą procedury składowane i funkcje zdefiniowane przez użytkownika, które wykonaj instrukcję SQL dynamicznych.  
  
-   Korzystanie z personifikacji z Transact-SQL AS wykonania klauzuli, zgodnie z opisem w [Dostosowywanie uprawnieniami personifikacja w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Rejestrowanie procedur składowanych z certyfikatami, zgodnie z opisem w [podpisywania procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>WYKONANIE AS  
 WYKONAJ jako klauzuli zastępuje uprawnienia obiektu wywołującego z użytkownika określonego w EXECUTE AS klauzuli. Zagnieżdżone procedur składowanych lub wyzwalaczy należy wykonać w kontekście zabezpieczeń użytkownika serwera proxy. Może to spowodować, że aplikacje, które zależą od zabezpieczenia na poziomie wiersza lub wymagają inspekcji. Niektóre funkcje, które zwracają tożsamości użytkownika Zwróć użytkownika określonego w EXECUTE AS klauzuli, nie oryginalny obiekt wywołujący. Kontekst wykonywania zostanie przywrócony do oryginalnego obiektu wywołującego tylko po wykonaniu procedury lub po wygenerowaniu instrukcji REVERT.  
  
### <a name="certificate-signing"></a>Podpisywanie certyfikatu  
 Podczas procedury składowanej, który został podpisany za pomocą certyfikatu, uprawnienia przyznane użytkownikowi certyfikatu są łączone z tymi obiektu wywołującego. Kontekst wykonywania pozostaje bez zmian; certyfikat użytkownika nie personifikują wywołującego. Rejestrowanie procedur składowanych wymaga podjęcia kilku czynności do wykonania. Zawsze, gdy procedura jest modyfikowany, musi ona być ponownie podpisane.  
  
### <a name="cross-database-access"></a>Krzyżowe dostęp do bazy danych  
 Tworzenie łańcucha własności między bazami danych nie działa w przypadkach, w którym są wykonywane utworzony dynamicznie instrukcji SQL. Można obejść to w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] , tworząc procedury przechowywanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywania procedury przy użyciu certyfikatu, który istnieje w obu bazach danych. To umożliwia użytkownikom dostęp do zasobów bazy danych używane przez procedurę bez przyznawania im dostępu do bazy danych lub uprawnieniami.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Procedury składowane](http://go.microsoft.com/fwlink/?LinkId=98233) i [iniekcja kodu SQL](http://go.microsoft.com/fwlink/?LinkId=98234) w dokumentacji SQL Server Books Online|Tematach opisano sposób tworzenia procedury składowane i jak działa iniekcja kodu SQL.|  
|[Nowe ataki obcięcie SQL oraz sposób ich uniknięcie](http://msdn.microsoft.com/msdnmag/issues/06/11/SQLSecurity/) w witrynie MSDN Magazine.|Opisuje sposób ograniczyć znaków i ciągi, iniekcja kodu SQL i modyfikacji obcięcie ataków.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Rejestrowanie procedur składowanych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
