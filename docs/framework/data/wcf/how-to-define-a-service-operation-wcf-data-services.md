---
title: 'Instrukcje: Zdefiniuj operację usługi (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 3154fadeda400440f68a184b430b7ff15a02203d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780084"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Instrukcje: Zdefiniuj operację usługi (Usługi danych programu WCF)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]uwidaczniaj metody, które są zdefiniowane na serwerze jako operacje usługi. Operacje usługi umożliwiają usłudze danych zapewnianie dostępu za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze. Aby zdefiniować operację usługi, zastosuj atrybut [`WebGet]` lub `[WebInvoke]` do metody. Aby obsługiwać operatory zapytań, operacja usługi musi zwracać <xref:System.Linq.IQueryable%601> wystąpienie. Operacje usługi mogą uzyskać dostęp do bazowego źródła danych <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> za pomocą właściwości <xref:System.Data.Services.DataService%601>w. Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).

Przykład w tym temacie definiuje operację usługi o `GetOrdersByCity` nazwie, która zwraca filtrowane <xref:System.Linq.IQueryable%601> wystąpienie `Orders` i powiązane `Order_Details` obiekty. Przykład uzyskuje dostęp <xref:System.Data.Objects.ObjectContext> do wystąpienia, które jest źródłem danych dla przykładowej usługi danych Northwind. Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md).

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Aby zdefiniować operację usługi w usłudze danych Northwind

1. W projekcie usługi danych Northwind Otwórz plik Northwind. svc.

2. W klasie Zdefiniuj metodę operacji usługi o nazwie `GetOrdersByCity` w następujący sposób: `Northwind`

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. W metodzie `Northwind` klasy Dodaj następujący kod, aby umożliwić dostęp do operacji usługi: `InitializeService`

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>Aby wykonać zapytanie dotyczące operacji usługi GetOrdersByCity

- W przeglądarce sieci Web wprowadź jeden z następujących identyfikatorów URI, aby wywołać operację usługi, która jest zdefiniowana w następującym przykładzie:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Przykład

Poniższy przykład implementuje operację usługi o nazwie `GetOrderByCity` w usłudze danych Northwind. Ta operacja używa Entity Framework ADO.NET do zwrócenia zestawu `Orders` i powiązanych `Order_Details` obiektów jako <xref:System.Linq.IQueryable%601> wystąpienia na podstawie podanej nazwy miasta.

> [!NOTE]
> Operatory zapytań są obsługiwane w tym punkcie końcowym operacji usługi, ponieważ metoda <xref:System.Linq.IQueryable%601> zwraca wystąpienie.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
