---
title: "Porady: Tworzenie usługi danych przy użyciu dostawcy odbicia (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343fc6043b4cfc7ea02ff33c18aaaf5ced14c11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Porady: Tworzenie usługi danych przy użyciu dostawcy odbicia (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umożliwia zdefiniowanie modelu danych, na podstawie klasy dowolnego tak długo, jak te klasy są widoczne jako obiekty, które implementują <xref:System.Linq.IQueryable%601> interfejsu. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano modelu danych, która obejmuje `Orders` i `Items`. Klasa kontenera jednostek `OrderItemData` ma dwóch metod publicznych, które zwracają <xref:System.Linq.IQueryable%601> interfejsów. Te interfejsy są zestawy jednostek tego `Orders` i `Items` typy jednostek. `Order` Może zawierać wielu `Items`, więc `Orders` typ jednostki ma `Items` właściwości nawigacji zwracającej Kolekcja `Items` obiektów. `OrderItemData` Klasy kontenera jednostka jest ogólny typ <xref:System.Data.Services.DataService%601> klasy, z którego `OrderItems` pochodzi usługi danych.  
  
> [!NOTE]
>  W tym przykładzie pokazano dostawcy danych w pamięci i zmiany nie są zachowywane poza bieżącego wystąpienia obiektu, nie istnieje żadnych korzyści pochodzi od wykonania <xref:System.Data.Services.IUpdatable> interfejsu. Na przykład, który implementuje <xref:System.Data.Services.IUpdatable> interfejsu, zobacz [porady: Tworzenie usługi danych przy użyciu składnika LINQ to SQL źródła danych](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
