---
title: 'Instrukcje: Definiowanie relacji jednostek (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 3bd2293f02e77ab2db5c3ba245596021e08b04c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517842"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Instrukcje: Definiowanie relacji jednostek (WCF Data Services)
Po dodaniu nowej jednostki w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], nie są automatycznie definiowane relacje między nimi i powiązanych jednostek. Można tworzyć i zmieniać relacje między wystąpieniami jednostki i biblioteki klienta odzwierciedlenia tych zmian w usłudze data service. Aby uzyskać więcej informacji, zobacz [aktualizacja usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext> można utworzyć elementu w kontekście oraz link do dotyczące odpowiednich zamówień. Wysyła komunikat żądania HTTP POST do danych usługi, kiedy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody w celu dodania `Order_Details` obiektu z odpowiednimi `Orders` obiektu z odwołaniem do określonego `Products` obiektu. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> i <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> metody definiowania relacji. W tym przykładzie właściwości nawigacji na `Order_Details` obiektu są także jawnie ustawić.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)
