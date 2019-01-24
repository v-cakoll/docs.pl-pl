---
title: Wykonywanie zapytań usługi danych (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: da015fcd20745ef67831b7133242d66392f923e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620412"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Wykonywanie zapytań usługi danych (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka kliencka pozwala na wykonywanie zapytań względem usługi danych przy użyciu dobrze znanych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wzorców programowania, w tym za pomocą zapytanie o języku zintegrowanym (LINQ). Biblioteka klienta tłumaczy kwerendę, która jest zdefiniowana na komputerze klienckim jako wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> klasy do komunikatu żądania HTTP GET. Biblioteka odbiera komunikat odpowiedzi i przekształca je w wystąpieniach klas usługi danych klienta. Te klasy są śledzone przez <xref:System.Data.Services.Client.DataServiceContext> do której <xref:System.Data.Services.Client.DataServiceQuery%601> należy.  
  
## <a name="data-service-queries"></a>Zapytań usługi danych  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Klasa ogólna reprezentuje zapytanie, które zwraca kolekcję zero lub więcej wystąpień typu jednostki. Zapytania usługi danych należy zawsze do istniejącego kontekstu usługi danych. Ten kontekst obsługuje usługi identyfikator URI i metadanych informacje, które są wymagane do tworzenia i wykonywanie zapytania.  
  
 Kiedy używasz **Dodaj odwołanie do usługi** okno dialogowe, aby dodać usługę danych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-tworzony jest aplikację kliencką opartą na, klasę kontenera jednostki, który dziedziczy z <xref:System.Data.Services.Client.DataServiceContext> klasy. Ta klasa zawiera właściwości, które zwracają wpisane <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpień. Brak jednej właściwości dla każdego zestawu jednostek usługi ujawnia w danych. Właściwości te ułatwiają Utwórz wystąpienie obiektu wpisane <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
 Zapytanie jest wykonywane w następujących scenariuszach:  
  
-   Gdy wyniki są wyliczane niejawnie, takich jak:  
  
    -   Gdy właściwość <xref:System.Data.Services.Client.DataServiceContext> reprezentujący i zestawem jednostek wyliczenia, takich jak podczas `foreach` (C#) lub `For Each` pętli (Visual Basic).  
  
    -   Gdy zapytanie jest przypisany do `List` kolekcji.  
  
-   Gdy <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> jawnie wywoływana jest metoda.  
  
-   Gdy LINQ wykonywania — operator zapytań, takich jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Single%2A> jest wywoływana.  
  
 Następujące zapytanie, gdy jest wykonywany, zwraca wszystkie `Customers` jednostki w usłudze danych Northwind:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient obsługuje zapytania dla obiektów z późnym wiązaniem, na przykład przy użyciu *dynamiczne* wpisać C#. Jednak ze względu na wydajność powinna zawsze tworzą silnie typizowane zapytań względem usługi danych. <xref:System.Tuple> Typu i obiektów dynamicznych nie są obsługiwane przez klienta.  
  
## <a name="linq-queries"></a>Zapytania LINQ  
 Ponieważ <xref:System.Data.Services.Client.DataServiceQuery%601> klasy implementuje <xref:System.Linq.IQueryable%601> interfejs zdefiniowany przez LINQ, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta jest w stanie przekształcić zapytania LINQ w odniesieniu do zestawu danych dotyczących jednostki w identyfikator URI, który reprezentuje wyrażenie zapytania, oceniane pod kątem usługi danych zasób. Poniższy przykład to zapytanie LINQ, który jest odpowiednikiem poprzedniego <xref:System.Data.Services.Client.DataServiceQuery%601> zwracającego `Orders` , kosztują Fracht ponad 30 USD i zamówień wyniki według Fracht kosztów:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 To zapytanie LINQ są tłumaczone na następującej kwerendy identyfikatora URI, który jest wykonywany na podstawie Northwind [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) usługi danych:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  Zestaw zapytań można wyrazić przy użyciu składni LINQ jest szerszy niż włączone w (REST) representational state transfer-na podstawie składni identyfikatora URI, który jest używany przez usługi danych. Element <xref:System.NotSupportedException> jest wywoływane, gdy zapytanie nie może być mapowana do identyfikatora URI w docelowej usługi danych.  
  
 Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Dodawanie opcji zapytania  
 Obsługa zapytań usługi danych wszystkie zapytania opcje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zapewnia s. Należy wywołać <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodę, aby dołączyć opcje zapytania do <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Zwraca nowy <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia, który jest odpowiednikiem wartości oryginalnego zapytania zestaw opcji — ale z nową kwerendę. Następujące zapytanie po wykonaniu zwraca `Orders` , są filtrowane według `Freight` wartości i według `OrderID`malejąco:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 Możesz użyć `$orderby` zapytania możliwość zarówno w kolejności według i filtrowanie zapytania według jedną właściwość, jak w poniższym przykładzie, filtry i porządkuje zwracanego `Orders` obiektów na podstawie wartości z `Freight` właściwości:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 Możesz wywołać <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda pod rząd w celu utworzenia wyrażeń złożonych zapytań. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie opcji zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Opcje zapytania umożliwiają express składniki składni zapytania LINQ w inny sposób. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  `$select` Stosowanie opcji zapytania nie można dodać do zapytania identyfikatora URI za pomocą <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Firma Microsoft zaleca, aby używać programu LINQ <xref:System.Linq.Enumerable.Select%2A> metoda klienta Generowanie `$select` zapytania opcji w identyfikatorze URI żądania.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>Klient, a wykonanie serwera  
 Klient wykonuje zapytanie w dwóch częściach. Zawsze, gdy jest to możliwe, wyrażenia w zapytaniu najpierw są obliczane na komputerze klienckim, a następnie generowane i wysyłane do usługi danych w wersji ewaluacyjnej względem danych w usłudze zapytań w oparciu o identyfikatorze URI. Należy wziąć pod uwagę następujące zapytanie LINQ:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 W tym przykładzie wyrażenie `(basePrice – (basePrice * discount))` jest oceniany na komputerze klienckim. W związku z tym rzeczywisty identyfikator URI zapytania `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` wysyłanego do danych usługi zawiera już obliczona wartość dziesiętna `90` w klauzuli filtru. Inne części wyrażenie filtrowania, w tym wyrażeniu podciąg, są oceniane przez usługę danych. Wyrażeń, które są obliczane na kliencie postępuj zgodnie z wspólnego języka semantykę środowiska uruchomieniowego (języka wspólnego CLR), natomiast wyrażeń wysyłane do usługi danych zależą od implementacji usługi danych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu. Należy także pamiętać o scenariusze, w którym oddzielne oceny może spowodować nieoczekiwane wyniki, takie jak kiedy klient i usługa wykonania oceny na podstawie czasu w różnych strefach czasowych.  
  
## <a name="query-responses"></a>Odpowiedzi na kwerendy  
 Po wykonaniu <xref:System.Data.Services.Client.DataServiceQuery%601> zwraca <xref:System.Collections.Generic.IEnumerable%601> typu żądanej jednostki. Tego wyniku kwerendy mogą być rzutowane na <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektu, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 Wystąpień typu jednostki, które reprezentują jednostki w usłudze danych są tworzone na komputerze klienckim w procesie nazywanym materializacja obiektu. Aby uzyskać więcej informacji, zobacz [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601> zapewniać dostęp do wyników zapytania.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> Ma również następujące elementy członkowskie, które umożliwiają dostęp do dodatkowych informacji na temat wyniku zapytania:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> -pobiera błąd zgłoszony przez operację, jeśli dowolny wystąpił.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> -zawiera kolekcję nagłówków odpowiedzi HTTP skojarzone z odpowiedzi na zapytanie.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> -pobiera oryginalny <xref:System.Data.Services.Client.DataServiceQuery%601> wygenerowaną <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> -pobiera kod odpowiedzi HTTP dla odpowiedzi na zapytanie.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> -pobiera całkowita liczba jednostek w jednostce ustawiane podczas <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metoda została wywołana na <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> -Zwraca <xref:System.Data.Services.Client.DataServiceQueryContinuation> obiekt, który zawiera identyfikator URI następnej strony wyników.  
  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zwraca tylko dane, które są jawnie wybierane przez identyfikator URI zapytania. Umożliwia to jawnie załadować dodatkowe dane z usługi danych, gdy jest to konieczne. Żądanie jest wysyłane do usługi danych każdorazowo jawnie ładować dane z usługi danych. Dane, które mogą zostać jawnie załadowane obejmuje powiązanych jednostek, dane odpowiedzi stronicowane i strumieni danych binarnych.  
  
> [!NOTE]
>  Ponieważ usługa danych może zwrócić odpowiedź stronicowane, zalecane jest aplikacji użycie programowania wzorca do obsługi odpowiedzi usługi stronicowanych danych. Aby uzyskać więcej informacji, zobacz [ładowanie zawartości odroczone](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Ponadto można zmniejszyć ilość danych zwracanych przez zapytanie, określając, że niektóre właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, zobacz [projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Wprowadzenie liczba całkowita liczba jednostek w zestawie  
 W niektórych przypadkach warto wiedzieć, całkowita liczba jednostek w zestawie jednostek i nie tylko liczbę zwróconych przez zapytanie. Wywołaj <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metody <xref:System.Data.Services.Client.DataServiceQuery%601> na żądanie, że to łączna liczba jednostek w zestawie zostanie uwzględniona w wyniku zapytania. W tym przypadku <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> właściwości zwracanego <xref:System.Data.Services.Client.QueryOperationResponse%601> zwraca łączna liczba jednostek w zestawie.  
  
 Można również uzyskać łączna liczba jednostek w zestawie albo jako <xref:System.Int32> lub jako <xref:System.Int64> wartość przez wywołanie metody <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.LongCount%2A> metody odpowiednio. Jeśli te metody są wywoływane, <xref:System.Data.Services.Client.QueryOperationResponse%601> nie jest zwracana; jest zwracana wartość liczby. Aby uzyskać więcej informacji, zobacz [jak: Określenie liczby jednostek zwróconych przez zapytanie](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [Zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Instrukcje: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Instrukcje: Określenie liczby jednostek zwróconych przez zapytanie](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Instrukcje: Określanie poświadczeń klienta usługi danych żądania](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Instrukcje: Ustawianie nagłówków w żądaniu klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Instrukcje: Projekt wyników zapytania](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Zobacz także
- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
