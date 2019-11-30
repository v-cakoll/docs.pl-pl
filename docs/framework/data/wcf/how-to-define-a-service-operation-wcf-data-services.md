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
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="0dd52-102">Instrukcje: Definiowanie operacji usługi (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="0dd52-102">How to: Define a Service Operation (WCF Data Services)</span></span>

<span data-ttu-id="0dd52-103">Usługi danych programu WCF uwidaczniaj metody, które są zdefiniowane na serwerze jako operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="0dd52-103">WCF Data Services expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="0dd52-104">Operacje usługi umożliwiają usłudze danych zapewnianie dostępu za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0dd52-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="0dd52-105">Aby zdefiniować operację usługi, zastosuj atrybut [`WebGet]` lub `[WebInvoke]` do metody.</span><span class="sxs-lookup"><span data-stu-id="0dd52-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="0dd52-106">Aby obsługiwać operatory zapytań, operacja usługi musi zwracać wystąpienie <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="0dd52-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="0dd52-107">Operacje usługi mogą uzyskać dostęp do bazowego źródła danych za pomocą właściwości <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> w <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="0dd52-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="0dd52-108">Aby uzyskać więcej informacji, zobacz [operacje usługi](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0dd52-108">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="0dd52-109">Przykład w tym temacie definiuje operację usługi o nazwie `GetOrdersByCity`, która zwraca filtrowane wystąpienie <xref:System.Linq.IQueryable%601> `Orders` i powiązane obiekty `Order_Details`.</span><span class="sxs-lookup"><span data-stu-id="0dd52-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="0dd52-110">Przykład uzyskuje dostęp do wystąpienia <xref:System.Data.Objects.ObjectContext>, które jest źródłem danych dla przykładowej usługi danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0dd52-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="0dd52-111">Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0dd52-111">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="0dd52-112">Aby zdefiniować operację usługi w usłudze danych Northwind</span><span class="sxs-lookup"><span data-stu-id="0dd52-112">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="0dd52-113">W projekcie usługi danych Northwind Otwórz plik Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="0dd52-113">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="0dd52-114">W klasie `Northwind` Zdefiniuj metodę operacji usługi o nazwie `GetOrdersByCity` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0dd52-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="0dd52-115">W metodzie `InitializeService` klasy `Northwind` Dodaj następujący kod, aby umożliwić dostęp do operacji usługi:</span><span class="sxs-lookup"><span data-stu-id="0dd52-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="0dd52-116">Aby wykonać zapytanie dotyczące operacji usługi GetOrdersByCity</span><span class="sxs-lookup"><span data-stu-id="0dd52-116">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="0dd52-117">W przeglądarce sieci Web wprowadź jeden z następujących identyfikatorów URI, aby wywołać operację usługi, która jest zdefiniowana w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0dd52-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="0dd52-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="0dd52-118">Example</span></span>

<span data-ttu-id="0dd52-119">Poniższy przykład implementuje operację usługi o nazwie `GetOrderByCity` w usłudze danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0dd52-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="0dd52-120">Ta operacja używa Entity Framework ADO.NET do zwrócenia zestawu `Orders` i powiązanych obiektów `Order_Details` jako wystąpienia <xref:System.Linq.IQueryable%601> na podstawie podanej nazwy miasta.</span><span class="sxs-lookup"><span data-stu-id="0dd52-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="0dd52-121">Operatory zapytań są obsługiwane w tym punkcie końcowym operacji usługi, ponieważ metoda zwraca wystąpienie <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="0dd52-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="0dd52-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dd52-122">See also</span></span>

- [<span data-ttu-id="0dd52-123">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="0dd52-123">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
