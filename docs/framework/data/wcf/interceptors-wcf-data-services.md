---
title: Interceptory (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: c9799037ae0ea8b29b5e989859aff29c310593d4
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568969"
---
# <a name="interceptors-wcf-data-services"></a>Interceptory (Usługi danych programu WCF)
Usługi danych programu WCF umożliwia aplikacji przechwycenie komunikatów żądania, aby można było dodać logikę niestandardową do operacji. Możesz użyć tej logiki niestandardowej do walidacji danych w wiadomościach przychodzących. Można go również użyć, aby dodatkowo ograniczyć zakres żądania zapytania, na przykład w celu wstawienia niestandardowych zasad autoryzacji na podstawie żądania.  
  
 Przechwytywanie jest wykonywane przez specjalnie przypisane metody w usłudze danych. Metody te są wywoływane przez Usługi danych programu WCF w odpowiednim momencie przetwarzania komunikatów. Interceptory są definiowane na podstawie zestawu jednostek, a metody przechwytywania nie mogą przyjmować parametrów z żądania, takie jak operacje usługi. Metody interceptora zapytań, które są wywoływane podczas przetwarzania żądania HTTP GET, muszą zwracać wyrażenie lambda, które określa, czy wystąpienie zestawu jednostek interceptora ma być zwracane przez wyniki zapytania. To wyrażenie jest używane przez usługę danych w celu dodatkowego uściślenia wymaganej operacji. Poniżej znajduje się przykładowa definicja interceptora zapytań.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [How to: przechwytywania komunikatów usługi danych](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Interceptory zmian, które są wywoływane podczas przetwarzania operacji innych niż zapytania, muszą zwracać `void` (`Nothing` w Visual Basic). Metody przechwytywania zmian muszą przyjmować następujące dwa parametry:  
  
1. Parametr typu, który jest zgodny z typem jednostki zestawu jednostek. Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru będzie odzwierciedlać informacje o jednostce wysyłane przez żądanie.  
  
2. Parametr typu <xref:System.Data.Services.UpdateOperations>. Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru będzie odzwierciedlać operację wykonywaną przez żądanie.  
  
 Poniżej znajduje się przykładowa definicja interceptora zmian.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [How to: przechwytywania komunikatów usługi danych](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Następujące atrybuty są obsługiwane w przypadku przechwycenia.  
  
 **[QueryInterceptor (** *entitySetName* **)]**  
 Metody z zastosowanym atrybutem <xref:System.Data.Services.QueryInterceptorAttribute> są wywoływane po odebraniu żądania HTTP GET dla zasobu zestawu jednostek dla obiektu. Te metody muszą zawsze zwracać wyrażenie lambda w postaci `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *entitySetName* **)]**  
 Metody z zastosowanym atrybutem <xref:System.Data.Services.ChangeInterceptorAttribute> są wywoływane, gdy odebrane zostanie żądanie HTTP inne niż żądanie HTTP GET dla zasobu zestawu jednostek dla obiektów przekierowanych. Te metody muszą zawsze zwracać `void` (`Nothing` w Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [How to: przechwytywania komunikatów usługi danych](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operacje usługi](service-operations-wcf-data-services.md)
