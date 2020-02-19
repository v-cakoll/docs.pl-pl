---
title: Rejestrowanie procedur składowanych w programie SQL Server
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 0131655d06a6ef543ea460d04739401538cac04b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452360"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Rejestrowanie procedur składowanych w programie SQL Server

Podpis cyfrowy jest szyfrowaniem danych zaszyfrowanym kluczem prywatnym osoby podpisującej. Klucz prywatny gwarantuje, że podpis cyfrowy jest unikatowy dla jego posiadacza lub właściciela. Można podpisywać procedury składowane, funkcje (z wyjątkiem wbudowanych funkcji zwracających tabele), wyzwalaczy i zestawów.

Procedurę składowaną można podpisać za pomocą certyfikatu lub klucza asymetrycznego. Jest to przeznaczone do scenariuszy, gdy uprawnienia nie mogą być dziedziczone przez tworzenie łańcucha własności lub w przypadku zerwania łańcucha własności, na przykład dynamicznego języka SQL. Następnie można utworzyć użytkownika zamapowanego na certyfikat, przyznając uprawnienia użytkownika certyfikatu do obiektów, do których procedura składowana musi uzyskać dostęp.

Możesz również utworzyć identyfikator logowania mapowany na ten sam certyfikat, a następnie udzielić wszelkich niezbędnych uprawnień na poziomie serwera dla tej nazwy logowania lub dodać nazwę logowania do co najmniej jednej roli serwera stałych. Ma to na celu uniknięcie włączenia ustawienia `TRUSTWORTHY` Database dla scenariuszy, w których są konieczne uprawnienia wyższego poziomu.

Po wykonaniu procedury składowanej SQL Server łączy uprawnienia użytkownika certyfikatu i/lub logowania się z osobami wywołującymi. W przeciwieństwie do klauzuli `EXECUTE AS` nie powoduje zmiany kontekstu wykonywania procedury. Wbudowane funkcje, które zwracają nazwy logowania i użytkownika zwracają nazwę obiektu wywołującego, a nie nazwę użytkownika certyfikatu.

## <a name="creating-certificates"></a>Tworzenie certyfikatów

Po podpisaniu procedury składowanej z certyfikatem lub kluczem asymetrycznym skrót danych składający się z szyfrowanego skrótu kodu procedury składowanej wraz z użytkownikiem EXECUTE AS jest tworzony przy użyciu klucza prywatnego. W czasie wykonywania skrót danych jest odszyfrowywany przy użyciu klucza publicznego i porównywany z wartością skrótu procedury składowanej. Zmiana wartości skrótu "EXECUTE AS" spowoduje, że podpis cyfrowy nie jest już zgodny. Modyfikacja procedury składowanej powoduje całkowite odrzucanie podpisu, co uniemożliwia osobie, która nie ma dostępu do klucza prywatnego, zmiana kodu procedury składowanej. W obu przypadkach należy wykonać ponowną rejestrację procedury za każdym razem, gdy zmieniasz kod lub użytkownika "EXECUTE AS".

Podpisywanie modułu obejmuje dwie wymagane kroki:

1. Utwórz certyfikat przy użyciu instrukcji języka Transact-SQL `CREATE CERTIFICATE [certificateName]`. Ta instrukcja zawiera kilka opcji umożliwiających ustawienie daty rozpoczęcia i zakończenia oraz hasła. Domyślna Data wygaśnięcia to jeden rok.

1. Podpisz procedurę z certyfikatem, korzystając z instrukcji Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]`.

Po podpisaniu modułu należy utworzyć co najmniej jeden podmiot zabezpieczeń w celu przechowywania dodatkowych uprawnień, które powinny być skojarzone z certyfikatem.

Jeśli moduł wymaga dodatkowych uprawnień na poziomie bazy danych:

1. Utwórz użytkownika bazy danych skojarzonego z tym certyfikatem przy użyciu instrukcji języka Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]`. Ten użytkownik istnieje tylko w bazie danych i nie jest skojarzony z logowaniem, o ile nie utworzono również nazwy logowania z tego samego certyfikatu.

1. Przyznaj użytkownikowi certyfikatu wymagane uprawnienia na poziomie bazy danych.

Jeśli moduł wymaga dodatkowych uprawnień na poziomie serwera:

1. Skopiuj certyfikat do bazy danych `master`.

1. Utwórz nazwę logowania skojarzoną z tym certyfikatem za pomocą instrukcji języka Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]`.

1. Przyznaj certyfikatowi zalogowanie wymagane uprawnienia na poziomie serwera.

> [!NOTE]
> Certyfikat nie może udzielić uprawnień użytkownikowi, który ma uprawnienia odwołane przy użyciu instrukcji Odmów. Odmów zawsze ma pierwszeństwo przed PRZYZNAniem, uniemożliwiając wywołującemu dziedziczenie uprawnień udzielonych użytkownikowi certyfikatu.

## <a name="external-resources"></a>Zasoby zewnętrzne

Więcej informacji zawierają poniższe zasoby.

|Zasób|Opis|
|--------------|-----------------|
|[Podpisywanie modułu](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))|Opisuje podpisywanie modułu, dostarczając przykładowy scenariusz i linki do odpowiednich artykułów języka Transact-SQL.|
|[Podpisywanie procedur składowanych przy użyciu certyfikatu](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)|Zawiera samouczek do podpisywania procedury składowanej przy użyciu certyfikatu.|

## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Dostosowywanie uprawnień personifikacji w programie SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../modifying-data-with-stored-procedures.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
