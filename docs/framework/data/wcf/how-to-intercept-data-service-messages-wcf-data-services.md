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
ms.openlocfilehash: b5fdbaa25f55caf3de2f0591b7258d4a7dcb1b7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586400"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="9c268-102">Instrukcje: Intercept Data Service Messages (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9c268-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="9c268-103">Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], mogą przechwycić komunikaty żądania, tak aby dodać logikę niestandardową operacji.</span><span class="sxs-lookup"><span data-stu-id="9c268-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="9c268-104">Aby przechwycenia wiadomości, należy użyć metody specjalnie atrybutami w usłudze data.</span><span class="sxs-lookup"><span data-stu-id="9c268-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="9c268-105">Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9c268-105">For more information, see [Interceptors](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="9c268-106">W przykładzie w tym temacie użyto usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="9c268-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="9c268-107">Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9c268-107">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="9c268-108">Aby zdefiniować interceptor zapytania dla zestawu jednostek zamówienia</span><span class="sxs-lookup"><span data-stu-id="9c268-108">To define a query interceptor for the Orders entity set</span></span>  
  
1.  <span data-ttu-id="9c268-109">W projekcie Usługa danych Northwind Otwórz plik Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="9c268-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="9c268-110">Na stronie kodowej dla `Northwind` klasy, Dodaj następujący kod `using` — instrukcja (`Imports` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9c268-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  <span data-ttu-id="9c268-111">W `Northwind` klasy, zdefiniuj metodę działania usługi o nazwie `OnQueryOrders` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c268-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="9c268-112">Aby zdefiniować interceptor zmiany dla zestawu jednostek produktów</span><span class="sxs-lookup"><span data-stu-id="9c268-112">To define a change interceptor for the Products entity set</span></span>  
  
1.  <span data-ttu-id="9c268-113">W projekcie Usługa danych Northwind Otwórz plik Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="9c268-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="9c268-114">W `Northwind` klasy, zdefiniuj metodę działania usługi o nazwie `OnChangeProducts` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c268-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="9c268-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c268-115">Example</span></span>  
 <span data-ttu-id="9c268-116">W tym przykładzie definiuje metodę interceptor zapytania `Orders` zestaw jednostek, która zwraca wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="9c268-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="9c268-117">To wyrażenie zawiera delegata, która filtruje żądania `Orders` oparte na powiązane `Customers` mają nazwę określonego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="9c268-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="9c268-118">Nazwa z kolei jest określana na podstawie użytkownika wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="9c268-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="9c268-119">W tym przykładzie założono, że usługa danych jest hostowana w aplikacji sieci Web platformy ASP.NET, która używa usługi WCF i czy jest włączone uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="9c268-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="9c268-120"><xref:System.Web.HttpContext> Klasa jest używana do pobierania zasady bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="9c268-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="9c268-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c268-121">Example</span></span>  
 <span data-ttu-id="9c268-122">W tym przykładzie definiuje metodę interceptor zmiany `Products` zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="9c268-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="9c268-123">Ta metoda sprawdza poprawność danych wejściowych do usługi w przypadku <xref:System.Data.Services.UpdateOperations.Add> lub <xref:System.Data.Services.UpdateOperations.Change> operacji i zgłasza wyjątek, jeśli wprowadzono zmiany, aby nieobsługiwane produktu.</span><span class="sxs-lookup"><span data-stu-id="9c268-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="9c268-124">Blokuje usunięcie produktów jako nieobsługiwanej operacji.</span><span class="sxs-lookup"><span data-stu-id="9c268-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="9c268-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c268-125">See also</span></span>
- [<span data-ttu-id="9c268-126">Instrukcje: Definiowanie operacji usługi</span><span class="sxs-lookup"><span data-stu-id="9c268-126">How to: Define a Service Operation</span></span>](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="9c268-127">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="9c268-127">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
