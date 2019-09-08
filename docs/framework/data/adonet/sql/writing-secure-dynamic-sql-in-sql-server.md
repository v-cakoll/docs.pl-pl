---
title: Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c02455ba8798df1de1d52f6b4db3426d41b95daf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791420"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server
Iniekcja SQL to proces, za pomocą którego złośliwy użytkownik wprowadza instrukcje języka Transact-SQL zamiast prawidłowych danych wejściowych. Jeśli dane wejściowe są przesyłane bezpośrednio do serwera bez sprawdzania poprawności i jeśli aplikacja przypadkowo wykonuje wprowadzony kod, atakujący może uszkodzić lub zniszczyć dane.  
  
 Każda procedura, która konstruuje instrukcje SQL, powinna zostać sprawdzona pod kątem luk w zabezpieczeniach, ponieważ SQL Server będzie wykonywała wszystkie zapytania z prawidłowymi składnią. Nawet sparametryzowane dane można manipulować przez wykwalifikowany i ustaloną osobę atakującą. Jeśli używasz dynamicznego języka SQL, pamiętaj, aby Sparametryzuj polecenia, i nigdy nie dodawaj wartości parametrów bezpośrednio do ciągu zapytania.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomia ataku polegającego na iniekcji SQL  
 Proces wstrzykiwania działa przez przedwcześnie zakończenie ciągu tekstowego i dołączenie nowego polecenia. Ze względu na to, że wstawione polecenie może mieć do niego dodatkowe ciągi, przed wykonaniem malefactor kończy wstrzykiwany ciąg z znacznikiem komentarza "--". Następny tekst jest ignorowany w czasie wykonywania. Można wstawiać wiele poleceń przy użyciu średnika (;) ogranicznik.  
  
 Tak długo, jak wstrzyknięty kod SQL ma poprawną składnię, nie można programowo wykryć naruszenia. W związku z tym należy zweryfikować wszystkie dane wejściowe użytkownika i uważnie przejrzeć kod, który wykonuje skonstruowane polecenia SQL na serwerze, który jest używany. Nigdy nie łącz danych wprowadzonych przez użytkownika, które nie zostały zweryfikowane. Łączenie ciągów to podstawowy punkt wejścia dla iniekcji skryptu.  
  
 Oto kilka przydatnych wskazówek:  
  
- Nigdy nie Kompiluj instrukcji języka Transact-SQL bezpośrednio z danych wejściowych użytkownika; Użyj procedur składowanych, aby sprawdzić poprawność danych wejściowych użytkownika.  
  
- Sprawdź poprawność danych wejściowych użytkownika, sprawdzając typ, długość, format i zakres. Użyj funkcji CYTATu języka Transact-SQL (), aby wypróbować nazwy systemu lub funkcję REPLACE () w celu ucieczki dowolnego znaku w ciągu.  
  
- Zaimplementuj wiele warstw walidacji w każdej warstwie aplikacji.  
  
- Przetestuj rozmiar i typ danych wejściowych i wymuś odpowiednie limity. Może to pomóc w zapobieganiu zamierzonym przekroczeniu buforu.  
  
- Przetestuj zawartość zmiennych ciągów i zaakceptuj tylko oczekiwane wartości. Odrzuć wpisy zawierające dane binarne, sekwencje ucieczki i znaki komentarza.  
  
- Podczas pracy z dokumentami XML Sprawdź poprawność wszystkich danych względem schematu w miarę ich wprowadzania.  
  
- W środowiskach wielowarstwowych wszystkie dane powinny być weryfikowane przed przystąpieniem do zaufanej strefy.  
  
- Nie Akceptuj następujących ciągów w polach, z których można utworzyć nazwy plików: AUX, CLOCK $, COM1 przez COM8, CON, CONFIG $, LPT1 przez LPT8, NUL i PRN.  
  
- Użyj <xref:System.Data.SqlClient.SqlParameter> obiektów z procedurami składowanymi i poleceniami, aby zapewnić sprawdzanie typu i weryfikację długości.  
  
- Używanie <xref:System.Text.RegularExpressions.Regex> wyrażeń w kodzie klienta do filtrowania nieprawidłowych znaków.  
  
## <a name="dynamic-sql-strategies"></a>Dynamiczne strategie SQL  
 Wykonywanie dynamicznie utworzonych instrukcji SQL w kodzie proceduralnym powoduje przerwanie łańcucha własności, co sprawia, że SQL Server sprawdzać uprawnienia obiektu wywołującego względem obiektów, do których uzyskuje się dostęp za pomocą dynamicznego języka SQL.  
  
 SQL Server ma metody udzielania użytkownikom dostępu do danych za pomocą procedur składowanych i funkcji zdefiniowanych przez użytkownika, które wykonują dynamiczne SQL.  
  
- Używanie personifikacji z klauzulą EXECUTE AS języka Transact-SQL, zgodnie z opisem w temacie [Dostosowywanie uprawnień przy użyciu personifikacji w SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Podpisywanie procedur składowanych z certyfikatami, zgodnie z opisem w temacie [procedury składowane podpisywania w SQL Server](signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>WYKONAJ JAKO  
 Klauzula EXECUTE AS zastępuje uprawnienia obiektu wywołującego określonym w klauzuli EXECUTE AS. Zagnieżdżone procedury składowane lub wyzwalacze są wykonywane w kontekście zabezpieczeń użytkownika serwera proxy. Może to spowodować uszkodzenie aplikacji, które korzystają z zabezpieczeń na poziomie wiersza lub wymagają inspekcji. Niektóre funkcje, które zwracają tożsamość użytkownika, zwracają użytkownika określonego w klauzuli EXECUTE AS, a nie oryginalnego obiektu wywołującego. Kontekst wykonywania jest przywracany do oryginalnego obiektu wywołującego dopiero po wykonaniu procedury lub po wydaniu instrukcji przywracania.  
  
### <a name="certificate-signing"></a>Podpisywanie certyfikatu  
 Po wykonaniu procedury składowanej podpisanej przy użyciu certyfikatu uprawnienia przyznane użytkownikowi certyfikatu są scalane z tymi obiektu wywołującego. Kontekst wykonywania pozostaje taki sam; Użytkownik certyfikatu nie personifikuje obiektu wywołującego. Procedury składowane podpisywania wymagają wykonania kilku kroków. Za każdym razem, gdy procedura jest modyfikowana, należy ją podpisać.  
  
### <a name="cross-database-access"></a>Dostęp między bazami danych  
 Tworzenie łańcucha własności między bazami danych nie działa w przypadkach, w których są wykonywane dynamiczne instrukcje SQL. Można obejść ten krok w SQL Server przez utworzenie procedury składowanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywanie procedury z certyfikatem, który istnieje w obu bazach danych. Zapewnia to użytkownikom dostęp do zasobów bazy danych używanych przez procedurę bez udzielania im dostępu do bazy danych lub uprawnień.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Procedury składowane](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) i [iniekcja kodu SQL](/sql/relational-databases/security/sql-injection) w usłudze SQL Server Books Online|Tematy opisują sposób tworzenia procedur składowanych i sposobu działania iniekcji SQL.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Rejestrowanie procedur składowanych w programie SQL Server](signing-stored-procedures-in-sql-server.md)
- [Dostosowywanie uprawnień personifikacji w programie SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
