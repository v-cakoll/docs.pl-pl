---
title: 'Instrukcje: Tworzenie punktu końcowego usługi w kodzie'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d91310ba86543343a6a8b446d70f882ce2fa2cb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>Instrukcje: Tworzenie punktu końcowego usługi w kodzie
W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest zdefiniowana w kodzie, w którym jest określone, że usługa musi używać <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Jest zwykle najlepszym rozwiązaniem, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie imperatively w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane. Ogólnie rzecz biorąc pamiętając powiązania i adresowanie poza kod umożliwia im to zmienić bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>Aby utworzyć punkt końcowy usługi w kodzie  
  
1.  Utwórz interfejs definiujący kontrakt usługi.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  Implementowanie kontraktu usługi, zdefiniowane w kroku 1.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  W hostingu aplikacji należy utworzyć adres podstawowy usługi i powiązania do użycia z usługą.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  Utwórz hosta i wywołanie <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> lub jednego z innych przeciążeń, aby dodać punkt końcowy usługi dla hosta.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     Określanie powiązania w kodzie, ale Użyj domyślnych punktów końcowych dostarczonym w czasie wykonywania, przekazać do konstruktora bass adres podczas tworzenia <xref:System.ServiceModel.ServiceHost>i nie wymagają <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     Aby uzyskać więcej informacji o domyślnych punktów końcowych, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: określanie wiązań usługi w kodzie](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
