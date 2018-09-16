---
title: 'Instrukcje: Zapewnianie dostępu do usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: eb9d7cd8e62a73f49fd2b0f2fc2572b01109553b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666619"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="7c83a-102">Instrukcje: Zapewnianie dostępu do usługi danych (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="7c83a-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="7c83a-103">W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], należy jawnie zezwolić na dostęp do zasobów, które są udostępniane przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="7c83a-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="7c83a-104">Oznacza to, że po utworzeniu nowej usługi danych, należy nadal jawnie określić, dostęp do poszczególnych zasobów jako zestawy jednostek.</span><span class="sxs-lookup"><span data-stu-id="7c83a-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="7c83a-105">W tym temacie przedstawiono sposób włączania odczytu i zapisu do pięciu jednostki zestawy w usługi danych Northwind, który jest tworzony po ukończeniu [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c83a-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="7c83a-106">Ponieważ <xref:System.Data.Services.EntitySetRights> wyliczenia jest definiowana za pomocą <xref:System.FlagsAttribute>, można użyć logicznych lub operatora, aby określić wiele uprawnień dla pojedynczej jednostki.</span><span class="sxs-lookup"><span data-stu-id="7c83a-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c83a-107">Każdy klient, który może uzyskiwać dostęp do aplikacji ASP.NET również dostęp do zasobów udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="7c83a-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="7c83a-108">W środowisku produkcyjnym usługi danych Aby uniemożliwić nieautoryzowany dostęp do zasobów, należy także zabezpieczyć samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7c83a-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="7c83a-109">Aby uzyskać więcej informacji, zobacz [NIB: zabezpieczenia programu ASP.NET](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="7c83a-109">For more information, see [NIB: ASP.NET Security](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="7c83a-110">Aby umożliwić dostęp do usługi danych</span><span class="sxs-lookup"><span data-stu-id="7c83a-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="7c83a-111">W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7c83a-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="7c83a-112">Dzięki temu klienci do odczytu i zapisu do `Orders` i `Order_Details` zestawów jednostek i dostęp tylko do odczytu do `Customers` zestawy jednostek.</span><span class="sxs-lookup"><span data-stu-id="7c83a-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c83a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c83a-113">See Also</span></span>  
 [<span data-ttu-id="7c83a-114">Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="7c83a-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="7c83a-115">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="7c83a-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
