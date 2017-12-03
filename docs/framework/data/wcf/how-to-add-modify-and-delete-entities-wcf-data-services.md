---
title: "Porady: Dodawanie, modyfikowanie i usuwanie jednostek (usługi danych WCF)"
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
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e41502fee9cfa272b154f6ddaf0e6a41a482bc7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Porady: Dodawanie, modyfikowanie i usuwanie jednostek (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotek klienta, możesz można tworzenia, aktualizacji i usuwania danych jednostki w usłudze danych przez wykonanie akcji odpowiadających obiektów w <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [aktualizacji usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> można utworzyć elementu w kontekście. Wysyła komunikat HTTP POST do danych usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera i modyfikuje istniejącego obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> zaznaczania elementu w ramach aktualizacji. Wysyła komunikat HTTP SCALANIE danych usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Przykład  
 Następujące wywołania przykład <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> do elementu w kontekście zostać oznaczone jako usunięte. Wysyła komunikat HTTP DELETE do danych usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowe wystąpienie obiektu, a następnie wywołuje <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> można utworzyć elementu w kontekście oraz łącza do powiązanego zamówienia. Wysyła komunikat HTTP POST do danych usługi, gdy <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Porady: dołączanie istniejącego obiektu do obiekcie DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)  
 [Porady: Definiowanie relacji między obiektami](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)  
 [Przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
