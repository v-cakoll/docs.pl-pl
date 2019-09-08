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
ms.openlocfilehash: c0d2d1dac43dd178680adbc123d5ce4f88fc0cc0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779885"
---
# <a name="linq-considerations-wcf-data-services"></a>Uwagi dotyczące LINQ (Usługi danych programu WCF)
Ten temat zawiera informacje na temat sposobu tworzenia i wykonywania zapytań LINQ, gdy [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] używasz klienta i ograniczeń programu LINQ do wysyłania zapytań do usługi danych [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]implementującej. Aby uzyskać więcej informacji o redagowaniu i wykonywaniu zapytań [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]dotyczących usługi danych opartych na usłudze, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Redagowanie zapytań LINQ  
 LINQ umożliwia tworzenie zapytań względem kolekcji obiektów, które implementują <xref:System.Collections.Generic.IEnumerable%601>. Zarówno okno dialogowe **Dodaj odwołanie do usługi** w programie Visual Studio, jak i Narzędzie DataSvcUtil. exe są używane do generowania reprezentacji [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi jako klasy kontenera jednostek, która dziedziczy po <xref:System.Data.Services.Client.DataServiceContext>, a także obiektów, które reprezentują jednostki zwrócone w źródłach danych. Narzędzia te generują również właściwości klasy kontenera jednostek dla kolekcji, które są udostępniane jako źródła danych przez usługę. Każda z tych właściwości klasy, która hermetyzuje usługę danych, zwraca <xref:System.Data.Services.Client.DataServiceQuery%601>. <xref:System.Data.Services.Client.DataServiceQuery%601> Ponieważ Klasa<xref:System.Linq.IQueryable%601> implementuje interfejs zdefiniowany przez LINQ, można utworzyć zapytanie LINQ względem kanałów ujawnianych przez usługę danych, które są tłumaczone przez bibliotekę kliencką na identyfikator URI żądania zapytania, który jest wysyłany do usługi danych na działania.  
  
> [!IMPORTANT]
> Zestaw zapytań można wyrazić elementu w składni LINQ jest szerszy niż te włączone w składni identyfikatora URI, który jest używany przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi danych. Występuje <xref:System.NotSupportedException> , gdy nie można zamapować zapytania na identyfikator URI w docelowej usłudze danych. Aby uzyskać więcej informacji, zobacz [nieobsługiwane metody LINQ](linq-considerations-wcf-data-services.md#unsupportedMethods) w tym temacie.  
  
 Poniższy przykład to zapytanie LINQ zwracające wartość `Orders` kosztu frachtu o wartości większej niż $30 i sortuje wyniki według daty wysyłki, rozpoczynając od ostatniego dnia wysyłki:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 To zapytanie LINQ jest tłumaczone na następujący identyfikator URI zapytania, który jest wykonywany względem usługi danych [szybkiego startu](quickstart-wcf-data-services.md) opartego na bazie Northwind:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Aby uzyskać więcej ogólnych informacji na temat LINQ, zobacz [Language-Integrated Query (LINQ C# ) —](../../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ umożliwia tworzenie zapytań przy użyciu instrukcji zapytania deklaracyjnego specyficznego dla języka, pokazanego w poprzednim przykładzie, jak również zestawu metod zapytania znanych jako standardowe operatory zapytań. Równoważne zapytanie do poprzedniego przykładu może być złożone przy użyciu tylko składni opartej na metodzie, jak pokazano na poniższym przykładzie:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient może przetłumaczyć oba rodzaje złożonych zapytań na identyfikator URI zapytania, a zapytanie LINQ, dołączając metody zapytania do wyrażenia zapytania. Podczas redagowania zapytań LINQ przez dołączenie składni metody do wyrażenia zapytania lub <xref:System.Data.Services.Client.DataServiceQuery%601>, operacje są dodawane do identyfikatora URI zapytania w kolejności, w której metody są wywoływane. Jest to równoznaczne z wywołaniem <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody w celu dodania każdej opcji zapytania do identyfikatora URI zapytania.  
  
## <a name="executing-linq-queries"></a>Wykonywanie zapytań LINQ  
 Niektóre metody zapytania LINQ, takie jak <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, po dołączeniu do zapytania, powodują wykonanie zapytania. Zapytanie jest również wykonywane, gdy wyniki są wyliczane niejawnie, `foreach` na przykład w pętli lub po przypisaniu zapytania `List` do kolekcji. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 Klient wykonuje zapytanie LINQ w dwóch częściach. Zawsze, gdy to możliwe, wyrażenia LINQ w zapytaniu są najpierw oceniane na kliencie, a następnie generowane jest zapytanie oparte na identyfikatorze URI i wysyłane do usługi danych w celu oceny danych w usłudze. Aby uzyskać więcej informacji, zapoznaj się z sekcją [klient i wykonanie serwera](querying-the-data-service-wcf-data-services.md#executingQueries) w temacie wykonywanie [zapytań do usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 Gdy nie można przetłumaczyć zapytania LINQ w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]identyfikator URI zgodny z zapytaniem, wyjątek jest zgłaszany, gdy zostanie podjęta próba wykonania. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Przykłady zapytań LINQ  
 Przykłady w poniższych sekcjach przedstawiają rodzaje zapytań LINQ, które mogą być wykonywane w odniesieniu [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do usługi.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrowanie  
 Przykłady zapytań LINQ w tej sekcji filtrują dane w kanale informacyjnym zwracanym przez usługę.  
  
 Poniższe przykłady są równoważnymi zapytaniami, które `Orders` filtrują zwrócone jednostki, dzięki czemu zwracane są tylko zamówienia o kosztach frachtu większym niż $30:  
  
- Przy użyciu składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]     
  
- Korzystanie z metod zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]       
  
- Opcja ciągu `$filter` zapytania identyfikatora URI:  
  
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
  
- Opcja ciągu `$orderby` zapytania URI):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Wszystkie poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Rzut  
 W poniższych przykładach pokazano równoważne zapytania, które program Project zwraca dane do `CustomerAddress` typu węższego:  
  
- Przy użyciu składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]         
  
- Korzystanie z metod zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]         

> [!NOTE]
> Nie można dodać opcji <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> zapytaniadoidentyfikatoraURIzapytaniaprzyużyciumetody.`$select` Zalecamy użycie metody LINQ <xref:System.Linq.Enumerable.Select%2A> , aby klient `$select` generował opcję zapytania w identyfikatorze URI żądania.  
  
 Oba poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Stronicowanie klienta  
 W poniższych przykładach pokazano równoważne zapytania, które żądają strony posortowanych obiektów Order, które zawierają 25 zamówień, pomijając pierwsze 50 zamówień:  
  
- Stosowanie metod zapytania do zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]     
  
