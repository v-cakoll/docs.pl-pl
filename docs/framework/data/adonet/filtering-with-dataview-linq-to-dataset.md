---
title: Filtrowanie za pomocą widoku danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 9cbd3d52c0e751097a937fa8781171c8c2a0058f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795040"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrowanie za pomocą widoku danych (LINQ to DataSet)
Możliwość filtrowania danych przy użyciu określonych kryteriów, a następnie prezentowania danych do klienta za pośrednictwem kontrolki interfejsu użytkownika jest ważnym aspektem powiązania danych. <xref:System.Data.DataView>oferuje kilka sposobów filtrowania danych i zwracania podzbiorów wierszy danych spełniających kryteria filtru. Oprócz funkcji <xref:System.Data.DataView> filtrowania opartych na ciągach zapewnia również możliwość używania [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] wyrażeń dla kryteriów filtrowania. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]wyrażenia umożliwiają wykonywanie bardziej złożonych i zaawansowanych operacji filtrowania niż filtrowanie oparte na ciągach.  
  
 Istnieją dwa sposoby filtrowania danych przy użyciu <xref:System.Data.DataView>:  
  
- <xref:System.Data.DataView> Utwórz z kwerendy LINQ to DataSetej z klauzulą WHERE.  
  
- Użyj istniejących funkcji <xref:System.Data.DataView>filtrowania opartych na ciągach.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Tworzenie elementu DataView z zapytania z informacjami o filtrowaniu  
 <xref:System.Data.DataView> Obiekt można utworzyć na podstawie zapytania LINQ to DataSet. Jeśli zapytanie zawiera `Where` klauzulę <xref:System.Data.DataView> , jest tworzona z informacjami o filtrowaniu z zapytania. Wyrażenie w `Where` klauzuli służy do określenia <xref:System.Data.DataView>, które wiersze danych zostaną uwzględnione w, i jest podstawą filtru.  
  
 Filtry oparte na wyrażeniach oferują bardziej zaawansowane i złożone filtrowanie niż prostsze filtry oparte na ciągach. Filtry oparte na ciągach i wyrażeniach wykluczają się wzajemnie. Gdy parametr <xref:System.Data.DataView.RowFilter%2A> jest ustawiony <xref:System.Data.DataView> po utworzeniu na podstawie zapytania, filtr oparty na wyrażeniach wywnioskowany na podstawie zapytania jest czyszczony.  
  
