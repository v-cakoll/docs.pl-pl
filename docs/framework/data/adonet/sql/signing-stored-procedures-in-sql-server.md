---
title: Rejestrowanie procedur składowanych w programie SQL Server
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 8dc62527be7273d3ce3222d4d261b81bc40b1e19
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791811"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Rejestrowanie procedur składowanych w programie SQL Server

Podpis cyfrowy jest szyfrowaniem danych zaszyfrowanym kluczem prywatnym osoby podpisującej. Klucz prywatny gwarantuje, że podpis cyfrowy jest unikatowy dla jego posiadacza lub właściciela. Można podpisywać procedury składowane, funkcje (z wyjątkiem wbudowanych funkcji zwracających tabele), wyzwalaczy i zestawów.

Procedurę składowaną można podpisać za pomocą certyfikatu lub klucza asymetrycznego. Jest to przeznaczone do scenariuszy, gdy uprawnienia nie mogą być dziedziczone przez tworzenie łańcucha własności lub w przypadku zerwania łańcucha własności, na przykład dynamicznego języka SQL. Następnie można utworzyć użytkownika zamapowanego na certyfikat, przyznając uprawnienia użytkownika certyfikatu do obiektów, do których procedura składowana musi uzyskać dostęp.

Możesz również utworzyć identyfikator logowania mapowany na ten sam certyfikat, a następnie udzielić wszelkich niezbędnych uprawnień na poziomie serwera dla tej nazwy logowania lub dodać nazwę logowania do co najmniej jednej roli serwera stałych. Jest to tak zaprojektowane, aby uniknąć `TRUSTWORTHY` włączania ustawienia bazy danych dla scenariuszy, w których są konieczne uprawnienia wyższego poziomu.

Po wykonaniu procedury składowanej SQL Server łączy uprawnienia użytkownika certyfikatu i/lub logowania się z osobami wywołującymi. W przeciwieństwie `EXECUTE AS` do klauzuli, nie zmienia kontekstu wykonywania procedury. Wbudowane funkcje, które zwracają nazwy logowania i użytkownika zwracają nazwę obiektu wywołującego, a nie nazwę użytkownika certyfikatu.

## <a name="creating-certificates"></a>Tworzenie certyfikatów

Po podpisaniu procedury składowanej z certyfikatem lub kluczem asymetrycznym skrót danych składający się z szyfrowanego skrótu kodu procedury składowanej wraz z użytkownikiem EXECUTE AS jest tworzony przy użyciu klucza prywatnego. W czasie wykonywania skrót danych jest odszyfrowywany przy użyciu klucza publicznego i porównywany z wartością skrótu procedury składowanej. Zmiana wartości skrótu "EXECUTE AS" spowoduje, że podpis cyfrowy nie jest już zgodny. Modyfikacja procedury składowanej powoduje całkowite odrzucanie podpisu, co uniemożliwia osobie, która nie ma dostępu do klucza prywatnego, zmiana kodu procedury składowanej. W obu przypadkach należy wykonać ponowną rejestrację procedury za każdym razem, gdy zmieniasz kod lub użytkownika "EXECUTE AS".

Podpisywanie modułu obejmuje dwie wymagane kroki:

1. Utwórz certyfikat przy użyciu instrukcji języka Transact- `CREATE CERTIFICATE [certificateName]` SQL. Ta instrukcja zawiera kilka opcji umożliwiających ustawienie daty rozpoczęcia i zakończenia oraz hasła. Domyślna Data wygaśnięcia to jeden rok.

1. Podpisz procedurę z certyfikatem przy użyciu instrukcji języka Transact `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` -SQL.

Po podpisaniu modułu należy utworzyć co najmniej jeden podmiot zabezpieczeń w celu przechowywania dodatkowych uprawnień, które powinny być skojarzone z certyfikatem.

Jeśli moduł wymaga dodatkowych uprawnień na poziomie bazy danych:

1. Utwórz użytkownika bazy danych skojarzonego z tym certyfikatem przy użyciu instrukcji języka `CREATE USER [userName] FROM CERTIFICATE [certificateName]` Transact-SQL. Ten użytkownik istnieje tylko w bazie danych i nie jest skojarzony z logowaniem, o ile nie utworzono również nazwy logowania z tego samego certyfikatu.

1. Przyznaj użytkownikowi certyfikatu wymagane uprawnienia na poziomie bazy danych.

Jeśli moduł wymaga dodatkowych uprawnień na poziomie serwera:

1. Skopiuj certyfikat do bazy danych `master` programu.

1. Utwórz nazwę logowania skojarzoną z tym certyfikatem przy użyciu instrukcji `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` języka Transact-SQL.

1. Przyznaj certyfikatowi zalogowanie wymagane uprawnienia na poziomie serwera.

> [!NOTE]
> Certyfikat nie może udzielić uprawnień użytkownikowi, który ma uprawnienia odwołane przy użyciu instrukcji Odmów. Odmów zawsze ma pierwszeństwo przed PRZYZNAniem, uniemożliwiając wywołującemu dziedziczenie uprawnień udzielonych użytkownikowi certyfikatu.

## <a name="external-resources"></a>Zasoby zewnętrzne

Aby uzyskać więcej informacji, zobacz następujące zasoby.

|Zasób|Opis|
|--------------|-----------------|
|[Podpisywanie modułu](https://go.microsoft.com/fwlink/?LinkId=98590) w SQL Server książki online|Opisuje podpisywanie modułu, dostarczając przykładowy scenariusz i linki do odpowiednich tematów języka Transact-SQL.|
|[Podpisywanie procedur składowanych przy użyciu certyfikatu w usłudze](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) SQL Server Books Online|Zawiera samouczek do podpisywania procedury składowanej przy użyciu certyfikatu.|

## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Dostosowywanie uprawnień personifikacji w programie SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Modyfikowanie danych za pomocą procedur składowanych](../modifying-data-with-stored-procedures.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
