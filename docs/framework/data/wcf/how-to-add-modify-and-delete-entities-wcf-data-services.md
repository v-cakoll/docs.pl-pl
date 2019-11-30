---
title: 'Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 501bec59a61b51ec4bece4b0ce2f941189b35ed0
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569201"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek (Usługi danych programu WCF)
Za pomocą bibliotek klienta Usługi danych programu WCF można tworzyć, aktualizować i usuwać dane jednostki w usłudze danych, wykonując równoważne akcje na obiektach w <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje metodę <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, aby utworzyć element w kontekście. Wiadomość HTTP POST jest wysyłana do usługi danych po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera i modyfikuje istniejący obiekt, a następnie wywołuje metodę <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, aby oznaczyć element w kontekście jako zaktualizowany. Komunikat scalania HTTP jest wysyłany do usługi danych po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje metodę <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, aby oznaczyć element w kontekście jako usunięty. Wiadomość HTTP DELETE jest wysyłana do usługi danych po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje metodę <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, aby utworzyć element w kontekście wraz z linkiem do powiązanej kolejności. Wiadomość HTTP POST jest wysyłana do usługi danych po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Instrukcje: Dołączanie istniejącej jednostki do obiektu DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md)
- [Instrukcje: Definiowanie relacji jednostek](how-to-define-entity-relationships-wcf-data-services.md)
- [Operacje przetwarzania wsadowego](batching-operations-wcf-data-services.md)
