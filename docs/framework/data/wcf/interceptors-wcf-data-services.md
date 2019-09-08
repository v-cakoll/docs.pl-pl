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
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790440"
---
# <a name="interceptors-wcf-data-services"></a>Interceptory (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia aplikacji przechwytywanie komunikatów żądań w celu dodania logiki niestandardowej do operacji. Możesz użyć tej logiki niestandardowej do walidacji danych w wiadomościach przychodzących. Można go również użyć, aby dodatkowo ograniczyć zakres żądania zapytania, na przykład w celu wstawienia niestandardowych zasad autoryzacji na podstawie żądania.  
  
 Przechwytywanie jest wykonywane przez specjalnie przypisane metody w usłudze danych. Metody te są wywoływane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] właściwy punkt w przetwarzaniu komunikatów. Interceptory są definiowane na podstawie zestawu jednostek, a metody przechwytywania nie mogą przyjmować parametrów z żądania, takie jak operacje usługi. Metody interceptora zapytań, które są wywoływane podczas przetwarzania żądania HTTP GET, muszą zwracać wyrażenie lambda, które określa, czy wystąpienie zestawu jednostek interceptora ma być zwracane przez wyniki zapytania. To wyrażenie jest używane przez usługę danych w celu dodatkowego uściślenia wymaganej operacji. Poniżej znajduje się przykładowa definicja interceptora zapytań.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.  
  
 Interceptory zmian, które są wywoływane podczas przetwarzania operacji innych niż zapytania, muszą zwracać `void` (`Nothing` w Visual Basic). Metody przechwytywania zmian muszą przyjmować następujące dwa parametry:  
  
1. Parametr typu, który jest zgodny z typem jednostki zestawu jednostek. Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru będzie odzwierciedlać informacje o jednostce wysyłane przez żądanie.  
  
2. Parametr typu <xref:System.Data.Services.UpdateOperations>. Gdy usługa danych wywołuje interceptor zmiany, wartość tego parametru będzie odzwierciedlać operację wykonywaną przez żądanie.  
  
 Poniżej znajduje się przykładowa definicja interceptora zmian.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.  
  
 Następujące atrybuty są obsługiwane w przypadku przechwycenia.  
  
 **[QueryInterceptor (** *entitySetName* **)]**  
 Metody z <xref:System.Data.Services.QueryInterceptorAttribute> zastosowanym atrybutem są wywoływane, gdy odebrane zostanie żądanie HTTP GET dla zasobu dla obiektu zestawu jednostek. Metody te muszą zawsze zwracać wyrażenie lambda w postaci `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *entitySetName* **)]**  
 Metody z <xref:System.Data.Services.ChangeInterceptorAttribute> zastosowanym atrybutem są wywoływane, gdy odebrane zostanie żądanie HTTP inne niż żądanie GET protokołu HTTP dla zasobu zestawu jednostek dla obiektu Target. Metody te muszą zawsze zwracać `void` (`Nothing` w Visual Basic).  
  
 Aby uzyskać więcej informacji, zobacz [jak: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.  
  
## <a name="see-also"></a>Zobacz także

- [Operacje usługi](service-operations-wcf-data-services.md)
