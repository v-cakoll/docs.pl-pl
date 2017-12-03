---
title: "Instrukcje: Określanie powiązań klienta w konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9db5559df52d0da2ee75945a25c026dfc6169969
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Instrukcje: Określanie powiązań klienta w konfiguracji
W tym przykładzie utworzono aplikacji konsoli klienta do używania usługi Kalkulator i deklaratywnie określono powiązania dla tego klienta w konfiguracji. Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługę i klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Procedury opisane przyjęto założenie, że jest uruchomiona usługa Kalkulator. Aby uzyskać informacje o sposobie budowania usługi, zobacz [porady: Określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Zastosowano [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) który [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] umożliwia automatyczne generowanie składników klienta. Narzędzie generuje kod klienta i konfiguracji do uzyskiwania dostępu do usługi.  
  
 Klient korzysta z wbudowanej w dwóch częściach. Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu. Ta aplikacja kliencka jest następnie tworzony przez tworzenia wystąpienia `ClientCalculator`.  
  
 Jest zwykle najlepszym rozwiązaniem, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie imperatively w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane. Ogólnie rzecz biorąc pamiętając powiązania i adresowanie poza kod umożliwia im to zmienić bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.  
  
 Można wykonać następujące kroki konfiguracji za pomocą [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) próbki.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Określanie powiązania w konfiguracji klienta  
  
1.  Użyj Svcutil.exe w wierszu polecenia, aby wygenerować kod na podstawie metadanych usługi.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  Wygenerowanego klienta zawiera także wykonania `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  Svcutil.exe generuje również konfiguracji klienta, który używa <xref:System.ServiceModel.BasicHttpBinding> klasy. Korzystając z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], nazwij ten plik App.config. Należy pamiętać, że adres i informacje o powiązaniu nie określono dowolnym wewnątrz implementacji usługi. Ponadto kodu nie ma do zapisania do pobierania informacji z pliku konfiguracji.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  Kompilowanie i uruchamianie klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
