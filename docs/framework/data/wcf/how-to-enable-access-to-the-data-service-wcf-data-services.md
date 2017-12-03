---
title: "Porady: Zapewnianie dostępu do usługi Data (usługi danych WCF)"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b41de296143d325ba0e1932831d4a3ef1bd7dc80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="cefa9-102">Porady: Zapewnianie dostępu do usługi Data (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="cefa9-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="cefa9-103">W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], należy jawnie zezwolić na dostęp do zasobów, które są udostępniane przez usługi danych.</span><span class="sxs-lookup"><span data-stu-id="cefa9-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="cefa9-104">Oznacza to, że po utworzeniu nowej usługi danych musi nadal jawnie Podaj, dostęp do poszczególnych zasobów jako zestawy jednostek.</span><span class="sxs-lookup"><span data-stu-id="cefa9-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="cefa9-105">W tym temacie przedstawiono sposób włączania odczytu i zapisu do pięciu jednostki ustawia w usłudze danych Northwind, który jest tworzony po zakończeniu [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cefa9-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="cefa9-106">Ponieważ <xref:System.Data.Services.EntitySetRights> wyliczenie zdefiniowano przy użyciu <xref:System.FlagsAttribute>, można użyć logiczną lub ustaw operatora, aby określić wiele uprawnienia dla pojedynczej jednostki.</span><span class="sxs-lookup"><span data-stu-id="cefa9-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cefa9-107">Klienta, który można uzyskać dostęp do aplikacji ASP.NET można również uzyskać dostęp do zasobów, udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="cefa9-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="cefa9-108">W usłudze danych w środowisku produkcyjnym aby uniemożliwić nieautoryzowany dostęp do zasobów, należy również zabezpieczyć samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cefa9-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="cefa9-109">Aby uzyskać więcej informacji, zobacz [NIB: zabezpieczenia w programie ASP.NET](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="cefa9-109">For more information, see [NIB: ASP.NET Security](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="cefa9-110">Aby włączyć dostęp do usługi danych</span><span class="sxs-lookup"><span data-stu-id="cefa9-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="cefa9-111">W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="cefa9-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="cefa9-112">Dzięki temu klienci miał do odczytu i zapisu do `Orders` i `Order_Details` zestawów jednostek i dostęp tylko do odczytu do `Customers` zestawów jednostek.</span><span class="sxs-lookup"><span data-stu-id="cefa9-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefa9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cefa9-113">See Also</span></span>  
 [<span data-ttu-id="cefa9-114">Porady: Tworzenie usługi danych WCF działającą na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="cefa9-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="cefa9-115">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="cefa9-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
