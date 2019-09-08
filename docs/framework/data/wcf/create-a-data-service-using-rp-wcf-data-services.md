---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790997"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, tak długo, jak te klasy są udostępniane jako obiekty, które <xref:System.Linq.IQueryable%601> implementują interfejs. Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano model danych, który `Orders` zawiera `Items`i. Klasa `OrderItemData` kontenera jednostek ma dwie metody publiczne, które zwracają <xref:System.Linq.IQueryable%601> interfejsy. Te interfejsy są zestawami `Orders` jednostek typów jednostek i. `Items` `Items` `Orders` `Items` Może zawierać wiele, więc typ jednostki ma właściwość nawigacji, która zwraca kolekcję `Items` obiektów. `Order` Klasa kontenera <xref:System.Data.Services.DataService%601> jednostek jest typem ogólnym klasy, z której `OrderItems` pochodzi usługa danych. `OrderItemData`  
  
> [!NOTE]
> Ponieważ ten przykład ilustruje dostawcę danych w pamięci, a zmiany nie są utrwalane poza bieżącymi wystąpieniami obiektów, nie ma korzyści wynikającej z implementacji <xref:System.Data.Services.IUpdatable> interfejsu. Aby zapoznać się z przykładem <xref:System.Data.Services.IUpdatable> implementującym Interfejs [, zobacz How to: Tworzenie usługi danych przy użyciu źródła](create-a-data-service-using-linq-to-sql-wcf.md)danych LINQ to SQL.  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych](create-a-data-service-using-linq-to-sql-wcf.md)
- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
