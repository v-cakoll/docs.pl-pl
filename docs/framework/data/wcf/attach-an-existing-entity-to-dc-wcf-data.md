---
title: "Porady: dołączanie istniejącego obiektu do obiekt DataServiceContext (usługi danych WCF)"
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
helpviewer_keywords: WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e389e0ff274b0b4c256bbd9764cd72805b09fcc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Porady: dołączanie istniejącego obiektu do obiekt DataServiceContext (usługi danych WCF)
Gdy obiekt już istnieje w usłudze danych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta umożliwia dołączyć obiekt, który reprezentuje jednostkę bezpośrednio do <xref:System.Data.Services.Client.DataServiceContext> bez uprzedniego wykonywanie zapytania. Aby uzyskać więcej informacji, zobacz [aktualizacji usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia istniejące `Customer` obiekt, który zawiera zmian do zapisania do usługi danych. Obiekt jest dołączony do kontekstu i <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metoda jest wywoływana, aby oznaczyć przyłączonego obiektu jako <xref:System.Data.Services.Client.EntityStates.Modified> przed <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