> [!NOTE]
> W większości przypadków wyrażenia używane do filtrowania nie powinny mieć efektów ubocznych i muszą być deterministyczne. Ponadto wyrażenia nie powinny zawierać żadnych logiki, które są zależne od ustawionej liczby wykonań, ponieważ operacje filtrowania mogą być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytania tabeli SalesOrderDetail są wysyłane w przypadku zamówień o ilości większej niż 2 i mniejszej niż 6; tworzy z tego zapytania i wiąże <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>z: <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy na <xref:System.Data.DataView> podstawie zapytania o zamówienia złożone po 6 czerwca 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Przykład  
 Filtrowanie może być również łączone z sortowaniem. Poniższy przykład tworzy <xref:System.Data.DataView> zapytanie dla kontaktów, których nazwisko zaczyna się od "S" i posortowane według nazwiska, a następnie imię:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie jest używany algorytm SoundEx do znajdowania kontaktów, których nazwisko jest podobne do "Zhu". Algorytm SoundEx jest implementowany w metodzie SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx jest algorytmem fonetycznym używanym do indeksowania nazw przez dźwięk, ponieważ są one wymawiane w języku angielskim, pierwotnie opracowane przez stany USA Biuro spisu. Metoda SoundEx zwraca 4-znakowy kod dla nazwy składającej się z litery angielskiej, a trzy cyfry. Litera jest pierwszą literą nazwy i numery, które kodują pozostałe spółgłoski w nazwie. Podobne nazwy dźwiękowe mają ten sam kod SoundEx. Implementacja SoundEx użyta w metodzie SoundEx poprzedniego przykładu jest pokazana tutaj:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Używanie właściwości RowFilter  
 Istniejące funkcje <xref:System.Data.DataView> filtrowania oparte na ciągach nadal działają w kontekście LINQ to DataSet. Aby uzyskać więcej informacji o filtrowaniu <xref:System.Data.DataView.RowFilter%2A> opartym na ciągach, zobacz [Sortowanie i filtrowanie danych](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Contact, a następnie <xref:System.Data.DataView.RowFilter%2A> ustawia właściwość, aby zwracała wiersze, w których nazwisko kontaktu ma wartość "Zhu":  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po utworzeniu z kwerendy lub LINQ to DataSet, można użyć <xref:System.Data.DataView.RowFilter%2A> właściwości, aby określić podzestawy wierszy na podstawie ich wartości kolumn. <xref:System.Data.DataTable> <xref:System.Data.DataView> Filtry oparte na ciągach i wyrażeniach wykluczają się wzajemnie. <xref:System.Data.DataView.RowFilter%2A> Ustawienie właściwości spowoduje wyczyszczenie wyrażenia filtru wywnioskowanego z kwerendy LINQ to DataSet i wyrażenia filtru nie można zresetować.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Jeśli chcesz zwrócić wyniki konkretnego zapytania dotyczącego danych, w przeciwieństwie do udostępnienia dynamicznego widoku podzbioru danych, <xref:System.Data.DataView.Find%2A> możesz użyć metod <xref:System.Data.DataView>lub <xref:System.Data.DataView.FindRows%2A> zamiast ustawić <xref:System.Data.DataView.RowFilter%2A> właściwość. <xref:System.Data.DataView.RowFilter%2A> Właściwość najlepiej jest używana w aplikacji powiązanej z danymi, gdzie kontrolka powiązania Wyświetla przefiltrowane wyniki. <xref:System.Data.DataView.RowFilter%2A> Ustawienie właściwości powoduje odbudowanie indeksu dla danych, dodanie obciążenia do aplikacji i zmniejszenie wydajności. Metody <xref:System.Data.DataView.Find%2A> i<xref:System.Data.DataView.FindRows%2A> używają bieżącego indeksu bez konieczności ponownego kompilowania indeksu. Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, należy użyć istniejącej <xref:System.Data.DataView>. Jeśli chcesz <xref:System.Data.DataView.Find%2A> wywoływać lub <xref:System.Data.DataView> <xref:System.Data.DataView.FindRows%2A> wiele razy, należy utworzyć nową, aby ponownie skompilować indeks w kolumnie, w której ma zostać wyszukane, a następnie wywołać <xref:System.Data.DataView.Find%2A> metody lub <xref:System.Data.DataView.FindRows%2A> . Aby uzyskać więcej informacji o <xref:System.Data.DataView.Find%2A> metodach <xref:System.Data.DataView.FindRows%2A> i zobacz [Znajdowanie wierszy](./dataset-datatable-dataview/finding-rows.md) i [wydajności widoku](dataview-performance.md)danych.  
  
## <a name="clearing-the-filter"></a>Czyszczenie filtru  
 Filtr dla <xref:System.Data.DataView> można wyczyścić po ustawieniu filtrowania <xref:System.Data.DataView.RowFilter%2A> przy użyciu właściwości. Filtr na stronie <xref:System.Data.DataView> można wyczyścić na dwa różne sposoby:  
  
- Ustaw <xref:System.Data.DataView.RowFilter%2A> właściwość `null`.  
  
- <xref:System.Data.DataView.RowFilter%2A> Ustaw właściwość na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy na <xref:System.Data.DataView> podstawie zapytania, a następnie czyści Właściwość `null`Filter by Setting <xref:System.Data.DataView.RowFilter%2A> :  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli <xref:System.Data.DataView.RowFilter%2A> zestaw właściwości, a następnie czyści filtr przez ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Sortowanie za pomocą widoku danych.](sorting-with-dataview-linq-to-dataset.md)
