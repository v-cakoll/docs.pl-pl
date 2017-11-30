---
title: "Ładowanie odłożone zawartości (usługi danych WCF)"
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
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43e7fc6ebc4101586b67b0982b16cefbfff2d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ładowanie odłożone zawartości (usługi danych WCF)
Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ogranicza ilość danych, która zwraca zapytanie. Można jednak w sposób jawny załadować dodatkowych danych, w tym powiązanych jednostek, dane odpowiedzi stronicowana i strumieni danych binarnych, w usłudze danych, gdy potrzebny jest. W tym temacie opisano, jak załadować takiej odroczonego zawartości do aplikacji.  
  
## <a name="related-entities"></a>Powiązanych jednostek  
 Podczas wykonywania zapytania, zwracane są tylko jednostki w zestawie jednostek zaadresowane. Na przykład, jeśli zapytanie z usługą danych Northwind zwraca `Customers` jednostek domyślnie pokrewny `Orders` jednostek nie są zwracane, nawet jeśli istnieje relacja między `Customers` i `Orders`. Ponadto włączenie stronicowania w usłudze danych, należy jawnie załadować danych kolejnych stron z usługi. Istnieją dwa sposoby załadować jednostek pokrewnych:  
  
-   **Ładowanie wczesny**: można użyć `$expand` opcji zapytania żądania, że kwerenda zwraca jednostki, które są powiązane przez skojarzenie, aby jednostka ustawić żądanego zapytania. Użyj <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda <xref:System.Data.Services.Client.DataServiceQuery%601> można dodać `$expand` opcję zapytania, które są wysyłane do usługi danych. Można zażądać obiektu pokrewnego wielu zestawów, oddzielając je przecinkami, jak w poniższym przykładzie. Wszystkie obiekty wymagane przez zapytanie są zwracane w pojedynczą odpowiedź. Poniższy przykład zwraca `Order_Details` i `Customers` razem z `Orders` zestawu jednostek:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ograniczone do 12 liczba zestawów jednostek, które mogą znajdować się w jednym zapytaniu przy użyciu `$expand` opcji zapytania.  
  
-   **Jawne ładowania**: można wywołać <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> wystąpienia by jawnie ładować powiązanych jednostek. Każde wywołanie <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metoda tworzy oddzielne żądanie do usługi danych. Poniższy przykład jawnie ładuje `Order_Details` dla `Orders` jednostki:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Przy należy wziąć pod uwagę opcji okazuje się, że istnieje zależności między liczby żądań do usługi danych i ilość danych, który jest zwracany w jednej odpowiedzi. Użyj wczesny ładowania, gdy aplikacja wymaga skojarzone obiekty i chce się uniknąć dodano opóźnienie dodatkowych żądań do jawnie je pobrać. Jednak jeśli istnieją przypadki, gdy aplikacja musi tylko dane dla wystąpień określonego obiektu pokrewnego, należy rozważyć jawnego ładowania tych jednostek, wywołując <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: obciążenia powiązanych jednostek](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Zawartość stronicowanej  
 Jeśli stronicowanie zostało włączone w usłudze danych, liczba wpisów w źródle danych, czy dane usługi zwraca jest ograniczona przez konfigurację usługi danych. Strony można skonfigurować limity, osobno dla każdego zestawu jednostek. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Gdy jest włączone stronicowanie, końcowy wpis w źródle danych zawiera łącze do następnej strony danych. To łącze znajduje się w <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> obiektu. Uzyskaj identyfikator URI do następnej strony danych przez wywołanie metody <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metoda <xref:System.Data.Services.Client.QueryOperationResponse%601> zwracane, jeśli <xref:System.Data.Services.Client.DataServiceQuery%601> jest wykonywana. Zwrócona <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> obiekt jest następnie używany do załadowania następnej strony wyników. Należy wyliczyć wyniku zapytania przed wywołaniem <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody. Należy rozważyć użycie `do…while` pętli najpierw wyliczyć wyniku zapytania, a następnie wyszukaj `non-null` łącza Następna wartość. Gdy <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metoda zwraca `null` (`Nothing` w języku Visual Basic), Brak stron dodatkowych wyników oryginalnego zapytania. W poniższym przykładzie przedstawiono `do…while` pętli, który ładuje stronicowanej dane klienta z usługi Northwind przykładowych danych.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextlink)]  
  
 Żądania zapytań, które jednostek powiązanych z są zwracane w pojedynczą odpowiedź wraz z zestawu jednostek żądanego, limity stronicowania może mieć wpływ na zagnieżdżonych źródeł danych, które są dołączone wbudowany z odpowiedzią. Na przykład, jeśli limit stronicowania jest ustawiona w usługę danych Northwind próbki dla `Customers` zestaw jednostek, niezależnie od limit stronicowania można również ustawić dla odnośnych `Orders` jednostki ustawić, jak w poniższym przykładzie z Northwind.svc.cs pliku Definiuje usługę Northwind przykładowych danych.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 W takim przypadku należy zaimplementować stronicowania dla obu najwyższego poziomu `Customers` i zagnieżdżone `Orders` źródeł danych jednostki. W poniższym przykładzie przedstawiono `while` pętli używana do załadowania strony `Orders` jednostki powiązane z zaznaczoną `Customers` jednostki.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextorderslink)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: wyników stronicowanej obciążenia](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Strumienie danych binarnych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umożliwia dostęp do danych dużego obiektu binarnego (BLOB) jako strumienia danych. Przesyłanie strumieniowe różni ładowanie danych binarnych, dopóki nie jest wymagana, a klient wydajniej może przetwarzać danych. Aby korzystać z tej funkcji, Usługa danych musi implementować <xref:System.Data.Services.Providers.IDataServiceStreamProvider> dostawcy. Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego dostawcy](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Po włączeniu przesyłania strumieniowego typów jednostek zwracanych bez powiązanych danych binarnych. W takim przypadku należy użyć <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metody <xref:System.Data.Services.Client.DataServiceContext> klasę, aby uzyskać dostęp do strumienia danych dla danych binarnych z usługi. Podobnie, użyj <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodę, aby dodać lub zmienić dane binarne dla jednostki jako strumień. Aby uzyskać więcej informacji, zobacz [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
