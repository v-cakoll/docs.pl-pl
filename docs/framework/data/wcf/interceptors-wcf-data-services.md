---
title: Interceptory (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: c2086d451af72157785796052af123cd210ee036
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202727"
---
# <a name="interceptors-wcf-data-services"></a>Interceptory (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umożliwia aplikacji przechwycenia komunikatów żądań, tak aby dodać logikę niestandardową operacji. Można użyć tej niestandardowej logiki do sprawdzania poprawności danych w wiadomości przychodzących. Można również użyć bardziej ograniczyć zakres żądania zapytania, takie jak wstawić niestandardowych zasad autoryzacji na podstawie danego żądania.  
  
 Przejmowanie odbywa się za pomocą metod specjalnie opartego na atrybutach usługi danych. Te metody są wywoływane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] we właściwym punkcie podczas przetwarzania komunikatu. Interceptory są zdefiniowane na podstawie zestawu jednostek i metody interceptor nie akceptuje parametrów z żądania, takie jak operacje usługi można. Metody interceptor zapytania, które są wywoływane podczas przetwarzania żądania HTTP GET, muszą zwracać Wyrażenie lambda, która określa, czy wystąpienie jednostki interceptor ustawić powinien być zwrócony przez wyniki zapytania. To wyrażenie jest używany przez usługę danych można uściślić żądanej operacji. Oto przykład definicji interceptor zapytania.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Interceptory zmiany, które są wywoływane podczas przetwarzania operacji niebędącą zapytaniem, musi zwracać `void` (`Nothing` w języku Visual Basic). Zmiana interceptor metody muszą zaakceptować następujące dwa parametry:  
  
1.  Parametr typu, który jest zgodny z typem jednostki z zestawu jednostek. Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru, zostanie naliczona informacje jednostki, które są wysyłane przez żądanie.  
  
2.  Parametr typu <xref:System.Data.Services.UpdateOperations>. Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru, zostanie naliczona operacji, które podejmuje próbę wykonania żądania.  
  
 Oto przykład definicji interceptor zmiany.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Następujące atrybuty są obsługiwane w przypadku zatrzymania.  
  
 **[QueryInterceptor (** *Nazwa zestawu jednostek* **)]**  
 Metody z <xref:System.Data.Services.QueryInterceptorAttribute> zastosowany są wywoływane po odebraniu żądania HTTP GET dla docelowej jednostki zestawu zasobów. Te metody muszą zawsze zwracać wyrażenia lambda w formie `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *Nazwa zestawu jednostek* **)]**  
 Metody z <xref:System.Data.Services.ChangeInterceptorAttribute> zastosowany są wywoływane po odebraniu żądania HTTP inne niż żądanie HTTP GET dla docelowej jednostki zestawu zasobów. Te metody muszą zawsze zwracać `void` (`Nothing` w języku Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [jak: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
