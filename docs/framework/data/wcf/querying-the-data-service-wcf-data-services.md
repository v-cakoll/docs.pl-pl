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
ms.openlocfilehash: e37a1654bdc62937bbb27c293a110293c9928645
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975167"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Wykonywanie zapytania dotyczącego usługi danych (Usługi danych programu WCF)

Biblioteka klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umożliwia wykonywanie zapytań dotyczących usługi danych przy użyciu znanych .NET Framework wzorców programistycznych, w tym przy użyciu języka Integrated Language Query (LINQ). Biblioteka klienta tłumaczy zapytanie, które jest zdefiniowane na kliencie jako wystąpienie klasy <xref:System.Data.Services.Client.DataServiceQuery%601>, do komunikatu żądania HTTP GET. Biblioteka otrzymuje komunikat odpowiedzi i tłumaczy ją na wystąpienia klas usługi danych klienta. Te klasy są śledzone przez <xref:System.Data.Services.Client.DataServiceContext>, do których należy <xref:System.Data.Services.Client.DataServiceQuery%601>.

## <a name="data-service-queries"></a>Zapytania dotyczące usługi danych

Klasa ogólna <xref:System.Data.Services.Client.DataServiceQuery%601> reprezentuje zapytanie, które zwraca kolekcję składającą się z zero lub więcej wystąpień typu jednostki. Zapytanie usługi danych zawsze należy do istniejącego kontekstu usługi danych. Ten kontekst przechowuje informacje o identyfikatorze URI usługi i metadanych, które są wymagane do tworzenia i wykonywania zapytania.

W przypadku dodawania usługi danych do aplikacji klienckiej opartej na .NET Framework przy użyciu okna dialogowego **Dodaj odwołanie do usługi** zostanie utworzona Klasa kontenera jednostki, która dziedziczy z klasy <xref:System.Data.Services.Client.DataServiceContext>. Ta klasa zawiera właściwości, które zwracają <xref:System.Data.Services.Client.DataServiceQuery%601> wystąpienia o określonym typie. Istnieje jedna właściwość dla każdego zestawu jednostek, który jest udostępniany przez usługę danych. Te właściwości ułatwiają tworzenie wystąpienia o określonym <xref:System.Data.Services.Client.DataServiceQuery%601>.

Zapytanie jest wykonywane w następujących scenariuszach:

