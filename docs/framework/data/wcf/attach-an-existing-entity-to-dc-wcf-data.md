---
title: 'Instrukcje: dołączanie istniejącej jednostki do obiekcie DataServiceContext (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 7c8355ea9e9823e7cab6f43c0f3f901948d1d539
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569379"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Instrukcje: dołączanie istniejącej jednostki do obiekcie DataServiceContext (Usługi danych programu WCF)
Gdy jednostka już istnieje w usłudze danych, Biblioteka klienta Usługi danych programu WCF umożliwia dołączenie obiektu, który reprezentuje jednostkę bezpośrednio do <xref:System.Data.Services.Client.DataServiceContext> bez wykonywania zapytania. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć istniejący obiekt `Customer`, który zawiera zmiany do zapisania w usłudze danych. Obiekt jest dołączony do kontekstu i wywoływana jest metoda <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>, aby oznaczyć dołączony obiekt jako <xref:System.Data.Services.Client.EntityStates.Modified> przed wywołaniem metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
