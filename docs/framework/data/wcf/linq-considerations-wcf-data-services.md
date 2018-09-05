---
title: Zagadnienia dotyczące LINQ (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 92b3444f81f00ee709c22836126073d342c6fa05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526820"
---
# <a name="linq-considerations-wcf-data-services"></a>Zagadnienia dotyczące LINQ (WCF Data Services)
Ten temat zawiera informacje o sposobie w LINQ, które zapytania są składa się i są stosowane podczas korzystania z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta i ograniczeń za pomocą LINQ do zapytań usługi danych, który implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Aby uzyskać więcej informacji na temat tworzenia i wykonywanie zapytań względem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie danych usługi, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Tworzenie zapytań LINQ  
 LINQ umożliwia tworzenie zapytań względem kolekcji obiektów, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Zarówno **Dodaj odwołanie do usługi** okno dialogowe w programie Visual Studio i narzędziu DataSvcUtil.exe są używane do generowania reprezentację [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi jako klasa kontenera jednostki, która dziedziczy z <xref:System.Data.Services.Client.DataServiceContext>, jak również obiekty reprezentujące zwróconych w kanałach informacyjnych. Te narzędzia są również wygenerować właściwości klasy kontenera jednostki dla kolekcji, które są dostępne jako źródła danych przez usługę. Każdego z tych właściwości klasy, która hermetyzuje usługi danych zwracany <xref:System.Data.Services.Client.DataServiceQuery%601>. Ponieważ <xref:System.Data.Services.Client.DataServiceQuery%601> klasy implementuje <xref:System.Linq.IQueryable%601> interfejs zdefiniowany przez LINQ, można utworzyć zapytanie LINQ do źródła danych udostępnianych przez usługę danych, które są tłumaczone przez bibliotekę klienta na żądania zapytania identyfikatora URI, który jest wysyłany do usługi danych na wykonanie.  
  
> [!IMPORTANT]
>  Zestaw zapytań można wyrazić przy użyciu składni LINQ jest szerszy niż włączone w składni identyfikatora URI, który jest używany przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi danych. Element <xref:System.NotSupportedException> jest wywoływane, gdy zapytanie nie może być mapowana do identyfikatora URI w docelowej usługi danych. Aby uzyskać więcej informacji, zobacz [nieobsługiwane LINQ metody](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) w tym temacie.  
  
 Poniższy przykład to zapytanie LINQ, która zwraca `Orders` kosztują Fracht ponad 30 USD i sortuje wyniki według daty wysyłki, począwszy od najnowszej daty:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 To zapytanie LINQ są tłumaczone na następującej kwerendy identyfikatora URI, który jest wykonywany na podstawie Northwind [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) usługi danych:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Aby uzyskać bardziej ogólne informacje dotyczące LINQ, zobacz [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 LINQ umożliwia tworzenie zapytań przy użyciu obu specyficzny dla języka deklaratywnego Składnia kwerendy, pokazano w poprzednim przykładzie, a także zestaw metod zapytania, znane jako standardowych operatorów zapytań. Kwerendę równoważny z poprzednim przykładem może być składana przy użyciu tylko oparte na metodzie składni, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta jest w stanie tłumaczenie obu rodzajów zapytań złożone identyfikator URI zapytania i zapytania LINQ można rozszerzyć przez dodanie metody zapytania do wyrażenia zapytania. Podczas tworzenia zapytań LINQ, dodając składni metody do wyrażenia zapytania lub <xref:System.Data.Services.Client.DataServiceQuery%601>, operacje są dodawane do zapytania identyfikatora URI w kolejności, w której metody są wywoływane. Jest to równoważne z wywoływaniem <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody w celu dodania każdej opcji zapytania do zapytania identyfikatora URI.  
  
## <a name="executing-linq-queries"></a>Wykonywanie zapytań LINQ  
 Niektóre LINQ zapytania metod, takich jak <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, gdy jest dołączany do zapytania, kwerenda do wykonania. Zapytanie jest również wykonywane, gdy wyniki są wyliczane niejawnie, takie jak podczas `foreach` pętli lub gdy zapytanie jest przypisany do `List` kolekcji. Aby uzyskać więcej informacji, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Klient wykonuje zapytanie LINQ w dwóch częściach. Jeśli to możliwe, wyrażenia LINQ w zapytaniu najpierw są obliczane na komputerze klienckim, a następnie generowane i wysyłane do usługi danych w wersji ewaluacyjnej względem danych w usłudze zapytań w oparciu o identyfikator URI. Aby uzyskać więcej informacji, zobacz sekcję [klienta i serwera wykonanie](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) w [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Gdy zapytanie LINQ nie można przekształcić w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-zgodne zapytania identyfikatora URI, wyjątek jest zgłaszany, gdy jest podejmowana próba wykonania. Aby uzyskać więcej informacji, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Przykłady zapytań LINQ  
 W przykładach w poniższych sekcjach przedstawiono rodzajów zapytań LINQ, które mogą być wykonywane względem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrowanie  
 Przykłady zapytań LINQ w tej sekcji filtrować dane w źródle danych zwróconych przez usługę.  
  
 Poniższe przykłady są równoważne kwerend, które filtrują zwracanego `Orders` są zwracane jednostki, która tylko zamówienia, większa niż 30 USD koszt transportu:  
  
-   Za pomocą składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   Za pomocą metody zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   Ciągu zapytania identyfikatora URI `$filter` opcji:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Wszystkich poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Sortowanie  
 W poniższych przykładach pokazano równoważne zapytań, które sortować dane zwrotne zarówno nazwy firmy, jak i według kod pocztowy, malejąco:  
  
-   Za pomocą składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   Za pomocą metody zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   Ciągu zapytania identyfikatora URI `$orderby` opcja):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Wszystkich poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Rzut  
 W poniższych przykładach pokazano równoważne zapytań, które zwrócone dane projektu na mniejszą niż `CustomerAddress` typu:  
  
-   Za pomocą składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   Za pomocą metody zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  `$select` Stosowanie opcji zapytania nie można dodać do zapytania identyfikatora URI za pomocą <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Firma Microsoft zaleca, aby używać programu LINQ <xref:System.Linq.Enumerable.Select%2A> metoda klienta Generowanie `$select` zapytania opcji w identyfikatorze URI żądania.  
  
 Zarówno poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Stronicowanie klienta  
 W poniższych przykładach pokazano równoważne zapytań, które żądania stronie kolejności posortowanej jednostki, która zawiera 25 zamówienia, pomijanie 50 pierwszych zamówień:  
  
-   Zastosowanie metody zapytania do zapytania LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   Ciągu zapytania identyfikatora URI `$skip` i `$top` opcje):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Zarówno poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Rozwiń węzeł  
 Podczas wysyłania zapytania [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi danych, możesz poprosić o uwzględnienia jednostki związane z jednostką objęte zapytanie zwróconego źródła danych. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Wywoływana jest metoda <xref:System.Data.Services.Client.DataServiceQuery%601> dla zestawu jednostek, objęte zapytanie LINQ, za pomocą powiązanej jednostki Nazwa zestawu podana jako `path` parametru. Aby uzyskać więcej informacji, zobacz [ładowanie zawartości odroczone](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 W poniższych przykładach pokazano równoważne sposoby na wykorzystanie <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody w zapytaniu:  
  
-   W składni zapytań LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   Za pomocą metody zapytania LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 Zarówno poprzednich przykładach są tłumaczone na zapytania identyfikatora URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Metody nieobsługiwane LINQ  
 Poniższa tabela zawiera klasy programu LINQ metod nie są obsługiwane i nie może być dołączany do zapytania wykonywane względem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi:  
  
|Typ operacji|Nieobsługiwanej metody|  
|--------------------|------------------------|  
|Operatory zestawu|Wszystkie operatory w zestawie nie są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>, które wchodzą następujące czynności:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Kolejność operatorów|Następujące operatory szeregowania, które wymagają <xref:System.Collections.Generic.IComparer%601> nie są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Prognoza i filtrowanie operatorów|Następujące rzutowania i operatorów filtrowania, które akceptują argument pozycyjny nie są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Operatory grupowania|Wszystkie operatory grupowania są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>, w tym następujące czynności:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Operacje muszą być wykonywane na komputerze klienckim.|  
|Operatory agregacji|Wszystkie operacje agregacji są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>, w tym następujące czynności:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Operacje agregacji albo muszą być wykonywane na komputerze klienckim, lub być zhermetyzowany przez operację usługi.|  
|Operatory stronicowania|Następujące operatory stronicowania nie są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Uwaga:** stronicowania operatorów, które są wykonywane na pustą sekwencją zwracać wartość null.|  
|Inne operatory|Następujące inne operatory nie są obsługiwane względem <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Wyrażenie obsługiwane funkcje  
 Poniższych metod środowiska uruchomieniowego języka wspólnego (CLR) i właściwości są obsługiwane, ponieważ mogą być tłumaczone w wyrażeniu zapytania do włączenia w identyfikatorze URI żądania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi:  
  
|<xref:System.String> Element członkowski|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
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
  
|<xref:System.DateTime> Element członkowski<sup>1</sup>|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>równoważne właściwości daty i godziny z <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, jak również <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> w języku Visual Basic są również obsługiwane.  
  
|<xref:System.Math> Element członkowski|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression> Element członkowski|Obsługiwane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] — funkcja|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient może być również mogli oceniać zestaw dodatkowych funkcji CLR na komputerze klienckim. Element <xref:System.NotSupportedException> jest wywoływane na dowolne wyrażenie, które nie może być ocenione na komputerze klienckim i nie można przekształcić na prawidłowy identyfikator URI żądania w wersji ewaluacyjnej na serwerze.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [OData: Zgodnie z konwencjami identyfikator URI](https://go.microsoft.com/fwlink/?LinkID=185564)
