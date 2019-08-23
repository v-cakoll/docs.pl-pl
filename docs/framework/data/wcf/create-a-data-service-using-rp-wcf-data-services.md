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
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, tak długo, jak te klasy są udostępniane jako obiekty, które <xref:System.Linq.IQueryable%601> implementują interfejs. Aby uzyskać więcej informacji, zobacz [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano model danych, który `Orders` zawiera `Items`i. Klasa `OrderItemData` kontenera jednostek ma dwie metody publiczne, które zwracają <xref:System.Linq.IQueryable%601> interfejsy. Te interfejsy są zestawami `Orders` jednostek typów jednostek i. `Items` `Items` `Orders` `Items` Może zawierać wiele, więc typ jednostki ma właściwość nawigacji, która zwraca kolekcję `Items` obiektów. `Order` Klasa kontenera <xref:System.Data.Services.DataService%601> jednostek jest typem ogólnym klasy, z której `OrderItems` pochodzi usługa danych. `OrderItemData`  
  
> [!NOTE]
> Ponieważ ten przykład ilustruje dostawcę danych w pamięci, a zmiany nie są utrwalane poza bieżącymi wystąpieniami obiektów, nie ma korzyści wynikającej z implementacji <xref:System.Data.Services.IUpdatable> interfejsu. Aby zapoznać się z przykładem <xref:System.Data.Services.IUpdatable> implementującym Interfejs [, zobacz How to: Tworzenie usługi danych przy użyciu źródła](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)danych LINQ to SQL.  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
