---
title: 'Instrukcje: Tworzenie punktu końcowego usługi w kodzie'
description: Dowiedz się, jak zaimplementować usługę w klasie i programowo zdefiniować jej punkt końcowy. W programie WCF punkty końcowe są zwykle zdefiniowane w pliku konfiguracji.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 3b2ff2a17975bc381db61edc2c0f85f67edd3325
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247055"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>Instrukcje: Tworzenie punktu końcowego usługi w kodzie
W tym przykładzie `ICalculator` jest definiowana umowa dla usługi kalkulatora, usługa jest zaimplementowana w `CalculatorService` klasie, a następnie jej punkt końcowy jest zdefiniowany w kodzie, w którym jest określony, że usługa musi używać <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi. Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>Aby utworzyć punkt końcowy usługi w kodzie  
  
1. Utwórz interfejs, który definiuje kontrakt usługi.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Zaimplementuj kontrakt usługi zdefiniowany w kroku 1.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. W aplikacji hostingowej Utwórz adres podstawowy usługi i powiązanie, które ma być używane z usługą.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Utwórz hosta i Wywołaj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> lub jedno z innych przeciążeń, aby dodać punkt końcowy usługi dla hosta.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     Aby określić powiązanie w kodzie, ale aby użyć domyślnych punktów końcowych dostarczonych przez środowisko uruchomieniowe, Przekaż adres podstawowy do konstruktora podczas tworzenia <xref:System.ServiceModel.ServiceHost> i nie wywołuj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType> .  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](../simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: określanie wiązań usługi w kodzie](../how-to-specify-a-service-binding-in-code.md)
