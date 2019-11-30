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
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia (Usługi danych programu WCF)
Usługi danych programu WCF umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, tak długo, jak te klasy są udostępniane jako obiekty implementujące interfejs <xref:System.Linq.IQueryable%601>. Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano model danych, który zawiera `Orders` i `Items`. Klasa kontenera jednostek `OrderItemData` ma dwie metody publiczne, które zwracają interfejsy <xref:System.Linq.IQueryable%601>. Te interfejsy są zestawami jednostek `Orders` i `Items` typów jednostek. `Order` może zawierać wiele `Items`, więc typ jednostki `Orders` ma właściwość nawigacji `Items`, która zwraca kolekcję obiektów `Items`. Klasa kontenera jednostek `OrderItemData` jest typem ogólnym klasy <xref:System.Data.Services.DataService%601>, z której pochodzi usługa danych `OrderItems`.  
  
> [!NOTE]
> Ponieważ ten przykład ilustruje dostawcę danych w pamięci i zmiany nie są utrwalane poza bieżącymi wystąpieniami obiektów, nie ma korzyści wynikającej z implementacji interfejsu <xref:System.Data.Services.IUpdatable>. Aby zapoznać się z przykładem implementującym interfejs <xref:System.Data.Services.IUpdatable>, zobacz [How to: Create a Data Service using a the LINQ to SQL Source Data](create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md)
- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
