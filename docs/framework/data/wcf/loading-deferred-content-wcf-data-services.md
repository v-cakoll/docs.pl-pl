---
title: Ładowanie odroczonej zawartości (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 905cf9933b726ba570c16719c8d1883a8588254d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227174"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ładowanie odroczonej zawartości (WCF Data Services)
Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ogranicza ilość danych zwracanych przez zapytanie. Jednak należy jawnie załadować dodatkowych danych, w tym powiązanych jednostek, dane odpowiedzi stronicowane i strumieni danych binarnych, od usługi danych, gdy jest to konieczne. W tym temacie opisano, jak ładowanie odroczonej zawartości do aplikacji.  
  
## <a name="related-entities"></a>Pokrewne jednostki  
 Podczas wykonywania zapytania, zwracane są tylko jednostki w zestawie jednostek zaadresowane. Na przykład, jeśli zapytanie względem usługi danych Northwind zwraca `Customers` jednostek domyślnie powiązane `Orders` jednostki nie są zwracane, mimo że istnieje relacja między `Customers` i `Orders`. Ponadto jeśli stronicowanie zostało włączone w usłudze danych, należy jawnie załadować stron kolejnych danych z usługi. Istnieją dwa sposoby ładowanie powiązanych jednostek:  
  
-   **Wczesne ładowanie**: Możesz użyć `$expand` opcji zapytania żądania, że zapytanie zwraca jednostki, które są powiązane przez skojarzenie go z jednostką ustawić żądanego zapytania. Użyj <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody <xref:System.Data.Services.Client.DataServiceQuery%601> dodać `$expand` opcję, aby zapytanie, które są wysyłane do usługi danych. Możesz poprosić o wielu powiązanych jednostek zestawy, oddzielając je przecinkami, jak w poniższym przykładzie. Wszystkie jednostki, żądane przez zapytania są zwracane w pojedynczą odpowiedź. Poniższy przykład zwraca `Order_Details` i `Customers` wraz z `Orders` zestaw jednostek:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ogranicza do 12 liczbę zestawy jednostek, które mogły zostać uwzględnione w ramach pojedynczego zapytania przy użyciu `$expand` opcji zapytania.  
  
-   **Jawne ładowanie**: Możesz wywołać <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody <xref:System.Data.Services.Client.DataServiceContext> wystąpienia by jawnie ładować powiązanych jednostek. Każde wywołanie <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metoda tworzy oddzielne żądanie do usługi danych. Poniższy przykład jawnie ładuje `Order_Details` dla `Orders` jednostki:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Po zastanowieniu się nad stosownej opcji, należy pamiętać, że istnieje zależność między licznie żądań do usługi danych i ilości danych, które są zwracane w pojedynczą odpowiedź. Za pomocą eager ładowania, gdy aplikacja wymaga skojarzone obiekty i chcesz uniknąć opóźnień dodano dodatkowe żądania jawnie pobierać je. Jednak jeśli istnieją przypadki, gdy aplikacja potrzebuje tylko dane dla określonej jednostki powiązane wystąpień, należy rozważyć jawne ładowanie tych jednostek, wywołując <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie powiązanych jednostek](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Zawartość stronicowana  
 Jeśli stronicowanie zostało włączone w usłudze danych, liczba wpisów w źródle danych, zwraca usługi danych jest ograniczona przez konfigurację usługi danych. Strona limity można ustawić osobno dla każdego zestawu jednostek. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Gdy jest włączone stronicowanie, końcowy wpis w źródle danych zawiera łącze do następnej strony danych. Ten link znajduje się w <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> obiektu. Identyfikator URI następnej strony danych można uzyskać przez wywołanie metody <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody <xref:System.Data.Services.Client.QueryOperationResponse%601> zwracane, jeśli <xref:System.Data.Services.Client.DataServiceQuery%601> jest wykonywany. Zwrócony <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> obiekt jest następnie używana do ładowania następnej strony wyników. Należy wyliczyć wyniku zapytania, przed wywołaniem <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody. Należy rozważyć użycie `do…while` pętli, aby najpierw wyliczyć wyniku zapytania, a następnie wyszukaj `non-null` łącze obok wartości. Gdy <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metoda zwraca `null` (`Nothing` w języku Visual Basic), brak wyniku dodatkowych stron do oryginalnego zapytania. W poniższym przykładzie przedstawiono `do…while` pętli, która ładuje stronicowanej dane klienta z usługi Northwind przykładowych danych.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextlink)]  
  
 Żądania zapytań, które powiązanych jednostek są zwracane w pojedynczą odpowiedź wraz z zestawem żądanej jednostki, limity stronicowania może mieć wpływ na zagnieżdżonych źródeł danych, które są wbudowane z odpowiedzią. Na przykład, gdy limit stronicowania jest skonfigurowany w usłudze Northwind przykładowych danych dla `Customers` zestaw jednostek, niezależnie od limitu stronicowania może być także ustawiona dla powiązane `Orders` jednostki zestawu, jak w poniższym przykładzie z Northwind.svc.cs pliku Definiuje usługę Northwind przykładowych danych.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 W takim przypadku należy zaimplementować stronicowania dla obu najwyższego poziomu `Customers` i zagnieżdżonego `Orders` źródła danych jednostki. W poniższym przykładzie przedstawiono `while` pętli używana do ładowania stron `Orders` jednostki dotyczą wybranego `Customers` jednostki.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextorderslink)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Ładowanie stronicowanych wyników](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Strumienie danych binarnych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia dostęp do danych binarnych, dużych obiektów (BLOB) jako strumień danych. Przesyłanie strumieniowe odracza ładowanie danych binarnych, dopóki nie jest to konieczne, a klient wydajniej może przetwarzać te dane. Aby można było skorzystać z tej funkcji, należy zaimplementować usługę danych <xref:System.Data.Services.Providers.IDataServiceStreamProvider> dostawcy. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Typy jednostek przesyłania strumieniowego jest włączona, są zwracane bez powiązanych danych binarnych. W takim przypadku należy użyć <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metody <xref:System.Data.Services.Client.DataServiceContext> klasy, aby uzyskać dostęp do strumienia danych dla danych binarnych z usługi. Podobnie, użyj <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodę, aby dodać lub zmienić dane binarne dla jednostki jako strumień. Aby uzyskać więcej informacji, zobacz [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
