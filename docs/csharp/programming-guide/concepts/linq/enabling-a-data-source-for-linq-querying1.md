---
title: Włączanie źródła danych do zapytań LINQ
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635772"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Włączanie źródła danych do zapytań LINQ
Istnieją różne sposoby, aby zwiększyć LINQ, aby umożliwić odszukanie dowolnego źródła danych w wzorcu LINQ. Źródłem danych może być między innymi struktura danych, usługi sieci Web, system plików lub baza danych. Wzorzec LINQ ułatwia klientom Wysyłanie zapytań do źródła danych, dla którego jest włączone zapytanie LINQ, ponieważ składnia i wzorzec zapytania nie są zmieniane. Sposoby rozszerzania LINQ do tych źródeł danych są następujące:  
  
- Implementowanie interfejsu <xref:System.Collections.Generic.IEnumerable%601> w typie w celu włączenia LINQ to Objects zapytania o ten typ.  
  
- Tworzenie standardowych metod operatorów zapytań, takich jak <xref:System.Linq.Enumerable.Where%2A> i <xref:System.Linq.Enumerable.Select%2A>, które rozszery typ, aby umożliwić niestandardowe zapytania LINQ tego typu.  
  
- Tworzenie dostawcy dla źródła danych, który implementuje interfejs <xref:System.Linq.IQueryable%601>. Dostawca implementujący ten interfejs odbiera zapytania LINQ w formie drzew wyrażeń, które mogą być wykonywane w sposób niestandardowy, na przykład zdalnie.  
  
- Tworzenie dostawcy dla źródła danych, który korzysta z istniejącej technologii LINQ. Taki dostawcy umożliwiłby nie tylko badanie, ale także wstawianie, aktualizowanie i usuwanie, a także mapowanie dla typów zdefiniowanych przez użytkownika.  
  
 W tym temacie omówiono te opcje.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak włączyć wykonywanie zapytań LINQ w odniesieniu do źródła danych  
  
### <a name="in-memory-data"></a>Dane w pamięci  
 Istnieją dwa sposoby włączania zapytań LINQ do danych w pamięci. Jeśli dane są typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, można wykonywać zapytania dotyczące danych przy użyciu LINQ to Objects. Jeśli nie ma sensu włączania wyliczania typu przez implementację interfejsu <xref:System.Collections.Generic.IEnumerable%601>, można zdefiniować metody operatora zapytania w standardzie LINQ w tym typie lub utworzyć metody standardowego operatora zapytań LINQ, które zwiększają typ. Niestandardowe implementacje standardowych operatorów kwerendy powinny stosować odroczone wykonania w celu zwracania wyników.  
  
### <a name="remote-data"></a>Dane zdalne  
 Najlepszą opcją włączenia zapytania LINQ do zdalnego źródła danych jest zaimplementowanie interfejsu <xref:System.Linq.IQueryable%601>. Jednak różni się to od rozszerzania dostawcy, takiego jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dla źródła danych. W programie Visual Studio 2008 nie są dostępne modele dostawcy służące do rozszerzania istniejących technologii LINQ, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], do innych typów źródeł danych.
  
## <a name="iqueryable-linq-providers"></a>Dostawy IQueryable LINQ  
 Dostawcy LINQ, którzy implementują <xref:System.Linq.IQueryable%601> mogą się znacznie różnić w ich złożoności. W tej sekcji omówiono różne poziomy złożoności.  
  
 Mniej złożony dostawca `IQueryable` może interfejsować za pomocą jednej metody usługi sieci Web. Ten typ dostawcy jest bardzo specyficzny, ponieważ oczekuje określonych informacji w kwerendach, które obsługuje. Posiada system zamkniętego typu, być może podając pojedynczy typ wyniku. Większość wykonywania zapytania odbywa się lokalnie, na przykład przy użyciu implementacji <xref:System.Linq.Enumerable> standardowych operatorów zapytań. Mniej skomplikowany dostawca może zbadać tylko jedną metodę wyrażenie wywołania w drzewie wyrażeń, które reprezentuje zapytanie i pozwala, aby pozostała logiki kwerendy była obsługiwana gdzie indziej.  
  
 Dostawca `IQueryable` średniej złożoności może kierować do źródła danych, które ma częściowo wyraźny język zapytań. Jeśli jest przeznaczona do usługi sieci Web, może współpracować z więcej niż jedną metodą usługi sieci Web i wybierać metodę do wywołania na podstawie pytania stawianego przez kwerendę. Dostawca średniej złożoności będzie miał bogatszy system typów niż prosty dostawca, ale nadal będzie to system stałych typów. Na przykład dostawca może ujawnić typy, które mają relacje jeden do wielu. Te typy można przemierzać, ale nie zapewnia to technologii mapowania dla typów zdefiniowanych przez użytkownika.  
  
 Złożony dostawca `IQueryable`, taki jak dostawca [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], może przetłumaczyć kompletne zapytania LINQ na język zapytań ekspresowych, taki jak SQL. Złożony dostawca jest bardziej ogólny niż dostawca mniej skomplikowany, ponieważ może obsługiwać szerszą gamy pytań w kwerendzie. Ma także system typu otwartego i dlatego musi zawierać rozległe infrastruktury do mapowania typów zdefiniowanych przez użytkownika. Opracowywanie złożonego dostawcy wymaga znacznej ilości wysiłku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
