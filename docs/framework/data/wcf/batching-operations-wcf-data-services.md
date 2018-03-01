---
title: "Przetwarzanie wsadowe operacji (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65bf6bfd0bd437848137506605a958f5f2e8d750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="batching-operations-wcf-data-services"></a>Przetwarzanie wsadowe operacji (usługi danych WCF)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Obsługuje przetwarzanie żądania wsadowe [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi. Aby uzyskać więcej informacji, zobacz [OData: przetwarzanie wsadowe](http://go.microsoft.com/fwlink/?LinkId=186075). W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], każdej operacji, która używa <xref:System.Data.Services.Client.DataServiceContext>, takiej jak wykonywanie zapytania lub zapisywania zmian, wyniki w oddzielnych żądania wysyłane do usługi danych. Aby zachować logicznej zakresu dla zestawów działań, można jawnie definiować partie operacyjnej. Dzięki temu wszystkie operacje w partii są wysyłane do usługi data pojedyncze żądanie HTTP, umożliwia serwerowi przetwarzania operacji automatycznie czy zmniejsza liczbę rund do usługi danych.  
  
## <a name="batching-query-operations"></a>Przetwarzanie wsadowe operacje kwerend  
 Do wykonania wielu zapytań w jednym zadaniu wsadowym, należy utworzyć każdego zapytania w partii jako oddzielnego wystąpienia <xref:System.Data.Services.Client.DataServiceRequest%601> klasy. Podczas tworzenia żądania zapytania w ten sposób samą kwerendę jest zdefiniowany jako identyfikatora URI i wynika z zasady na potrzeby adresowania zasobów. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Żąda wsadów zapytania są wysyłane do danych usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> wywoływana jest metoda, który zawiera obiekty żądania zapytania. Ta metoda zwraca <xref:System.Data.Services.Client.DataServiceResponse> obiektu, który jest kolekcją z <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów, które reprezentują odpowiedzi na zapytania poszczególnych w partii, z których każdy zawiera kolekcję obiektów zwróconych przez zapytanie lub błąd informacji. W przypadku awarii żadnej operacji pojedynczego zapytania w partii informacje o błędzie jest zwracany w <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektu dla tej operacji, które zakończyły się niepowodzeniem i pozostałe operacje nadal są wykonywane. Aby uzyskać więcej informacji, zobacz [porady: wykonywanie zapytań w partii](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Wsadów zapytania mogą być również wykonywane asynchronicznie. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Przetwarzanie wsadowe operacji SaveChanges  
 Podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda, wszystkie zmiany, które ścieżki są tłumaczone na operacje opartego na interfejsie REST, które są wysyłane w kontekście żądania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi. Domyślnie te zmiany nie są wysyłane w komunikacie pojedyncze żądanie. Aby wymagać, że pojedyncze żądanie wysłania wszystkie zmiany, należy wywołać <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> — metoda i zawiera wartość <xref:System.Data.Services.Client.SaveChangesOptions.Batch> w <xref:System.Data.Services.Client.SaveChangesOptions> wyliczenie się do metody.  
  
 Można również asynchronicznie zapisać zmiany wsadowej. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
