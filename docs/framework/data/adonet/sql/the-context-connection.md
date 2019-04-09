---
title: Połączenie kontekstu
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: f942bf6a8df034ee96b595a791a07e64bc2ec179
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195361"
---
# <a name="the-context-connection"></a>Połączenie kontekstu
Problem dostęp do danych wewnętrznych jest dość typowy scenariusz. Oznacza to, że chcesz uzyskać dostęp do tego samego serwera swoje środowisko uruchomieniowe języka wspólnego (CLR) procedury składowanej lub funkcji jest wykonywany. Jedną z opcji jest utworzyć połączenie przy użyciu <xref:System.Data.SqlClient.SqlConnection>Określ parametry połączenia, który wskazuje na serwerze lokalnym, a Otwórz połączenie. Wymagane jest określenie poświadczeń do zalogowania się. Połączenie jest w sesji innej bazy danych niż procedurę składowaną lub funkcję, mogą mieć różne `SET` opcji, znajduje się w oddzielnej transakcji, nie zobaczą tabel tymczasowych, i tak dalej. Jeśli usługi zarządzanej procedury składowanej lub funkcji kod jest wykonywany w procesie programu SQL Server, jest to, ponieważ ktoś połączona z tym serwerem i instrukcja SQL, aby wywołać go. Prawdopodobnie procedury składowanej lub funkcji, które można wykonać w kontekście tego połączenia, wraz z jego transakcji `SET` opcje i tak dalej. Jest to połączenie kontekstu.  
  
 Połączenie kontekstu umożliwia wykonywanie instrukcji języka Transact-SQL w tym samym kontekście, że kod został wywołany w pierwszej kolejności. Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
1.  [Połączenie kontekstu](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
