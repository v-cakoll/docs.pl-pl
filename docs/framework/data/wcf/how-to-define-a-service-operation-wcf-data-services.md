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
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="f5cbf-102">Instrukcje: Zdefiniuj operację usługi (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="f5cbf-102">How to: Define a Service Operation (WCF Data Services)</span></span>

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="f5cbf-103">uwidaczniaj metody, które są zdefiniowane na serwerze jako operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-103">expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="f5cbf-104">Operacje usługi umożliwiają usłudze danych zapewnianie dostępu za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="f5cbf-105">Aby zdefiniować operację usługi, zastosuj atrybut [`WebGet]` lub `[WebInvoke]` do metody.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="f5cbf-106">Aby obsługiwać operatory zapytań, operacja usługi musi zwracać <xref:System.Linq.IQueryable%601> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="f5cbf-107">Operacje usługi mogą uzyskać dostęp do bazowego źródła danych <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> za pomocą właściwości <xref:System.Data.Services.DataService%601>w.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="f5cbf-108">Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f5cbf-108">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="f5cbf-109">Przykład w tym temacie definiuje operację usługi o `GetOrdersByCity` nazwie, która zwraca filtrowane <xref:System.Linq.IQueryable%601> wystąpienie `Orders` i powiązane `Order_Details` obiekty.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="f5cbf-110">Przykład uzyskuje dostęp <xref:System.Data.Objects.ObjectContext> do wystąpienia, które jest źródłem danych dla przykładowej usługi danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="f5cbf-111">Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f5cbf-111">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="f5cbf-112">Aby zdefiniować operację usługi w usłudze danych Northwind</span><span class="sxs-lookup"><span data-stu-id="f5cbf-112">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="f5cbf-113">W projekcie usługi danych Northwind Otwórz plik Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-113">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="f5cbf-114">W klasie Zdefiniuj metodę operacji usługi o nazwie `GetOrdersByCity` w następujący sposób: `Northwind`</span><span class="sxs-lookup"><span data-stu-id="f5cbf-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="f5cbf-115">W metodzie `Northwind` klasy Dodaj następujący kod, aby umożliwić dostęp do operacji usługi: `InitializeService`</span><span class="sxs-lookup"><span data-stu-id="f5cbf-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="f5cbf-116">Aby wykonać zapytanie dotyczące operacji usługi GetOrdersByCity</span><span class="sxs-lookup"><span data-stu-id="f5cbf-116">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="f5cbf-117">W przeglądarce sieci Web wprowadź jeden z następujących identyfikatorów URI, aby wywołać operację usługi, która jest zdefiniowana w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f5cbf-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="f5cbf-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5cbf-118">Example</span></span>

<span data-ttu-id="f5cbf-119">Poniższy przykład implementuje operację usługi o nazwie `GetOrderByCity` w usłudze danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="f5cbf-120">Ta operacja używa Entity Framework ADO.NET do zwrócenia zestawu `Orders` i powiązanych `Order_Details` obiektów jako <xref:System.Linq.IQueryable%601> wystąpienia na podstawie podanej nazwy miasta.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="f5cbf-121">Operatory zapytań są obsługiwane w tym punkcie końcowym operacji usługi, ponieważ metoda <xref:System.Linq.IQueryable%601> zwraca wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f5cbf-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="f5cbf-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5cbf-122">See also</span></span>

- [<span data-ttu-id="f5cbf-123">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="f5cbf-123">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
