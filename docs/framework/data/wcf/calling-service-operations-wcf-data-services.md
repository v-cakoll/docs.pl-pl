---
title: Operacje usługi wywołującej (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 21ae73054935373607909902e0b3e82ba5146f43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791146"
---
# <a name="calling-service-operations-wcf-data-services"></a>Operacje usługi wywołującej (Usługi danych programu WCF)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Definiuje operacje usługi dla usługi danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia definiowanie takich operacji jako metod usługi danych. Podobnie jak w przypadku innych zasobów usługi danych, te operacje usług są rozwiązywane przy użyciu identyfikatorów URI. Operacja usługi może zwracać kolekcje typów jednostek, pojedyncze wystąpienia typu jednostki i typy pierwotne, takie jak liczba całkowita i ciąg. Operacja usługi może również zwrócić `null` (`Nothing` w Visual Basic). Biblioteka [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kliencka może służyć do uzyskiwania dostępu do operacji usługi, które obsługują żądania HTTP GET. Te rodzaje operacji usługi są definiowane jako metody, które mają <xref:System.ServiceModel.Web.WebGetAttribute> zastosowanie. Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).  
  
 Operacje usługi są ujawniane w metadanych zwracanych przez usługę danych implementującą [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. W metadanych operacje usługi są reprezentowane jako `FunctionImport` elementy. Podczas generowania jednoznacznie określonego <xref:System.Data.Services.Client.DataServiceContext>typu narzędzia Dodaj odwołanie do usługi i DataSvcUtil. exe ignorują ten element. W związku z tym nie znajdziesz metody w kontekście, która może być używana do bezpośredniego wywoływania operacji usługi. Można jednak nadal używać [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta do wywoływania operacji usługi na jeden z tych dwóch sposobów:  
  
- Przez wywołanie <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody <xref:System.Data.Services.Client.DataServiceContext>w, dostarczenie identyfikatora URI operacji usługi wraz z dowolnymi parametrami. Ta metoda służy do wywoływania dowolnej operacji pobierania usługi.  
  
- Za pomocą <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metody <xref:System.Data.Services.Client.DataServiceContext> w celu utworzenia <xref:System.Data.Services.Client.DataServiceQuery%601> obiektu. Podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, nazwa operacji usługi jest dostarczana `entitySetName` do parametru. Ta metoda zwraca <xref:System.Data.Services.Client.DataServiceQuery%601> obiekt, który wywołuje operację usługi po wyliczeniu lub <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> Kiedy metoda jest wywoływana. Ta metoda służy do wywoływania operacji pobierania usługi, które zwracają kolekcję. Pojedynczy parametr można dostarczyć przy użyciu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601> Obiekt zwrócony przez tę metodę może być bardziej złożony względem dowolnego obiektu zapytania. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Zagadnienia dotyczące operacji usługi wywołującej  
 W przypadku używania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta do wywoływania operacji usługi należy wziąć pod uwagę następujące kwestie.  
  
- W przypadku asynchronicznego <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> uzyskiwania dostępu do usługi danych należy użyć odpowiednich metod asynchronicznych / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> dla <xref:System.Data.Services.Client.DataServiceContext> lub <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / metod w <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- Biblioteka [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kliencka nie może zmaterializowania wyników operacji usługi, która zwraca kolekcję typów pierwotnych.  
  
- Biblioteka [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kliencka nie obsługuje wywoływania operacji post Service. Operacje usługi, które są wywoływane przez wpis http, są definiowane przy użyciu <xref:System.ServiceModel.Web.WebInvokeAttribute> `Method="POST"` parametru z parametrem. Aby wywołać operację usługi przy użyciu żądania HTTP POST, należy zamiast tego użyć <xref:System.Net.HttpWebRequest>.  
  
- Nie można użyć <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do wywołania operacji pobierania usługi zwracającej pojedynczy wynik, dla jednostki lub typu pierwotnego lub wymagającej więcej niż jednego parametru wejściowego. Zamiast tego należy wywołać <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodę.  
  
- Rozważ utworzenie metody rozszerzenia dla klasy częściowej o jednoznacznie <xref:System.Data.Services.Client.DataServiceContext> określonym typie, która jest generowana przez narzędzia, która używa <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> albo metody do wywołania operacji usługi. Umożliwia to wywoływanie operacji usługi bezpośrednio z kontekstu. Aby uzyskać więcej informacji, zobacz operacje usługi wpis w blogu [i klienta usługi danych programu WCF](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
- W przypadku użycia <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> programu w celu wywołania operacji usługi Biblioteka klienta automatycznie wyprowadza znaki dostarczone <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> do obiektu przez wykonanie kodowania procentowo znaków zarezerwowanych, takich jak znak handlowego "i" (&) i ucieczki pojedynczego cudzysłowu w długooci. Jednak w przypadku wywołania jednej z metod *wykonywania* w celu wywołania operacji usługi należy pamiętać, aby wykonać to anulowanie wartości ciągów dostarczonych przez użytkownika. Pojedyncze cudzysłowy w identyfikatorach URI są wyprowadzane jako pary pojedynczego cudzysłowu.  
  
## <a name="examples-of-calling-service-operations"></a>Przykłady operacji usługi wywołującej  
 Ta sekcja zawiera następujące przykłady sposobu wywoływania operacji usługi przy użyciu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckiej programu:  
  
- [Wywoływanie&lt;Execute&gt; T w celu zwrócenia kolekcji jednostek](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Korzystanie z kwerendy&lt;T&gt; w celu zwrócenia kolekcji jednostek](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Wywoływanie&lt;Execute&gt; T w celu zwrócenia pojedynczej jednostki](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Wywoływanie&lt;Execute&gt; T w celu zwrócenia kolekcji wartości pierwotnych](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Wywołanie Execute&lt;T&gt; w celu zwrócenia pojedynczej wartości pierwotnej](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Wywoływanie operacji usługi, która nie zwraca danych](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Asynchroniczne wywoływanie operacji usługi](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Wywoływanie\<Execute T > w celu zwrócenia kolekcji jednostek  
 Poniższy przykład wywołuje operację usługi o nazwie GetOrdersByCity, która przyjmuje parametr `city` ciągu i <xref:System.Linq.IQueryable%601>zwraca:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 W tym przykładzie operacja usługi zwraca kolekcję `Order` obiektów z powiązanymi `Order_Detail` obiektami.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Zwracanie kolekcji jednostek\<przy użyciu polecenia @ query T >  
 W poniższym przykładzie użyto <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do zwrócenia elementu <xref:System.Data.Services.Client.DataServiceQuery%601> , który jest używany do wywołania tej samej operacji usługi GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 W tym przykładzie <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Metoda jest używana do dodawania parametru do zapytania, <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> a metoda jest używana do dołączania powiązanych obiektów Order_Details w wynikach.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Wywoływanie\<Execute T > w celu zwrócenia pojedynczej jednostki  
 Poniższy przykład wywołuje operację usługi o nazwie GetNewestOrder, która zwraca tylko jedną jednostkę Order:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 W tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> Metoda jest używana do żądania tylko pojedynczej jednostki Order przy wykonywaniu.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Wywoływanie\<Execute T > w celu zwrócenia kolekcji wartości pierwotnych  
 Poniższy przykład wywołuje operację usługi, która zwraca kolekcję wartości ciągów:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Wywoływanie\<Execute T > w celu zwrócenia pojedynczej wartości pierwotnej  
 Poniższy przykład wywołuje operację usługi, która zwraca pojedynczą wartość ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 W tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> Metoda jest używana do żądania tylko pojedynczej wartości całkowitej przy wykonywaniu.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Wywoływanie operacji usługi, która nie zwraca danych  
 Poniższy przykład wywołuje operację usługi, która nie zwraca żadnych danych:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Ponieważ nie są zwracane żadne dane, wartość wykonywania nie jest przypisana. Jedyną informacją o tym, że żądanie powiodło się, <xref:System.Data.Services.Client.DataServiceQueryException> jest to, że nie zostało zgłoszone.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchroniczne wywoływanie operacji usługi  
 Poniższy przykład wywołuje operację usługi asynchronicznie, wywołując <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> i: <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Ponieważ żadne dane nie są zwracane, wartość zwrócona przez wykonanie nie zostanie przypisana. Jedyną informacją o tym, że żądanie powiodło się, <xref:System.Data.Services.Client.DataServiceQueryException> jest to, że nie zostało zgłoszone.  
  
 Poniższy przykład wywołuje tę samą operację usługi asynchronicznie przy użyciu <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
