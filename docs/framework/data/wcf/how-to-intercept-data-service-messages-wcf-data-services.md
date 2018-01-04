---
title: "Porady: Przechwytywanie danych usługi wiadomości (usługi danych WCF)"
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
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28f69bb7f584c8d9e7031d969dce0052b1541aad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Porady: Przechwytywanie danych usługi wiadomości (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], mogą przechwycić komunikaty żądania, aby mogli dodawać niestandardowej logiki do operacji. Do przechwycenia wiadomości, używasz metody oparte na atrybutach specjalnie w usłudze danych. Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto usługę Northwind przykładowych danych. Ta usługa jest utworzone po zakończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Aby zdefiniować interceptor zapytań wymaga dla zestawu jednostek zlecenia  
  
1.  W projekcie usługi danych Northwind Otwórz plik Northwind.svc.  
  
2.  Na stronie kodu `Northwind` klasy, Dodaj następujący `using` instrukcji (`Imports` w języku Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  W `Northwind` klasy, zdefiniuj metody operację usługi o nazwie `OnQueryOrders` w następujący sposób:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Aby zdefiniować interceptora zmian, dla zestawu jednostek produktów  
  
1.  W projekcie usługi danych Northwind Otwórz plik Northwind.svc.  
  
2.  W `Northwind` klasy, zdefiniuj metody operację usługi o nazwie `OnChangeProducts` w następujący sposób:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje metody interceptora zapytań dla `Orders` zestaw jednostek, który zwraca wartość wyrażenia lambda. Wyrażenie nie zawiera delegata filtrujące żądany `Orders` oparte na powiązanych `Customers` zawierających nazwę określonego kontaktu. Nazwa z kolei jest określana na podstawie użytkownika żądającego. W tym przykładzie przyjęto założenie, że usługa danych jest obsługiwana w aplikacji sieci Web ASP.NET, która używa usług WCF i czy jest włączone uwierzytelnianie. <xref:System.Web.HttpContext> Klasa służy do pobierania zasady bieżącego żądania.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje metodę interceptora zmian `Products` zestawu jednostek. Ta metoda sprawdza dane wejściowe do usługi <xref:System.Data.Services.UpdateOperations.Add> lub <xref:System.Data.Services.UpdateOperations.Change> operacji i zgłasza wyjątek, jeśli wprowadzono zmiany, aby wycofane produktu. Ponadto pozwala na blokowanie usunięcie produktów jako nieobsługiwanej operacji.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Definiowanie operacji usługi](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
