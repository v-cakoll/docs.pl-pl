---
title: Przetwarzanie wsadowe operacji (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 6d2e3ff7c1dcf3f2c5beb4f6fa9ce8391e2fca2e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087897"
---
# <a name="batching-operations-wcf-data-services"></a>Przetwarzanie wsadowe operacji (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Obsługuje wsadowe przetwarzanie żądań [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi. Aby uzyskać więcej informacji, zobacz [OData: przetwarzanie wsadowe](https://go.microsoft.com/fwlink/?LinkId=186075). W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], każda operacja, która używa <xref:System.Data.Services.Client.DataServiceContext>, takich jak wykonywanie zapytania lub zapisywania zmian, wyniki w oddzielnym żądaniu wysyłanych do usługi danych. W celu utrzymania logiczne zakres rodzaje operacji, można jawnie zdefiniować operacyjnej partii. Zapewnia to, że wszystkie operacje w partii są wysyłane do usługi danych w ramach pojedynczego żądania HTTP, korzystanie z serwera przetwarzania niepodzielne operacje i zmniejsza liczbę rund do usługi danych.  
  
## <a name="batching-query-operations"></a>Przetwarzanie wsadowe operacji zapytań  
 Aby wykonywać wiele zapytań w jednej partii, należy utworzyć każdej kwerendy w zadaniu wsadowym jako osobne wystąpienie <xref:System.Data.Services.Client.DataServiceRequest%601> klasy. Tworząc w ten sposób żądania zapytania, samo zapytanie jest zdefiniowany jako identyfikator URI i jest zgodna z zasadami na potrzeby adresowania zasobów. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Zapytanie wsadowej żądania są wysyłane do danych usługi, kiedy <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metoda jest wywoływana, zawierającą obiekty żądania zapytania. Ta metoda zwraca <xref:System.Data.Services.Client.DataServiceResponse> obiektu, który jest kolekcją z <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów, które reprezentują odpowiedzi do poszczególnych kwerend w zadaniu wsadowym, z których każdy zawiera kolekcję obiektów zwróconych przez zapytanie lub błąd informacji. W przypadku dowolnego pojedynczego zapytania w partii nie powiedzie, informacje o błędzie jest zwracany w <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektu dla tej operacji, który uległ awarii, a pozostałe operacje nadal są wykonywane. Aby uzyskać więcej informacji, zobacz [porady: wykonywanie zapytań w partii](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Wsadowa zapytania mogą być również wykonywane asynchronicznie. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Przetwarzanie wsadowe operacji SaveChanges  
 Gdy wywołujesz <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody, wszystkie zmiany, które żądania kontekst ścieżki są tłumaczone na operacje oparte na protokole REST, które są wysyłane jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi. Domyślnie te zmiany nie są wysyłane w komunikacie pojedynczego żądania. Aby wymagać, że pojedyncze żądanie wysłania wszystkie zmiany, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> metody i obejmują wartości <xref:System.Data.Services.Client.SaveChangesOptions.Batch> w <xref:System.Data.Services.Client.SaveChangesOptions> wyliczenie, które udostępniają metody.  
  
 Można również asynchronicznie Zapisz zmiany wsadowej. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
