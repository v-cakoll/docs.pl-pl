---
title: Wykonywanie zapytania dotyczącego usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: 50dc56a3c4c87bf9ac197b127c036c41ac833a88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931123"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Wykonywanie zapytania dotyczącego usługi danych (Usługi danych programu WCF)

Biblioteka [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta umożliwia wykonywanie zapytań dotyczących usługi danych za pomocą znanych .NET Framework wzorców programistycznych, w tym przy użyciu języka Integrated Language Query (LINQ). Biblioteka klienta tłumaczy zapytanie, które jest zdefiniowane na kliencie jako wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601> klasy w komunikacie żądania HTTP GET. Biblioteka otrzymuje komunikat odpowiedzi i tłumaczy ją na wystąpienia klas usługi danych klienta. Te klasy są śledzone przez <xref:System.Data.Services.Client.DataServiceContext> , do <xref:System.Data.Services.Client.DataServiceQuery%601> których należy.

## <a name="data-service-queries"></a>Zapytania dotyczące usługi danych

Klasa <xref:System.Data.Services.Client.DataServiceQuery%601> generyczna reprezentuje zapytanie, które zwraca kolekcję składającą się z zero lub więcej wystąpień typu jednostki. Zapytanie usługi danych zawsze należy do istniejącego kontekstu usługi danych. Ten kontekst przechowuje informacje o identyfikatorze URI usługi i metadanych, które są wymagane do tworzenia i wykonywania zapytania.

W przypadku dodawania usługi danych do aplikacji klienckiej opartej na .NET Framework przy użyciu okna dialogowego **Dodaj odwołanie do usługi** zostanie utworzona Klasa kontenera jednostki, która dziedziczy z <xref:System.Data.Services.Client.DataServiceContext> klasy. Ta klasa zawiera właściwości, które zwracają <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia wpisane. Istnieje jedna właściwość dla każdego zestawu jednostek, który jest udostępniany przez usługę danych. Te właściwości ułatwiają tworzenie wystąpienia typu <xref:System.Data.Services.Client.DataServiceQuery%601>.

Zapytanie jest wykonywane w następujących scenariuszach:

- Gdy wyniki są wyliczane niejawnie, na przykład:

  - Gdy właściwość w <xref:System.Data.Services.Client.DataServiceContext> programie, która reprezentuje i zostanie wyliczona, `foreach` na przykład w pętli (C#) lub `For Each` (Visual Basic).

  - Po przypisaniu zapytania do `List` kolekcji.

- Gdy metoda <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> or jest jawnie wywoływana. <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A>

- Gdy operator wykonywania zapytania LINQ, taki jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Single%2A> jest wywoływany.

Następujące zapytanie, gdy jest wykonywane, zwraca wszystkie `Customers` jednostki w usłudze danych Northwind:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Aby uzyskać więcej informacji, zobacz [jak: Wykonaj zapytania](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)dotyczące usługi danych.

Klient obsługuje zapytania dotyczące obiektów z późnym wiązaniem, na przykład w przypadku użycia typu *dynamicznego* w C# [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Jednak ze względu na wydajność należy zawsze tworzyć zapytania o jednoznacznie określonym typie względem usługi danych. <xref:System.Tuple> Typ i obiekty dynamiczne nie są obsługiwane przez klienta.

## <a name="linq-queries"></a>Zapytania LINQ

Ponieważ klasa implementuje interfejs zdefiniowany przez LINQ, biblioteka klienckamożeprzetwarzaćzapytaniaLINQwzględemdanychzestawujednostekdoidentyfikatoraURI,któryreprezentujewyrażeniezapytania,którejestocenianewzględemusługidanych[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <xref:System.Linq.IQueryable%601> <xref:System.Data.Services.Client.DataServiceQuery%601> zasoby. Poniższy przykład to zapytanie LINQ, które jest równoważne poprzedniemu <xref:System.Data.Services.Client.DataServiceQuery%601> , które zwraca `Orders` , że koszt frachtu przekracza $30 i porządkuje wyniki według kosztu frachtu:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

To zapytanie LINQ jest tłumaczone na następujący identyfikator URI zapytania, który jest wykonywany względem usługi danych [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) opartego na bazie Northwind:

```
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> Zestaw zapytań można wyrazić elementu w składni LINQ jest szerszy niż te włączone w składni identyfikatorów URI opartych na reprezentacji stanu (REST), które są używane przez usługi danych. Występuje <xref:System.NotSupportedException> , gdy nie można zamapować zapytania na identyfikator URI w docelowej usłudze danych.

Aby uzyskać więcej informacji, zobacz temat zagadnienia dotyczące [LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Dodawanie opcji zapytania

Zapytania dotyczące usługi danych obsługują wszystkie opcje zapytania, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]które zapewnia. Wywoływana jest <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Metoda dołączania opcji zapytania <xref:System.Data.Services.Client.DataServiceQuery%601> do wystąpienia. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>Zwraca nowe <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienie, które jest równoważne z oryginalnym zapytaniem, ale z ustawioną nową opcją zapytania. Następujące zapytanie, gdy wykonywane, zwraca `Orders` , które są filtrowane `Freight` według `OrderID`wartości i uporządkowane według, malejąco:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

Można użyć `$orderby` opcji zapytania do porządkowania i filtrowania zapytania na podstawie pojedynczej właściwości, tak jak w poniższym przykładzie, który filtruje i porządkuje zwracane `Orders` obiekty na podstawie wartości `Freight` właściwości:

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

Można wywołać metodę po <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> kolei, aby skonstruować złożone wyrażenia zapytań. Aby uzyskać więcej informacji, zobacz [jak: Dodaj opcje zapytania do zapytania](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)usługi danych.

Opcje zapytania dają inny sposób na wyrażenie składników składni zapytania LINQ. Aby uzyskać więcej informacji, zobacz temat zagadnienia dotyczące [LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).

> [!NOTE]
> Nie można dodać opcji <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> zapytaniadoidentyfikatoraURIzapytaniaprzyużyciumetody.`$select` Zalecamy użycie metody LINQ <xref:System.Linq.Enumerable.Select%2A> , aby klient `$select` generował opcję zapytania w identyfikatorze URI żądania.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>Klient a wykonywanie serwera

Klient wykonuje zapytanie w dwóch częściach. W miarę możliwości wyrażenia w zapytaniu są najpierw oceniane na kliencie, a następnie generowane jest zapytanie oparte na identyfikatorze URI i wysyłane do usługi danych w celu oceny danych w usłudze. Weź pod uwagę następujące zapytanie LINQ:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

W tym przykładzie wyrażenie `(basePrice – (basePrice * discount))` jest oceniane na kliencie. W związku z tym rzeczywisty identyfikator URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` zapytania, który jest wysyłany do usługi danych, zawiera już obliczoną `90` wartość dziesiętną w klauzuli Filter. Pozostałe części wyrażenia filtrowania, w tym wyrażenie podciągu, są oceniane przez usługę danych. Wyrażenia, które są oceniane na kliencie, są zgodne z semantyką środowiska uruchomieniowego języka wspólnego (CLR), podczas gdy wyrażenia wysyłane do usługi danych korzystają z implementacji [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu usługi danych. Należy również wziąć pod uwagę scenariusze, w których ta oddzielna Ocena może spowodować nieoczekiwane wyniki, na przykład kiedy klient i usługa przeprowadzają oceny oparte na czasie w różnych strefach czasowych.

## <a name="query-responses"></a>Odpowiedzi na zapytania

Gdy wykonywane, <xref:System.Collections.Generic.IEnumerable%601> zwraca <xref:System.Data.Services.Client.DataServiceQuery%601> a dla żądanego typu jednostki. Ten wynik zapytania może być rzutowany do <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektu, jak w poniższym przykładzie:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Wystąpienia typu jednostki reprezentujące jednostki w usłudze danych są tworzone na kliencie przez proces o nazwie Object materializację. Aby uzyskać więcej informacji, zobacz [obiekt materializację](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Obiekt implementuje<xref:System.Collections.Generic.IEnumerable%601> , aby zapewnić dostęp do wyników zapytania.

<xref:System.Data.Services.Client.QueryOperationResponse%601> Ponadto ma następujących członków, którzy umożliwiają dostęp do dodatkowych informacji na temat wyniku zapytania:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A>-Pobiera błąd wygenerowany przez operację, jeśli wystąpił.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A>-zawiera kolekcję nagłówków odpowiedzi HTTP skojarzonych z odpowiedzią na zapytanie.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>-Pobiera oryginalną <xref:System.Data.Services.Client.DataServiceQuery%601> , wygenerowaną <xref:System.Data.Services.Client.QueryOperationResponse%601>przez.

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A>-Pobiera kod odpowiedzi HTTP dla odpowiedzi na zapytanie.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>-Pobiera łączną liczbę jednostek w zestawie jednostek, gdy <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> Metoda została wywołana <xref:System.Data.Services.Client.DataServiceQuery%601>w.

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>-zwraca <xref:System.Data.Services.Client.DataServiceQueryContinuation> obiekt, który zawiera identyfikator URI następnej strony wyników.

Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zwraca tylko dane, które są jawnie wybrane przez identyfikator URI zapytania. Dzięki temu można jawnie ładować dodatkowe dane z usługi danych, gdy jest to konieczne. Żądanie jest wysyłane do usługi danych przy każdym jawnie załadowaniu danych z usługi danych. Dane, które mogą zostać załadowane jawnie obejmują powiązane jednostki, stronicowane dane odpowiedzi i strumienie danych binarnych.

> [!NOTE]
> Ponieważ usługa danych może zwrócić stronicowaną odpowiedź, zalecamy, aby aplikacja korzystała ze wzorca programowania do obsługi odpowiedzi na stronicowaną usługę danych. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).

Ilość danych zwracanych przez zapytanie może być również zmniejszana przez określenie, że tylko niektóre właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, zobacz [projekcje zapytań](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Pobieranie liczby łącznej liczby jednostek w zestawie

W niektórych scenariuszach warto znać łączną liczbę jednostek w zestawie jednostek, a nie tylko liczbę zwróconą przez zapytanie. Wywołaj <xref:System.Data.Services.Client.DataServiceQuery%601> metodę w programie, aby zażądać, aby całkowita liczba jednostek w zestawie była uwzględniona w wyniku zapytania. <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> W takim przypadku <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> Właściwość <xref:System.Data.Services.Client.QueryOperationResponse%601> zwracanej wartości zwraca łączną liczbę jednostek w zestawie.

Możesz również uzyskać tylko całkowitą liczbę jednostek w zestawie <xref:System.Int32> jako lub <xref:System.Int64> jako wartość, wywołując <xref:System.Linq.Enumerable.Count%2A> odpowiednio metody lub <xref:System.Linq.Enumerable.LongCount%2A> . Gdy te metody są wywoływane, element <xref:System.Data.Services.Client.QueryOperationResponse%601> nie jest zwracany; zwracana jest tylko wartość Count. Aby uzyskać więcej informacji, zobacz [jak: Określ liczbę jednostek zwróconych przez zapytanie](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).

## <a name="in-this-section"></a>W tej sekcji

- [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

- [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)

- [Zagadnienia dotyczące LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [Instrukcje: Wykonaj zapytania dotyczące usługi danych](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [Instrukcje: Określanie liczby jednostek zwróconych przez zapytanie](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)

- [Instrukcje: Określ poświadczenia klienta dla żądania usługi danych](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)

- [Instrukcje: Ustawianie nagłówków w żądaniu klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [Instrukcje: Wyniki zapytania projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
