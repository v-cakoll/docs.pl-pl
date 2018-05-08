---
title: Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: b54d1d6146b9751fdd12502771de01fe52854c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Klasa udostępnia właściwości, które można użyć, aby ograniczyć liczbę wystąpień lub sesji są tworzone na poziomie aplikacji. To zachowanie można dostosować wydajność aplikacji Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Kontrolowanie wystąpień usługi i równoczesnych wywołań  
 Użyj <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> właściwość, aby określić maksymalną liczbę komunikatów aktywnie przetwarzanych w obrębie <xref:System.ServiceModel.ServiceHost> klasy, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwość, aby określić maksymalną liczbę <xref:System.ServiceModel.InstanceContext> obiektów w usłudze.  
  
 Ponieważ określania ustawień tych właściwości zwykle odbywa się po rzeczywistych środowisko uruchamiania aplikacji przed ładowania ustawień <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> właściwości jest zazwyczaj określana w konfiguracji aplikacji plików przy użyciu [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) elementu.  
  
 W poniższym przykładzie pokazano sposób użycia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> klasy z pliku konfiguracji aplikacji, która ustawia <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwości na wartość 1 jako przykład prosta. Praktyczne doświadczenie określa optymalne ustawienia dla każdej określonej aplikacji.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Dokładne zachowania w czasie wykonywania zależy od wartości <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości, które kontrolują, ile komunikatów można wykonać wewnątrz operacji jednocześnie i okresy istnienia usługi <xref:System.ServiceModel.InstanceContext> względem przychodzących sesji kanału , odpowiednio.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, i <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
