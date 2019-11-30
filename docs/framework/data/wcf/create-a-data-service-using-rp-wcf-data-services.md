---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569291"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="40c2c-102">Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="40c2c-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="40c2c-103">Usługi danych programu WCF umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, tak długo, jak te klasy są udostępniane jako obiekty implementujące interfejs <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="40c2c-103">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="40c2c-104">Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="40c2c-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40c2c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="40c2c-105">Example</span></span>  
 <span data-ttu-id="40c2c-106">W poniższym przykładzie zdefiniowano model danych, który zawiera `Orders` i `Items`.</span><span class="sxs-lookup"><span data-stu-id="40c2c-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="40c2c-107">Klasa kontenera jednostek `OrderItemData` ma dwie metody publiczne, które zwracają interfejsy <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="40c2c-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="40c2c-108">Te interfejsy są zestawami jednostek `Orders` i `Items` typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="40c2c-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="40c2c-109">`Order` może zawierać wiele `Items`, więc typ jednostki `Orders` ma właściwość nawigacji `Items`, która zwraca kolekcję obiektów `Items`.</span><span class="sxs-lookup"><span data-stu-id="40c2c-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="40c2c-110">Klasa kontenera jednostek `OrderItemData` jest typem ogólnym klasy <xref:System.Data.Services.DataService%601>, z której pochodzi usługa danych `OrderItems`.</span><span class="sxs-lookup"><span data-stu-id="40c2c-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40c2c-111">Ponieważ ten przykład ilustruje dostawcę danych w pamięci i zmiany nie są utrwalane poza bieżącymi wystąpieniami obiektów, nie ma korzyści wynikającej z implementacji interfejsu <xref:System.Data.Services.IUpdatable>.</span><span class="sxs-lookup"><span data-stu-id="40c2c-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="40c2c-112">Aby zapoznać się z przykładem implementującym interfejs <xref:System.Data.Services.IUpdatable>, zobacz [How to: Create a Data Service using a the LINQ to SQL Source Data](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="40c2c-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="40c2c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40c2c-113">See also</span></span>

- [<span data-ttu-id="40c2c-114">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="40c2c-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="40c2c-115">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="40c2c-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="40c2c-116">Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="40c2c-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
