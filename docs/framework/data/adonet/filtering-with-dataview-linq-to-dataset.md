---
title: Filtrowanie za pomocą widoku danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: b41b95ba06f031dc45c0267432d0d6afb7f3a7d9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645692"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrowanie za pomocą widoku danych (LINQ to DataSet)
Możliwość filtrowania danych przy użyciu określonych kryteriów, a następnie prezentować dane do klienta za pomocą kontrolki interfejsu użytkownika jest istotnym elementem powiązanie danych. <xref:System.Data.DataView> oferuje kilka sposobów, aby filtrować dane i zwracanie podzbiorów danych wiersze spełniające kryteria filtru określonego. Oprócz parametrów na podstawie funkcji filtrowania <xref:System.Data.DataView> udostępnia również możliwość używania [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] wyrażeń do kryteriów filtrowania. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] wyrażenia pozwalają znacznie bardziej złożone i zaawansowane operacje filtrowania niż filtrowania opartego na ciąg.  
  
 Istnieją dwa sposoby, aby odfiltrować dane przy użyciu <xref:System.Data.DataView>:  
  
- Tworzenie <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, w której klauzula.  
  
- Korzystając z istniejących, oparte na ciągach filtrowania możliwości <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Tworzenie widoku danych zapytania z informacjami filtrowania  
 A <xref:System.Data.DataView> obiektu można tworzyć na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Jeśli kwerenda zawiera `Where` klauzuli <xref:System.Data.DataView> są tworzone za pomocą filtrowania informacji z zapytania. Wyrażenie w `Where` jest używana do określenia, które wiersze danych, które zostaną uwzględnione w <xref:System.Data.DataView>, i jest podstawą dla filtru.  
  
 Filtry oparte na wyrażeniach oferują lepszą i bardziej złożone filtrowanie niż prostsze filtry oparte na ciąg. Filtry oparte na ciągach i oparte na wyrażeniach wzajemnie się wykluczają. Gdy opartego na ciągach <xref:System.Data.DataView.RowFilter%2A> jest ustawiany po <xref:System.Data.DataView> jest tworzona na podstawie zapytania, wyrażenie filtru zależności wywnioskowane z kwerendy jest wyczyszczone.  
  
> [!NOTE]
>  W większości przypadków wyrażenia używane do filtrowania nie powinny mieć skutki uboczne i musi być deterministyczna. Ponadto wyrażenia nie może zawierać dowolną logikę, która jest zależna od określona liczba wykonań, ponieważ operacje filtrowania może być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje kwerendę tabeli Szczegóły zamówienia sprzedaży zamówień o ilości większej niż 2 i mniej niż 6. Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania dla zamówienia umieszczone po 6 czerwca 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Przykład  
 Filtrowanie można również łączyć z sortowaniem. Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania o kontakty której ostatnia nazwa rozpoczyna się od "S" i posortowane według nazwiska, a następnie imię:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto algorytmu SoundEx, aby znaleźć kontaktów, których nazwisko jest podobny do "Zhu". Algorytm SoundEx jest implementowany przez metodę SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx jest fonetycznych algorytm indeksowania nazwy przez dźwięku, ponieważ są one Wymowa w języku angielskim, pierwotnie opracowana przez amerykański Biuro spisu. Metoda SoundEx zwraca kod Czteroznakowy nazwę składającą się z litery angielskiej następują trzy cyfry. Litera jest pierwszą literę nazwy i numery kodowanie pozostałe Spółgłoski w nazwie. Podobnych nazwach brzmiącą współużytkować ten sam kod SoundEx. Implementacja SoundEx używany w metodzie SoundEx poprzedniego przykładu, jest następujący:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Przy użyciu właściwości RowFilter  
 Istniejące oparte na ciągach filtrowania funkcjonalność <xref:System.Data.DataView> nadal działa w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontekstu. Aby uzyskać więcej informacji na temat oparte na ciągach <xref:System.Data.DataView.RowFilter%2A> filtrowania, zobacz [sortowanie i filtrowanie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Kontakt, a następnie ustawia <xref:System.Data.DataView.RowFilter%2A> właściwość zwraca wiersze, których nazwisko kontaktu jest "Zhu":  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po <xref:System.Data.DataView> została utworzona na podstawie <xref:System.Data.DataTable> lub [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, można użyć <xref:System.Data.DataView.RowFilter%2A> właściwości w celu określenia podzbiór wierszy na podstawie ich wartości w kolumnach. Filtry oparte na ciągach i oparte na wyrażeniach wzajemnie się wykluczają. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwość spowoduje wyczyszczenie wyrażenie filtru, na podstawie wywnioskować [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytań i wyrażenia filtru nie może być resetowany.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Jeśli mają być zwracane wyniki zapytania określonego na danych, w przeciwieństwie do realizacji dynamiczny widok podzbiór danych, można użyć <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, zamiast ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości. <xref:System.Data.DataView.RowFilter%2A> Właściwość najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki Wyświetla wyfiltrowanych wyników. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwość odbudowania indeksu dla danych, obciążenie dodawanie do aplikacji i zmniejszenie wydajności. <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeks odbudowany. Jeśli wywołanie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, użyj istniejącego <xref:System.Data.DataView>. Jeśli wywołanie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wielokrotnie, należy utworzyć nową <xref:System.Data.DataView> do odbudowania indeksu w kolumnie, aby wyszukać, a następnie wywołaj <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody. Aby uzyskać więcej informacji na temat <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> Zobacz metody [znajdowanie wierszy](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) i [wydajność widoku danych](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Trwa czyszczenie filtru  
 Filtr na <xref:System.Data.DataView> może być obsadzona po filtrowania została ustawiona za pomocą <xref:System.Data.DataView.RowFilter%2A> właściwości. Filtr na <xref:System.Data.DataView> można wyczyścić na dwa sposoby:  
  
- Ustaw <xref:System.Data.DataView.RowFilter%2A> właściwość `null`.  
  
- Ustaw <xref:System.Data.DataView.RowFilter%2A> właściwości na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> w wyniku zapytania i następnie czyści filtr, ustawiając <xref:System.Data.DataView.RowFilter%2A> właściwości `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli ustawia <xref:System.Data.DataView.RowFilter%2A> właściwości i następnie czyści filtr, ustawiając <xref:System.Data.DataView.RowFilter%2A> właściwości na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Sortowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
