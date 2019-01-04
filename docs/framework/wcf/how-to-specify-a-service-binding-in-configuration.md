---
title: 'Instrukcje: Określanie wiązania usługi w konfiguracji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 1d9a6d0a556613576a14c600aa72d3f4524cdc3e
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029635"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Instrukcje: Określanie wiązania usługi w konfiguracji
W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi podstawowa Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest skonfigurowany w pliku Web.config, gdzie jest określone, że usługa używa <xref:System.ServiceModel.BasicHttpBinding> . Aby uzyskać opis sposobu konfigurowania tej usługi przy użyciu kodu, a nie z konfiguracji, zobacz [jak: Określanie wiązań usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Jest zwykle najlepszym rozwiązaniem jest, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie obowiązkowo w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana. Ogólnie rzecz biorąc zachowanie wiązania i adresowanie z kodu pozwala na zmianę bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.  
  
 Wszystkie poniższe czynności konfiguracyjne można podjąć przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Źródło kopię w tym przykładzie można zobaczyć [element basicbinding elementem](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Aby określić BasicHttpBinding służące do konfigurowania usługi  
  
1.  Definiowanie kontraktu usługi dla typu usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Implementowanie kontraktu usługi, w klasie usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Nie określono adresu lub powiązania informacji wewnątrz implementacji usługi. Ponadto kod nie ma do zapisania do pobrania informacji z pliku konfiguracji.  
  
3.  Tworzenie pliku Web.config w celu konfigurowania punktu końcowego dla `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding>.  
  
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
  
4.  Utwórz plik Service.svc, który zawiera następujący wiersz i umieścić go w katalogu wirtualnego Internet Information Services (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Aby zmodyfikować domyślne wartości właściwości powiązania  
  
1.  Aby zmodyfikować jedną z domyślnych wartości właściwości z <xref:System.ServiceModel.WSHttpBinding>, utworzyć nową nazwę konfiguracji powiązania — `<binding name="Binding1">` — w ramach [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element i ustaw nowe wartości dla atrybutów powiązania, w tym elemencie powiązania. Na przykład aby zmienić open domyślne i zamknąć wartości limitu czasu wynoszącym 1 minutę na 2 minuty, w pliku konfiguracji dodać.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
