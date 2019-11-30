---
title: Uwagi dotyczące LINQ (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 41f1d1f0ca04dff0faa9eb070882f845ef4827d2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568960"
---
# <a name="linq-considerations-wcf-data-services"></a>Uwagi dotyczące LINQ (Usługi danych programu WCF)
Ten temat zawiera informacje na temat sposobu tworzenia i wykonywania zapytań LINQ, gdy używasz klienta Usługi danych programu WCF i ograniczenia przy użyciu LINQ do wysyłania zapytań do usługi danych implementującej protokół Open Data Protocol (OData). Aby uzyskać więcej informacji o tworzeniu i wykonywaniu zapytań dotyczących usługi danych opartych na protokole OData, zobacz [wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Redagowanie zapytań LINQ  
 LINQ umożliwia tworzenie zapytań względem kolekcji obiektów, które implementują <xref:System.Collections.Generic.IEnumerable%601>. Zarówno okno dialogowe **Dodaj odwołanie do usługi** w programie Visual Studio, jak i Narzędzie DataSvcUtil. exe są używane do generowania reprezentacji usługi OData jako klasy kontenera jednostek, która dziedziczy po <xref:System.Data.Services.Client.DataServiceContext>, jak również obiektów, które reprezentują jednostki zwracane w źródłach danych. Narzędzia te generują również właściwości klasy kontenera jednostek dla kolekcji, które są udostępniane jako źródła danych przez usługę. Każda z tych właściwości klasy, która hermetyzuje usługę danych, zwraca <xref:System.Data.Services.Client.DataServiceQuery%601>. Ponieważ Klasa <xref:System.Data.Services.Client.DataServiceQuery%601> implementuje interfejs <xref:System.Linq.IQueryable%601> zdefiniowany przez LINQ, można utworzyć zapytanie LINQ względem kanałów ujawnianych przez usługę danych, które są tłumaczone przez bibliotekę kliencką na identyfikator URI żądania zapytania, który jest wysyłany do usługi danych podczas wykonywania.  
  
> [!IMPORTANT]
> Zestaw zapytań można wyrazić elementu w składni LINQ jest szerszy niż te włączone w składni identyfikatora URI, który jest używany przez usługi danych OData. <xref:System.NotSupportedException> jest zgłaszane, gdy nie można zamapować zapytania na identyfikator URI w docelowej usłudze danych. Aby uzyskać więcej informacji, zobacz [nieobsługiwane metody LINQ](linq-considerations-wcf-data-services.md#unsupportedMethods) w tym temacie.  
  
 Poniższy przykład to zapytanie LINQ, które zwraca `Orders`, które mają koszt frachtu większy niż $30 i sortuje wyniki według daty wysyłki, rozpoczynając od najnowszej daty wydania:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 To zapytanie LINQ jest tłumaczone na następujący identyfikator URI zapytania, który jest wykonywany względem usługi danych [szybkiego startu](quickstart-wcf-data-services.md) opartego na bazie Northwind:  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Aby uzyskać więcej ogólnych informacji na temat LINQ, zobacz [Language-Integrated Query (LINQ C# ) —](../../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ umożliwia tworzenie zapytań przy użyciu instrukcji zapytania deklaracyjnego specyficznego dla języka, pokazanego w poprzednim przykładzie, jak również zestawu metod zapytania znanych jako standardowe operatory zapytań. Równoważne zapytanie do poprzedniego przykładu może być złożone przy użyciu tylko składni opartej na metodzie, jak pokazano na poniższym przykładzie:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 Klient Usługi danych programu WCF może przetłumaczyć oba rodzaje złożonych zapytań na identyfikator URI zapytania i można ją rozłożyć, dołączając metody zapytania do wyrażenia zapytania. Podczas redagowania zapytań LINQ przez dołączenie składni metody do wyrażenia zapytania lub <xref:System.Data.Services.Client.DataServiceQuery%601>, operacje są dodawane do identyfikatora URI zapytania w kolejności, w której metody są wywoływane. Jest to równoznaczne z wywołaniem metody <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> w celu dodania każdej opcji zapytania do identyfikatora URI zapytania.  
  
## <a name="executing-linq-queries"></a>Wykonywanie zapytań LINQ  
 Niektóre metody zapytania LINQ, takie jak <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, po dołączeniu do zapytania, powodują wykonanie zapytania. Zapytanie jest również wykonywane, gdy wyniki są wyliczane niejawnie, na przykład w pętli `foreach` lub po przypisaniu zapytania do kolekcji `List`. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 Klient wykonuje zapytanie LINQ w dwóch częściach. Zawsze, gdy to możliwe, wyrażenia LINQ w zapytaniu są najpierw oceniane na kliencie, a następnie generowane jest zapytanie oparte na identyfikatorze URI i wysyłane do usługi danych w celu oceny danych w usłudze. Aby uzyskać więcej informacji, zapoznaj się z sekcją [klient i wykonanie serwera](querying-the-data-service-wcf-data-services.md#executingQueries) w temacie wykonywanie [zapytań do usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 Gdy zapytania LINQ nie można przetłumaczyć na identyfikator URI zapytania zgodnego z protokołem OData, wyjątek jest zgłaszany w przypadku próby wykonania. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Przykłady zapytań LINQ  
 Przykłady w poniższych sekcjach przedstawiają rodzaje zapytań LINQ, które mogą być wykonywane względem usługi OData.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrowanie  
 Przykłady zapytań LINQ w tej sekcji filtrują dane w kanale informacyjnym zwracanym przez usługę.  
  
 Poniższe przykłady są równoważnymi zapytaniami, które filtrują zwrócone jednostki `Orders`, dzięki czemu zwracane są tylko zamówienia o kosztach frachtu większym niż $30:  
  
- Przy użyciu składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]     
  
- Korzystanie z metod zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]       
  
- Ciąg zapytania identyfikatora URI `$filter` opcja:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Wszystkie poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Sortowanie  
 W poniższych przykładach pokazano równoważne zapytania, które sortują zwracane dane zarówno przez nazwę firmy, jak i kod pocztowy, malejąco:  
  
- Przy użyciu składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]        
  
- Korzystanie z metod zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]        
  
- Ciąg zapytania identyfikatora URI `$orderby` opcja):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Wszystkie poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Rzut  
 W poniższych przykładach pokazano równoważne zapytania, które program Project zwraca dane do wąskiego `CustomerAddress` typu:  
  
- Przy użyciu składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]         
  
