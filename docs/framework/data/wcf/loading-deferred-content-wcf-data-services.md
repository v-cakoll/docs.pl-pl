---
title: Ładowanie odroczonej zawartości (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 7c53ad18e029dbe1f882035c1bffc8f4bfbaa2f9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790413"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ładowanie odroczonej zawartości (Usługi danych programu WCF)
Domyślnie program [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ogranicza ilość danych zwracanych przez zapytanie. Można jednak jawnie ładować dodatkowe dane, w tym powiązane jednostki, stronicowane dane odpowiedzi i strumienie danych binarnych, z usługi danych, gdy jest to potrzebne. W tym temacie opisano sposób ładowania wywnioskowanej zawartości do aplikacji.  
  
## <a name="related-entities"></a>Powiązane jednostki  
 Po wykonaniu zapytania zwracane są tylko jednostki w zestawie jednostek. Na przykład gdy zapytanie względem usługi danych Northwind `Customers` zwraca jednostki, domyślnie powiązane `Orders` jednostki nie są zwracane, nawet jeśli istnieje relacja między `Customers` i `Orders`. Ponadto po włączeniu stronicowania w usłudze danych należy jawnie załadować kolejne strony danych z usługi. Istnieją dwa sposoby ładowania powiązanych jednostek:  
  
- **Eager ładowanie**: Możesz użyć `$expand` opcji zapytania, aby zażądać, aby zapytanie zwracało jednostki powiązane przez skojarzenie z zestawem jednostek, którego żądał zapytanie. Użyj metody z, <xref:System.Data.Services.Client.DataServiceQuery%601> aby dodać `$expand` opcję do zapytania, które jest wysyłane do usługi danych. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Można zażądać wielu powiązanych zestawów jednostek, rozdzielając je przecinkami, tak jak w poniższym przykładzie. Wszystkie jednostki żądane przez zapytanie są zwracane w pojedynczej odpowiedzi. Poniższy przykład zwraca `Order_Details` i `Customers` wraz z `Orders` zestawem jednostek:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ogranicza do 12 liczbę zestawów jednostek, które mogą być uwzględnione w pojedynczym zapytaniu przy użyciu `$expand` opcji zapytania.  
  
- **Jawne ładowanie**: Można wywołać <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodę <xref:System.Data.Services.Client.DataServiceContext> na wystąpieniu, aby jawnie załadować powiązane jednostki. Każde wywołanie <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody tworzy oddzielne żądanie do usługi danych. Poniższy przykład jest jawnie ładowany `Order_Details` `Orders` dla jednostki:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Kiedy należy wziąć pod uwagę, której opcji użyć, należy pamiętać, że istnieje kompromis między liczbą żądań do usługi danych i ilością danych zwracanych w ramach jednej odpowiedzi. Użyj eager ładowania, gdy aplikacja wymaga skojarzonych obiektów i chcesz uniknąć dodanych opóźnień dodatkowych żądań, aby je jawnie pobrać. Jeśli jednak w przypadku aplikacji potrzebne są tylko dane dla konkretnych powiązanych wystąpień jednostek, należy rozważyć jawne załadowanie tych jednostek przez wywołanie <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: Załaduj jednostki](how-to-load-related-entities-wcf-data-services.md)powiązane.  
  
## <a name="paged-content"></a>Zawartość stronicowana  
 Po włączeniu stronicowania w usłudze danych Liczba wpisów w źródle danych zwracanych przez usługę dane jest ograniczona przez konfigurację usługi danych. Limity stron można ustawić osobno dla każdego zestawu jednostek. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md). Po włączeniu stronicowania końcowy wpis w kanale informacyjnym zawiera link do następnej strony danych. Ten link jest zawarty w <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> obiekcie. Aby uzyskać identyfikator URI na następnej stronie danych, należy wywołać <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metodę <xref:System.Data.Services.Client.QueryOperationResponse%601> na zwracanym czasie <xref:System.Data.Services.Client.DataServiceQuery%601> . Zwrócony <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> obiekt jest następnie używany do załadowania następnej strony wyników. Przed wywołaniem <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody należy wyliczyć wynik zapytania. Rozważ użycie `do…while` pętli, aby najpierw wyliczyć wynik zapytania, a następnie wyszukać `non-null` następną wartość linku. Gdy metoda zwróci wartość `null` (`Nothing` w Visual Basic), nie ma dodatkowych stron wynikowych dla oryginalnego zapytania. <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> W poniższym przykładzie przedstawiono `do…while` pętlę, która ładuje dane klienta stronicowanego z przykładowej usługi danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Gdy zapytanie żąda, że powiązane jednostki są zwracane w pojedynczej odpowiedzi wraz z żądanym zestawem jednostek, limity stronicowania mogą mieć wpływ na zagnieżdżone źródła, które są zawarte w tekście odpowiedzi. Na przykład po ustawieniu limitu stronicowania w usłudze danych przykładowych Northwind dla `Customers` zestawu jednostek można również ustawić niezależny limit stronicowania dla powiązanego `Orders` zestawu jednostek, tak jak w poniższym przykładzie z pliku Northwind.svc.cs, który definiuje przykładową usługę danych Northwind.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 W takim przypadku należy zaimplementować stronicowanie zarówno dla źródła danych najwyższego `Customers` poziomu, jak `Orders` i zagnieżdżonych. Poniższy przykład pokazuje `while` pętlę używaną do ładowania `Orders` stron jednostek powiązanych z wybraną `Customers` jednostką.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Załaduj stronicowane](how-to-load-paged-results-wcf-data-services.md)wyniki.  
  
## <a name="binary-data-streams"></a>Strumienie danych binarnych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia dostęp do danych obiektów binarnych (BLOB) w postaci strumienia danych. Przesyłanie strumieniowe polega na załadowaniu danych binarnych, dopóki nie jest to konieczne, a klient może efektywniej przetwarzać te dane. Aby można było skorzystać z tej funkcji, usługa danych musi implementować <xref:System.Data.Services.Providers.IDataServiceStreamProvider> dostawcę. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md). Po włączeniu przesyłania strumieniowego typy jednostek są zwracane bez pokrewnych danych binarnych. W takim przypadku należy użyć <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metody <xref:System.Data.Services.Client.DataServiceContext> klasy, aby uzyskać dostęp do strumienia danych danych binarnych z usługi. Podobnie Użyj <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metody, aby dodać lub zmienić dane binarne dla jednostki jako strumień. Aby uzyskać więcej informacji, zobacz [Praca z danymi binarnymi](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
