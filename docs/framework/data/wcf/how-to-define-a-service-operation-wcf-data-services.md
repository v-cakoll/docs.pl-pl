---
title: 'Instrukcje: Definiowanie operacji usługi (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: e9d15698c1e020f5b4179efb3e8492f3754ff02f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569131"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Instrukcje: Definiowanie operacji usługi (Usługi danych programu WCF)

Usługi danych programu WCF uwidaczniaj metody, które są zdefiniowane na serwerze jako operacje usługi. Operacje usługi umożliwiają usłudze danych zapewnianie dostępu za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze. Aby zdefiniować operację usługi, zastosuj atrybut [`WebGet]` lub `[WebInvoke]` do metody. Aby obsługiwać operatory zapytań, operacja usługi musi zwracać wystąpienie <xref:System.Linq.IQueryable%601>. Operacje usługi mogą uzyskać dostęp do bazowego źródła danych za pomocą właściwości <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> w <xref:System.Data.Services.DataService%601>. Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).

Przykład w tym temacie definiuje operację usługi o nazwie `GetOrdersByCity`, która zwraca filtrowane wystąpienie <xref:System.Linq.IQueryable%601> `Orders` i powiązane obiekty `Order_Details`. Przykład uzyskuje dostęp do wystąpienia <xref:System.Data.Objects.ObjectContext>, które jest źródłem danych dla przykładowej usługi danych Northwind. Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md).

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Aby zdefiniować operację usługi w usłudze danych Northwind

1. W projekcie usługi danych Northwind Otwórz plik Northwind. svc.

2. W klasie `Northwind` Zdefiniuj metodę operacji usługi o nazwie `GetOrdersByCity` w następujący sposób:

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. W metodzie `InitializeService` klasy `Northwind` Dodaj następujący kod, aby umożliwić dostęp do operacji usługi:

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>Aby wykonać zapytanie dotyczące operacji usługi GetOrdersByCity

- W przeglądarce sieci Web wprowadź jeden z następujących identyfikatorów URI, aby wywołać operację usługi, która jest zdefiniowana w następującym przykładzie:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Przykład

Poniższy przykład implementuje operację usługi o nazwie `GetOrderByCity` w usłudze danych Northwind. Ta operacja używa Entity Framework ADO.NET do zwrócenia zestawu `Orders` i powiązanych obiektów `Order_Details` jako wystąpienia <xref:System.Linq.IQueryable%601> na podstawie podanej nazwy miasta.

> [!NOTE]
> Operatory zapytań są obsługiwane w tym punkcie końcowym operacji usługi, ponieważ metoda zwraca wystąpienie <xref:System.Linq.IQueryable%601>.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
