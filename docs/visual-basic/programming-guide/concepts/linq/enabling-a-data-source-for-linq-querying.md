---
title: Włączanie źródła danych dla LINQ Querying2
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: 0904d646014fa6a0525e624bc3466dee12b3cc02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643799"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Włączanie źródła danych do zapytań LINQ
Istnieją różne sposoby rozszerzania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] umożliwiające dowolnego źródła danych w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wzorca. Źródłem danych może być między innymi struktura danych, usługi sieci Web, system plików lub baza danych. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Wzorzec ułatwia klientom zapytania źródła danych, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań jest włączony, ponieważ składnia i wzorzec zapytania nie powoduje zmiany. Sposoby, w którym [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] może zostać rozszerzony do tych danych źródła są następujące:  
  
-   Implementowanie <xref:System.Collections.Generic.IEnumerable%601> interfejsu w typie, aby włączyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do badania obiektów tego typu.  
  
-   Tworzenie standardowej kwerendy, operator metod takich jak <xref:System.Linq.Enumerable.Where%2A> i <xref:System.Linq.Enumerable.Select%2A> który rozszerzenie typu, aby włączyć niestandardowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań tego typu.  
  
-   Tworzenie dostawcy dla źródła danych, który implementuje <xref:System.Linq.IQueryable%601> interfejsu. Odbiera dostawcę, który implementuje ten interfejs [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania w formie drzewa wyrażeń, które go może zostać uruchomiony w niestandardowy sposób, na przykład zdalnie.  
  
-   Tworzenie dostawcy dla źródła danych, która korzysta z istniejącej [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologii. Taki dostawcy umożliwiłby nie tylko badanie, ale także wstawianie, aktualizowanie i usuwanie, a także mapowanie dla typów zdefiniowanych przez użytkownika.  
  
 W tym temacie omówiono te opcje.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak włączyć wykonywanie zapytań LINQ w odniesieniu do źródła danych  
  
### <a name="in-memory-data"></a>Dane w pamięci  
 Istnieją dwa sposoby można włączyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyszukiwanie danych w pamięci. Jeśli dane są typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, dane można badać przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów. Jeśli go nie ma sensu umożliwiające wyliczenie danego typu zaimplementowanie <xref:System.Collections.Generic.IEnumerable%601> interfejsu, można zdefiniować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowe metody operatora w tego typu zapytań, lub utworzyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody — operator zapytań standardowe, stanowiące rozszerzenie typu. Niestandardowe implementacje standardowych operatorów kwerendy powinny stosować odroczone wykonania w celu zwracania wyników.  
  
### <a name="remote-data"></a>Dane zdalne  
 Najlepszym rozwiązaniem umożliwiających [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyszukiwanie zdalnego źródła danych jest zaimplementowanie <xref:System.Linq.IQueryable%601> interfejsu. Jednak ta różni się od takich jak rozszerzanie dostawcę [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dla źródła danych. Żadnych modeli dostawcy do rozszerzania istniejących [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologii, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], do innego typu źródła danych są dostępne w [!INCLUDE[vs_orcas_long](~/includes/vs-orcas-long-md.md)].  
  
## <a name="iqueryable-linq-providers"></a>Dostawy IQueryable LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców, które implementują <xref:System.Linq.IQueryable%601> mogą mieć różne powszechnie złożoności. W tej sekcji omówiono różne poziomy złożoności.  
  
 Mniej złożona `IQueryable` dostawcy mogą łączyć się z jednej metody usługi sieci Web. Ten typ dostawcy jest bardzo specyficzny, ponieważ oczekuje określonych informacji w kwerendach, które obsługuje. Posiada system zamkniętego typu, być może podając pojedynczy typ wyniku. Większość wykonywania zapytania występuje lokalnie, na przykład za pomocą <xref:System.Linq.Enumerable> implementacje standardowych operatorów zapytań. Mniej skomplikowany dostawca może zbadać tylko jedną metodę wyrażenie wywołania w drzewie wyrażeń, które reprezentuje zapytanie i pozwala, aby pozostała logiki kwerendy była obsługiwana gdzie indziej.  
  
 `IQueryable` Dostawcy średnia złożoności może docelowego źródła danych z językiem częściowo obszerne zapytania. Jeśli jest przeznaczona do usługi sieci Web, może współpracować z więcej niż jedną metodą usługi sieci Web i wybierać metodę do wywołania na podstawie pytania stawianego przez kwerendę. Dostawca średniej złożoności będzie miał bogatszy system typów niż prosty dostawca, ale nadal będzie to system stałych typów. Na przykład dostawca może ujawnić typy, które mają relacje jeden do wielu. Te typy można przemierzać, ale nie zapewnia to technologii mapowania dla typów zdefiniowanych przez użytkownika.  
  
 Złożony `IQueryable` dostawcy, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dostawcy, może tłumaczyć pełną [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania języka obszerne zapytania, takie jak SQL. Złożony dostawca jest bardziej ogólny niż dostawca mniej skomplikowany, ponieważ może obsługiwać szerszą gamy pytań w kwerendzie. Ma także system typu otwartego i dlatego musi zawierać rozległe infrastruktury do mapowania typów zdefiniowanych przez użytkownika. Opracowywanie złożonego dostawcy wymaga znacznej ilości wysiłku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.IQueryable%601>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 <xref:System.Linq.Enumerable>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
