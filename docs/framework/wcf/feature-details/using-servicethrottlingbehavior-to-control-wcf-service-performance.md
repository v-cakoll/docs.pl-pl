---
title: Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 9cc5141805504bc46391105f475860b032f12d32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600234"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>Klasa uwidacznia właściwości, których można użyć, aby ograniczyć liczbę wystąpień lub sesji tworzonych na poziomie aplikacji. Korzystając z tego zachowania, można dostosować wydajność aplikacji Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Kontrolowanie wystąpień usług i współbieżnych wywołań  
 Użyj <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> właściwości, aby określić maksymalną liczbę komunikatów aktywnie przetwarzanych przez <xref:System.ServiceModel.ServiceHost> klasę i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> Właściwość, aby określić maksymalną liczbę <xref:System.ServiceModel.InstanceContext> obiektów w usłudze.  
  
 Ponieważ określenie ustawień tych właściwości zwykle odbywa się po rzeczywistym doświadczeniu uruchamiania aplikacji przed załadowaniem, ustawienia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> właściwości są zwykle określane w pliku konfiguracyjnym aplikacji przy użyciu [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) elementu.  
  
 Poniższy przykład kodu pokazuje użycie <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> klasy z pliku konfiguracyjnego aplikacji, który ustawia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> właściwości,, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> na 1 jako uproszczony przykład. Rzeczywiste środowisko pracy określa optymalne ustawienia dla konkretnej aplikacji.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Dokładne zachowanie w czasie wykonywania zależy od wartości <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości i, które kontrolują, ile komunikatów może być wykonywanych wewnątrz operacji jednocześnie i okresów istnienia usługi <xref:System.ServiceModel.InstanceContext> względem sesji przychodzącego kanału.  
  
 Aby uzyskać szczegółowe informacje, zobacz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
