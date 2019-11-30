---
title: 'Instrukcje: Przechwytywanie komunikatów usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 4f2d6cf34c820c60181d5287298898af5eb8d038
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569043"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="017c5-102">Instrukcje: Przechwytywanie komunikatów usługi danych (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="017c5-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="017c5-103">Za pomocą Usługi danych programu WCF można przechwycić komunikaty żądania, aby można było dodać logikę niestandardową do operacji.</span><span class="sxs-lookup"><span data-stu-id="017c5-103">With WCF Data Services, you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="017c5-104">Aby przechwycić komunikat, należy użyć specjalnie przypisanych metod w usłudze danych.</span><span class="sxs-lookup"><span data-stu-id="017c5-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="017c5-105">Aby uzyskać więcej informacji, zobacz [Interceptory](interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="017c5-105">For more information, see [Interceptors](interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="017c5-106">W przykładzie w tym temacie jest stosowana Przykładowa usługa danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="017c5-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="017c5-107">Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="017c5-107">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="017c5-108">Aby zdefiniować interceptor zapytania dla zestawu jednostek Orders</span><span class="sxs-lookup"><span data-stu-id="017c5-108">To define a query interceptor for the Orders entity set</span></span>  
  
1. <span data-ttu-id="017c5-109">W projekcie usługi danych Northwind Otwórz plik Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="017c5-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="017c5-110">Na stronie kodowej klasy `Northwind` Dodaj następującą instrukcję `using` (`Imports` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="017c5-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. <span data-ttu-id="017c5-111">W klasie `Northwind` Zdefiniuj metodę operacji usługi o nazwie `OnQueryOrders` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="017c5-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="017c5-112">Aby zdefiniować interceptor zmiany dla zestawu jednostek Products</span><span class="sxs-lookup"><span data-stu-id="017c5-112">To define a change interceptor for the Products entity set</span></span>  
  
1. <span data-ttu-id="017c5-113">W projekcie usługi danych Northwind Otwórz plik Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="017c5-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="017c5-114">W klasie `Northwind` Zdefiniuj metodę operacji usługi o nazwie `OnChangeProducts` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="017c5-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="017c5-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="017c5-115">Example</span></span>  
 <span data-ttu-id="017c5-116">W tym przykładzie zdefiniowano metodę interceptora zapytania dla zestawu jednostek `Orders`, który zwraca wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="017c5-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="017c5-117">To wyrażenie zawiera delegata, który filtruje żądany `Orders` w oparciu o powiązane `Customers` z określoną nazwą kontaktu.</span><span class="sxs-lookup"><span data-stu-id="017c5-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="017c5-118">Nazwa jest z kolei określana na podstawie żądającego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="017c5-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="017c5-119">W tym przykładzie przyjęto założenie, że usługa danych jest hostowana w aplikacji sieci Web ASP.NET używającej programu WCF, a uwierzytelnianie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="017c5-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="017c5-120">Klasa <xref:System.Web.HttpContext> jest używana do pobierania zasady bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="017c5-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="017c5-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="017c5-121">Example</span></span>  
 <span data-ttu-id="017c5-122">W tym przykładzie zdefiniowano metodę interceptora zmian dla zestawu jednostek `Products`.</span><span class="sxs-lookup"><span data-stu-id="017c5-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="017c5-123">Ta metoda sprawdza poprawność danych wejściowych do usługi dla <xref:System.Data.Services.UpdateOperations.Add> lub <xref:System.Data.Services.UpdateOperations.Change> operacji i zgłasza wyjątek w przypadku wprowadzenia zmiany do wycofanego produktu.</span><span class="sxs-lookup"><span data-stu-id="017c5-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="017c5-124">Blokuje również usuwanie produktów jako nieobsługiwaną operację.</span><span class="sxs-lookup"><span data-stu-id="017c5-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="017c5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="017c5-125">See also</span></span>

- [<span data-ttu-id="017c5-126">Instrukcje: Definiowanie operacji usługi</span><span class="sxs-lookup"><span data-stu-id="017c5-126">How to: Define a Service Operation</span></span>](how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="017c5-127">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="017c5-127">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
