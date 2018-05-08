---
title: Wywołania operacji usługi (usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 82bba149f06fc68f2f01e0e7641d98ebb861dbe6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="calling-service-operations-wcf-data-services"></a>Wywołania operacji usługi (usługi danych WCF)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Definiuje operacji usługi dla usługi danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia zdefiniowanie takich operacji jako metody w usłudze danych. Podobnie jak inne zasoby usługi danych tych operacji usługi są adresowane za pomocą identyfikatorów URI. Operacja usługi może zwrócić kolekcji typów jednostek, wystąpień typów pojedynczej jednostki i typy pierwotne, takie jak liczba całkowita i ciąg. Operacja usługi można także wrócić `null` (`Nothing` w języku Visual Basic). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta mogą być używane do dostępu operacji usługi, które obsługują żądania HTTP GET. Tego rodzaju operacje usług są zdefiniowane jako metody, które mają <xref:System.ServiceModel.Web.WebGetAttribute> zastosowane. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Operacje usług są widoczne w metadane zwrócony przez usługę danych, który implementuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. W metadanych, operacje usług są reprezentowane jako `FunctionImport` elementów. Podczas generowania jednoznacznie <xref:System.Data.Services.Client.DataServiceContext>, Dodaj odwołanie do usługi i DataSvcUtil.exe narzędzia ignorowania tego elementu. W związku z tym nie będzie zawierał metody w kontekście, który może służyć do wywołania operacji usługi bezpośrednio. Jednakże, nadal można [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta do wywołania operacji usługi w jeden z tych dwóch sposobów:  
  
-   Wywołując <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metoda <xref:System.Data.Services.Client.DataServiceContext>, podając identyfikator URI operacji usługi, wraz z parametrami. Ta metoda jest używana do wywołania żadnej operacji usługi GET.  
  
-   Za pomocą <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> utworzyć <xref:System.Data.Services.Client.DataServiceQuery%601> obiektu. Podczas wywoływania metody <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, nazwa operacji usługi został dostarczony do `entitySetName` parametru. Ta metoda zwraca <xref:System.Data.Services.Client.DataServiceQuery%601> obiekt, który wywołuje operację usługi, gdy wyliczyć lub <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> metoda jest wywoływana. Ta metoda jest używana do wywołania operacji usługi GET, które zwracają kolekcji. Pojedynczy parametr mogą być dostarczane za pomocą <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601> Obiektu zwróconego przez tę metodę mogą dodatkowo składane przed jak inne obiekty zapytania. Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Uwagi dotyczące wywoływania operacji usługi  
 Następujące kwestie przy użyciu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta do wywołania operacji usługi.  
  
-   Podczas uzyskiwania dostępu do usługi data asynchronicznie, należy użyć odpowiednikiem asynchroniczne <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> metod <xref:System.Data.Services.Client.DataServiceContext> lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta nie zmaterializowania wyników z operacji usługi, która zwraca kolekcję typów pierwotnych.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta nie obsługuje wywoływania operacji usługi POST. Operacje usług, które są wywoływane przez metody POST protokołu HTTP są zdefiniowane przy użyciu <xref:System.ServiceModel.Web.WebInvokeAttribute> z `Method="POST"` parametru. Do wywołania operacji usługi za pomocą żądania HTTP POST, zamiast niej należy użyć <xref:System.Net.HttpWebRequest>.  
  
-   Nie można użyć <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do wywołania operacji usługi GET zwracającą wynik jednej jednostki lub typu pierwotnego lub wymagają więcej niż jeden parametr wejściowy. Zamiast tego należy wywołać <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody.  
  
-   Należy rozważyć utworzenie metody rozszerzenia na silnie typizowaną <xref:System.Data.Services.Client.DataServiceContext> częściowej klasy, która jest generowana przez narzędzia, używający jednego <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> lub <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodę do wywołania operacji usługi. Umożliwia wywoływanie operacji usługi bezpośrednio z kontekstu. Aby uzyskać więcej informacji, zobacz w blogu [operacji usługi i klienta usługi danych WCF](http://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Jeśli używasz <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do wywołania operacji usługi, biblioteki klienta automatycznie specjalne znaków przekazany do <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> , wykonując procent kodowanie znaków zastrzeżonych, takich jak handlowego "i" (&) i anulowanie znaków pojedynczego cudzysłowu w ciągi. Jednak jeśli wywołasz jedną z *Execute* metod do wywołania operacji usługi, należy pamiętać wykonać to anulowanie wartości ciągu podanego przez użytkownika. Pojedynczej oferty w identyfikatory URI są anulowane jako pary znaków pojedynczego cudzysłowu.  
  
## <a name="examples-of-calling-service-operations"></a>Przykłady wywołania operacji usługi  
 Ta sekcja zawiera następujące przykłady wywołania operacji usługi za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta:  
  
-   [Wykonanie wywołania&lt;T&gt; zwrócić kolekcję jednostek](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [Przy użyciu CreateQuery&lt;T&gt; zwrócić kolekcję jednostek](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Wykonanie wywołania&lt;T&gt; do zwrócenia pojedynczej jednostki](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Wykonanie wywołania&lt;T&gt; aby zwracać kolekcji wartości pierwotnych](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Wykonanie wywołania&lt;T&gt; aby zwracać pojedynczą wartość pierwotne](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Wywoływanie operacji usługi, która zwraca żadnych danych](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Asynchroniczne wywoływanie operacji usługi](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Wykonanie wywołania\<T > zwrócić kolekcję jednostek  
 Poniższy przykład wywołania operacji usługi o nazwie GetOrdersByCity, która przyjmuje parametr ciągu `city` i zwraca <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 W tym przykładzie operacji usługi zwraca kolekcję `Order` obiektów pokrewnych `Order_Detail` obiektów.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Przy użyciu CreateQuery\<T > zwrócić kolekcję jednostek  
 W poniższym przykładzie użyto <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do zwrócenia <xref:System.Data.Services.Client.DataServiceQuery%601> używany do wywołania tej samej operacji usługi GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 W tym przykładzie <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda jest używana do dodać parametr do zapytania i <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda jest używana do uwzględnienia w wynikach obiekty powiązane szczegóły zamówienia.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Wykonanie wywołania\<T > do zwrócenia pojedynczej jednostki  
 Poniższy przykład wywołuje operację usługi o nazwie GetNewestOrder zwracającą tylko do jednej jednostki kolejności:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 W tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda jest używana do tylko jednej jednostki kolejność wykonywania żądań.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Wykonanie wywołania\<T > Aby zwracać kolekcji wartości pierwotnych  
 Poniższy przykład wywołuje operację usługi, która zwraca kolekcję wartości ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Wykonanie wywołania\<T > Aby zwracać pojedynczą wartość pierwotne  
 Poniższy przykład wywołuje operację usługi, która zwraca wartość jednego ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Ponownie w tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda służy do żądania tylko jedną wartość całkowitą na wykonanie.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Wywoływanie operacji usługi, która zwraca żadnych danych  
 Poniższy przykład wywołuje operację usługi, która zwraca żadnych danych:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Ponieważ dane nie są zwracane, wartość wykonywania nie jest przypisany. Jedyną reakcją, jaką żądanie zakończyła się pomyślnie. jest to, że nie <xref:System.Data.Services.Client.DataServiceQueryException> jest wywoływane.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchroniczne wywoływanie operacji usługi  
 Poniższy przykład wywołania operacji usługi asynchronicznie przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> i <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Ponieważ żadne dane nie zwrócone, wartość zwracana przez wykonanie nie jest przypisany. Jedyną reakcją, jaką żądanie zakończyła się pomyślnie. jest to, że nie <xref:System.Data.Services.Client.DataServiceQueryException> jest wywoływane.  
  
 Poniższy przykład wywołuje operację usługi asynchronicznie za pomocą <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
