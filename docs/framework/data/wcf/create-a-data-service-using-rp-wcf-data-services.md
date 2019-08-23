---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: fb40a60850739147b2bf0f15a3babfe1d0dfa486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965792"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="114f2-102">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="114f2-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="114f2-103">umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, tak długo, jak te klasy są udostępniane jako obiekty, które <xref:System.Linq.IQueryable%601> implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="114f2-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="114f2-104">Aby uzyskać więcej informacji, zobacz [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="114f2-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="114f2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="114f2-105">Example</span></span>  
 <span data-ttu-id="114f2-106">W poniższym przykładzie zdefiniowano model danych, który `Orders` zawiera `Items`i.</span><span class="sxs-lookup"><span data-stu-id="114f2-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="114f2-107">Klasa `OrderItemData` kontenera jednostek ma dwie metody publiczne, które zwracają <xref:System.Linq.IQueryable%601> interfejsy.</span><span class="sxs-lookup"><span data-stu-id="114f2-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="114f2-108">Te interfejsy są zestawami `Orders` jednostek typów jednostek i. `Items`</span><span class="sxs-lookup"><span data-stu-id="114f2-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="114f2-109">`Items` `Orders` `Items` Może zawierać wiele, więc typ jednostki ma właściwość nawigacji, która zwraca kolekcję `Items` obiektów. `Order`</span><span class="sxs-lookup"><span data-stu-id="114f2-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="114f2-110">Klasa kontenera <xref:System.Data.Services.DataService%601> jednostek jest typem ogólnym klasy, z której `OrderItems` pochodzi usługa danych. `OrderItemData`</span><span class="sxs-lookup"><span data-stu-id="114f2-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="114f2-111">Ponieważ ten przykład ilustruje dostawcę danych w pamięci, a zmiany nie są utrwalane poza bieżącymi wystąpieniami obiektów, nie ma korzyści wynikającej z implementacji <xref:System.Data.Services.IUpdatable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="114f2-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="114f2-112">Aby zapoznać się z przykładem <xref:System.Data.Services.IUpdatable> implementującym Interfejs [, zobacz How to: Tworzenie usługi danych przy użyciu źródła](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)danych LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="114f2-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="114f2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="114f2-113">See also</span></span>

- [<span data-ttu-id="114f2-114">Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych</span><span class="sxs-lookup"><span data-stu-id="114f2-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="114f2-115">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="114f2-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="114f2-116">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="114f2-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
