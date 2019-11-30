---
title: 'Instrukcje: Definiowanie relacji jednostek (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: f693579883ae03a6c8df3e9a9f4941e1f9940a4c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569117"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Instrukcje: Definiowanie relacji jednostek (Usługi danych programu WCF)
Po dodaniu nowej jednostki w Usługi danych programu WCF wszelkie relacje między nowym obiektem a powiązanymi jednostkami nie są definiowane automatycznie. Można tworzyć i zmieniać relacje między wystąpieniami jednostek, a ich Biblioteka kliencka odzwierciedla te zmiany w usłudze danych. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje metodę <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, aby utworzyć element w kontekście wraz z linkiem do powiązanej kolejności. Wiadomość HTTP POST jest wysyłana do usługi danych po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak za pomocą metody <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> dodać obiekt `Order_Details` do powiązanego obiektu `Orders` z odwołaniem do określonego obiektu `Products`. Metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> i <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> definiują relacje. W tym przykładzie właściwości nawigacji w obiekcie `Order_Details` są również jawnie ustawione.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek](how-to-add-modify-and-delete-entities-wcf-data-services.md)
