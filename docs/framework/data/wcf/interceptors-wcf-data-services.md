---
title: Interceptory (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 17926e144fae206d702c2bcb4f88dd2093442ed5
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517905"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="97578-102">Interceptory (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="97578-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="97578-103">umożliwia aplikacji przechwycenia komunikatów żądań, tak aby dodać logikę niestandardową operacji.</span><span class="sxs-lookup"><span data-stu-id="97578-103">enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="97578-104">Można użyć tej niestandardowej logiki do sprawdzania poprawności danych w wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="97578-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="97578-105">Można również użyć bardziej ograniczyć zakres żądania zapytania, takie jak wstawić niestandardowych zasad autoryzacji na podstawie danego żądania.</span><span class="sxs-lookup"><span data-stu-id="97578-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="97578-106">Przejmowanie odbywa się za pomocą metod specjalnie opartego na atrybutach usługi danych.</span><span class="sxs-lookup"><span data-stu-id="97578-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="97578-107">Te metody są wywoływane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] we właściwym punkcie podczas przetwarzania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="97578-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="97578-108">Interceptory są zdefiniowane na podstawie zestawu jednostek i metody interceptor nie akceptuje parametrów z żądania, takie jak operacje usługi można.</span><span class="sxs-lookup"><span data-stu-id="97578-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="97578-109">Metody interceptor zapytania, które są wywoływane podczas przetwarzania żądania HTTP GET, muszą zwracać Wyrażenie lambda, która określa, czy wystąpienie jednostki interceptor ustawić powinien być zwrócony przez wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="97578-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="97578-110">To wyrażenie jest używany przez usługę danych można uściślić żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="97578-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="97578-111">Oto przykład definicji interceptor zapytania.</span><span class="sxs-lookup"><span data-stu-id="97578-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="97578-112">Aby uzyskać więcej informacji, zobacz [jak: Przechwytywanie wiadomości usługi danych](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="97578-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="97578-113">Interceptory zmiany, które są wywoływane podczas przetwarzania operacji niebędącą zapytaniem, musi zwracać `void` (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="97578-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="97578-114">Zmiana interceptor metody muszą zaakceptować następujące dwa parametry:</span><span class="sxs-lookup"><span data-stu-id="97578-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="97578-115">Parametr typu, który jest zgodny z typem jednostki z zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="97578-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="97578-116">Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru, zostanie naliczona informacje jednostki, które są wysyłane przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="97578-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="97578-117">Parametr typu <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="97578-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="97578-118">Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru, zostanie naliczona operacji, które podejmuje próbę wykonania żądania.</span><span class="sxs-lookup"><span data-stu-id="97578-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="97578-119">Oto przykład definicji interceptor zmiany.</span><span class="sxs-lookup"><span data-stu-id="97578-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="97578-120">Aby uzyskać więcej informacji, zobacz [jak: Przechwytywanie wiadomości usługi danych](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="97578-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="97578-121">Następujące atrybuty są obsługiwane w przypadku zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="97578-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="97578-122">**[QueryInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="97578-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="97578-123">Metody z <xref:System.Data.Services.QueryInterceptorAttribute> zastosowany są wywoływane po odebraniu żądania HTTP GET dla docelowej jednostki zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="97578-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="97578-124">Te metody muszą zawsze zwracać wyrażenia lambda w formie `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="97578-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="97578-125">**[ChangeInterceptor (** *Nazwa zestawu jednostek* **)]**</span><span class="sxs-lookup"><span data-stu-id="97578-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="97578-126">Metody z <xref:System.Data.Services.ChangeInterceptorAttribute> zastosowany są wywoływane po odebraniu żądania HTTP inne niż żądanie HTTP GET dla docelowej jednostki zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="97578-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="97578-127">Te metody muszą zawsze zwracać `void` (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="97578-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="97578-128">Aby uzyskać więcej informacji, zobacz [jak: Przechwytywanie wiadomości usługi danych](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="97578-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97578-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97578-129">See also</span></span>

- [<span data-ttu-id="97578-130">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="97578-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
