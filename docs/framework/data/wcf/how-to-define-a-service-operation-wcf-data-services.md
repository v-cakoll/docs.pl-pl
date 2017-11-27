---
title: "Porady: Definiowanie operacji usługi (usługi danych WCF)"
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
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: feac51c92a7e963d440eefbae94a58b94f49797e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Porady: Definiowanie operacji usługi (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ujawnia metody, które są zdefiniowane na serwerze jako operacji usługi. Operacje usługi Zezwalaj na dostęp za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze usługi danych. Aby zdefiniować operacji usługi, należy zastosować [`WebGet]` lub `[WebInvoke]` atrybut do metody. Aby obsługiwać operatorów zapytań, musi zwracać operacji usługi <xref:System.Linq.IQueryable%601> wystąpienia. Operacje usługi może uzyskać dostępu do źródła danych za pośrednictwem <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> właściwość <xref:System.Data.Services.DataService%601>. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie zdefiniowano operacji usługi o nazwie `GetOrdersByCity` zwraca wartość filtru <xref:System.Linq.IQueryable%601> wystąpienia `Orders` i pokrewnych `Order_Details` obiektów. Przykład uzyskuje dostęp do <xref:System.Data.Objects.ObjectContext> wystąpienia, który jest źródłem danych Northwind przykładowych danych usługi. Ta usługa jest utworzone po zakończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Aby zdefiniować operacji usługi w usłudze danych Northwind  
  
1.  W projekcie usługi danych Northwind Otwórz plik Northwind.svc.  
  
2.  W `Northwind` klasy, zdefiniuj metody operację usługi o nazwie `GetOrdersByCity` w następujący sposób:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  W `InitializeService` metody `Northwind` klasy, Dodaj następujący kod, aby umożliwić dostęp do operacji usługi:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>Do operacji usługi GetOrdersByCity zapytań  
  
-   W przeglądarce sieci Web wpisz jedno z następujących identyfikatorów URI do wywołania operacji usługi, która jest zdefiniowana w poniższym przykładzie:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje operację usługi o nazwie `GetOrderByCity` w usłudze danych Northwind. Tę operację za pomocą programu ADO.NET Entity Framework zestaw `Orders` i pokrewnych `Order_Details` obiekty jako <xref:System.Linq.IQueryable%601> wystąpienia na podstawie podanych Miasto nazwy.  
  
> [!NOTE]
>  Operatory zapytań są obsługiwane na tym punkcie końcowym operacji usługi, ponieważ metoda zwraca <xref:System.Linq.IQueryable%601> wystąpienia.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usługi danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
