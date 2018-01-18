---
title: Filtrowanie z DataView (LINQ do DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f1eb878bcc38d8bbeed42638cc5ccda230f60f1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrowanie z DataView (LINQ do DataSet)
Filtrowanie danych przy użyciu określonych kryteriów, a następnie prezentować danych do klienta za pomocą formantu interfejsu użytkownika jest ważnym aspektem wiązania z danymi. <xref:System.Data.DataView>udostępnia kilka metod filtrowania danych i zwracanie podzbiorów danych wiersze spełniające kryteria określonego filtru. Oprócz podstawie ciąg możliwości filtrowania <xref:System.Data.DataView> udostępnia również możliwość używania [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] wyrażenia kryteria filtrowania. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]wyrażenia umożliwia bardziej złożone i zaawansowane operacje filtrowania niż filtrowanie oparte na ciągach.  
  
 Istnieją dwa sposoby filtrowanie danych przy użyciu <xref:System.Data.DataView>:  
  
-   Utwórz <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, w której klauzuli.  
  
-   Korzystanie z istniejących, na podstawie ciągu filtrowania możliwości <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Tworzenie widoku danych z zapytania o informacje filtrowania  
 A <xref:System.Data.DataView> można utworzyć obiektu z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Jeśli kwerenda zawiera `Where` klauzuli <xref:System.Data.DataView> jest tworzony przy użyciu filtrowania informacji z zapytania. Wyrażenie w `Where` jest używana do określenia wiersze danych, które mają być uwzględnieni w <xref:System.Data.DataView>, i jest podstawą dla filtru.  
  
 Filtry oparte na wyrażeniach oferuje bardziej zaawansowaną i złożone filtrowania niż prostsze filtry oparte na ciągach. Filtry oparte na ciągach i oparte na wyrażeniach wzajemnie się wykluczają. Po ciągu podstawie <xref:System.Data.DataView.RowFilter%2A> jest ustawiany po <xref:System.Data.DataView> jest tworzona na podstawie kwerendy, wyrażenie filtru na podstawie wywnioskować na podstawie zapytania jest wyczyszczone.  
  
> [!NOTE]
>  W większości przypadków wyrażenia używane do filtrowania nie powinny mieć efekty uboczne i musi być deterministyczny. Ponadto wyrażenia nie może zawierać dowolną logikę, która jest zależna od zestawu Liczba wykonań, ponieważ filtrowania operacje mogą być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład odpytuje tabelę Szczegóły zamówienia sprzedaży zamówień o liczbę większą od 2 do mniej niż 6; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania dla zleceń umieszczona po 6 czerwca 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Przykład  
 Filtrowanie można również łączyć z sortowania. Poniższy przykład tworzy <xref:System.Data.DataView> w wyniku zapytania kontaktów których ostatnia nazwa rozpoczyna się od "S" i posortowane według nazwisko, a następnie imię:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto algorytm SoundEx można znaleźć kontaktów, których nazwisko jest podobna do "Zhu". Algorytm SoundEx jest implementowany przez metodę SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx to fonetyczne algorytm używany do indeksowania nazw za pomocą dźwięku, ponieważ są one Wymowa w języku angielskim, przeznaczony głównie przez amerykański Biuro spisu. Metoda SoundEx zwraca kod czterech znaków dla nazwy składające się z litery angielskie następują trzy cyfry. Litera jest pierwszą literę nazwy i numery kodowania pozostałych Spółgłoski w nazwie. Podobne nazwy pomiarowe współużytkować ten sam kod SoundEx. Implementacja SoundEx używany w metodzie SoundEx w poprzednim przykładzie pokazano tutaj:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Za pomocą właściwości RowFilter  
 Istniejące na podstawie ciągu filtrowania funkcjonalność <xref:System.Data.DataView> nadal działa w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontekstu. Aby uzyskać więcej informacji na temat na podstawie ciągu <xref:System.Data.DataView.RowFilter%2A> filtrowania, zobacz [sortowanie i filtrowanie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z skontaktuj się z tabeli, a następnie ustawia <xref:System.Data.DataView.RowFilter%2A> zwracanie wszystkich wierszy, gdzie nazwisko osoby kontaktowej jest "Zhu" dla właściwości:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po <xref:System.Data.DataView> została utworzona na podstawie <xref:System.Data.DataTable> lub [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kwerendy, można użyć <xref:System.Data.DataView.RowFilter%2A> właściwości w celu określenia podzbiór wierszy na podstawie ich kolumny wartości. Filtry oparte na ciągach i oparte na wyrażeniach wzajemnie się wykluczają. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości usunie wyrażenie filtru wywnioskować na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytań i wyrażenia filtru nie może być resetowany.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Jeśli chcesz zwrócić wyników określonego zapytania na danych, w przeciwieństwie do zapewniające widoku dynamicznego podzbiór danych, można użyć <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, zamiast ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości. <xref:System.Data.DataView.RowFilter%2A> Właściwości najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki wyświetla filtrowane wyniki. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości odtwarza indeksu dla danych narzut dodawanie do swojej aplikacji i zmniejszenie wydajności. <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeksu, który ma zostać również przebudowany. Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, następnie należy użyć istniejącego <xref:System.Data.DataView>. Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wielokrotnie, należy utworzyć nowy <xref:System.Data.DataView> odbudować indeksu w kolumnie, aby wyszukać, a następnie wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody. Aby uzyskać więcej informacji na temat <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> Zobacz metody [znajdowanie wierszy](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) i [wydajności DataView](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Wyczyszczenie filtru  
 Filtr <xref:System.Data.DataView> można wyczyścić po filtrowanie przy użyciu <xref:System.Data.DataView.RowFilter%2A> właściwości. Filtr <xref:System.Data.DataView> można wyczyścić na dwa sposoby:  
  
-   Ustaw <xref:System.Data.DataView.RowFilter%2A> właściwości `null`.  
  
-   Ustaw <xref:System.Data.DataView.RowFilter%2A> właściwości na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> w wyniku zapytania, a następnie czyści przez ustawienie filtru <xref:System.Data.DataView.RowFilter%2A> właściwości `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli ustawia <xref:System.Data.DataView.RowFilter%2A> właściwości, a następnie czyści przez ustawienie filtru <xref:System.Data.DataView.RowFilter%2A> właściwości na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Sortowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
