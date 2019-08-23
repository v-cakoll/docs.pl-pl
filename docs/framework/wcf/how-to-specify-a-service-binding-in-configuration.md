---
title: 'Instrukcje: Określanie powiązania usługi w konfiguracji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: d3224b1d732fb82ffe68e8ce0bd410850004cb95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967154"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Instrukcje: Określanie powiązania usługi w konfiguracji
W tym przykładzie `ICalculator` jest definiowana umowa dla podstawowej usługi kalkulatora, usługa jest zaimplementowana `CalculatorService` w klasie, a następnie jej punkt końcowy jest skonfigurowany w pliku Web. config, gdzie jest określony <xref:System.ServiceModel.BasicHttpBinding> , że usługa używa . Opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji można znaleźć w temacie [How to: Określ powiązanie usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi. Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.  
  
 Wszystkie poniższe kroki konfiguracji można wykonać za pomocą [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Aby uzyskać kopię źródła tego przykładu, [](../../../docs/framework/wcf/samples/basicbinding.md)Zobacz temat BasicBinding.  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Aby określić BasicHttpBinding do użycia w celu skonfigurowania usługi  
  
1. Zdefiniuj kontrakt usługi dla typu usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Zaimplementuj kontrakt usługi w klasie usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Nie określono informacji o adresie lub powiązaniu w implementacji usługi. Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.  
  
3. Utwórz plik Web. config, aby skonfigurować punkt końcowy dla programu `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding>programu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
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
  
4. Utwórz plik Service. svc zawierający poniższy wiersz i umieść go w katalogu wirtualnym Internet Information Services (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Aby zmodyfikować wartości domyślne właściwości powiązania  
  
1. Aby zmodyfikować jedną z domyślnych wartości <xref:System.ServiceModel.WSHttpBinding>właściwości, Utwórz nową nazwę konfiguracji powiązania — `<binding name="Binding1">` w obrębie elementu [ \<WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) i Ustaw nowe wartości atrybutów powiązania w ramach tego powiązania. postaci. Na przykład aby zmienić domyślne wartości limitu czasu otwierania i zamykania z 1 minuty na 2 minuty, Dodaj następujący kod do pliku konfiguracji.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
