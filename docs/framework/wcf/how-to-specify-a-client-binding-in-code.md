---
title: 'Instrukcje: Określanie wiązania klienta w kodzie'
description: Dowiedz się, jak w kodzie określić powiązanie dla klienta WCF. Klient uzyskuje dostęp do usługi w tym przykładzie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: e5e1dff98121985a598579d83043de838e21e5f1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244507"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Instrukcje: Określanie wiązania klienta w kodzie
W tym przykładzie klient został utworzony w celu korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określone w kodzie. Klient uzyskuje dostęp do `CalculatorService` , który implementuje `ICalculator` interfejs, a zarówno usługa, jak i klient używają <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 W tej procedurze przyjęto założenie, że usługa kalkulatora jest uruchomiona. Aby uzyskać informacje na temat tworzenia usługi, zobacz [How to: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md). Używa także narzędzia do [przesyłania metadanych modelu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) zapewnia automatyczne generowanie składników klienta. Narzędzie generuje kod klienta na potrzeby uzyskiwania dostępu do usługi.  
  
 Klient jest skompilowany w dwóch częściach. Svcutil.exe generuje `ClientCalculator` , który implementuje `ICalculator` interfejs. Ta aplikacja kliencka jest następnie tworzona przez konstruowanie wystąpienia, `ClientCalculator` a następnie określenie powiązania i adresu usługi w kodzie.  
  
 Aby uzyskać kopię źródła tego przykładu, zobacz przykład [podstawowabinding](./samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Aby określić niestandardowe powiązanie w kodzie  
  
1. Użyj Svcutil.exe z wiersza polecenia w celu wygenerowania kodu z metadanych usługi.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Wygenerowany klient również zawiera implementację programu `ClientCalculator` .  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Utwórz wystąpienie `ClientCalculator` , które używa <xref:System.ServiceModel.BasicHttpBinding> klasy w aplikacji klienckiej, a następnie Wywołaj operacje usługi pod podanym adresem.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Kompiluj i uruchom klienta.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
