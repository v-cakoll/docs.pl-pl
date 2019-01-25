---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 723f4759f8f3f0152e08b46163545b833727d2d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691757"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia zdefiniowanie modelu danych, który opiera się na dowolne klasy tak długo, jak te klasy są widoczne jako obiekty, które implementują <xref:System.Linq.IQueryable%601> interfejsu. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano modelu danych, która obejmuje `Orders` i `Items`. Klasa kontenera jednostki `OrderItemData` oferuje dwie metody publiczne, które zwracają <xref:System.Linq.IQueryable%601> interfejsów. Te interfejsy są zestawy jednostek `Orders` i `Items` typów jednostek. `Order` Może zawierać wiele `Items`, więc `Orders` typ jednostki ma `Items` właściwość nawigacji, która zwraca kolekcję `Items` obiektów. `OrderItemData` Klasy kontenera jednostki jest ogólny typ <xref:System.Data.Services.DataService%601> klasa, z której `OrderItems` usługi danych jest tworzony.  
  
> [!NOTE]
>  Ponieważ w tym przykładzie przedstawiono dostawcę danych w pamięci, a zmiany nie są utrwalane poza bieżącego wystąpienia obiektu, jest żadnych korzyści pochodną Implementowanie <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać przykład, który implementuje <xref:System.Data.Services.IUpdatable> interfejsu, zobacz [jak: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
