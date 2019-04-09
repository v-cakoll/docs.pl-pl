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
ms.openlocfilehash: 75691a49624c179166d18225fac9fdc6c17a2308
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138102"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="454bd-102">Instrukcje: Definiowanie operacji usługi (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="454bd-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="454bd-103">ujawniać metod, które są zdefiniowane na serwerze jako operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="454bd-103">expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="454bd-104">Operacje usługi umożliwiają usługi danych w celu zapewnienia dostępu za pomocą identyfikatora URI do metody, która jest zdefiniowana na serwerze.</span><span class="sxs-lookup"><span data-stu-id="454bd-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="454bd-105">Aby zdefiniować operacji usługi, należy zastosować [`WebGet]` lub `[WebInvoke]` atrybutu do metody.</span><span class="sxs-lookup"><span data-stu-id="454bd-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="454bd-106">Aby zapewnić obsługę operatorów zapytań, operacja usługi musi zwracać <xref:System.Linq.IQueryable%601> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="454bd-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="454bd-107">Operacje usługi mogą uzyskiwać dostęp do bazowego źródła danych za pośrednictwem <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> właściwość <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="454bd-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="454bd-108">Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="454bd-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="454bd-109">W przykładzie w tym temacie zdefiniowano operacji usługi o nazwie `GetOrdersByCity` zwracającego filtrowane <xref:System.Linq.IQueryable%601> wystąpienie `Orders` i pokrewnych `Order_Details` obiektów.</span><span class="sxs-lookup"><span data-stu-id="454bd-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="454bd-110">Przykład uzyskuje dostęp do <xref:System.Data.Objects.ObjectContext> wystąpienia, który jest źródłem danych usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="454bd-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="454bd-111">Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="454bd-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="454bd-112">Definiowanie operacji usługi w usłudze danych Northwind</span><span class="sxs-lookup"><span data-stu-id="454bd-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="454bd-113">W projekcie Usługa danych Northwind Otwórz plik Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="454bd-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="454bd-114">W `Northwind` klasy, zdefiniuj metodę działania usługi o nazwie `GetOrdersByCity` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="454bd-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="454bd-115">W `InitializeService` metody `Northwind` klasy, Dodaj następujący kod, aby umożliwić dostęp do operacji usługi:</span><span class="sxs-lookup"><span data-stu-id="454bd-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="454bd-116">Aby wykonać zapytanie GetOrdersByCity operacji usługi</span><span class="sxs-lookup"><span data-stu-id="454bd-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="454bd-117">W przeglądarce internetowej wprowadź jedną z następujących identyfikatorów URI do wywołania operacji usługi, która jest zdefiniowana w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="454bd-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="454bd-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="454bd-118">Example</span></span>  
 <span data-ttu-id="454bd-119">Poniższy przykład wykonuje operacji usługi o nazwie `GetOrderByCity` na Usługa danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="454bd-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="454bd-120">Ta operacja użyto ADO.NET Entity Framework, aby zwrócić zestaw `Orders` i pokrewnych `Order_Details` obiektów jako <xref:System.Linq.IQueryable%601> wystąpienia na podstawie miasta podanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="454bd-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="454bd-121">Operatory zapytań są obsługiwane dla tego punktu końcowego operacji usługi, ponieważ metoda ta zwraca <xref:System.Linq.IQueryable%601> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="454bd-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="454bd-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="454bd-122">See also</span></span>

- [<span data-ttu-id="454bd-123">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="454bd-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
