---
title: Zapytanie usługi danych (usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: bcdeb4f9755f526827045a9cc63bc8bdad4b28d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="querying-the-data-service-wcf-data-services"></a>Zapytanie usługi danych (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta umożliwia wykonywanie zapytań względem usługi danych przy użyciu znanych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] programowania wzorce, jak również za pomocą języka zapytań zintegrowanym (LINQ). Biblioteka klienta tłumaczy kwerendę, która jest zdefiniowana na kliencie jako wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> klasy na komunikat żądania HTTP GET. Biblioteki odbiera komunikat odpowiedzi i przekształca ją w wystąpień klas usług danych klienta. Te klasy są śledzone przez <xref:System.Data.Services.Client.DataServiceContext> do którego <xref:System.Data.Services.Client.DataServiceQuery%601> należy.  
  
## <a name="data-service-queries"></a>Wysyła zapytanie do usługi danych  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Klasa ogólna reprezentuje kwerendę, która zwraca kolekcję zero lub więcej wystąpień typów jednostek. Zapytanie usługi danych zawsze należy do kontekstu usługi istniejących danych. Ten kontekst obsługuje usługi metadanych i identyfikator URI informacje wymagane do tworzenia i wykonać zapytanie.  
  
 Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego, aby dodać usługę danych do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-dziedziczący z tworzenia aplikacji opartych na klienta, klasę kontenera jednostek <xref:System.Data.Services.Client.DataServiceContext> klasy. Ta klasa zawiera właściwości, które zwracają maszynowy <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpień. Brak jednej właściwości dla każdego zestawu jednostek, usługa ujawnia danych. Te właściwości ułatwiają tworzenie wystąpienia typu <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
 Zapytanie jest wykonywane w następujących scenariuszach:  
  
-   Gdy wyniki są wyliczane niejawnie, takich jak:  
  
    -   Gdy właściwość <xref:System.Data.Services.Client.DataServiceContext> reprezentujący i zestawu jednostek jest wyliczyć, takich jak podczas `foreach` (C#) lub `For Each` pętli (Visual Basic).  
  
    -   Jeśli zapytanie jest przypisany do `List` kolekcji.  
  
-   Gdy <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> jawnie wywoływana jest metoda.  
  
-   Gdy LINQ wykonywania — operator zapytań, takich jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Single%2A> jest wywoływana.  
  
 Następujące zapytanie po jego wykonaniu zwraca wszystkie `Customers` obiekty usługi danych Northwind:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta obsługuje zapytania dla obiektów z późnym wiązaniem, na przykład przy użyciu *dynamiczne* typu w języku C#. Jednak ze względu na wydajność należy zawsze utworzyć jednoznacznie zapytań dotyczących usługi danych. <xref:System.Tuple> Typu i obiekty dynamiczne nie są obsługiwane przez klienta.  
  
## <a name="linq-queries"></a>Zapytania LINQ  
 Ponieważ <xref:System.Data.Services.Client.DataServiceQuery%601> klasa implementuje <xref:System.Linq.IQueryable%601> interfejs zdefiniowany przez składnik LINQ, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta jest w stanie przekształcania zapytań LINQ jednostki zestawu danych na identyfikator URI, który reprezentuje w wyrażeniu kwerendy ocenić pod kątem usługi danych zasób. Poniższy przykład jest zapytania LINQ, który jest odpowiednikiem poprzedniego <xref:System.Data.Services.Client.DataServiceQuery%601> zwracającą `Orders` zawierających koszt transport ponad 30 $ i zamówień wyniki przez transport koszt:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Ta kwerenda LINQ jest przekształcana na następujące zapytanie identyfikator URI, który jest wykonywany przed systemem Northwind [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) Usługa danych:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  Zestaw kwerendy można wyrazić w składni LINQ jest szerszy niż włączone w stanie representational transfer (REST) — na podstawie składni identyfikatora URI, który jest używany przez usługi danych. A <xref:System.NotSupportedException> jest wywoływane, gdy nie można zamapować zapytania do identyfikatora URI w usłudze danych docelowych.  
  
 Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Dodawanie opcje zapytania  
 Obsługa zapytań usługi danych wszystkie zapytania opcji [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zapewnia s. Należy wywołać <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodę, aby dołączyć opcje zapytania do <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Zwraca nowy <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia, który jest odpowiednikiem oryginalne zapytanie ale bez nowe zapytanie opcji set. Zwraca następujące zapytanie po wykonaniu `Orders` który są filtrowane według `Freight` wartości i uporządkowanych według `OrderID`, uporządkowanej malejąco:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 Można użyć `$orderby` opcji zarówno porządek zapytania i Filtruj zapytanie na podstawie jednej właściwości, jak w poniższym przykładzie, filtry i porządkuje zwróconego `Orders` obiektów na podstawie wartości z `Freight` właściwości:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 Możesz wywołać <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody kolejno w celu utworzenia wyrażenia złożonych zapytań. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie opcje zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Opcje zapytania umożliwiają express składniki składni zapytania LINQ w inny sposób. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  `$select` Opcji zapytania nie można dodać do zapytania identyfikatora URI przy użyciu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Zalecane jest użycie LINQ <xref:System.Linq.Enumerable.Select%2A> metody, aby klienci Generowanie `$select` opcji w identyfikatorze URI żądania zapytania.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>Klienta i serwera wykonywania  
 Klient wykonuje zapytanie w dwóch częściach. Jeśli to możliwe, wyrażenia w zapytaniu najpierw są obliczane na kliencie, a następnie wygenerować i wysyłane do usługi danych w wersji ewaluacyjnej w odniesieniu do danych w usłudze kwerendy na podstawie identyfikatora URI. Należy wziąć pod uwagę następujące kwerendy LINQ:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 W tym przykładzie wyrażenie `(basePrice – (basePrice * discount))` jest obliczane na kliencie. W związku z tym rzeczywisty identyfikator URI zapytania `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` wysyłanego do danych usługi zawiera już obliczona wartość dziesiętną `90` w klauzuli filtru. Inne części wyrażenie filtrowania, w tym wyrażeniu podciąg są oceniane przez usługę danych. Wyrażeń, które są oceniane na kliencie wykonaj wspólnej semantykę języka wspólnego (CLR), gdy wyrażenia wysyłane do usługi data zależne od implementacji usługi danych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu. Należy wziąć pod uwagę scenariusze, w których ocena oddzielne może spowodować nieoczekiwane wyniki, takie jak kiedy klient i usługa wykonać oceny na podstawie czasu w różnych strefach czasowych.  
  
## <a name="query-responses"></a>Odpowiedzi na kwerendy  
 Po wykonaniu <xref:System.Data.Services.Client.DataServiceQuery%601> zwraca <xref:System.Collections.Generic.IEnumerable%601> typu żądanej jednostki. Wynik tego zapytania mogą być rzutowane na <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektu, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 Wystąpień typu jednostki, które reprezentują obiekty usługi danych są tworzone na kliencie przez proces, nazywany materialization obiektu. Aby uzyskać więcej informacji, zobacz [Materialization obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601> do zapewniania dostępu do wyników zapytania.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> Ma również następujące elementy członkowskie, które umożliwiają dostęp do dodatkowych informacji dotyczących wyniku zapytania:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> -pobiera błąd zgłoszony przez operację, jeśli dowolne wystąpił.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> -zawiera kolekcję nagłówków odpowiedzi HTTP skojarzone z odpowiedzią zapytania.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> -pobiera oryginalny <xref:System.Data.Services.Client.DataServiceQuery%601> generowany <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> -pobiera kod odpowiedzi HTTP. odpowiedzi na kwerendę.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> -pobiera całkowitą liczbę jednostek w jednostce ustawiane podczas <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> wywołano metodę na <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> -Zwraca <xref:System.Data.Services.Client.DataServiceQueryContinuation> obiekt, który zawiera identyfikator URI następnej strony wyników.  
  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zwraca tylko dane, które jest w sposób jawny wybrany przez identyfikator URI zapytania. Zapewnia opcję, aby w sposób jawny załadować dodatkowe dane z usługi danych, gdy jest to potrzebne. Żądanie jest wysyłane do usługi danych zawsze jawnie ładować dane z usługi danych. Dane, które mogą być ładowane jawnie obejmuje powiązanych jednostek, dane odpowiedzi stronicowana i strumieni danych binarnych.  
  
> [!NOTE]
>  Ponieważ usługa danych może zwrócić stronicowanych odpowiedzi, zalecane jest aplikacji użycie programowania wzorzec do obsługi danych stronicowanych odpowiedzi usługi. Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Również można zmniejszyć ilość danych zwróconych przez kwerendę, określając, że niektóre właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, zobacz [projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Pobieranie liczby całkowitej liczby jednostek w zestawie  
 W niektórych scenariuszach warto dowiedzieć się, liczba jednostek w zestawie jednostek i nie tylko liczba zwróconych przez kwerendę. Wywołanie <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metoda <xref:System.Data.Services.Client.DataServiceQuery%601> na żądanie, że ta liczba jednostek w zestawie zostanie uwzględniona w wyniku zapytania. W takim przypadku <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> właściwości zwracana <xref:System.Data.Services.Client.QueryOperationResponse%601> zwraca liczbę jednostek w zestawie.  
  
 Można także uzyskać łączna liczba jednostek w zestawie albo jako <xref:System.Int32> lub jako <xref:System.Int64> wartość wywołując <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.LongCount%2A> metody odpowiednio. Wywołanego tych metod <xref:System.Data.Services.Client.QueryOperationResponse%601> nie są zwracane; zwracany jest tylko wartość licznika. Aby uzyskać więcej informacji, zobacz [porady: określić numer z jednostek zwróconych przez kwerendę](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [Zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Instrukcje: Wykonywanie zapytań usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Instrukcje: Określanie liczby jednostek zwróconych przez zapytanie](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Instrukcje: Określanie poświadczeń klienta dla żądania usługi danych](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Instrukcje: Ustawianie nagłówków w żądaniu klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Instrukcje: Projekt wyników zapytania](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
