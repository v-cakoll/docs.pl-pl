---
title: Wywołania operacji usługi (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 5ef00861624531e68ad5b8a3b080810040ae3ff6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109476"
---
# <a name="calling-service-operations-wcf-data-services"></a>Wywołania operacji usługi (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Definiuje operacji usługi dla usługi danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia zdefiniowanie takich operacji jako metody na usługę danych. Podobnie jak inne zasoby usługi data operacje te usługi są adresowane za pomocą identyfikatorów URI. Operacja usługi może zwracać kolekcji typów jednostek, wystąpienia typu pojedynczej jednostki i typy pierwotne, takie jak liczba całkowita i ciąg. Operacja usługi może również zwracać `null` (`Nothing` w języku Visual Basic). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta może służyć do dostępu do operacji usługi, które obsługują żądania HTTP GET. Te rodzaje operacji usługi są zdefiniowane jako metody, które mają <xref:System.ServiceModel.Web.WebGetAttribute> stosowane. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Operacje usługi są widoczne w metadanych zwróconych przez usługę danych, która implementuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. W metadanych operacji usługi są reprezentowane jako `FunctionImport` elementów. Podczas generowania silnie typizowaną <xref:System.Data.Services.Client.DataServiceContext>, Dodaj odwołanie do usługi i DataSvcUtil.exe narzędzia Ignoruj ten element. W związku z tym nie będą dostępne metody w kontekście, który może służyć do wywołania operacji usługi bezpośrednio. Jednak nadal można użyć [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta do wywołania operacji usługi w jednym z następujących dwóch sposobów:  
  
-   Przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody <xref:System.Data.Services.Client.DataServiceContext>, podając identyfikator URI operacji usługi, oraz wszelkie parametry. Ta metoda jest używana do wywołania dowolnego GET operacji usługi.  
  
-   Za pomocą <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metody <xref:System.Data.Services.Client.DataServiceContext> utworzyć <xref:System.Data.Services.Client.DataServiceQuery%601> obiektu. Podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, nazwą operacji, usługa jest dostarczony do `entitySetName` parametru. Ta metoda zwraca <xref:System.Data.Services.Client.DataServiceQuery%601> obiekt, który wywołuje operacji usługi, gdy wyliczenia lub <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> metoda jest wywoływana. Ta metoda jest używana do wywołania operacji usługi GET, które zwracają kolekcję. Pojedynczy parametr mogą być dostarczane za pomocą <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601> Obiektu zwróconego przez tę metodę mogą być dodatkowo składane względem jak inne obiekty zapytania. Aby uzyskać więcej informacji, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Uwagi dotyczące wywoływania operacji usługi  
 Obowiązują następujące zastrzeżenia, korzystając z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta do wywołania operacji usługi.  
  
-   Podczas uzyskiwania dostępu do usługi danych asynchronicznie, należy użyć odpowiednik asynchroniczne <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> metod <xref:System.Data.Services.Client.DataServiceContext> lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metod <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta nie zmaterializowania wyniki z operacji usługi, które zwraca kolekcję typów pierwotnych.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka kliencka nie obsługuje wywoływania operacji usługi POST. Operacje usług, które są wywoływane przez metody POST protokołu HTTP są zdefiniowane przy użyciu <xref:System.ServiceModel.Web.WebInvokeAttribute> z `Method="POST"` parametru. Aby wywołać operację usługi za pomocą żądania HTTP POST, musisz użyć <xref:System.Net.HttpWebRequest>.  
  
-   Nie można użyć <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do wywołania operacji usługi GET zwracającą wynik pojedynczej jednostki lub typ pierwotny, lub który wymaga więcej niż jeden parametr wejściowy. Zamiast tego należy wywołać <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody.  
  
-   Należy rozważyć utworzenie metodę rozszerzającą na silnie typizowaną <xref:System.Data.Services.Client.DataServiceContext> częściowe klasy, która jest generowany przez narzędzia, który używa albo <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> lub <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodę do wywołania operacji usługi. Umożliwia wywoływanie operacji usługi bezpośrednio z kontekstu. Aby uzyskać więcej informacji, zobacz wpis w blogu [operacji usługi i klienta usługi danych WCF](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Kiedy używasz <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do wywołania operacji usługi, biblioteki klienta automatycznie zmienia znaczenie znaków dostarczane do <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> , wykonując procent kodowanie znaków zarezerwowanych, takich jak handlowe "i" (&) i anulowania zapewnianego element znaków cudzysłowu pojedynczego w ciągi. Jednak wywołanie jednej z *Execute* metod do wywołania operacji usługi, należy pamiętać, aby wykonać to anulowanie wszelkich wartości ciągu podanego przez użytkownika. Cudzysłowy pojedynczego identyfikatorów URI będą miały zmienione znaczenie jako pary pojedynczym cudzysłowie.  
  
## <a name="examples-of-calling-service-operations"></a>Przykłady wywoływanie operacji usługi  
 Ta sekcja zawiera następujące przykłady sposób wywołania operacji usługi za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta:  
  
-   [Wykonywanie wywołania&lt;T&gt; zwracać kolekcję jednostek](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [Za pomocą CreateQuery&lt;T&gt; zwracać kolekcję jednostek](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Wykonywanie wywołania&lt;T&gt; do zwrócenia pojedynczej jednostki](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Wykonywanie wywołania&lt;T&gt; zwracać kolekcję wartości pierwotnych](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Wykonywanie wywołania&lt;T&gt; do zwrócenia pojedynczej wartości pierwotnych](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Wywoływanie operacji usługi, która nie zwraca żadnych danych](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Asynchroniczne wywoływanie operacji usługi](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Wykonywanie wywołania\<T > do zwrócenia kolekcji jednostek  
 Poniższy przykład wywołania operacji usługi o nazwie GetOrdersByCity, który przyjmuje parametr ciąg `city` i zwraca <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 W tym przykładzie operacji usługi zwraca kolekcję `Order` powiązanych obiektów `Order_Detail` obiektów.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Za pomocą CreateQuery\<T > do zwrócenia kolekcji jednostek  
 W poniższym przykładzie użyto <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do zwrócenia <xref:System.Data.Services.Client.DataServiceQuery%601> używanego do wywołania tej samej operacji usługi GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 W tym przykładzie <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda służy do Dodaj parametr do zapytania i <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda jest używana do włączenia obiekty powiązane szczegóły zamówienia w wynikach.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Wykonywanie wywołania\<T > do zwrócenia pojedynczej jednostki  
 Poniższy przykład wywołuje operacji usługi o nazwie GetNewestOrder zwracającą tylko do jednej jednostki zamówienia:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 W tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda służy do żądania tylko do jednej jednostki zamówienia na wykonanie.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Wykonywanie wywołania\<T > zwracać kolekcję wartości pierwotnych  
 Poniższy przykład wywołuje operację usługi, które zwraca kolekcję wartości ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Wykonywanie wywołania\<T > do zwrócenia pojedynczej wartości pierwotnych  
 Poniższy przykład wywołuje operację usługi, która zwraca wartość ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Ponownie w tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda służy do żądania tylko jedną wartość całkowitą na wykonanie.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Wywoływanie operacji usługi, która nie zwraca żadnych danych  
 Poniższy przykład wywołuje operacji usługi, która nie zwraca żadnych danych:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Ponieważ dane nie są zwracane, wartość wykonywania nie jest przypisany. Jest to tylko wskazuje, że żądanie powiodło się, że nie <xref:System.Data.Services.Client.DataServiceQueryException> jest wywoływane.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchroniczne wywoływanie operacji usługi  
 Poniższy przykład wywołania operacji usługi asynchronicznie przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> i <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Ponieważ dane nie są zwracane, wartość zwracana przez wykonanie nie jest przypisany. Jest to tylko wskazuje, że żądanie powiodło się, że nie <xref:System.Data.Services.Client.DataServiceQueryException> jest wywoływane.  
  
 Poniższy przykład wywołuje tę samą operację usługi asynchronicznie za pomocą <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
