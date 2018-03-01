---
title: "Porady: Definiowanie relacji między obiektami (usługi danych WCF)"
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
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a584e78c15d900bad8bdd3a85abe5e090ed47de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Porady: Definiowanie relacji między obiektami (usługi danych WCF)
Po dodaniu nowej jednostki w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], wszystkie relacje między nimi i powiązanych jednostek nie są automatycznie zdefiniowane. Można utworzyć i zmienić relacje między wystąpieniami jednostki i biblioteki klienta odzwierciedlenia tych zmian w usłudze danych. Aby uzyskać więcej informacji, zobacz [aktualizacji usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> można utworzyć elementu w kontekście oraz łącza do powiązanego zamówienia. Wysyła komunikat HTTP POST do danych usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody w celu dodania `Order_Details` obiektu z odpowiednimi `Orders` obiektu z odwołaniem do konkretnego `Products` obiektu. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> i <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> metody Definiowanie relacji. W tym przykładzie właściwości nawigacji na `Order_Details` obiektu są również jawnie ustawione.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)
