---
title: 'Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 5816cb6a765a7cdf49aca9ac50461a4e50e6df14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122190"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek (WCF Data Services)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotekom klienckim możesz można utworzyć, aktualizacji i usunąć dane jednostki w usłudze danych, wykonując czynności równoważne na obiektach w <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [aktualizacja usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext> można utworzyć elementu w kontekście. Wysyła komunikat żądania HTTP POST do danych usługi, kiedy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera i modyfikuje istniejący obiekt, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext> do oznaczania elementów w kontekście uaktualnione. Wysyła komunikat HTTP scalania z danymi usług, kiedy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext> do oznaczania elementów w kontekście jako usunięty. Wysyła komunikat HTTP DELETE do danych usługi, kiedy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext> można utworzyć elementu w kontekście oraz link do dotyczące odpowiednich zamówień. Wysyła komunikat żądania HTTP POST do danych usługi, kiedy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Instrukcje: Dołączanie istniejącej jednostki do obiektu DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)
- [Instrukcje: Definiowanie relacji jednostek](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)
- [Operacje przetwarzania wsadowego](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
