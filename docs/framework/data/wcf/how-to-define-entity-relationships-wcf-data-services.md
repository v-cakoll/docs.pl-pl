---
title: 'Instrukcje: Definiuj relacje jednostek (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 63714f97e691b2ba0177a36a599b62ca7681dcf6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790650"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Instrukcje: Definiuj relacje jednostek (Usługi danych programu WCF)
Po dodaniu nowej jednostki w programie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]wszelkie relacje między nową jednostką i powiązanymi jednostkami nie są definiowane automatycznie. Można tworzyć i zmieniać relacje między wystąpieniami jednostek, a ich Biblioteka kliencka odzwierciedla te zmiany w usłudze danych. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodę <xref:System.Data.Services.Client.DataServiceContext> w celu utworzenia elementu w kontekście wraz z linkiem do powiązanej kolejności. Wiadomość http post jest wysyłana do usługi danych po <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> wywołaniu metody.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> , jak używać metody do `Order_Details` dodawania obiektu do powiązanego `Orders` obiektu z odwołaniem do określonego `Products` obiektu. Metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> i<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> definiują relacje. W tym przykładzie właściwości `Order_Details` nawigacji obiektu są również jawnie ustawione.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek](how-to-add-modify-and-delete-entities-wcf-data-services.md)
