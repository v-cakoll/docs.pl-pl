---
title: 'Instrukcje: Definiowanie operacji usługi (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: fc738f7e81c02e44075ce5ed151ed42452650c94
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518126"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Instrukcje: Definiowanie operacji usługi (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ujawniać metod, które są zdefiniowane na serwerze jako operacji usługi. Operacje usługi umożliwiają usługi danych w celu zapewnienia dostępu za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze. Aby zdefiniować operacji usługi, należy zastosować [`WebGet]` lub `[WebInvoke]` atrybutu do metody. Aby zapewnić obsługę operatorów zapytań, operacja usługi musi zwracać <xref:System.Linq.IQueryable%601> wystąpienia. Operacje usługi mogą uzyskiwać dostęp do bazowego źródła danych za pośrednictwem <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> właściwość <xref:System.Data.Services.DataService%601>. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie zdefiniowano operacji usługi o nazwie `GetOrdersByCity` zwracającego filtrowane <xref:System.Linq.IQueryable%601> wystąpienie `Orders` i pokrewnych `Order_Details` obiektów. Przykład uzyskuje dostęp do <xref:System.Data.Objects.ObjectContext> wystąpienia, który jest źródłem danych usługi Northwind przykładowych danych. Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Definiowanie operacji usługi w usłudze danych Northwind  
  
1. W projekcie Usługa danych Northwind Otwórz plik Northwind.svc.  
  
2. W `Northwind` klasy, zdefiniuj metodę działania usługi o nazwie `GetOrdersByCity` w następujący sposób:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3. W `InitializeService` metody `Northwind` klasy, Dodaj następujący kod, aby umożliwić dostęp do operacji usługi:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>Aby wykonać zapytanie GetOrdersByCity operacji usługi  
  
-   W przeglądarce internetowej wprowadź jedną z następujących identyfikatorów URI do wywołania operacji usługi, która jest zdefiniowana w poniższym przykładzie:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje operacji usługi o nazwie `GetOrderByCity` na Usługa danych Northwind. Ta operacja użyto ADO.NET Entity Framework, aby zwrócić zestaw `Orders` i pokrewnych `Order_Details` obiektów jako <xref:System.Linq.IQueryable%601> wystąpienia na podstawie miasta podanej nazwy.  
  
> [!NOTE]
>  Operatory zapytań są obsługiwane dla tego punktu końcowego operacji usługi, ponieważ metoda ta zwraca <xref:System.Linq.IQueryable%601> wystąpienia.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
