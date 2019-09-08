---
title: Interceptory (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790440"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="a7f28-102">Interceptory (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="a7f28-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a7f28-103">umożliwia aplikacji przechwytywanie komunikatów żądań w celu dodania logiki niestandardowej do operacji.</span><span class="sxs-lookup"><span data-stu-id="a7f28-103">enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="a7f28-104">Możesz użyć tej logiki niestandardowej do walidacji danych w wiadomościach przychodzących.</span><span class="sxs-lookup"><span data-stu-id="a7f28-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="a7f28-105">Można go również użyć, aby dodatkowo ograniczyć zakres żądania zapytania, na przykład w celu wstawienia niestandardowych zasad autoryzacji na podstawie żądania.</span><span class="sxs-lookup"><span data-stu-id="a7f28-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="a7f28-106">Przechwytywanie jest wykonywane przez specjalnie przypisane metody w usłudze danych.</span><span class="sxs-lookup"><span data-stu-id="a7f28-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="a7f28-107">Metody te są wywoływane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] właściwy punkt w przetwarzaniu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a7f28-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="a7f28-108">Interceptory są definiowane na podstawie zestawu jednostek, a metody przechwytywania nie mogą przyjmować parametrów z żądania, takie jak operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="a7f28-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="a7f28-109">Metody interceptora zapytań, które są wywoływane podczas przetwarzania żądania HTTP GET, muszą zwracać wyrażenie lambda, które określa, czy wystąpienie zestawu jednostek interceptora ma być zwracane przez wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="a7f28-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="a7f28-110">To wyrażenie jest używane przez usługę danych w celu dodatkowego uściślenia wymaganej operacji.</span><span class="sxs-lookup"><span data-stu-id="a7f28-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="a7f28-111">Poniżej znajduje się przykładowa definicja interceptora zapytań.</span><span class="sxs-lookup"><span data-stu-id="a7f28-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="a7f28-112">Aby uzyskać więcej informacji, zobacz [jak: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.</span><span class="sxs-lookup"><span data-stu-id="a7f28-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a7f28-113">Interceptory zmian, które są wywoływane podczas przetwarzania operacji innych niż zapytania, muszą zwracać `void` (`Nothing` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a7f28-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="a7f28-114">Metody przechwytywania zmian muszą przyjmować następujące dwa parametry:</span><span class="sxs-lookup"><span data-stu-id="a7f28-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="a7f28-115">Parametr typu, który jest zgodny z typem jednostki zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="a7f28-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="a7f28-116">Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru będzie odzwierciedlać informacje o jednostce wysyłane przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="a7f28-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="a7f28-117">Parametr typu <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="a7f28-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="a7f28-118">Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru będzie odzwierciedlać operację wykonywaną przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="a7f28-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="a7f28-119">Poniżej znajduje się przykładowa definicja interceptora zmian.</span><span class="sxs-lookup"><span data-stu-id="a7f28-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="a7f28-120">Aby uzyskać więcej informacji, zobacz [jak: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.</span><span class="sxs-lookup"><span data-stu-id="a7f28-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a7f28-121">Następujące atrybuty są obsługiwane w przypadku przechwycenia.</span><span class="sxs-lookup"><span data-stu-id="a7f28-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="a7f28-122">**[QueryInterceptor (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="a7f28-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="a7f28-123">Metody z <xref:System.Data.Services.QueryInterceptorAttribute> zastosowanym atrybutem są wywoływane, gdy odebrane zostanie żądanie HTTP GET dla zasobu dla obiektu zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="a7f28-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="a7f28-124">Metody te muszą zawsze zwracać wyrażenie lambda w postaci `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="a7f28-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="a7f28-125">**[ChangeInterceptor (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="a7f28-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="a7f28-126">Metody z <xref:System.Data.Services.ChangeInterceptorAttribute> zastosowanym atrybutem są wywoływane, gdy odebrane zostanie żądanie HTTP inne niż żądanie GET protokołu HTTP dla zasobu zestawu jednostek dla obiektu Target.</span><span class="sxs-lookup"><span data-stu-id="a7f28-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="a7f28-127">Metody te muszą zawsze zwracać `void` (`Nothing` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a7f28-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="a7f28-128">Aby uzyskać więcej informacji, zobacz [jak: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.</span><span class="sxs-lookup"><span data-stu-id="a7f28-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f28-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7f28-129">See also</span></span>

- [<span data-ttu-id="a7f28-130">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="a7f28-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
