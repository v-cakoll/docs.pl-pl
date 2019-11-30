---
title: 'Instrukcje: Włączanie dostępu do usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 0ec9c9a730516b22b4eaa215e042e9393c01d752
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569105"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="40e9c-102">Instrukcje: Włączanie dostępu do usługi danych (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="40e9c-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="40e9c-103">W Usługi danych programu WCF należy jawnie udzielić dostępu do zasobów, które są udostępniane przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="40e9c-103">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="40e9c-104">Oznacza to, że po utworzeniu nowej usługi danych nadal trzeba jawnie zapewnić dostęp do poszczególnych zasobów jako zestawy jednostek.</span><span class="sxs-lookup"><span data-stu-id="40e9c-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="40e9c-105">W tym temacie pokazano, jak włączyć dostęp do odczytu i zapisu do pięciu zestawów jednostek w usłudze danych Northwind, która została utworzona po zakończeniu [przewodnika Szybki Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="40e9c-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="40e9c-106">Ponieważ Wyliczenie <xref:System.Data.Services.EntitySetRights> jest zdefiniowane przy użyciu <xref:System.FlagsAttribute>, można użyć operatora logicznego OR, aby określić wiele uprawnień dla jednego zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="40e9c-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40e9c-107">Każdy klient, który może uzyskać dostęp do aplikacji ASP.NET, może również uzyskać dostęp do zasobów udostępnianych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="40e9c-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="40e9c-108">W przypadku usługi danych produkcyjnych aby zapobiec nieautoryzowanemu dostępowi do zasobów, należy również zabezpieczyć samą aplikację.</span><span class="sxs-lookup"><span data-stu-id="40e9c-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="40e9c-109">Aby uzyskać więcej informacji, zobacz [Zabezpieczanie witryn sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="40e9c-109">For more information, see [Securing ASP.NET Web Sites](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="40e9c-110">Aby włączyć dostęp do usługi danych</span><span class="sxs-lookup"><span data-stu-id="40e9c-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="40e9c-111">W kodzie usługi danych Zastąp symbol zastępczy w funkcji `InitializeService` następującym:</span><span class="sxs-lookup"><span data-stu-id="40e9c-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="40e9c-112">Dzięki temu klienci mają dostęp do odczytu i zapisu do `Orders` i `Order_Details` zestawy jednostek oraz dostęp tylko do odczytu do zestawów `Customers`ych jednostek.</span><span class="sxs-lookup"><span data-stu-id="40e9c-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e9c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40e9c-113">See also</span></span>

- [<span data-ttu-id="40e9c-114">Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS</span><span class="sxs-lookup"><span data-stu-id="40e9c-114">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="40e9c-115">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="40e9c-115">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