- Korzystanie z metod zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]         

> [!NOTE]
> Opcji zapytania `$select` nie można dodać do identyfikatora URI zapytania przy użyciu metody <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. Zalecamy użycie metody LINQ <xref:System.Linq.Enumerable.Select%2A>, aby klient generował opcję kwerendy `$select` w identyfikatorze URI żądania.  
  
 Oba poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Stronicowanie klienta  
 W poniższych przykładach pokazano równoważne zapytania, które żądają strony posortowanych obiektów Order, które zawierają 25 zamówień, pomijając pierwsze 50 zamówień:  
  
- Stosowanie metod zapytania do zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]     
  
- Ciąg zapytania identyfikatora URI `$skip` i opcje `$top`):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Oba poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Rozwiń  
 Podczas wykonywania zapytania dotyczącego usługi danych OData można zażądać, aby jednostki powiązane z jednostką dodaną przez zapytanie były dołączone do zwróconego źródła danych. Metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> jest wywoływana na <xref:System.Data.Services.Client.DataServiceQuery%601> dla zestawu jednostek przeznaczonego dla zapytania LINQ, z pokrewną nazwą zestawu jednostek podaną jako parametr `path`. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).  
  
 W poniższych przykładach pokazano równoważne sposoby używania metody <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> w kwerendzie:  
  
- W składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- Z metodami zapytań LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]       

 Oba poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Nieobsługiwane metody LINQ  
 Poniższa tabela zawiera klasy metod LINQ, które nie są obsługiwane i nie mogą być uwzględniane w zapytaniach wykonywanych względem usługi OData:  
  
|Typ operacji|Nieobsługiwana Metoda|  
|--------------------|------------------------|  
|Ustaw operatory|Wszystkie operatory zestawów są nieobsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>, które obejmują następujące elementy:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Operatory porządkowania|Następujące operatory porządkowania, które wymagają <xref:System.Collections.Generic.IComparer%601> są nieobsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Operatory projekcji i filtrowania|Następujące operatory rzutowania i filtrowania, które akceptują argument pozycyjny, nie są obsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Operatory grupowania|Wszystkie operatory grupowania nie są obsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>, w tym następujących:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Na kliencie należy wykonać operacje grupowania.|  
|Operatory agregujące|Wszystkie operacje agregujące nie są obsługiwane w odniesieniu do <xref:System.Data.Services.Client.DataServiceQuery%601>, w tym następujących:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Operacje agregujące muszą być wykonywane na kliencie lub być hermetyzowane przez operację usługi.|  
|Operatory stronicowania|Następujące operatory stronicowania nie są obsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Uwaga:** operatory stronicowania wykonywane na pustej sekwencji zwracają wartość null.|  
|Inne operatory|Następujące inne operatory nie są obsługiwane w odniesieniu do <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1. <xref:System.Linq.Enumerable.Empty%2A><br />2. <xref:System.Linq.Enumerable.Range%2A><br />3. <xref:System.Linq.Enumerable.Repeat%2A><br />4. <xref:System.Linq.Enumerable.ToDictionary%2A><br />5. <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Obsługiwane funkcje wyrażeń  
 Obsługiwane są następujące metody i właściwości środowiska uruchomieniowego języka wspólnego (CLR), ponieważ mogą one być tłumaczone w wyrażeniu zapytania w celu uwzględnienia w identyfikatorze URI żądania do usługi OData:  
  
|<xref:System.String> składową|Obsługiwana funkcja OData|  
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
  
|<xref:System.DateTime> członek<sup>1</sup>|Obsługiwana funkcja OData|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup> Obsługiwane są również równoważne właściwości daty i godziny <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, a także Metoda <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> w Visual Basic.  
  
|<xref:System.Math> składową|Obsługiwana funkcja OData|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression> składową|Obsługiwana funkcja OData|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient może również mieć możliwość oszacowania dodatkowych funkcji CLR na kliencie. <xref:System.NotSupportedException> jest wywoływane dla dowolnego wyrażenia, które nie może być oceniane na kliencie i nie może zostać przetłumaczone na prawidłowy identyfikator URI żądania na potrzeby oceny na serwerze.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
- [Projekcje zapytania](query-projections-wcf-data-services.md)
- [Materializacja obiektu](object-materialization-wcf-data-services.md)
- [OData: konwencje URI](https://go.microsoft.com/fwlink/?LinkID=185564)
