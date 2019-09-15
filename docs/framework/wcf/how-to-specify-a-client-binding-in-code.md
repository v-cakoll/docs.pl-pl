---
title: 'Instrukcje: Określanie powiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990236"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Instrukcje: Określanie powiązania klienta w kodzie
W tym przykładzie klient został utworzony w celu korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określone w kodzie. Klient uzyskuje dostęp `CalculatorService`do, który `ICalculator` implementuje interfejs, a zarówno usługa, <xref:System.ServiceModel.BasicHttpBinding> jak i klient używają klasy.  
  
 W tej procedurze przyjęto założenie, że usługa kalkulatora jest uruchomiona. Aby uzyskać informacje na temat tworzenia usługi, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Używa także [narzędzia Svcutil. exe (narzędzie do przesyłania metadanych Windows Communication Foundation)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)(WCF) zapewnia automatyczne generowanie składników klienta. Narzędzie generuje kod klienta na potrzeby uzyskiwania dostępu do usługi.  
  
 Klient jest skompilowany w dwóch częściach. Svcutil. exe generuje `ClientCalculator` , który `ICalculator` implementuje interfejs. Ta aplikacja kliencka jest następnie tworzona przez konstruowanie wystąpienia `ClientCalculator` , a następnie określenie powiązania i adresu usługi w kodzie.  
  
 Aby uzyskać kopię źródła tego przykładu, zobacz przykład [podstawowabinding](../../../docs/framework/wcf/samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Aby określić niestandardowe powiązanie w kodzie  
  
1. Użyj Svcutil. exe z wiersza polecenia w celu wygenerowania kodu z metadanych usługi.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Wygenerowany klient również zawiera implementację `ClientCalculator`programu.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Utwórz wystąpienie `ClientCalculator` , które <xref:System.ServiceModel.BasicHttpBinding> używa klasy w aplikacji klienckiej, a następnie Wywołaj operacje usługi pod podanym adresem.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Kompiluj i uruchom klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
