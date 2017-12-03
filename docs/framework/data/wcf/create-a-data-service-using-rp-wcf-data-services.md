---
title: "Porady: Tworzenie usługi danych przy użyciu dostawcy odbicia (usługi danych WCF)"
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
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11f01a88e1d276321384f00f3e103322ccaef339
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="8896b-102">Porady: Tworzenie usługi danych przy użyciu dostawcy odbicia (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="8896b-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="8896b-103">Umożliwia zdefiniowanie modelu danych, na podstawie klasy dowolnego tak długo, jak te klasy są widoczne jako obiekty, które implementują <xref:System.Linq.IQueryable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8896b-103"> enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="8896b-104">Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8896b-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8896b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8896b-105">Example</span></span>  
 <span data-ttu-id="8896b-106">W poniższym przykładzie zdefiniowano modelu danych, która obejmuje `Orders` i `Items`.</span><span class="sxs-lookup"><span data-stu-id="8896b-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="8896b-107">Klasa kontenera jednostek `OrderItemData` ma dwóch metod publicznych, które zwracają <xref:System.Linq.IQueryable%601> interfejsów.</span><span class="sxs-lookup"><span data-stu-id="8896b-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="8896b-108">Te interfejsy są zestawy jednostek tego `Orders` i `Items` typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="8896b-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="8896b-109">`Order` Może zawierać wielu `Items`, więc `Orders` typ jednostki ma `Items` właściwości nawigacji zwracającej Kolekcja `Items` obiektów.</span><span class="sxs-lookup"><span data-stu-id="8896b-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="8896b-110">`OrderItemData` Klasy kontenera jednostka jest ogólny typ <xref:System.Data.Services.DataService%601> klasy, z którego `OrderItems` pochodzi usługi danych.</span><span class="sxs-lookup"><span data-stu-id="8896b-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8896b-111">W tym przykładzie pokazano dostawcy danych w pamięci i zmiany nie są zachowywane poza bieżącego wystąpienia obiektu, nie istnieje żadnych korzyści pochodzi od wykonania <xref:System.Data.Services.IUpdatable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8896b-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="8896b-112">Na przykład, który implementuje <xref:System.Data.Services.IUpdatable> interfejsu, zobacz [porady: Tworzenie usługi danych przy użyciu składnika LINQ to SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8896b-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="8896b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8896b-113">See Also</span></span>  
 [<span data-ttu-id="8896b-114">Porady: Tworzenie usługi danych do źródła danych SQL za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="8896b-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [<span data-ttu-id="8896b-115">Dostawców usług danych</span><span class="sxs-lookup"><span data-stu-id="8896b-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="8896b-116">Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8896b-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
