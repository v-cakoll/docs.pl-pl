---
title: Włączanie źródła danych dla LINQ Querying2
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: f705db90f4838479621117bd9303f5a374d33d4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676500"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Włączanie źródła danych do zapytań LINQ

Istnieją różne sposoby rozszerzania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] umożliwiające dowolnego źródła danych można wykonać zapytania w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wzorca. Źródłem danych może być między innymi struktura danych, usługi sieci Web, system plików lub baza danych. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Wzorzec ułatwia klientom badanie źródła danych, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań jest włączony, ponieważ składnia i wzorzec kwerendy nie zmienia się. W ten sposób [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] można rozszerzyć do tych danych źródeł obejmują następujące elementy:

-   Implementowanie <xref:System.Collections.Generic.IEnumerable%601> interfejsu w typie, aby umożliwić [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] badanie obiektów tego typu.

-   Tworzenie metod operatorów standardowej kwerendy takich jak <xref:System.Linq.Enumerable.Where%2A> i <xref:System.Linq.Enumerable.Select%2A> rozszerzających typu, aby umożliwić niestandardowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] tego typu.

-   Tworzenie dostawcy dla źródła danych, który implementuje <xref:System.Linq.IQueryable%601> interfejsu. Dostawca, który implementuje ten interfejs otrzymuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy w postaci drzew wyrażeń, które może wykonać w niestandardowy sposób, na przykład zdalnie.

-   Tworzenie dostawcy dla źródła danych, który wykorzystuje istniejące [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologii. Taki dostawcy umożliwiłby nie tylko badanie, ale także wstawianie, aktualizowanie i usuwanie, a także mapowanie dla typów zdefiniowanych przez użytkownika.

W tym temacie omówiono te opcje.

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak włączyć wykonywanie zapytań LINQ w odniesieniu do źródła danych

### <a name="in-memory-data"></a>Dane w pamięci
 Istnieją dwa sposoby, aby umożliwić [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przesyłanie zapytań dotyczących danych w pamięci. Jeśli dane są typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, możesz tworzyć zapytania dotyczące danych za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów. Jeśli go nie ma sensu Włączanie wyliczania tego typu przez zaimplementowanie <xref:System.Collections.Generic.IEnumerable%601> interfejsu, można zdefiniować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowe metody operatora w tego typu zapytania lub Utwórz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metod standardowych operatorów zapytań, które rozszerzają typu. Niestandardowe implementacje standardowych operatorów kwerendy powinny stosować odroczone wykonania w celu zwracania wyników.

### <a name="remote-data"></a>Dane zdalne
 Najlepsza opcja włączania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przesyłanie zapytań dotyczących zdalnego źródła danych jest zaimplementowanie <xref:System.Linq.IQueryable%601> interfejsu. Jednak to różni się od rozszerzania dostawcy, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dla źródła danych. Żadne modele dostawcy rozszerzania istniejących [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologii, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]do innych typów źródła danych są dostępne w programie Visual Studio 2008.

## <a name="iqueryable-linq-providers"></a>Dostawy IQueryable LINQ
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy, które implementują <xref:System.Linq.IQueryable%601> mogą się znacznie zmieniać w swojej złożoności. W tej sekcji omówiono różne poziomy złożoności.

 Mniej skomplikowany `IQueryable` dostawca może współpracować z jednej metody usługi sieci Web. Ten typ dostawcy jest bardzo specyficzny, ponieważ oczekuje określonych informacji w kwerendach, które obsługuje. Posiada system zamkniętego typu, być może podając pojedynczy typ wyniku. Większość wykonanie zapytania występuje lokalnie, na przykład za pomocą <xref:System.Linq.Enumerable> implementacje standardowych operatorów zapytań. Mniej skomplikowany dostawca może zbadać tylko jedną metodę wyrażenie wywołania w drzewie wyrażeń, które reprezentuje zapytanie i pozwala, aby pozostała logiki kwerendy była obsługiwana gdzie indziej.

 `IQueryable` Dostawca średniej złożoności może docelowe źródło danych, który ma częściowo wyrażeniowy język zapytań. Jeśli jest przeznaczona do usługi sieci Web, może współpracować z więcej niż jedną metodą usługi sieci Web i wybierać metodę do wywołania na podstawie pytania stawianego przez kwerendę. Dostawca średniej złożoności będzie miał bogatszy system typów niż prosty dostawca, ale nadal będzie to system stałych typów. Na przykład dostawca może ujawnić typy, które mają relacje jeden do wielu. Te typy można przemierzać, ale nie zapewnia to technologii mapowania dla typów zdefiniowanych przez użytkownika.

 Złożony `IQueryable` dostawcy, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dostawcy, może tłumaczyć kompletne [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażeniowy język zapytań, takich jak SQL. Złożony dostawca jest bardziej ogólny niż dostawca mniej skomplikowany, ponieważ może obsługiwać szerszą gamy pytań w kwerendzie. Ma także system typu otwartego i dlatego musi zawierać rozległe infrastruktury do mapowania typów zdefiniowanych przez użytkownika. Opracowywanie złożonego dostawcy wymaga znacznej ilości wysiłku.

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)