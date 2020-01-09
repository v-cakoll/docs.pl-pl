---
title: Sortowanie za pomocą widoku danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 2998de7dee34f9b5410bfe53988e0b7cfa797784
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634758"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Sortowanie za pomocą widoku danych (LINQ to DataSet)
Możliwość sortowania danych na podstawie określonych kryteriów, a następnie prezentowania danych do klienta za pośrednictwem kontrolki interfejsu użytkownika jest ważnym aspektem powiązania danych. <xref:System.Data.DataView> oferuje kilka sposobów sortowania danych i zwracania wierszy danych uporządkowanych według określonych kryteriów określania kolejności. Oprócz funkcji sortowania opartych na ciągach, <xref:System.Data.DataView> umożliwia także użycie wyrażeń języka LINQ (Integrated Language) dla kryteriów sortowania. Wyrażenia LINQ umożliwiają znacznie bardziej skomplikowane i zaawansowane operacje sortowania niż sortowanie oparte na ciągach. W tym temacie opisano oba podejścia do sortowania przy użyciu <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Tworzenie elementu DataView z zapytania z informacjami o sortowaniu  
 Obiekt <xref:System.Data.DataView> można utworzyć na podstawie zapytania LINQ to DataSetowego. Jeśli zapytanie zawiera klauzulę <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>lub <xref:System.Linq.Enumerable.ThenByDescending%2A>, wyrażenia w tych klauzulach są używane jako podstawa sortowania danych w <xref:System.Data.DataView>. Na przykład, jeśli zapytanie zawiera klauzule `Order By…`i `Then By…`, wyniki <xref:System.Data.DataView> spowodują uporządkowanie danych według obydwu określonych kolumn.  
  
 Sortowanie oparte na wyrażeniach oferuje bardziej zaawansowane i złożone sortowanie niż prostsze sortowanie oparte na ciągach. Należy zauważyć, że sortowanie oparte na ciągach i wyrażeniach wykluczają się wzajemnie. Jeśli <xref:System.Data.DataView.Sort%2A> oparty na ciągach jest ustawiony po utworzeniu <xref:System.Data.DataView> na podstawie zapytania, filtr oparty na wyrażeniach wnioskowany na podstawie zapytania jest wyczyszczony i nie można go zresetować.  
  
 Indeks <xref:System.Data.DataView> jest kompilowany zarówno podczas tworzenia <xref:System.Data.DataView>, jak i w przypadku modyfikacji informacji o sortowaniu lub filtrowaniu. Najlepszą wydajność uzyskuje się, dostarczając kryteria sortowania w kwerendzie LINQ to DataSet, z której utworzono <xref:System.Data.DataView>, a nie modyfikując informacji o sortowaniu w późniejszym czasie. Aby uzyskać więcej informacji, zobacz temat [wydajność widoku](dataview-performance.md)danych.  
  
> [!NOTE]
> W większości przypadków wyrażenia używane do sortowania nie powinny mieć efektów ubocznych i muszą być deterministyczne. Ponadto wyrażenia nie powinny zawierać żadnych logiki, które są zależne od ustawionej liczby wykonań, ponieważ operacje sortowania mogą być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do tabeli SalesOrderHeader i porządkuje zwracane wiersze według daty zamówienia; tworzy <xref:System.Data.DataView> z tego zapytania; i wiąże <xref:System.Data.DataView> z <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do tabeli SalesOrderHeader i porządkuje zwrócony wiersz według łącznej kwoty należnej; tworzy <xref:System.Data.DataView> z tego zapytania; i wiąże <xref:System.Data.DataView> z <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do tabeli SalesOrderDetail i porządkuje zwrócone wiersze według liczby porządkowej, a następnie według identyfikatora zamówienia sprzedaży; tworzy <xref:System.Data.DataView> z tego zapytania; i wiąże <xref:System.Data.DataView> z <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Używanie właściwości sortowania opartej na ciągach  
 Funkcja sortowania oparta na ciągach <xref:System.Data.DataView> nadal współpracuje z LINQ to DataSet. Po utworzeniu <xref:System.Data.DataView> na podstawie zapytania LINQ to DataSet można użyć właściwości <xref:System.Data.DataView.Sort%2A>, aby ustawić sortowanie na <xref:System.Data.DataView>.  
  
 Funkcja sortowania oparta na ciągach i wyrażeniach wykluczają się wzajemnie. Ustawienie właściwości <xref:System.Data.DataView.Sort%2A> spowoduje wyczyszczenie sortowania opartego na wyrażeniach dziedziczone z zapytania, z którego utworzono <xref:System.Data.DataView>.  
  
 Aby uzyskać więcej informacji na temat filtrowania <xref:System.Data.DataView.Sort%2A> opartego na ciągach, zobacz [Sortowanie i filtrowanie danych](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tworzenie <xref:System.Data.DataView> z tabeli kontaktowej i sortowanie wierszy według nazwiska w kolejności malejącej, a następnie imię i nazwisko w kolejności rosnącej:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do tabeli Contact dla ostatnich nazw, które zaczynają się literą "S".  <xref:System.Data.DataView> jest tworzony na podstawie tego zapytania i powiązany z obiektem <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Czyszczenie sortowania  
 Informacje o sortowaniu <xref:System.Data.DataView> mogą zostać wyczyszczone po ustawieniu przy użyciu właściwości <xref:System.Data.DataView.Sort%2A>. Istnieją dwa sposoby czyszczenia informacji o sortowaniu w <xref:System.Data.DataView>:  
  
- Ustaw <xref:System.Data.DataView.Sort%2A> właściwość `null`.  
  
- Ustaw właściwość <xref:System.Data.DataView.Sort%2A> na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania i czyści sortowanie przez ustawienie właściwości <xref:System.Data.DataView.Sort%2A> na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli kontakt i ustawia właściwość <xref:System.Data.DataView.Sort%2A> do sortowania według nazwiska w kolejności malejącej. Informacje o sortowaniu są wyczyszczone przez ustawienie właściwości <xref:System.Data.DataView.Sort%2A> na `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Filtrowanie za pomocą widoku danych.](filtering-with-dataview-linq-to-dataset.md)
- [Sortowanie danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