- Gdy wyniki są wyliczane niejawnie, na przykład:

  - Gdy właściwość <xref:System.Data.Services.Client.DataServiceContext>, która reprezentuje i zostanie wyliczona, na przykład w pętli `foreach` (C#) lub `For Each` (Visual Basic).

  - Po przypisaniu zapytania do kolekcji `List`.

- Gdy metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> jest jawnie wywoływana.

- Gdy jest wywoływany operator wykonywania zapytań LINQ, taki jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Single%2A>.

Następujące zapytanie, gdy jest wykonywane, zwraca wszystkie jednostki `Customers` w usłudze danych Northwind:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Aby uzyskać więcej informacji, zobacz [jak: wykonywać zapytania dotyczące usługi danych](how-to-execute-data-service-queries-wcf-data-services.md).

Klient [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje zapytania dotyczące obiektów z późnym wiązaniem, takich jak użycie typu *dynamicznego* w C#. Jednak ze względu na wydajność należy zawsze tworzyć zapytania o jednoznacznie określonym typie względem usługi danych. Typ <xref:System.Tuple> i obiekty dynamiczne nie są obsługiwane przez klienta.

## <a name="linq-queries"></a>Zapytania LINQ

Ponieważ Klasa <xref:System.Data.Services.Client.DataServiceQuery%601> implementuje interfejs <xref:System.Linq.IQueryable%601> zdefiniowany przez LINQ, Biblioteka klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] może przetwarzać zapytania LINQ względem danych zestawu jednostek w identyfikatorze URI, który reprezentuje wyrażenie zapytania, które jest oceniane względem zasobu usługi danych. Poniższy przykład to zapytanie LINQ, które jest równoważne poprzedniej <xref:System.Data.Services.Client.DataServiceQuery%601>, która zwraca `Orders`, które mają koszt frachtu większy niż $30, i porządkuje wyniki według kosztu frachtu:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

To zapytanie LINQ jest tłumaczone na następujący identyfikator URI zapytania, który jest wykonywany względem usługi danych [szybkiego startu](quickstart-wcf-data-services.md) opartego na bazie Northwind:

```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> Zestaw zapytań można wyrazić elementu w składni LINQ jest szerszy niż te włączone w składni identyfikatorów URI opartych na reprezentacji stanu (REST), które są używane przez usługi danych. <xref:System.NotSupportedException> jest zgłaszane, gdy nie można zamapować zapytania na identyfikator URI w docelowej usłudze danych.

Aby uzyskać więcej informacji, zobacz temat [zagadnienia dotyczące LINQ](linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Dodawanie opcji zapytania

Zapytania dotyczące usługi danych obsługują wszystkie opcje zapytania, które zapewnia [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s. Należy wywołać metodę <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>, aby dołączyć opcje zapytania do wystąpienia <xref:System.Data.Services.Client.DataServiceQuery%601>. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> zwraca nowe wystąpienie <xref:System.Data.Services.Client.DataServiceQuery%601>, które jest równoważne z oryginalnym zapytaniem, ale z ustawioną nową opcją zapytania. Następujące zapytanie, gdy wykonywane, zwraca `Orders`, które są filtrowane przez `Freight` wartość i uporządkowane według `OrderID`, malejąco:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

Opcji zapytania `$orderby` można użyć do porządkowania i filtrowania zapytania na podstawie pojedynczej właściwości, tak jak w poniższym przykładzie, który filtruje i porządkuje zwracane obiekty `Orders` na podstawie wartości właściwości `Freight`:

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

Można wywołać metodę <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> po kolei, aby skonstruować złożone wyrażenia zapytań. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie opcji zapytania do zapytania do usługi danych](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).

Opcje zapytania dają inny sposób na wyrażenie składników składni zapytania LINQ. Aby uzyskać więcej informacji, zobacz temat [zagadnienia dotyczące LINQ](linq-considerations-wcf-data-services.md).

> [!NOTE]
> Opcji zapytania `$select` nie można dodać do identyfikatora URI zapytania przy użyciu metody <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. Zalecamy użycie metody LINQ <xref:System.Linq.Enumerable.Select%2A>, aby klient generował opcję kwerendy `$select` w identyfikatorze URI żądania.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>Klient a wykonywanie serwera

Klient wykonuje zapytanie w dwóch częściach. W miarę możliwości wyrażenia w zapytaniu są najpierw oceniane na kliencie, a następnie generowane jest zapytanie oparte na identyfikatorze URI i wysyłane do usługi danych w celu oceny danych w usłudze. Weź pod uwagę następujące zapytanie LINQ:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

W tym przykładzie wyrażenie `(basePrice – (basePrice * discount))` jest oceniane na kliencie. W związku z tym rzeczywisty identyfikator URI zapytania `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)`, który jest wysyłany do usługi danych, zawiera już obliczoną wartość dziesiętną `90` w klauzuli Filter. Pozostałe części wyrażenia filtrowania, w tym wyrażenie podciągu, są oceniane przez usługę danych. Wyrażenia, które są oceniane na kliencie, są zgodne z semantyką środowiska uruchomieniowego języka wspólnego (CLR), podczas gdy wyrażenia wysyłane do usługi danych korzystają z implementacji protokołu OData. Należy również wziąć pod uwagę scenariusze, w których ta oddzielna Ocena może spowodować nieoczekiwane wyniki, na przykład kiedy klient i usługa przeprowadzają oceny oparte na czasie w różnych strefach czasowych.

## <a name="query-responses"></a>Odpowiedzi na zapytania

Podczas wykonywania <xref:System.Data.Services.Client.DataServiceQuery%601> zwraca <xref:System.Collections.Generic.IEnumerable%601> żądanego typu jednostki. Wynik zapytania można rzutować na obiekt <xref:System.Data.Services.Client.QueryOperationResponse%601>, jak w poniższym przykładzie:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Wystąpienia typu jednostki reprezentujące jednostki w usłudze danych są tworzone na kliencie przez proces o nazwie Object materializację. Aby uzyskać więcej informacji, zobacz [obiekt materializację](object-materialization-wcf-data-services.md). Obiekt <xref:System.Data.Services.Client.QueryOperationResponse%601> implementuje <xref:System.Collections.Generic.IEnumerable%601>, aby zapewnić dostęp do wyników zapytania.

<xref:System.Data.Services.Client.QueryOperationResponse%601> ma również następujące elementy członkowskie, które umożliwiają dostęp do dodatkowych informacji na temat wyniku zapytania:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A> — pobiera błąd wygenerowany przez operację, jeśli wystąpił.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A> — zawiera kolekcję nagłówków odpowiedzi HTTP skojarzonych z odpowiedzią na zapytanie.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> — pobiera oryginalny <xref:System.Data.Services.Client.DataServiceQuery%601>, który wygenerował <xref:System.Data.Services.Client.QueryOperationResponse%601>.

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> — Pobiera kod odpowiedzi HTTP dla odpowiedzi na zapytanie.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> — pobiera łączną liczbę jednostek w zestawie jednostek, gdy metoda <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> została wywołana w <xref:System.Data.Services.Client.DataServiceQuery%601>.

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> — zwraca obiekt <xref:System.Data.Services.Client.DataServiceQueryContinuation>, który zawiera identyfikator URI następnej strony wyników.

Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zwraca tylko dane, które są jawnie wybierane przez identyfikator URI zapytania. Dzięki temu można jawnie ładować dodatkowe dane z usługi danych, gdy jest to konieczne. Żądanie jest wysyłane do usługi danych przy każdym jawnie załadowaniu danych z usługi danych. Dane, które mogą zostać załadowane jawnie obejmują powiązane jednostki, stronicowane dane odpowiedzi i strumienie danych binarnych.

> [!NOTE]
> Ponieważ usługa danych może zwrócić stronicowaną odpowiedź, zalecamy, aby aplikacja korzystała ze wzorca programowania do obsługi odpowiedzi na stronicowaną usługę danych. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).

Ilość danych zwracanych przez zapytanie może być również zmniejszana przez określenie, że tylko niektóre właściwości jednostki są zwracane w odpowiedzi. Aby uzyskać więcej informacji, zobacz [projekcje zapytań](query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Pobieranie liczby łącznej liczby jednostek w zestawie

W niektórych scenariuszach warto znać łączną liczbę jednostek w zestawie jednostek, a nie tylko liczbę zwróconą przez zapytanie. Wywołaj metodę <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> na <xref:System.Data.Services.Client.DataServiceQuery%601>, aby zażądać, aby całkowita liczba jednostek w zestawie była uwzględniona w wyniku zapytania. W takim przypadku Właściwość <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> zwróconego <xref:System.Data.Services.Client.QueryOperationResponse%601> zwraca łączną liczbę jednostek w zestawie.

Możesz również uzyskać tylko łączną liczbę jednostek w zestawie jako <xref:System.Int32> lub jako wartość <xref:System.Int64>, wywołując odpowiednio metody <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.LongCount%2A>. Gdy te metody są wywoływane, <xref:System.Data.Services.Client.QueryOperationResponse%601> nie jest zwracany; zwracana jest tylko wartość Count. Aby uzyskać więcej informacji, zobacz [How to: Określanie liczby jednostek zwróconych przez zapytanie](number-of-entities-returned-by-a-query-wcf.md).

## <a name="in-this-section"></a>W tej sekcji

- [Projekcje zapytania](query-projections-wcf-data-services.md)

- [Materializacja obiektu](object-materialization-wcf-data-services.md)

- [Zagadnienia dotyczące LINQ](linq-considerations-wcf-data-services.md)

- [Instrukcje: Wykonywanie zapytań usługi danych](how-to-execute-data-service-queries-wcf-data-services.md)

- [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [Instrukcje: Określanie liczby jednostek zwróconych przez zapytanie](number-of-entities-returned-by-a-query-wcf.md)

- [Instrukcje: Określanie poświadczeń klienta dla żądania usługi danych](specify-client-creds-for-a-data-service-request-wcf.md)

- [Instrukcje: Ustawianie nagłówków w żądaniu klienta](how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [Instrukcje: Projekt wyników zapytania](how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
