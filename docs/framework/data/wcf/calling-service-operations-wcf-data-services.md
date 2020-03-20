---
title: Operacje wywoływania usługi (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 41aac38cec97ae1afdd3c3c051d04ff242e7729d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174358"
---
# <a name="calling-service-operations-wcf-data-services"></a>Operacje wywoływania usługi (WCF Data Services)
Protokół Open Data Protocol (OData) definiuje operacje usługi dla usługi danych. Usługi danych WCF umożliwia definiowanie takich operacji, jak metody w usłudze danych. Podobnie jak inne zasoby usługi danych, te operacje usługi są adresowane przy użyciu identyfikatorów URI. Operacja usługi może zwracać kolekcje typów jednostek, wystąpienia typu pojedynczej jednostki i typów pierwotnych, takich jak liczba całkowita i ciąg. Operacja usługi może `null` również`Nothing` powrócić (w języku Visual Basic). Biblioteka klienta usług danych WCF może służyć do uzyskiwania dostępu do operacji usługi, które obsługują żądania HTTP GET. Tego rodzaju operacje usługi są definiowane <xref:System.ServiceModel.Web.WebGetAttribute> jako metody, które mają zastosowane. Aby uzyskać więcej informacji, zobacz [Operacje serwisowe](service-operations-wcf-data-services.md).  
  
 Operacje usługi są udostępniane w metadanych zwracanych przez usługę danych, która implementuje OData. W metadanych operacje usługi są `FunctionImport` reprezentowane jako elementy. Podczas generowania silnie typizowane <xref:System.Data.Services.Client.DataServiceContext>, Dodaj odwołanie do usługi i DataSvcUtil.exe narzędzia ignorują ten element. Z tego powodu nie znajdziesz metody w kontekście, który może służyć do wywołania operacji usługi bezpośrednio. Jednak nadal można użyć klienta WCF Data Services do wywoływania operacji usługi na jeden z następujących dwóch sposobów:  
  
- Wywołując <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodę na <xref:System.Data.Services.Client.DataServiceContext>, dostarczanie identyfikatora URI operacji usługi, wraz z dowolnymi parametrami. Ta metoda jest używana do wywoływania dowolnej operacji usługi GET.  
  
- Za pomocą <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metody <xref:System.Data.Services.Client.DataServiceContext> na, <xref:System.Data.Services.Client.DataServiceQuery%601> aby utworzyć obiekt. Podczas <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>wywoływania nazwa operacji usługi jest `entitySetName` dostarczana do parametru. Ta metoda <xref:System.Data.Services.Client.DataServiceQuery%601> zwraca obiekt, który wywołuje operację usługi po <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> wyliczenia lub gdy metoda jest wywoływana. Ta metoda jest używana do wywoływania operacji usługi GET, które zwracają kolekcję. Pojedynczy parametr może być dostarczony <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> przy użyciu metody. Obiekt <xref:System.Data.Services.Client.DataServiceQuery%601> zwrócony przez tę metodę może być dalej składa się z jak każdy obiekt kwerendy. Aby uzyskać więcej informacji, zobacz [Kwerenda usługi danych](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Zagadnienia dotyczące wywoływania operacji usługi  
 Następujące zagadnienia mają zastosowanie podczas korzystania z klienta usług danych WCF do wywoływania operacji usługi.  
  
- Podczas uzyskiwania dostępu do usługi danych asynchronicznie należy użyć <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> równoważnych <xref:System.Data.Services.Client.DataServiceContext> metod <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> asynchronicznych lub metod włączonych <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- Biblioteka klienta usług danych WCF nie może zmaterializować wyniki z operacji usługi, która zwraca kolekcję typów pierwotnych.  
  
- Biblioteka klienta usług danych WCF nie obsługuje wywoływania operacji usługi POST. Operacje usługi, które są wywoływane przez <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP `Method="POST"` POST są definiowane przy użyciu parametru. Aby wywołać operację usługi przy użyciu żądania HTTP POST, należy zamiast tego użyć pliku <xref:System.Net.HttpWebRequest>.  
  
- Nie można <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> wywołać operacji usługi GET, która zwraca pojedynczy wynik, typu jednostki lub pierwotnego lub który wymaga więcej niż jednego parametru wejściowego. Zamiast tego należy <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> wywołać metodę.  
  
- Należy rozważyć utworzenie metody rozszerzenia na <xref:System.Data.Services.Client.DataServiceContext> silnie typizowane klasy częściowej, który jest generowany <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> przez <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> narzędzia, który używa lub metody do wywołania operacji usługi. Dzięki temu można wywołać operacje usługi bezpośrednio z kontekstu. Aby uzyskać więcej informacji, zobacz wpis w blogu [Operacje usługi i klient usług danych WCF](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).  
  
- Podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> operacji usługi biblioteka klienta automatycznie unika znaków <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> dostarczonych do znaków, wykonując procent kodowania znaków zastrzeżonych, takich jak ampersand (&) i ucieczki pojedynczych cudzysłowów w ciągach. Jednak po wywołaniu jednej z *Execute* metody wywołania operacji usługi, należy pamiętać, aby wykonać tę ucieczkę wszelkich wartości ciągów dostarczonych przez użytkownika. Pojedyncze cudzysłowy w identyfikatorach URI są uniknęły jako pary pojedynczych cudzysłowów.  
  
## <a name="examples-of-calling-service-operations"></a>Przykłady operacji wywoływania usługi  
 Ta sekcja zawiera następujące przykłady sposobu wywoływania operacji usługi przy użyciu biblioteki klienta usług danych WCF:  
  
- [Wywołanie&lt;&gt; execute T do zwrócenia kolekcji jednostek](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Tworzeniequery&lt;T&gt; do zwrócenia kolekcji jednostek](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Wywołanie&lt;&gt; execute T do zwrócenia pojedynczej jednostki](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Wywołanie&lt;&gt; execute T do zwrócenia kolekcji wartości pierwotnych](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Wywołanie&lt;&gt; execute T w celu zwrócenia pojedynczej pierwotnej wartości](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Wywoływanie operacji usługi, która nie zwraca żadnych danych](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Wywołanie operacji usługi asynchronicznie](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Wywołanie\<execute T> do zwrócenia kolekcji jednostek  
 Poniższy przykład wywołuje operację usługi o nazwie GetOrdersByCity, która przyjmuje parametr ciągu `city` i <xref:System.Linq.IQueryable%601>zwraca:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 W tym przykładzie operacja usługi `Order` zwraca kolekcję obiektów z powiązanych `Order_Detail` obiektów.  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Przy użyciu\<CreateQuery T> do zwrócenia kolekcji jednostek  
 Poniższy przykład używa <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> do <xref:System.Data.Services.Client.DataServiceQuery%601> zwrócenia, który jest używany do wywołania tej samej operacji usługi GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 W tym przykładzie <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda jest używana do dodawania <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> parametru do kwerendy, a metoda jest używana do uwzględnienia powiązanych obiektów Order_Details w wynikach.  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>Wywołanie\<execute T> do zwrócenia pojedynczej jednostki  
 Poniższy przykład wywołuje operację usługi o nazwie GetNewestOrder, która zwraca tylko jedną encję Order:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 W tym przykładzie <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda jest używana do żądania tylko jednej jednostki Zlecenia w wykonaniu.  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Wywołanie\<execute T> do zwrócenia kolekcji wartości pierwotnych  
 Poniższy przykład wywołuje operację usługi, która zwraca kolekcję wartości ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Wywołanie\<execute T> do zwrócenia pojedynczej pierwotnej wartości  
 Poniższy przykład wywołuje operację usługi, która zwraca wartość pojedynczego ciągu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Ponownie w tym <xref:System.Linq.Enumerable.FirstOrDefault%2A> przykładzie metoda jest używana do żądania tylko pojedynczej wartości całkowitej podczas wykonywania.  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>Wywoływanie operacji usługi, która nie zwraca żadnych danych  
 Poniższy przykład wywołuje operację usługi, która zwraca żadnych danych:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Ponieważ nie są zwracane dane, wartość wykonania nie jest przypisana. Jedyną wskazówką, że żądanie zakończyło <xref:System.Data.Services.Client.DataServiceQueryException> się pomyślnie, jest to, że nie jest wywoływane.  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>Wywołanie operacji usługi asynchronicznie  
 Poniższy przykład wywołuje operację usługi asynchronicznie przez wywołanie <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> i: <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Ponieważ żadne dane nie są zwracane, wartość zwracana przez wykonanie nie jest przypisana. Jedyną wskazówką, że żądanie zakończyło <xref:System.Data.Services.Client.DataServiceQueryException> się pomyślnie, jest to, że nie jest wywoływane.  
  
 W poniższym przykładzie wywołuje tę samą operację <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>usługi asynchronicznie przy użyciu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Zobacz też

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
