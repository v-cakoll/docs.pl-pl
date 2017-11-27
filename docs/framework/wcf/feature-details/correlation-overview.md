---
title: "Przegląd korelacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d4320c088c66abdc2c4ff226eb99d66fcbd3b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="correlation-overview"></a>Przegląd korelacji
Korelacja jest mechanizm dotyczących komunikatów usługi przepływu pracy lub stan wystąpienia aplikacji, takich jak odpowiedzi na żądanie początkowej lub identyfikator określonej kolejności stanu utrwalonego kolejność przetwarzania przepływu pracy. Ten temat zawiera przegląd korelacji. W innych tematach w tej sekcji zawierają dodatkowe informacje dla każdego typu korelacji.  
  
## <a name="types-of-correlation"></a>Typy korelacji  
 Korelacja może być opartych na protokole lub na podstawie zawartości. Opartych na protokole korelacji Użyj dane dostarczone przez infrastrukturę dostarczania wiadomości, aby określić mapowanie między wiadomości. Wiadomości, które są skorelowane przy użyciu opartych na protokole korelacji są powiązane ze sobą przy użyciu obiektu w pamięci, takich jak <xref:System.ServiceModel.Channels.RequestContext>, lub przez token dostarczony przez protokół transportu. Na podstawie zawartości korelacji odnoszą się komunikaty ze sobą przy użyciu danych z określonych aplikacji. Wiadomości, które są skorelowane przy użyciu korelacji na podstawie zawartości są ze sobą powiązane przez niektóre dane zdefiniowane przez aplikację w wiadomości, takie jak numer klienta.  
  
 Działania, które uczestniczą w użyciu korelacji <xref:System.ServiceModel.Activities.CorrelationHandle> powiązać razem działania obsługi wiadomości. Na przykład <xref:System.ServiceModel.Activities.Send> używany do wywołania usługi i kolejnej <xref:System.ServiceModel.Activities.Receive> używany do odbierania wywołania zwrotnego z usługą, identyczny <xref:System.ServiceModel.Activities.CorrelationHandle>. Ten wzorzec podstawowe służy czy korelacji jest zawartość lub protokół. Dojście korelacji można jawnie ustawiona na każde działanie lub działania mogą być zawarte w <xref:System.ServiceModel.Activities.CorrelationScope> działania. Działań zawartych w <xref:System.ServiceModel.Activities.CorrelationScope> ma ich dojścia korelacji zarządza <xref:System.ServiceModel.Activities.CorrelationScope> i nie wymagają <xref:System.ServiceModel.Activities.CorrelationHandle> należy jawnie ustawić. A <xref:System.ServiceModel.Activities.CorrelationScope> zakres udostępnia <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania dla korelacji żądanie odpowiedź i jeden typ dodatkowe korelacji. Hostowane przy użyciu usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost> mają tej samej obsługi korelacji domyślne jako <xref:System.ServiceModel.Activities.CorrelationScope> działania. Zarządzanie korelacji ten domyślny zazwyczaj oznacza, że w wielu scenariuszach wiadomości działań w <xref:System.ServiceModel.Activities.CorrelationScope> lub usługi przepływu pracy nie wymagają ich <xref:System.ServiceModel.Activities.CorrelationHandle> ustawić wiele działań wiadomości znajdują się w równoległego lub nakładają się na siebie, takie jak dwa <xref:System.ServiceModel.Activities.Receive> działania równoległego lub dwóch <xref:System.ServiceModel.Activities.Send> czynności zostały wykonane przez dwa <xref:System.ServiceModel.Activities.Receive> działań. Więcej informacji na temat korelacji domyślny znajduje się w tematach w tej sekcji, które obejmują poszczególnych typów korelacji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]działania obsługi komunikatów, zobacz [wiadomości działania](../../../../docs/framework/wcf/feature-details/messaging-activities.md) i [porady: Tworzenie usługi przepływu pracy z działaniami wiadomości](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md).  
  
## <a name="protocol-based-correlation"></a>Opartych na protokole korelacji  
 Opartych na protokole korelacji używany mechanizm transportu do powiązania wiadomości i odpowiednie wystąpienie. Niektóre korelacji protokołu dostarczane przez system obejmują korelacja żądań i odpowiedzi i kontekstowa korelacji. Korelacja żądań i odpowiedzi służy do skorelowania pojedynczego parę działania obsługi komunikatów do utworzenia dwukierunkowe operacji, takich jak <xref:System.ServiceModel.Activities.Send> sparowanego z <xref:System.ServiceModel.Activities.ReceiveReply>, lub <xref:System.ServiceModel.Activities.Receive> sparowanego z <xref:System.ServiceModel.Activities.SendReply>. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Projektanta przepływów pracy udostępnia również zestaw szablonów działania szybkie rozpoczęcie tego wzorca. Kontekstowa korelacji jest oparta na mechanizm wymiany kontekstu opisanego w [Specyfikacja protokół wymiany kontekstu .NET](http://go.microsoft.com/fwlink/?LinkID=166059). Do użycia na podstawie kontekstu korelacji, na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> lub <xref:System.ServiceModel.NetTcpContextBinding> musi być używany w punkcie końcowym.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Protokół korelacji, zobacz [wymiana kontekstu](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md), [trwałe dupleksu](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md), i [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] szablony działania projektanta przepływów pracy, zobacz [wiadomości działania](../../../../docs/framework/wcf/feature-details/messaging-activities.md). Przykładowy kod, zobacz [trwałe dupleksu &#91; WF — przykłady &#93; ](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md) i [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) próbek.  
  
## <a name="content-based-correlation"></a>Korelacja na podstawie zawartości  
 Na podstawie zawartości korelacji używa elementu informacji w komunikacie Aby skojarzyć ją do określonego wystąpienia. W przeciwieństwie do opartych na protokole korelacji korelacji na podstawie zawartości wymaga Autor aplikacji jawnie określić, gdzie te dane znajdują się w każdej wiadomości pokrewne. Operacje używające korelacji na podstawie zawartości określić te dane wiadomości przy użyciu <xref:System.ServiceModel.MessageQuerySet>. Na podstawie zawartości korelacji jest przydatne podczas komunikowania się z usługami, które nie korzystają z jednym z powiązań kontekstu, takich jak <xref:System.ServiceModel.BasicHttpContextBinding>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Korelacja na podstawie zawartości, zobacz [na podstawie zawartości](../../../../docs/framework/wcf/feature-details/content-based-correlation.md). Przykładowy kod, zobacz [na podstawie zawartości korelacji](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md) i [skorelowane Kalkulator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) próbek.  
  
## <a name="see-also"></a>Zobacz też  
 [Korelacja na podstawie zawartości](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [Kalkulator skorelowane](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)  
 [Niezawodna komunikacja dwukierunkowa &#91; WF — przykłady &#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)  
 [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)
