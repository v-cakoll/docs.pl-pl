---
title: "Instrukcje: Określanie powiązania klienta w kodzie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6c44bc03642eb83a28497b320a77b2f9f8c6fb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Instrukcje: Określanie powiązania klienta w kodzie
W tym przykładzie klient jest tworzony na korzystanie z usługi Kalkulator i imperatively określono powiązania dla tego klienta w kodzie. Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługę i klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 W tej procedurze założono, że jest uruchomiona usługa Kalkulator. Dla informacji o tworzeniu usługi, zobacz [porady: Określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Zastosowano [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] umożliwia automatyczne generowanie składników klienta. Narzędzie generuje kod klienta do uzyskiwania dostępu do usługi.  
  
 Klient korzysta z wbudowanej w dwóch częściach. Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu. Ta aplikacja kliencka jest następnie tworzony przez tworzenia wystąpienia `ClientCalculator` , a następnie określając powiązanie i adres dla usługi w kodzie.  
  
 Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) próbki.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Aby określić niestandardowego powiązania w kodzie  
  
1.  Użyj Svcutil.exe w wierszu polecenia, aby wygenerować kod na podstawie metadanych usługi.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  Wygenerowanego klienta zawiera także wykonania `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  Utwórz wystąpienie `ClientCalculator` używającą <xref:System.ServiceModel.BasicHttpBinding> klasy w aplikacji klienta, a następnie wywołać operacji usługi pod określonym adresem.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  Kompilowanie i uruchamianie klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
