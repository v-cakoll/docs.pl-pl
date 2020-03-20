---
title: 'Instrukcje: Określanie wiązania usługi w konfiguracji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 245fe50ed5a80c51163652defb642cebefd55dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184030"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Instrukcje: Określanie wiązania usługi w konfiguracji
W tym przykładzie `ICalculator` kontrakt jest zdefiniowany dla podstawowej usługi kalkulatora, usługa jest implementowana w `CalculatorService` klasie, a następnie jej punkt końcowy jest konfigurowany w pliku Web.config, gdzie określono, że usługa używa <xref:System.ServiceModel.BasicHttpBinding>. . Aby uzyskać opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji, zobacz [Jak: Określanie powiązania usługi w kodzie](how-to-specify-a-service-binding-in-code.md).  
  
 Zazwyczaj jest najlepszym rozwiązaniem, aby określić informacje dotyczące powiązania i adresu deklaratywnie w konfiguracji, a nie bezwzględnie w kodzie. Definiowanie punktów końcowych w kodzie zwykle nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi zazwyczaj różnią się od tych używanych podczas opracowywania usługi. Bardziej ogólnie, utrzymywanie powiązanie i adresowanie informacji z kodu pozwala na ich zmiany bez konieczności ponownego kompilowania lub ponownego rozmieszczenia aplikacji.  
  
 Wszystkie następujące kroki konfiguracji można wykonać za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](configuration-editor-tool-svcconfigeditor-exe.md)  
  
 Aby zapoznać się z kopią źródłową tego przykładu, zobacz [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Aby określić podstawowe powiązaniehttpa, które ma być używane do konfigurowania usługi  
  
1. Zdefiniuj umowę serwisową dla typu usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Zaimplementuj umowę serwisową w klasie usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Adres lub wiążące informacje nie jest określony wewnątrz implementacji usługi. Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.  
  
3. Utwórz plik Web.config, aby skonfigurować `CalculatorService` punkt końcowy <xref:System.ServiceModel.WSHttpBinding>dla punktu, który używa pliku .  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Utwórz plik Service.svc zawierający następujący wiersz i umieść go w katalogu wirtualnym internetowych usług informacyjnych (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Aby zmodyfikować wartości domyślne właściwości wiązania  
  
1. Aby zmodyfikować jedną z domyślnych wartości właściwości <xref:System.ServiceModel.WSHttpBinding>, `<binding name="Binding1">` utwórz nową nazwę konfiguracji powiązania - — w ramach [ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element i ustawić nowe wartości dla atrybutów powiązania w tym elemencie wiązania. Na przykład, aby zmienić domyślne wartości limitu czasu otwarcia i zamknięcia od 1 minuty do 2 minut, dodaj następujące wartości do pliku konfiguracji.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
- [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md)
