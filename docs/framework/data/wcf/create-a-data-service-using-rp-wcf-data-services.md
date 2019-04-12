---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 233b17de17b7f50547b2f4fbf6a543d7258183cf
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517099"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="bddd9-102">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="bddd9-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="bddd9-103">Umożliwia zdefiniowanie modelu danych, który opiera się na dowolne klasy tak długo, jak te klasy są widoczne jako obiekty, które implementują <xref:System.Linq.IQueryable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bddd9-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="bddd9-104">Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="bddd9-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bddd9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="bddd9-105">Example</span></span>  
 <span data-ttu-id="bddd9-106">W poniższym przykładzie zdefiniowano modelu danych, która obejmuje `Orders` i `Items`.</span><span class="sxs-lookup"><span data-stu-id="bddd9-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="bddd9-107">Klasa kontenera jednostki `OrderItemData` oferuje dwie metody publiczne, które zwracają <xref:System.Linq.IQueryable%601> interfejsów.</span><span class="sxs-lookup"><span data-stu-id="bddd9-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="bddd9-108">Te interfejsy są zestawy jednostek `Orders` i `Items` typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="bddd9-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="bddd9-109">`Order` Może zawierać wiele `Items`, więc `Orders` typ jednostki ma `Items` właściwość nawigacji, która zwraca kolekcję `Items` obiektów.</span><span class="sxs-lookup"><span data-stu-id="bddd9-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="bddd9-110">`OrderItemData` Klasy kontenera jednostki jest ogólny typ <xref:System.Data.Services.DataService%601> klasa, z której `OrderItems` usługi danych jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="bddd9-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bddd9-111">Ponieważ w tym przykładzie przedstawiono dostawcę danych w pamięci, a zmiany nie są utrwalane poza bieżącego wystąpienia obiektu, jest żadnych korzyści pochodną Implementowanie <xref:System.Data.Services.IUpdatable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bddd9-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="bddd9-112">Aby uzyskać przykład, który implementuje <xref:System.Data.Services.IUpdatable> interfejsu, zobacz [jak: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="bddd9-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="bddd9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bddd9-113">See also</span></span>

- [<span data-ttu-id="bddd9-114">Instrukcje: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych</span><span class="sxs-lookup"><span data-stu-id="bddd9-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="bddd9-115">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="bddd9-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="bddd9-116">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="bddd9-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