- Ciąg `$skip` i`$top` opcje zapytania identyfikatora URI:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Oba poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Expand  
 Podczas wykonywania zapytania dotyczącego [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi danych można zażądać, aby jednostki powiązane z jednostką dodaną przez zapytanie były dołączone do zwróconego źródła danych. Metoda jest wywoływana <xref:System.Data.Services.Client.DataServiceQuery%601> dla elementu dla zestawu jednostek przeznaczonego dla zapytania LINQ, z pokrewną nazwą `path` zestawu jednostek podaną jako parametr. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).  
  
 W poniższych przykładach pokazano równoważne sposoby używania <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody w kwerendzie:  
  
- W składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- Z metodami zapytań LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]       

 Oba poprzednie przykłady są tłumaczone na identyfikator URI zapytania: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Nieobsługiwane metody LINQ  
 Poniższa tabela zawiera klasy metod LINQ, które nie są obsługiwane i nie mogą być uwzględnione w zapytaniu wykonanym [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dla usługi:  
  
|Typ operacji|Nieobsługiwanej metody|  
|--------------------|------------------------|  
|Ustaw operatory|Wszystkie operatory zestawów są nieobsługiwane w <xref:System.Data.Services.Client.DataServiceQuery%601>odniesieniu do elementu, który obejmuje następujące elementy:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Operatory porządkowania|Następujące operatory porządkowania, które wymagają <xref:System.Collections.Generic.IComparer%601> , nie są obsługiwane <xref:System.Data.Services.Client.DataServiceQuery%601>w przypadku:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Operatory projekcji i filtrowania|Następujące operatory rzutowania i filtrowania, które akceptują argument pozycyjny, nie są obsługiwane <xref:System.Data.Services.Client.DataServiceQuery%601>dla:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Operatory grupowania|Wszystkie operatory grupowania są nieobsługiwane <xref:System.Data.Services.Client.DataServiceQuery%601>w programie, w tym:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Na kliencie należy wykonać operacje grupowania.|  
|Operatory agregujące|Wszystkie operacje agregacji są nieobsługiwane <xref:System.Data.Services.Client.DataServiceQuery%601>w odniesieniu do programu, w tym:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Operacje agregujące muszą być wykonywane na kliencie lub być hermetyzowane przez operację usługi.|  
|Operatory stronicowania|Następujące operatory stronicowania nie są obsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A>**Uwaga:**  Operatory stronicowania wykonywane na pustej sekwencji zwracają wartość null.|  
|Inne operatory|Następujące inne operatory nie są obsługiwane w przypadku <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Obsługiwane funkcje wyrażeń  
 Obsługiwane są następujące metody i właściwości środowiska uruchomieniowego języka wspólnego (CLR), ponieważ mogą one być tłumaczone w wyrażeniu zapytania w celu uwzględnienia w identyfikatorze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] URI żądania do usługi:  
  
|<xref:System.String>Członkiem|Obsługiwana [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkcja|  
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
  
|<xref:System.DateTime>Członek<sup>1</sup>|Obsługiwana [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkcja|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup> Obsługiwane są również równoważne właściwości <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>daty i godziny, a także <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Metoda w Visual Basic.  
  
|<xref:System.Math>Członkiem|Obsługiwana [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkcja|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Członkiem|Obsługiwana [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkcja|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient może również mieć możliwość oszacowania dodatkowych funkcji CLR na kliencie. Element <xref:System.NotSupportedException> jest wywoływany dla dowolnego wyrażenia, które nie może zostać obliczone na kliencie i nie może zostać przetłumaczone na prawidłowy identyfikator URI żądania na potrzeby oceny na serwerze.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
- [Projekcje zapytania](query-projections-wcf-data-services.md)
- [Materializacja obiektu](object-materialization-wcf-data-services.md)
- [Wykonała Konwencje identyfikatora URI](https://go.microsoft.com/fwlink/?LinkID=185564)
