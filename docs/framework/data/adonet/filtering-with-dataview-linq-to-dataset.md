---
title: Filtrowanie za pomocą widoku danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 426e8c43f0ff8af94ab56230cf002637f351cd75
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634862"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrowanie za pomocą widoku danych (LINQ to DataSet)
Możliwość filtrowania danych przy użyciu określonych kryteriów, a następnie prezentowania danych do klienta za pośrednictwem kontrolki interfejsu użytkownika jest ważnym aspektem powiązania danych. <xref:System.Data.DataView> oferuje kilka sposobów filtrowania danych i zwracania podzbiorów wierszy danych spełniających kryteria filtru. Oprócz funkcji filtrowania opartych na ciągach <xref:System.Data.DataView> zapewnia także możliwość używania wyrażeń LINQ dla kryteriów filtrowania. Wyrażenia LINQ umożliwiają wykonywanie bardziej złożonych i zaawansowanych operacji filtrowania niż filtrowanie oparte na ciągach.  
  
 Istnieją dwa sposoby filtrowania danych przy użyciu <xref:System.Data.DataView>:  
  
- Utwórz <xref:System.Data.DataView> z zapytania LINQ to DataSet z klauzulą WHERE.  
  
- Użyj istniejących funkcji filtrowania opartych na ciągach <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Tworzenie elementu DataView z zapytania z informacjami o filtrowaniu  
 Obiekt <xref:System.Data.DataView> można utworzyć na podstawie zapytania LINQ to DataSetowego. Jeśli zapytanie zawiera klauzulę `Where`, <xref:System.Data.DataView> jest tworzony z informacjami o filtrowaniu z zapytania. Wyrażenie w klauzuli `Where` służy do określenia, które wiersze danych zostaną uwzględnione w <xref:System.Data.DataView>, i jest podstawą filtru.  
  
 Filtry oparte na wyrażeniach oferują bardziej zaawansowane i złożone filtrowanie niż prostsze filtry oparte na ciągach. Filtry oparte na ciągach i wyrażeniach wykluczają się wzajemnie. Gdy <xref:System.Data.DataView.RowFilter%2A> oparty na ciągach jest ustawiony po utworzeniu <xref:System.Data.DataView> na podstawie zapytania, filtr oparty na wyrażeniach wnioskowany na podstawie zapytania jest wyczyszczony.  
  
> [!NOTE]
> W większości przypadków wyrażenia używane do filtrowania nie powinny mieć efektów ubocznych i muszą być deterministyczne. Ponadto wyrażenia nie powinny zawierać żadnych logiki, które są zależne od ustawionej liczby wykonań, ponieważ operacje filtrowania mogą być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytania tabeli SalesOrderDetail są wysyłane w przypadku zamówień o ilości większej niż 2 i mniejszej niż 6; tworzy <xref:System.Data.DataView> z tego zapytania; i wiąże <xref:System.Data.DataView> z <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania dla zamówień złożonych po 6 czerwca 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Przykład  
 Filtrowanie może być również łączone z sortowaniem. Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania dla kontaktów, których nazwisko zaczyna się od "S" i posortowane według nazwiska, a następnie imię:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie jest używany algorytm SoundEx do znajdowania kontaktów, których nazwisko jest podobne do "Zhu". Algorytm SoundEx jest implementowany w metodzie SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx jest algorytmem fonetycznym używanym do indeksowania nazw przez dźwięk, ponieważ są one wymawiane w języku angielskim, pierwotnie opracowane przez Biuro spisu USA. Metoda SoundEx zwraca 4-znakowy kod dla nazwy składającej się z litery angielskiej, a trzy cyfry. Litera jest pierwszą literą nazwy i numery, które kodują pozostałe spółgłoski w nazwie. Podobne nazwy dźwiękowe mają ten sam kod SoundEx. Implementacja SoundEx użyta w metodzie SoundEx poprzedniego przykładu jest pokazana tutaj:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Używanie właściwości RowFilter  
 Istniejące funkcje filtrowania opartego na ciągach <xref:System.Data.DataView> nadal działają w kontekście LINQ to DataSet. Aby uzyskać więcej informacji na temat filtrowania <xref:System.Data.DataView.RowFilter%2A> opartego na ciągach, zobacz [Sortowanie i filtrowanie danych](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli kontaktowej, a następnie ustawia właściwość <xref:System.Data.DataView.RowFilter%2A>, aby zwracała wiersze, w których nazwisko kontaktu ma wartość "Zhu":  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po utworzeniu <xref:System.Data.DataView> z kwerendy <xref:System.Data.DataTable> lub LINQ to DataSet można użyć właściwości <xref:System.Data.DataView.RowFilter%2A>, aby określić podzestawy wierszy na podstawie ich wartości kolumn. Filtry oparte na ciągach i wyrażeniach wykluczają się wzajemnie. Ustawienie właściwości <xref:System.Data.DataView.RowFilter%2A> spowoduje wyczyszczenie wyrażenia filtru wywnioskowanego z kwerendy LINQ to DataSet i nie można zresetować wyrażenia filtru.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Jeśli chcesz zwrócić wyniki konkretnego zapytania dotyczącego danych, w przeciwieństwie do udostępnienia dynamicznego widoku podzbioru danych, możesz użyć metod <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> <xref:System.Data.DataView>zamiast ustawić właściwość <xref:System.Data.DataView.RowFilter%2A>. Właściwość <xref:System.Data.DataView.RowFilter%2A> najlepiej jest używana w aplikacji powiązanej z danymi, gdzie kontrolka powiązania wyświetla filtrowane wyniki. Ustawienie właściwości <xref:System.Data.DataView.RowFilter%2A> powoduje odbudowanie indeksu dla danych, dodanie obciążenia do aplikacji i zmniejszenie wydajności. Metody <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> używają bieżącego indeksu bez konieczności ponownego kompilowania indeksu. Jeśli chcesz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, należy użyć istniejącej <xref:System.Data.DataView>. Aby wywoływać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wiele razy, należy utworzyć nowy <xref:System.Data.DataView> w celu odbudowania indeksu w kolumnie, która ma być wyszukiwana, a następnie wywołać metody <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A>. Aby uzyskać więcej informacji na temat metod <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> zobacz [Znajdowanie wierszy](./dataset-datatable-dataview/finding-rows.md) i [wydajności widoku](dataview-performance.md)danych.  
  
## <a name="clearing-the-filter"></a>Czyszczenie filtru  
 Filtr na <xref:System.Data.DataView> może zostać wyczyszczony po ustawieniu filtrowania przy użyciu właściwości <xref:System.Data.DataView.RowFilter%2A>. Filtr na <xref:System.Data.DataView> można wyczyścić na dwa różne sposoby:  
  
- Ustaw <xref:System.Data.DataView.RowFilter%2A> właściwość `null`.  
  
- Ustaw właściwość <xref:System.Data.DataView.RowFilter%2A> na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> na podstawie zapytania, a następnie czyści Właściwość Filter według ustawienia <xref:System.Data.DataView.RowFilter%2A>, aby `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli ustawia właściwość <xref:System.Data.DataView.RowFilter%2A>, a następnie czyści filtr, ustawiając właściwość <xref:System.Data.DataView.RowFilter%2A> na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Sortowanie za pomocą widoku danych.](sorting-with-dataview-linq-to-dataset.md)
