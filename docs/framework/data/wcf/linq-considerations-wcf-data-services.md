---
title: "Zagadnienia dotyczące LINQ (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b992cafbc0f8c68cfa695f244b9ec82d9d344af
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="linq-considerations-wcf-data-services"></a>Zagadnienia dotyczące LINQ (usługi danych WCF)
Ten temat zawiera informacje o sposobie, w których LINQ składa się i wykonywać, gdy używasz zapytania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta i ograniczenia dotyczące korzystania z LINQ do badania Usługa danych, która implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie i wykonywanie zapytań dotyczących [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie danych usługi, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Tworzenie zapytań LINQ  
 LINQ umożliwia tworzenia zapytań dotyczących kolekcji obiektów, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Zarówno **Dodaj odwołanie do usługi** okno dialogowe w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] i narzędzie DataSvcUtil.exe są używane do generowania reprezentację [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi jako klasy kontenera jednostka, która dziedziczy <xref:System.Data.Services.Client.DataServiceContext>, a także obiekty, które reprezentują zwróconych w źródłach. Narzędzia te również generować właściwości klasy kontenera jednostki dla kolekcji, które są dostępne jako źródła danych przez usługę. Każdej z tych właściwości klasy, która hermetyzuje usługę danych zwracany <xref:System.Data.Services.Client.DataServiceQuery%601>. Ponieważ <xref:System.Data.Services.Client.DataServiceQuery%601> klasa implementuje <xref:System.Linq.IQueryable%601> interfejs zdefiniowany przez składnik LINQ, można utworzyć zapytania LINQ względem źródła danych udostępnianych przez usługę danych, które przetłumaczyć przez bibliotekę klienta żądania identyfikator URI, który jest przesyłany do usługi danych wykonanie.  
  
> [!IMPORTANT]
>  Zestaw kwerendy można wyrazić w składni LINQ jest szerszy niż włączone w składni identyfikatora URI, który jest używany przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usług danych. A <xref:System.NotSupportedException> jest wywoływane, gdy nie można zamapować zapytania do identyfikatora URI w usłudze danych docelowych. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][nieobsługiwanej metody LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) w tym temacie.  
  
 Poniższy przykład jest zapytań LINQ, która zwraca `Orders` koszt transport, ponad 30 $ i sortujące wyniki według daty wysyłki, począwszy od najnowszej daty:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 Ta kwerenda LINQ jest przekształcana na następujące zapytanie identyfikator URI, który jest wykonywany przed systemem Northwind [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) Usługa danych:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Aby uzyskać więcej ogólnych informacji na temat LINQ, zobacz [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 LINQ umożliwia utworzenie zapytania przy użyciu oba specyficzny dla języka deklaratywne składnię, pokazano w poprzednim przykładzie, a także zestaw metod zapytania znane jako standardowych operatorów zapytań. Odpowiednik zapytania z poprzednim przykładem mogą być składane przy użyciu tylko oparte na metodzie składni, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient jest w stanie tłumaczenie oba rodzaje składa zapytania na identyfikator URI zapytania i zapytań LINQ można rozszerzyć przez dodanie metody zapytań do wyrażenia zapytania. Podczas tworzenia zapytań LINQ przez dodanie metody do wyrażenia zapytania lub <xref:System.Data.Services.Client.DataServiceQuery%601>, działania są dodawane do zapytania identyfikatora URI w kolejności, w którym są wywoływane metody. Jest to odpowiednik wywołania <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody w celu dodania poszczególnych opcji zapytania do zapytania identyfikatora URI.  
  
## <a name="executing-linq-queries"></a>Wykonywanie zapytań LINQ  
 Niektóre LINQ zapytania metody, takie jak <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, gdy dodany do kwerendy, kwerenda może być wykonywane. Zapytanie również jest wykonywane, gdy wyniki są wyliczane niejawnie, takich jak podczas `foreach` pętli lub jeśli zapytanie jest przypisany do `List` kolekcji. Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Klient wykonuje zapytania LINQ w dwóch częściach. Jeśli to możliwe, wyrażenia LINQ w zapytaniu najpierw są oceniane na kliencie, a następnie kwerendy na podstawie identyfikatora URI jest generowany i wysyłane do usługi danych w wersji ewaluacyjnej w odniesieniu do danych w usłudze. Aby uzyskać więcej informacji, zobacz sekcję [klienta i serwera wykonanie](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) w [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Jeśli kwerenda LINQ nie można przetłumaczyć w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-zgodne zapytania identyfikatora URI, wyjątek jest wywoływane, gdy jest podejmowana próba wykonania. Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Przykłady zapytań LINQ  
 W przykładach w poniższych sekcjach przedstawiono typy zapytań LINQ, które mogą być wykonywane przed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrowanie  
 Przykłady zapytań LINQ w tej sekcji Filtrowanie danych w źródle danych zwróconych przez usługę.  
  
 Poniższe przykłady są równoważne zapytań, które filtrować zwróconego `Orders` są zwracane jednostki, który tylko porządkuje większą od 30 $ kosztem transport:  
  
-   Za pomocą składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   Przy użyciu metody zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   Ciąg zapytania URI `$filter` opcji:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Wszystkich poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Sortowanie  
 W poniższych przykładach pokazano równoważne zapytań, które posortuj zwrócone dane nazwy firmy i kodem pocztowym, malejąco:  
  
-   Za pomocą składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   Przy użyciu metody zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   Ciąg zapytania URI `$orderby` opcja):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Wszystkich poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Rzut  
 W poniższych przykładach pokazano równoważne zapytań, które zwróconych danych projektu na mniejszą niż `CustomerAddress` typu:  
  
-   Za pomocą składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   Przy użyciu metody zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  `$select` Opcji zapytania nie można dodać do zapytania identyfikatora URI przy użyciu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Zalecane jest użycie LINQ <xref:System.Linq.Enumerable.Select%2A> metody, aby klienci Generowanie `$select` opcji w identyfikatorze URI żądania zapytania.  
  
 Zarówno w poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Stronicowanie klienta  
 W poniższych przykładach pokazano równoważne kwerendy stronę jednostek posortowane obejmuje 25 zlecenia, pomijanie najpierw 50 zleceń:  
  
-   Zastosowanie metody zapytań do kwerend LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   Ciąg zapytania URI `$skip` i `$top` opcje):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Zarówno w poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Rozwiń węzeł  
 Jeśli zapytanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Usługa danych, możesz poprosić uwzględnienia jednostki powiązane z jednostką docelową przez zapytanie zwrócony źródła danych. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Wywoływana jest metoda <xref:System.Data.Services.Client.DataServiceQuery%601> dla zestawu jednostek objęci zapytania LINQ, z powiązanych jednostek Nazwa zestawu podana jako `path` parametru. Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 W poniższych przykładach pokazano równoważne sposoby używania <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody w zapytaniu:  
  
