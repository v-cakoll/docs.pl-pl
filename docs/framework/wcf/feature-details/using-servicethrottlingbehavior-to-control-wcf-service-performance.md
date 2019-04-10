---
title: Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: e42f44b5fa103d5c083bdce3086b6499c5bb3673
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211520"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Klasa udostępnia właściwości, których można użyć, aby ograniczyć liczbę wystąpień lub sesji są tworzone na poziomie aplikacji. To zachowanie można dostosować wydajność aplikacji Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Kontrolowanie wystąpień usługi i współbieżnych wywołań  
 Użyj <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> właściwość, aby określić maksymalną liczbę komunikatów aktywnie przetwarzanie <xref:System.ServiceModel.ServiceHost> klasy, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwość, aby określić maksymalną liczbę <xref:System.ServiceModel.InstanceContext> obiektów w usłudze.  
  
 Ponieważ określania ustawień tych właściwości, zwykle ma miejsce po ochronę aplikacji przed praktyczne doświadczenie ładowania ustawień <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> właściwości jest zazwyczaj określana w konfiguracji pliku aplikacji przy użyciu [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) elementu.  
  
 Poniższy przykład kodu pokazuje użycie <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> klasy z pliku konfiguracji aplikacji, która ustawia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwości na wartość 1 jako przykład prosta. Rzeczywiste środowisko pracy określa optymalnych ustawień dla każdej określonej aplikacji.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Dokładne zachowanie w czasie wykonywania zależy od wartości <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości, które kontrolują, ile komunikatów można wykonywać w operacji naraz i okresy istnienia usługi <xref:System.ServiceModel.InstanceContext> względem przychodzące sesje kanału , odpowiednio.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
