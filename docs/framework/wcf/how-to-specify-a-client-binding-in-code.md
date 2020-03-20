---
title: 'Instrukcje: Określanie wiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184055"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Instrukcje: Określanie wiązania klienta w kodzie
W tym przykładzie klient jest tworzony do korzystania z usługi kalkulatora i powiązanie dla tego klienta jest określony bezwzględnie w kodzie. Klient uzyskuje dostęp `CalculatorService`do , `ICalculator` który implementuje interfejs, a zarówno <xref:System.ServiceModel.BasicHttpBinding> usługi i klienta używać klasy.  
  
 Ta procedura zakłada, że usługa kalkulatora jest uruchomiona. Aby uzyskać informacje na temat tworzenia usługi, zobacz [Jak: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md). Używa również [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) zapewnia do automatycznego generowania składników klienta. Narzędzie generuje kod klienta dostępu do usługi.  
  
 Klient jest zbudowany w dwóch częściach. Svcutil.exe `ClientCalculator` generuje, który implementuje `ICalculator` interfejs. Ta aplikacja kliencka jest następnie konstruowana przez konstruowanie wystąpienia, `ClientCalculator` a następnie określanie powiązania i adresu dla usługi w kodzie.  
  
 Aby uzyskać kopię źródłową tego przykładu, zobacz [BasicBinding](./samples/basicbinding.md) próbki.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Aby określić niestandardowe powiązanie w kodzie  
  
1. Użyj programu Svcutil.exe z wiersza polecenia, aby wygenerować kod z metadanych usługi.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Klient, który jest `ICalculator` generowany zawiera interfejs, który definiuje umowy serwisowej, że implementacja klienta musi spełniać.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Wygenerowany klient zawiera również `ClientCalculator`implementację pliku .  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Utwórz `ClientCalculator` wystąpienie, które <xref:System.ServiceModel.BasicHttpBinding> używa klasy w aplikacji klienckiej, a następnie wywołać operacje usługi pod określonym adresem.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Skompiluj i uruchom klienta.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
