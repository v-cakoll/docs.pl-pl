---
title: 'Instrukcje: Intercept Data Service Messages (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: ad0673f72b1a81d6bcfaf0704ccd698eda7bb20c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517846"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Instrukcje: Intercept Data Service Messages (WCF Data Services)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], mogą przechwycić komunikaty żądania, tak aby dodać logikę niestandardową operacji. Aby przechwycenia wiadomości, należy użyć metody specjalnie atrybutami w usłudze data. Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto usługi Northwind przykładowych danych. Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Aby zdefiniować interceptor zapytania dla zestawu jednostek zamówienia  
  
1. W projekcie Usługa danych Northwind Otwórz plik Northwind.svc.  
  
2. Na stronie kodowej dla `Northwind` klasy, Dodaj następujący kod `using` — instrukcja (`Imports` w języku Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. W `Northwind` klasy, zdefiniuj metodę działania usługi o nazwie `OnQueryOrders` w następujący sposób:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Aby zdefiniować interceptor zmiany dla zestawu jednostek produktów  
  
1. W projekcie Usługa danych Northwind Otwórz plik Northwind.svc.  
  
2. W `Northwind` klasy, zdefiniuj metodę działania usługi o nazwie `OnChangeProducts` w następujący sposób:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje metodę interceptor zapytania `Orders` zestaw jednostek, która zwraca wyrażenie lambda. To wyrażenie zawiera delegata, która filtruje żądania `Orders` oparte na powiązane `Customers` mają nazwę określonego kontaktu. Nazwa z kolei jest określana na podstawie użytkownika wysyłającego żądanie. W tym przykładzie założono, że usługa danych jest hostowana w aplikacji sieci Web platformy ASP.NET, która używa usługi WCF i czy jest włączone uwierzytelnianie. <xref:System.Web.HttpContext> Klasa jest używana do pobierania zasady bieżącego żądania.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje metodę interceptor zmiany `Products` zestawu jednostek. Ta metoda sprawdza poprawność danych wejściowych do usługi w przypadku <xref:System.Data.Services.UpdateOperations.Add> lub <xref:System.Data.Services.UpdateOperations.Change> operacji i zgłasza wyjątek, jeśli wprowadzono zmiany, aby nieobsługiwane produktu. Blokuje usunięcie produktów jako nieobsługiwanej operacji.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie operacji usługi](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
