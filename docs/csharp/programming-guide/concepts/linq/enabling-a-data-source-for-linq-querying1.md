---
title: Włączanie źródła danych do zapytań LINQ
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635772"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Włączanie źródła danych do zapytań LINQ
Istnieją różne sposoby rozszerzenia LINQ, aby umożliwić dowolnego źródła danych, które mają być badane w wzorzec LINQ. Źródłem danych może być między innymi struktura danych, usługi sieci Web, system plików lub baza danych. Wzorzec LINQ ułatwia klientom wykonywanie zapytań o źródło danych, dla którego włączono wykonywanie zapytań LINQ, ponieważ składnia i wzorzec kwerendy nie ulegnie zmianie. Sposoby, w których LINQ można rozszerzyć na te źródła danych, są następujące:  
  
- Implementowanie <xref:System.Collections.Generic.IEnumerable%601> interfejsu w typie, aby włączyć LINQ do obiektów zapytań tego typu.  
  
- Tworzenie standardowych metod operatora <xref:System.Linq.Enumerable.Where%2A> kwerendy, takich jak i <xref:System.Linq.Enumerable.Select%2A> rozszerzają typ, aby włączyć niestandardowe zapytanie LINQ tego typu.  
  
- Tworzenie dostawcy dla źródła danych, <xref:System.Linq.IQueryable%601> który implementuje interfejs. Dostawca, który implementuje ten interfejs odbiera zapytania LINQ w postaci drzew wyrażeń, które można wykonać w sposób niestandardowy, na przykład zdalnie.  
  
- Tworzenie dostawcy dla źródła danych, który korzysta z istniejącej technologii LINQ. Taki dostawcy umożliwiłby nie tylko badanie, ale także wstawianie, aktualizowanie i usuwanie, a także mapowanie dla typów zdefiniowanych przez użytkownika.  
  
 W tym temacie omówiono te opcje.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak włączyć wykonywanie zapytań LINQ w odniesieniu do źródła danych  
  
### <a name="in-memory-data"></a>Dane w pamięci  
 Istnieją dwa sposoby, aby włączyć LINQ zapytanie danych w pamięci. Jeśli dane są typu, który <xref:System.Collections.Generic.IEnumerable%601>implementuje , można zbadać dane za pomocą LINQ do obiektów. Jeśli nie ma sensu, aby włączyć wyliczenie <xref:System.Collections.Generic.IEnumerable%601> typu przez implementowanie interfejsu, można zdefiniować linq standardowych metod operatorkwerendy w tym typie lub utworzyć linq standardowych metod operatorkwerendy, które rozszerzają typ. Niestandardowe implementacje standardowych operatorów kwerendy powinny stosować odroczone wykonania w celu zwracania wyników.  
  
### <a name="remote-data"></a>Dane zdalne  
 Najlepszym rozwiązaniem dla włączania LINQ zapytanie zdalnego źródła <xref:System.Linq.IQueryable%601> danych jest zaimplementowanie interfejsu. Jednak różni się to od rozszerzenia [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dostawcy, takich jak dla źródła danych. W programie Visual Studio 2008 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]nie są dostępne żadne modele dostawców rozszerzające istniejące technologie LINQ, takie jak , do innych typów źródeł danych.
  
## <a name="iqueryable-linq-providers"></a>Dostawy IQueryable LINQ  
 Dostawcy LINQ, <xref:System.Linq.IQueryable%601> którzy implementują, mogą się znacznie różnić pod względem złożoności. W tej sekcji omówiono różne poziomy złożoności.  
  
 Mniej złożony `IQueryable` dostawca może interfejs z jednej metody usługi sieci Web. Ten typ dostawcy jest bardzo specyficzny, ponieważ oczekuje określonych informacji w kwerendach, które obsługuje. Posiada system zamkniętego typu, być może podając pojedynczy typ wyniku. Większość wykonywania kwerendy występuje lokalnie, na <xref:System.Linq.Enumerable> przykład przy użyciu implementacji standardowych operatorów kwerend. Mniej skomplikowany dostawca może zbadać tylko jedną metodę wyrażenie wywołania w drzewie wyrażeń, które reprezentuje zapytanie i pozwala, aby pozostała logiki kwerendy była obsługiwana gdzie indziej.  
  
 Dostawca `IQueryable` średniej złożoności może kierować źródło danych, które ma częściowo wyrazisty język zapytania. Jeśli jest przeznaczona do usługi sieci Web, może współpracować z więcej niż jedną metodą usługi sieci Web i wybierać metodę do wywołania na podstawie pytania stawianego przez kwerendę. Dostawca średniej złożoności będzie miał bogatszy system typów niż prosty dostawca, ale nadal będzie to system stałych typów. Na przykład dostawca może ujawnić typy, które mają relacje jeden do wielu. Te typy można przemierzać, ale nie zapewnia to technologii mapowania dla typów zdefiniowanych przez użytkownika.  
  
 Złożony `IQueryable` dostawca, takich [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] jak dostawca, może tłumaczyć pełne zapytania LINQ do języka zapytań ekspresyjnych, takich jak SQL. Złożony dostawca jest bardziej ogólny niż dostawca mniej skomplikowany, ponieważ może obsługiwać szerszą gamy pytań w kwerendzie. Ma także system typu otwartego i dlatego musi zawierać rozległe infrastruktury do mapowania typów zdefiniowanych przez użytkownika. Opracowywanie złożonego dostawcy wymaga znacznej ilości wysiłku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [LINQ do obiektów (C#)](./linq-to-objects.md)
