---
title: Włączanie źródła danych dla LINQ Querying2
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: 312a880158e4d9254d6ead81538dc9a17e5c31b0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "68959787"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Włączanie źródła danych do zapytań LINQ

Istnieją różne sposoby, które należy [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wykonać, aby umożliwić odszukanie dowolnego źródła danych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] we wzorcu. Źródłem danych może być między innymi struktura danych, usługi sieci Web, system plików lub baza danych. Wzorzec ułatwia klientom Wysyłanie zapytań do źródła danych, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] włączono zapytania, ponieważ składnia i wzorzec zapytania nie są zmieniane. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sposoby, w których [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] można rozszerzyć następujące źródła danych, to m.in.:

- Implementowanie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] interfejsu w typie w celu włączenia obiektów do zapytania o ten typ. <xref:System.Collections.Generic.IEnumerable%601>

- Tworzenie standardowych metod operatorów zapytań, takich <xref:System.Linq.Enumerable.Where%2A> jak <xref:System.Linq.Enumerable.Select%2A> i, które poszerzają typ, aby [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] włączyć niestandardowe zapytania dla tego typu.

- Tworzenie dostawcy dla źródła danych, który implementuje <xref:System.Linq.IQueryable%601> interfejs. Dostawca implementujący ten interfejs odbiera [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania w formie drzew wyrażeń, które mogą być wykonywane w sposób niestandardowy, na przykład zdalnie.

- Tworzenie dostawcy dla źródła danych, który korzysta z istniejącej [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologii. Taki dostawcy umożliwiłby nie tylko badanie, ale także wstawianie, aktualizowanie i usuwanie, a także mapowanie dla typów zdefiniowanych przez użytkownika.

W tym temacie omówiono te opcje.

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak włączyć wykonywanie zapytań LINQ w odniesieniu do źródła danych

### <a name="in-memory-data"></a>Dane w pamięci
 Istnieją dwa sposoby włączania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań dotyczących danych w pamięci. Jeśli dane są typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, można wysyłać zapytania o dane za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów. Jeśli nie ma sensu włączania wyliczania typu przez implementację <xref:System.Collections.Generic.IEnumerable%601> interfejsu, można zdefiniować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowe metody operatorów zapytań w tym typie lub utworzyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowe metody operatorów zapytań, które powiększają typ. Niestandardowe implementacje standardowych operatorów kwerendy powinny stosować odroczone wykonania w celu zwracania wyników.

### <a name="remote-data"></a>Dane zdalne
 Najlepszą opcją włączenia [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do zdalnego źródła danych jest <xref:System.Linq.IQueryable%601> zaimplementowanie interfejsu. Jednak różni się to od rozszerzania dostawcy, takiego [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] jak dla źródła danych. Żadne modele dostawcy do rozszerzania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] istniejących technologii, takich [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]jak, do innych typów źródeł danych, są dostępne w programie Visual Studio 2008.

## <a name="iqueryable-linq-providers"></a>Dostawy IQueryable LINQ
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]dostawcy implementujący <xref:System.Linq.IQueryable%601> mogą się znacznie różnić w ich złożoności. W tej sekcji omówiono różne poziomy złożoności.

 Mniej złożony `IQueryable` dostawca może interfejsować za pomocą jednej metody usługi sieci Web. Ten typ dostawcy jest bardzo specyficzny, ponieważ oczekuje określonych informacji w kwerendach, które obsługuje. Posiada system zamkniętego typu, być może podając pojedynczy typ wyniku. Większość wykonywania zapytania odbywa się lokalnie, na przykład przy użyciu <xref:System.Linq.Enumerable> implementacji standardowych operatorów zapytań. Mniej skomplikowany dostawca może zbadać tylko jedną metodę wyrażenie wywołania w drzewie wyrażeń, które reprezentuje zapytanie i pozwala, aby pozostała logiki kwerendy była obsługiwana gdzie indziej.

 `IQueryable` Dostawca średniej złożoności może kierować do źródła danych, które ma częściowo wyraźny język zapytań. Jeśli jest przeznaczona do usługi sieci Web, może współpracować z więcej niż jedną metodą usługi sieci Web i wybierać metodę do wywołania na podstawie pytania stawianego przez kwerendę. Dostawca średniej złożoności będzie miał bogatszy system typów niż prosty dostawca, ale nadal będzie to system stałych typów. Na przykład dostawca może ujawnić typy, które mają relacje jeden do wielu. Te typy można przemierzać, ale nie zapewnia to technologii mapowania dla typów zdefiniowanych przez użytkownika.

 Złożony `IQueryable` dostawca, taki [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] jak dostawca, może przetłumaczyć kompletne [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania na język zapytań ekspresowych, taki jak SQL. Złożony dostawca jest bardziej ogólny niż dostawca mniej skomplikowany, ponieważ może obsługiwać szerszą gamy pytań w kwerendzie. Ma także system typu otwartego i dlatego musi zawierać rozległe infrastruktury do mapowania typów zdefiniowanych przez użytkownika. Opracowywanie złożonego dostawcy wymaga znacznej ilości wysiłku.

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
