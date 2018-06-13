---
title: Interceptory (usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: f3ff08dd4cd20e7ce226750a386cfddb27731923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363803"
---
# <a name="interceptors-wcf-data-services"></a>Interceptory (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umożliwia aplikacji przechwycić komunikaty żądania, aby mogli dodawać niestandardowej logiki do operacji. Można użyć tej niestandardowej logiki do sprawdzania poprawności danych w komunikatach przychodzących. Można również użyć bardziej ograniczyć zakres żądania zapytania, takie jak, aby wstawić niestandardowych zasad autoryzacji na podstawie danego żądania.  
  
 Przechwycenie odbywa się za pomocą metod specjalnie oparte na atrybutach usługi danych. Te metody są wywoływane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] we właściwym momencie podczas przetwarzania wiadomości. Interceptory są zdefiniowane na podstawie zestawu na jednostki i metody interceptora nie może przyjmować parametrów z żądania, jak operacji usługi. Metody interceptora zapytań, które są wywoływane podczas przetwarzania żądania HTTP GET, musi zwracać Wyrażenie lambda, które określa, czy wystąpienie jednostki interceptora ustawić powinny być zwracane w wynikach zapytania. To wyrażenie jest używane przez usługę danych do uściślenia żądanej operacji. Oto przykład definicji interceptora zapytań.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Przechwytywanie danych komunikatów usługi](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Interceptory zmiany, które są wywoływane podczas przetwarzania operacji-query, musi zwracać `void` (`Nothing` w języku Visual Basic). Metody interceptora zmian, musisz zaakceptować poniższe dwa parametry:  
  
1.  Parametr typu, który jest zgodny z typem jednostki z zestawu jednostek. Gdy usługa danych wywołuje interceptora zmian, wartość tego parametru, zostaną one zastosowane informacje jednostki, które są wysyłane przez żądanie.  
  
2.  Parametr typu <xref:System.Data.Services.UpdateOperations>. Gdy usługa danych wywołuje interceptora zmian, wartość tego parametru, zostaną one zastosowane żądanie próbuje wykonać operację.  
  
 Oto przykład definicji interceptora zmian.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Przechwytywanie danych komunikatów usługi](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Następujące atrybuty są obsługiwane w przypadku zatrzymania.  
  
 **[QueryInterceptor (** *EnitySetName* **)]**  
 Metody z <xref:System.Data.Services.QueryInterceptorAttribute> atrybutu stosowane są wywoływane po odebraniu żądania HTTP GET dla docelowej jednostki zestawu zasobów. Te metody zawsze musi zwracać wyrażenia lambda w formie `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *EnitySetName* **)]**  
 Metody z <xref:System.Data.Services.ChangeInterceptorAttribute> atrybutu stosowane są wywoływane po odebraniu żądania HTTP innych niż żądanie HTTP GET dla docelowej jednostki zestawu zasobów. Te metody muszą zawsze zwracać `void` (`Nothing` w języku Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [porady: Przechwytywanie danych komunikatów usługi](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
