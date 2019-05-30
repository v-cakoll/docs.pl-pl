---
title: 'Instrukcje: tworzenie punktu końcowego w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 9b7b983122b9e30fd7c6b0d0c517a9483b8881c5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301465"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>Instrukcje: tworzenie punktu końcowego w kodzie
W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest zdefiniowana w kodzie, w której jest określony, że należy używać usługa programu <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Jest zwykle najlepszym rozwiązaniem jest, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie obowiązkowo w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana. Ogólnie rzecz biorąc zachowanie wiązania i adresowanie z kodu pozwala na zmianę bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>Aby utworzyć punkt końcowy usługi w kodzie  
  
1. Utwórz interfejs, który definiuje kontrakt usługi.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Implementowanie kontraktu usługi, zdefiniowane w kroku 1.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. W aplikacji macierzystej Utwórz adres podstawowy dla usługi i powiązania do użycia z usługą.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Tworzenie hosta i wywołania <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> lub jednego z innych przeciążeń, aby dodać punkt końcowy usługi dla hosta.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     Aby określić powiązanie w kodzie, ale Użyj domyślnych punktów końcowych, udostępniane przez środowisko uruchomieniowe, Przekaż adres podstawowy do konstruktora podczas tworzenia <xref:System.ServiceModel.ServiceHost>, a nie wywołuj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie wiązań usługi w kodzie](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
