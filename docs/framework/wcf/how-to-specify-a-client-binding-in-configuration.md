---
title: 'Instrukcje: Określanie wiązań klienta w konfiguracji'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184036"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Instrukcje: Określanie wiązań klienta w konfiguracji
W tym przykładzie aplikacja konsoli klienta jest tworzony do korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określony deklaratywnie w konfiguracji. Klient uzyskuje dostęp `CalculatorService`do , `ICalculator` który implementuje interfejs, a zarówno <xref:System.ServiceModel.BasicHttpBinding> usługi i klienta używać klasy.  
  
 Opisana procedura zakłada, że usługa kalkulatora jest uruchomiona. Aby uzyskać informacje dotyczące sposobu tworzenia usługi, zobacz [Jak: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md). Używa również [ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md) które program Windows Communication Foundation (WCF) zapewnia do automatycznego generowania składników klienta. Narzędzie generuje kod klienta i konfiguracji dostępu do usługi.  
  
 Klient jest zbudowany w dwóch częściach. Svcutil.exe `ClientCalculator` generuje, który implementuje `ICalculator` interfejs. Ta aplikacja kliencka jest następnie konstruowana przez skonstruowanie wystąpienia . `ClientCalculator`  
  
 Zazwyczaj jest najlepszym rozwiązaniem, aby określić informacje dotyczące powiązania i adresu deklaratywnie w konfiguracji, a nie bezwzględnie w kodzie. Definiowanie punktów końcowych w kodzie zwykle nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi zazwyczaj różnią się od tych używanych podczas opracowywania usługi. Bardziej ogólnie, utrzymywanie powiązanie i adresowanie informacji z kodu pozwala na ich zmiany bez konieczności ponownego kompilowania lub ponownego rozmieszczenia aplikacji.  
  
 Wszystkie następujące kroki konfiguracji można wykonać za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](configuration-editor-tool-svcconfigeditor-exe.md)  
  
 Aby uzyskać kopię źródłową tego przykładu, zobacz [BasicBinding](./samples/basicbinding.md) próbki.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Określanie powiązania klienta w konfiguracji  
  
1. Użyj programu Svcutil.exe z wiersza polecenia, aby wygenerować kod z metadanych usługi.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Klient, który jest `ICalculator` generowany zawiera interfejs, który definiuje umowy serwisowej, że implementacja klienta musi spełniać.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Wygenerowany klient zawiera również `ClientCalculator`implementację pliku .  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe generuje również konfigurację dla klienta, <xref:System.ServiceModel.BasicHttpBinding> który używa klasy. Podczas korzystania z programu Visual Studio, nazwa tego pliku App.config. Należy zauważyć, że adres i informacje o powiązaniach nie są określone w dowolnym miejscu wewnątrz implementacji usługi. Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołaj operacje usługi.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Skompiluj i uruchom klienta.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
