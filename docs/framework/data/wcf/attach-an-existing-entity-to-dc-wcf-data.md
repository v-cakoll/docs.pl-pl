---
title: 'Instrukcje: Dołączanie istniejącej jednostki do obiekcie DataServiceContext (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 160f0afc2e1baf033557b7114a51145a5c983e29
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791182"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Instrukcje: Dołączanie istniejącej jednostki do obiekcie DataServiceContext (Usługi danych programu WCF)
Gdy jednostka już istnieje w usłudze danych, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta umożliwia dołączenie obiektu, który reprezentuje jednostkę bezpośrednio do, <xref:System.Data.Services.Client.DataServiceContext> bez wykonywania zapytania. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć istniejący `Customer` obiekt, który zawiera zmiany do zapisania w usłudze danych. Obiekt jest dołączony do kontekstu, a <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> Metoda jest wywoływana w celu oznaczenia dołączonego obiektu, tak jak <xref:System.Data.Services.Client.EntityStates.Modified> przed <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> wywołaniem metody.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
