---
title: Omówienie LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: de49febdc81eaf4f487423c5804d1e5cc897cdce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794968"
---
# <a name="linq-to-dataset-overview"></a>Omówienie LINQ to DataSet
<xref:System.Data.DataSet> Jest jednym z powszechnie używanych składników programu ADO.NET. Jest to kluczowy element modelu programowania rozłączonego, na którym bazuje ADO.NET, i umożliwia jawne buforowanie danych z różnych źródeł danych. W przypadku warstwy <xref:System.Data.DataSet> prezentacji jest ściśle zintegrowana z kontrolkami graficznego interfejsu użytkownika w celu powiązania danych. W przypadku warstwy środkowej zapewnia ona pamięć podręczną, która zachowuje relacyjny kształt danych i obejmuje szybkie proste usługi nawigacji w postaci zapytań i hierarchii. Typową techniką używaną do obniżyć liczbę żądań w bazie danych jest użycie <xref:System.Data.DataSet> do buforowania w warstwie środkowej. Rozważmy na przykład aplikację sieci Web ASP.NET opartej na danych. Często znacząca część danych aplikacji nie zmienia się często i jest wspólna dla sesji lub użytkowników. Te dane mogą być przechowywane w pamięci na serwerze sieci Web, co zmniejsza liczbę żądań względem bazy danych i przyspiesza Interakcje użytkownika. Innym przydatnym aspektem <xref:System.Data.DataSet> jest to, że umożliwia aplikacji przenoszenie podzbiorów danych z jednego lub większej liczby źródeł danych do obszaru aplikacji. Następnie aplikacja może manipulować danymi w pamięci przy zachowaniu jej kształtu relacyjnego.  
  
 Pomimo wyeksponowanie <xref:System.Data.DataSet> ma ograniczone możliwości zapytań. Metoda może służyć do filtrowania i sortowania, <xref:System.Data.DataRow.GetChildRows%2A> a metody i <xref:System.Data.DataRow.GetParentRow%2A> mogą być używane do nawigacji w hierarchii. <xref:System.Data.DataTable.Select%2A> Niemniej jednak, Deweloper musi napisać zapytanie niestandardowe. Może to spowodować, że aplikacje działają nieprawidłowo i są trudne do utrzymania.  
  
 LINQ to DataSet ułatwia i przyspiesza wykonywanie zapytań dotyczących danych w pamięci podręcznej <xref:System.Data.DataSet> w obiekcie. Zapytania te są wyrażane w języku programowania, a nie jako literały ciągu osadzone w kodzie aplikacji. Oznacza to, że deweloperzy nie muszą uczyć się oddzielnego języka zapytań. Ponadto LINQ to DataSet umożliwia deweloperom programu Visual Studio wydajniejszą pracę, ponieważ środowisko IDE programu Visual Studio zapewnia sprawdzanie składni w czasie kompilacji, statyczne pisanie i obsługę technologii IntelliSense dla [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. LINQ to DataSet można również użyć do wykonywania zapytań dotyczących danych, które zostały skonsolidowane z co najmniej jednego źródła danych. Dzięki temu wiele scenariuszy, które wymagają elastyczności, w jaki sposób dane są reprezentowane i obsługiwane. W szczególności, ogólne raporty, analizy i aplikacje analizy biznesowej wymagają tej metody manipulowania.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Wykonywanie zapytania dotyczącego zestawów danych przy użyciu LINQ to DataSet  
 Zanim zaczniesz wykonywać zapytania <xref:System.Data.DataSet> względem obiektu za pomocą LINQ to DataSet, musisz <xref:System.Data.DataSet>wypełnić element. Istnieje kilka sposobów ładowania danych do programu <xref:System.Data.DataSet>, na przykład <xref:System.Data.Common.DataAdapter> przy użyciu klasy lub [LINQ to SQL](./sql/linq/index.md). Po załadowaniu danych do <xref:System.Data.DataSet> obiektu można rozpocząć wykonywanie zapytania do niego. Formułowanie zapytań przy użyciu LINQ to DataSet jest podobne do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] użycia z [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]innymi źródłami danych. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]zapytania można wykonywać w odniesieniu do pojedynczych <xref:System.Data.DataSet> tabel w lub względem więcej niż jednej tabeli przy <xref:System.Linq.Enumerable.Join%2A> użyciu <xref:System.Linq.Enumerable.GroupJoin%2A> i standardowych operatorów zapytań.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]zapytania są obsługiwane zarówno w przypadku <xref:System.Data.DataSet> obiektów typu, jak i typów. Jeśli schemat <xref:System.Data.DataSet> programu jest znany w czasie projektowania aplikacji, zalecany jest typ <xref:System.Data.DataSet> . W określonym typie <xref:System.Data.DataSet>tabele i wiersze mają typy elementów członkowskich dla każdej z kolumn, co sprawia, że zapytania są prostsze i bardziej czytelne.  
  
 Oprócz standardowych operatorów zapytań zaimplementowanych w programie System. Core. dll, LINQ to DataSet dodaje kilka <xref:System.Data.DataSet>rozszerzeń, które ułatwiają wykonywanie zapytań dotyczących <xref:System.Data.DataRow> zestawu obiektów. Te <xref:System.Data.DataSet>rozszerzenia obejmują operatory do porównywania sekwencji wierszy, a także metod, które zapewniają dostęp do wartości <xref:System.Data.DataRow>kolumn.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Aplikacje N-warstwowe i LINQ to DataSet  
 Wielowarstwowe aplikacje danych to aplikacje zorientowane na dane, które są rozdzielone na wiele warstw logicznych (lub warstw). Typowa aplikacja N-warstwowa zawiera warstwę prezentacji, warstwę środkową i warstwę danych. Rozdzielanie składników aplikacji w oddzielne warstwy ułatwia konserwację i zwiększa skalowalność aplikacji. Aby uzyskać więcej informacji na temat aplikacji N-warstwowych danych, zobacz [Work with datasetss in aplikacje N-warstwowe](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 W aplikacjach <xref:System.Data.DataSet> N-warstwowych jest często używana w warstwie środkowej do buforowania informacji dla aplikacji sieci Web. Funkcje wykonywania zapytań LINQ to DataSet są implementowane za pomocą metod rozszerzających i rozszerza istniejące ADO.NET <xref:System.Data.DataSet>2,0.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytania do zestawów danych](querying-datasets-linq-to-dataset.md)
- [Language-Integrated Query (LINQ) —C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