-   W składni zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   Z metody zapytań LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 Zarówno w poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Metody nieobsługiwany LINQ  
 Poniższa tabela zawiera klasy LINQ metod nie są obsługiwane i nie może być dołączany do zapytania wykonywane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi:  
  
|Typ operacji|Nieobsługiwany — metoda|  
|--------------------|------------------------|  
|Operatory zestawów|Wszystkie operatory zestawów nie są obsługiwane dla <xref:System.Data.Services.Client.DataServiceQuery%601>, które wchodzą następujące:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Operatory porządkowania|Następujące operatory porządkowania, które wymagają <xref:System.Collections.Generic.IComparer%601> nieobsługiwanych przed <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Filtrowanie operatory i projekcji|Przed nie są obsługiwane następujące projekcji i operatory filtrowania, które akceptują argument pozycyjny <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Operatory grupowania|Wszystkie operatory grupowania są obsługiwane dla <xref:System.Data.Services.Client.DataServiceQuery%601>, takie jak:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Należy wykonać operacji grupowania na kliencie.|  
|Operatory agregacji|Wszystkie operacje agregacji nie są obsługiwane dla <xref:System.Data.Services.Client.DataServiceQuery%601>, takie jak:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Operacje agregacji albo musi zostać wykonana na komputerze klienckim lub być zamknięte przez operację usługi.|  
|Operatory stronicowania|Następujące operatory stronicowania nie są obsługiwane na <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A>**Uwaga:** operatory stronicowania, które są wykonywane na pustej sekwencji zwracać wartość null.|  
|Inne operatory|Następujące inne operatory nie są obsługiwane na <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Wyrażenie obsługiwane funkcje  
 Następujące środowisko uruchomieniowe języka wspólnego (CLR) metody i właściwości są obsługiwane, ponieważ mogą być przekonwertowana w wyrażeniu zapytania do dołączenia do identyfikatora URI żądania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi:  
  
|<xref:System.String>Element członkowski|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
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
  
|<xref:System.DateTime>Element członkowski<sup>1</sup>|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>równoważne właściwości daty i godziny z <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, a także <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> metody w języku Visual Basic są również obsługiwane.  
  
|<xref:System.Math>Element członkowski|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Element członkowski|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient może być również może korzystać z dodatkowych funkcji CLR na kliencie. A <xref:System.NotSupportedException> jest wywoływane dla dowolnego wyrażenia, którego nie można oszacować na kliencie i nie można przetłumaczyć identyfikatora URI żądania prawidłowy w wersji ewaluacyjnej na serwerze.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [Obiekt Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [OData: Konwencje identyfikatora URI](http://go.microsoft.com/fwlink/?LinkID=185564)
