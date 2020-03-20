---
title: Zagadnienia LINQ (Usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 6c0cd7dcebb46b5408079848862ef4da1bb7f0a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174670"
---
# <a name="linq-considerations-wcf-data-services"></a>Zagadnienia LINQ (Usługi danych WCF)
Ten temat zawiera informacje o sposobie, w jaki zapytania LINQ są tworzone i wykonywane podczas korzystania z klienta WCF Data Services i ograniczenia przy użyciu LINQ do kwerendy usługi danych, która implementuje Open Data Protocol (OData). Aby uzyskać więcej informacji na temat redagowania i wykonywania kwerend względem usługi danych opartej na danych OData, zobacz [Kwerenda usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Tworzenie zapytań LINQ  
 LINQ umożliwia tworzenie kwerend względem kolekcji obiektów, które <xref:System.Collections.Generic.IEnumerable%601>implementuje . Zarówno okno dialogowe **Dodawanie odwołania do usługi** w programie Visual Studio, jak i narzędzie DataSvcUtil.exe są używane <xref:System.Data.Services.Client.DataServiceContext>do generowania reprezentacji usługi OData jako klasy kontenera jednostki, która dziedziczy po , a także obiektów, które reprezentują jednostki zwracane w źródłach danych. Narzędzia te również generować właściwości w klasie kontenera jednostki dla kolekcji, które są udostępniane jako źródła danych przez usługę. Każda z tych właściwości klasy, która hermetyzuje <xref:System.Data.Services.Client.DataServiceQuery%601>usługę danych zwraca . Ponieważ <xref:System.Data.Services.Client.DataServiceQuery%601> klasa implementuje <xref:System.Linq.IQueryable%601> interfejs zdefiniowany przez LINQ, można skomponować kwerendę LINQ względem kanałów informacyjnych udostępniane przez usługę danych, które są tłumaczone przez bibliotekę klienta do identyfikatora URI żądania kwerendy, który jest wysyłany do usługi danych podczas wykonywania.  
  
> [!IMPORTANT]
> Zestaw zapytań wyrażonych w składni LINQ jest szerszy niż te włączone w składni identyfikatora URI, który jest używany przez usługi danych OData. A <xref:System.NotSupportedException> jest wywoływana, gdy kwerenda nie może być mapowana do identyfikatora URI w docelowej usłudze danych. Aby uzyskać więcej informacji, zobacz [nieobsługiwanych metod LINQ](linq-considerations-wcf-data-services.md#unsupportedMethods) w tym temacie.  
  
 Poniższy przykład jest linq `Orders` kwerendy, która zwraca, które mają koszt frachtu więcej niż $30 i sortuje wyniki według daty wysyłki, począwszy od najpóźniejszej daty wysyłki:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 Ta kwerenda LINQ jest tłumaczona na następujący identyfikator URI kwerendy, który jest wykonywany w usłudze szybkiego startu opartej na usłudze [szybkiego startu](quickstart-wcf-data-services.md) northwind:  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Aby uzyskać bardziej ogólne informacje na temat LINQ, zobacz [Zapytanie zintegrowane z językiem (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) lub [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ umożliwia tworzenie kwerend przy użyciu zarówno składni kwerendy deklaratywnej specyficzne dla języka, pokazane w poprzednim przykładzie, jak również zestaw metod kwerendy, znany jako operatory zapytań standardowych. Kwerenda równoważna poprzedniemu przykładowi może być skomponowana przy użyciu tylko składni opartej na metodzie, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 Klient usług danych WCF jest w stanie przetłumaczyć oba rodzaje złożonych zapytań na identyfikator URI kwerendy i można rozszerzyć kwerendę LINQ, dołączając metody kwerendy do wyrażenia kwerendy. Podczas redagowania zapytań LINQ przez dołączanie składni metody do <xref:System.Data.Services.Client.DataServiceQuery%601>wyrażenia kwerendy lub , operacje są dodawane do identyfikatora URI kwerendy w kolejności, w jakiej metody są wywoływane. Jest to równoważne <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> wywołanie metody, aby dodać każdą opcję kwerendy do identyfikatora URI kwerendy.  
  
## <a name="executing-linq-queries"></a>Wykonywanie zapytań LINQ  
 Niektóre metody kwerendy LINQ, takie jak <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, po dołączeniu do kwerendy, powodują wykonanie kwerendy. Kwerenda jest również wykonywana, gdy wyniki są wyliczane niejawnie, na przykład podczas `foreach` pętli lub gdy kwerenda jest przypisana `List` do kolekcji. Aby uzyskać więcej informacji, zobacz [Kwerenda usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 Klient wykonuje kwerendę LINQ w dwóch częściach. W miarę możliwości wyrażenia LINQ w kwerendzie są najpierw oceniane na kliencie, a następnie kwerenda oparta na identyfikatorze URI jest generowana i wysyłana do usługi danych w celu oceny danych w usłudze. Aby uzyskać więcej informacji, zobacz sekcję [Wykonywanie klient a serwer](querying-the-data-service-wcf-data-services.md#executingQueries) w sekcji [Kwerenda usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 Jeśli kwerendy LINQ nie można przetłumaczyć w identyfikatorze URI kwerendy zgodnej z OData, wyjątek jest wywoływany podczas próby wykonania. Aby uzyskać więcej informacji, zobacz [Kwerenda usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Przykłady zapytań LINQ  
 Przykłady w poniższych sekcjach pokazują rodzaje zapytań LINQ, które mogą być wykonywane względem usługi OData.  
  
<a name="filtering"></a>
### <a name="filtering"></a>Filtrowanie  
 Przykłady kwerendy LINQ w tej sekcji filtrują dane w kanale informacyjnym zwróconym przez usługę.  
  
 Poniższe przykłady są równoważne kwerendy, które filtrują zwracane `Orders` jednostki, tak aby zwracane są tylko zamówienia o koszcie frachtu większym niż 30 USD:  
  
- Korzystanie ze składni kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- Korzystanie z metod kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- Opcja ciągu `$filter` zapytania identyfikatora URI:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 Wszystkie poprzednie przykłady są tłumaczone na identyfikator `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`URI kwerendy: .  
  
<a name="sorting"></a>
### <a name="sorting"></a>Sortowanie  
 Poniższe przykłady przedstawiają równoważne kwerendy sortujące zwrócone dane zarówno według nazwy firmy, jak i według kodu pocztowego, malejąco:  
  
- Korzystanie ze składni kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- Korzystanie z metod kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- Opcja ciągu `$orderby` zapytania identyfikatora URI):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 Wszystkie poprzednie przykłady są tłumaczone na identyfikator `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`URI kwerendy: .  
  
<a name="projection"></a>
### <a name="projection"></a>Projekcja  
 Poniższe przykłady pokazują równoważne zapytania, które `CustomerAddress` projekt zwrócił dane do węższego typu:  
  
- Korzystanie ze składni kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- Korzystanie z metod kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> Nie `$select` można dodać opcji kwerendy do identyfikatora URI kwerendy przy użyciu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Zaleca się użycie metody <xref:System.Linq.Enumerable.Select%2A> LINQ, aby klient `$select` wygenerował opcję kwerendy w identyfikatorze URI żądania.  
  
 Oba poprzednie przykłady są tłumaczone na identyfikator `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`URI kwerendy: .  
  
<a name="paging"></a>
### <a name="client-paging"></a>Stronicowanie klienta  
 Poniższe przykłady przedstawiają równoważne kwerendy, które żądają strony jednostek sortowanych zamówień, która zawiera 25 zamówień, pomijając pierwsze 50 zamówień:  
  
- Stosowanie metod kwerendy do kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- Ciąg `$skip` i `$top` opcje zapytania URI):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 Oba poprzednie przykłady są tłumaczone na identyfikator `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`URI kwerendy: .  
  
<a name="expand"></a>
### <a name="expand"></a>Rozwiń  
 Podczas kwerendy usługi danych OData, można zażądać, aby jednostki związane z jednostką, do której skierowana jest kwerenda, zostały uwzględnione zwrócony kanał informacyjny. Metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> jest wywoływana <xref:System.Data.Services.Client.DataServiceQuery%601> dla zestawu jednostek, na które odnosi się kwerenda `path` LINQ, z nazwą zestawu jednostek pokrewne podana jako parametr. Aby uzyskać więcej informacji, zobacz [Ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).  
  
 Poniższe przykłady pokazują równoważne <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> sposoby użycia metody w kwerendzie:  
  
- W składni kwerendy LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- W metodach zapytań LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 Oba poprzednie przykłady są tłumaczone na identyfikator `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`URI kwerendy: .  
  
<a name="unsupportedMethods"></a>
## <a name="unsupported-linq-methods"></a>Nieobsługiwanych metod LINQ  
 Poniższa tabela zawiera klasy metod LINQ nie są obsługiwane i nie mogą być uwzględnione w kwerendzie wykonywanej dla usługi OData:  
  
|Typ operacji|Metoda nieobsługiwała|  
|--------------------|------------------------|  
|Ustawianie operatorów|Wszystkie operatory zestawu nie są <xref:System.Data.Services.Client.DataServiceQuery%601>obsługiwane względem , który obejmował następujące elementy:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Operatorzy zamawiania|Następujące operatory zamawiania, które wymagają, <xref:System.Collections.Generic.IComparer%601> nie <xref:System.Data.Services.Client.DataServiceQuery%601>są obsługiwane względem:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Operatory projekcji i filtrowania|Następujące operatory rzutowania i filtrowania, które akceptują argument <xref:System.Data.Services.Client.DataServiceQuery%601>pozycyjny, nie są obsługiwane względem:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Operatorzy grupowania|Wszystkie operatory grupowania nie są <xref:System.Data.Services.Client.DataServiceQuery%601>obsługiwane względem , w tym:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Operacje grupowania muszą być wykonywane na kliencie.|  
|Operatorzy agregatów|Wszystkie operacje agregowane nie są <xref:System.Data.Services.Client.DataServiceQuery%601>obsługiwane względem , w tym:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Operacje agregacji muszą być wykonywane na kliencie lub być hermetyzowane przez operację usługi.|  
|Operatory stronicowania|Następujące operatory stronicowania nie <xref:System.Data.Services.Client.DataServiceQuery%601>są obsługiwane względem:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/>**Uwaga:**  Operatory stronicowania, które są wykonywane w pustej sekwencji zwracają wartość null.|  
|Inni operatorzy|Następujące podmioty nie są również <xref:System.Data.Services.Client.DataServiceQuery%601>obsługiwane w stosunku do:<br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>
## <a name="supported-expression-functions"></a>Obsługiwane funkcje ekspresji  
 Następujące metody i właściwości środowiska wykonawczego języka wspólnego (CLR) są obsługiwane, ponieważ można je przetłumaczyć w wyrażeniu zapytania w celu włączenia do identyfikatora URI żądania do usługi OData:  
  
|<xref:System.String>Członkowskich|Obsługiwana funkcja OData|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime>Członek<sup>1</sup>|Obsługiwana funkcja OData|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1.</sup> Obsługiwane są również właściwości <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> daty <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> i godziny i metody w języku Visual Basic.  
  
|<xref:System.Math>Członkowskich|Obsługiwana funkcja OData|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Członkowskich|Obsługiwana funkcja OData|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient może również być w stanie ocenić dodatkowe funkcje CLR na kliencie. A <xref:System.NotSupportedException> jest wywoływana dla dowolnego wyrażenia, które nie mogą być oceniane na kliencie i nie można przetłumaczyć na prawidłowy identyfikator URI żądania do oceny na serwerze.  
  
## <a name="see-also"></a>Zobacz też

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
- [Projekcje zapytania](query-projections-wcf-data-services.md)
- [Materializacja obiektu](object-materialization-wcf-data-services.md)
- [OData: Konwencje identyfikatora URI](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
