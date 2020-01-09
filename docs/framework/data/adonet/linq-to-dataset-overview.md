---
title: Omówienie LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 20d9be052ba2567c16718b4b1c1019427c9b5df1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634823"
---
# <a name="linq-to-dataset-overview"></a>Omówienie LINQ to DataSet
<xref:System.Data.DataSet> jest jednym z powszechnie używanych składników ADO.NET. Jest to kluczowy element modelu programowania rozłączonego, na którym bazuje ADO.NET, i umożliwia jawne buforowanie danych z różnych źródeł danych. W przypadku warstwy prezentacji <xref:System.Data.DataSet> jest ściśle zintegrowana z kontrolkami graficznego interfejsu użytkownika w celu powiązania danych. W przypadku warstwy środkowej zapewnia ona pamięć podręczną, która zachowuje relacyjny kształt danych i obejmuje szybkie proste usługi nawigacji w postaci zapytań i hierarchii. Częstą techniką używaną do obniżyć liczbę żądań w bazie danych jest użycie <xref:System.Data.DataSet> do buforowania w warstwie środkowej. Rozważmy na przykład aplikację sieci Web ASP.NET opartej na danych. Często znacząca część danych aplikacji nie zmienia się często i jest wspólna dla sesji lub użytkowników. Te dane mogą być przechowywane w pamięci na serwerze sieci Web, co zmniejsza liczbę żądań względem bazy danych i przyspiesza Interakcje użytkownika. Innym przydatnym aspektem <xref:System.Data.DataSet> jest umożliwienie aplikacji przenoszenia podzbiorów danych z jednego lub większej liczby źródeł danych do obszaru aplikacji. Następnie aplikacja może manipulować danymi w pamięci przy zachowaniu jej kształtu relacyjnego.  
  
 Pomimo jej wyeksponowanie <xref:System.Data.DataSet> ma ograniczone możliwości zapytań. Metoda <xref:System.Data.DataTable.Select%2A> może służyć do filtrowania i sortowania, a metody <xref:System.Data.DataRow.GetChildRows%2A> i <xref:System.Data.DataRow.GetParentRow%2A> mogą służyć do nawigacji w hierarchii. Niemniej jednak, Deweloper musi napisać zapytanie niestandardowe. Może to spowodować, że aplikacje działają nieprawidłowo i są trudne do utrzymania.  
  
 LINQ to DataSet ułatwia i przyspiesza wykonywanie zapytań dotyczących danych w pamięci podręcznej w obiekcie <xref:System.Data.DataSet>. Zapytania te są wyrażane w języku programowania, a nie jako literały ciągu osadzone w kodzie aplikacji. Oznacza to, że deweloperzy nie muszą uczyć się oddzielnego języka zapytań. Ponadto LINQ to DataSet umożliwia deweloperom programu Visual Studio wydajniejszą pracę, ponieważ środowisko IDE programu Visual Studio zapewnia sprawdzanie składni w czasie kompilacji, statyczne pisanie i obsługę technologii IntelliSense dla LINQ. LINQ to DataSet można również użyć do wykonywania zapytań dotyczących danych, które zostały skonsolidowane z co najmniej jednego źródła danych. Dzięki temu wiele scenariuszy, które wymagają elastyczności, w jaki sposób dane są reprezentowane i obsługiwane. W szczególności, ogólne raporty, analizy i aplikacje analizy biznesowej wymagają tej metody manipulowania.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Wykonywanie zapytania dotyczącego zestawów danych przy użyciu LINQ to DataSet  
 Zanim zaczniesz wykonywać zapytania dotyczące obiektu <xref:System.Data.DataSet> przy użyciu LINQ to DataSet, musisz wypełnić <xref:System.Data.DataSet>. Istnieje kilka sposobów ładowania danych do <xref:System.Data.DataSet>, na przykład przy użyciu klasy <xref:System.Data.Common.DataAdapter> lub [LINQ to SQL](./sql/linq/index.md). Po załadowaniu danych do obiektu <xref:System.Data.DataSet> można rozpocząć wykonywanie zapytania do niego. Formułowanie zapytań przy użyciu LINQ to DataSet jest podobne do korzystania z funkcji Query-Integrated Language (LINQ) dla innych źródeł danych obsługujących LINQ. Zapytania LINQ można wykonywać w odniesieniu do pojedynczych tabel w <xref:System.Data.DataSet> lub dla więcej niż jednej tabeli przy użyciu standardowych operatorów zapytań <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>.  
  
 Zapytania LINQ są obsługiwane w przypadku obiektów <xref:System.Data.DataSet> typów i nienależących do typu. Jeśli schemat <xref:System.Data.DataSet> jest znany w czasie projektowania aplikacji, zaleca się <xref:System.Data.DataSet> z określonym typem. W przypadku wpisanej <xref:System.Data.DataSet>tabele i wiersze mają typy Członkowskie dla każdej z kolumn, co sprawia, że zapytania są prostsze i bardziej czytelne.  
  
 Oprócz standardowych operatorów zapytań zaimplementowanych w System. Core. dll, LINQ to DataSet dodaje kilka rozszerzeń specyficznych dla <xref:System.Data.DataSet>, które ułatwiają zapytania dotyczące zestawu <xref:System.Data.DataRow> obiektów. Te rozszerzenia specyficzne dla <xref:System.Data.DataSet>obejmują operatory porównujące sekwencje wierszy, a także metody zapewniające dostęp do wartości kolumn <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Aplikacje N-warstwowe i LINQ to DataSet  
 Wielowarstwowe aplikacje danych to aplikacje zorientowane na dane, które są rozdzielone na wiele warstw logicznych (lub warstw). Typowa aplikacja N-warstwowa zawiera warstwę prezentacji, warstwę środkową i warstwę danych. Rozdzielanie składników aplikacji w oddzielne warstwy ułatwia konserwację i zwiększa skalowalność aplikacji. Aby uzyskać więcej informacji na temat aplikacji N-warstwowych danych, zobacz [Work with datasetss in aplikacje N-warstwowe](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 W aplikacjach N-warstwowych <xref:System.Data.DataSet> jest często używana w warstwie środkowej do buforowania informacji dla aplikacji sieci Web. Funkcje wykonywania zapytań LINQ to DataSet są implementowane za pomocą metod rozszerzających i rozszerza istniejące <xref:System.Data.DataSet>ADO.NET 2,0.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytania do zestawów danych](querying-datasets-linq-to-dataset.md)
- [Language-Integrated Query (LINQ) —C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
