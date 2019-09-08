---
title: Scenariusze zabezpieczeń aplikacji w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf844f35a3504af52cdb6bf745862ad5098dfc5f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782693"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scenariusze zabezpieczeń aplikacji w programie SQL Server
Nie ma żadnego poprawnego sposobu tworzenia bezpiecznego SQL Server aplikacji klienckiej. Każda aplikacja jest unikatowa w wymaganiach, środowisku wdrażania i wypełnieniu użytkownika. Aplikacja, która jest w stanie bezpiecznie wdrożona, może stać się mniej bezpieczna w czasie. Nie jest możliwe przewidywalność z dokładnością, jakie zagrożenia mogą pojawić się w przyszłości.  
  
 SQL Server, jako produkt, został rozwijający wiele wersji w celu uwzględnienia najnowszych funkcji zabezpieczeń, które umożliwiają deweloperom tworzenie bezpiecznych aplikacji baz danych. Jednak zabezpieczenia nie są dostępne w tym polu. wymaga ciągłego monitorowania i aktualizowania.  
  
## <a name="common-threats"></a>Typowe zagrożenia  
 Deweloperzy muszą zrozumieć zagrożenia bezpieczeństwa, Narzędzia udostępniane do ich rozwiązywania oraz jak unikać samodziałających luk w zabezpieczeniach. Bezpieczeństwo może być najlepszym rozwiązaniem w postaci łańcucha, w którym przerwa w jednym łączu narusza intensywność całości. Poniższa lista zawiera kilka typowych zagrożeń zabezpieczeń, które zostały omówione bardziej szczegółowo w tematach w tej sekcji.  
  
### <a name="sql-injection"></a>Iniekcja SQL  
 Iniekcja SQL to proces, za pomocą którego złośliwy użytkownik wprowadza instrukcje języka Transact-SQL zamiast prawidłowych danych wejściowych. Jeśli dane wejściowe są przesyłane bezpośrednio do serwera bez sprawdzania poprawności i jeśli aplikacja przypadkowo wykonuje wprowadzony kod, atakujący może uszkodzić lub zniszczyć dane. Ataki z iniekcją SQL Server można zablokować za pomocą procedur składowanych i sparametryzowanych poleceń, unikając dynamicznego języka SQL i ograniczania uprawnień do wszystkich użytkowników.  
  
### <a name="elevation-of-privilege"></a>Podniesienie uprawnień  
 Podniesienie uprawnień dostępu występuje, gdy użytkownik może założyć uprawnienia zaufanego konta, takiego jak właściciel lub administrator. Należy zawsze uruchamiać konta użytkowników z najniższymi uprawnieniami i przypisywać tylko odpowiednie uprawnienia. Unikaj używania kont administracyjnych lub właścicieli do wykonywania kodu. Ogranicza to liczbę szkód, które mogą wystąpić w przypadku pomyślnego ataku. Podczas wykonywania zadań wymagających dodatkowych uprawnień Użyj podpisywania procedury lub personifikacji tylko w czasie trwania zadania. Można podpisywać procedury składowane z certyfikatami lub używać personifikacji do tymczasowego przypisywania uprawnień.  
  
### <a name="probing-and-intelligent-observation"></a>Badanie i inteligentne obserwacje  
 Atak na sondowanie może korzystać z komunikatów o błędach wygenerowanych przez aplikację w celu wyszukania luk w zabezpieczeniach. Zaimplementuj obsługę błędów we wszystkich kod proceduralny, aby zapobiec zwracaniu SQL Server informacji o błędzie do użytkownika końcowego.  
  
### <a name="authentication"></a>Uwierzytelnianie  
 Atak polegający na iniekcji parametrów połączenia może wystąpić podczas korzystania z SQL Server logowania, jeśli parametry połączenia oparte na danych wejściowych użytkownika są konstruowane w czasie wykonywania. Jeśli parametry połączenia nie są sprawdzane pod kątem prawidłowych par słów kluczowych, osoba atakująca może wstawić dodatkowe znaki, potencjalnie uzyskujących dostęp do poufnych danych lub innych zasobów na serwerze. Użyj uwierzytelniania systemu Windows wszędzie tam, gdzie to możliwe. Jeśli musisz użyć SQL Server logowań, użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder> , aby utworzyć i zweryfikować parametry połączenia w czasie wykonywania.  
  
### <a name="passwords"></a>Haśle  
 Wiele ataków zakończyło się pomyślnie, ponieważ intruz mógł uzyskać lub złamać hasło dla użytkownika z uprawnieniami. Hasła są pierwszym wierszem obrony przed intruzami, więc ustawienie silnych haseł jest niezbędne dla bezpieczeństwa systemu. Tworzenie i wymuszanie zasad haseł do uwierzytelniania w trybie mieszanym.  
  
 Zawsze należy przypisać silne hasło do `sa` konta, nawet w przypadku korzystania z uwierzytelniania systemu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)  
 Opisuje sposób korzystania z procedur składowanych w celu zarządzania uprawnieniami i kontroli dostępu do danych. Korzystanie z procedur składowanych jest efektywnym sposobem na reagowanie na wiele zagrożeń bezpieczeństwa.  
  
 [Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server](writing-secure-dynamic-sql-in-sql-server.md)  
 Opisuje techniki pisania bezpiecznego dynamicznego SQL przy użyciu procedur składowanych.  
  
 [Rejestrowanie procedur składowanych w programie SQL Server](signing-stored-procedures-in-sql-server.md)  
 Opisuje sposób podpisywania procedury składowanej przy użyciu certyfikatu w celu umożliwienia użytkownikom pracy z danymi, do których nie ma bezpośredniego dostępu. Dzięki temu procedury składowane mogą wykonywać operacje, których obiekt wywołujący nie ma uprawnień do bezpośredniego wykonania.  
  
 [Dostosowywanie uprawnień personifikacji w programie SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)  
 Opisuje sposób użycia klauzuli EXECUTE AS do personifikacji innego użytkownika. Personifikacja przełącza kontekst wykonywania od wywołującego do określonego użytkownika.  
  
 [Udzielanie uprawnień na poziomie wiersza w programie SQL Server](granting-row-level-permissions-in-sql-server.md)  
 Opisuje sposób implementacji uprawnień na poziomie wiersza w celu ograniczenia dostępu do danych.  
  
 [Tworzenie ról aplikacji w programie SQL Server](creating-application-roles-in-sql-server.md)  
 Opisuje funkcje i funkcje ról aplikacji.  
  
 [Włączanie dostępu między bazami danych w programie SQL Server](enabling-cross-database-access-in-sql-server.md)  
 Opisuje sposób włączania dostępu między bazami danych bez naruszania zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia serwera SQL](sql-server-security.md)
- [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)
- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
