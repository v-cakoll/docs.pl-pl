---
title: 'Instrukcje: Określanie powiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: c95e30c65c6096140fca0c1241e76fbc7af4df3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929132"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Instrukcje: Określanie powiązania klienta w kodzie
W tym przykładzie zostanie utworzona usługa Kalkulator klienta i obowiązkowo określono powiązania dla tego klienta w kodzie. Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługi oraz klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 W tej procedurze założono, że usługa Kalkulator jest uruchomiona. Aby uzyskać informacje o tworzeniu usługi, zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Korzysta również [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) umożliwia automatyczne generowanie składniki klienta. Narzędzie generuje kod klienta do uzyskania dostępu do usługi.  
  
 Klient została stworzona w dwóch częściach. Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu. Ta aplikacja kliencka jest następnie tworzony przez utworzenie wystąpienia `ClientCalculator` , a następnie określając powiązania i adres usługi w kodzie.  
  
 Źródło kopię w tym przykładzie można zobaczyć [element basicbinding elementem](../../../docs/framework/wcf/samples/basicbinding.md) próbki.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Aby określić niestandardowe powiązanie w kodzie  
  
1. Umożliwia Svcutil.exe w wierszu polecenia generowanie kodu na podstawie metadanych usługi.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Wygenerowanego klienta zawiera również implementację `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Utwórz wystąpienie obiektu `ClientCalculator` , który używa <xref:System.ServiceModel.BasicHttpBinding> klasy w aplikacji klienckiej, a następnie Wywołaj operacje usług pod podanym adresem.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Kompilowanie i uruchamianie klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
