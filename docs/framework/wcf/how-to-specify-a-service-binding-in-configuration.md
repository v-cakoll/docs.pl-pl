---
title: "Instrukcje: Określanie powiązania usługi w konfiguracji"
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
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea54b2f84c9de233ff2560795dc97f79c15aa0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Instrukcje: Określanie powiązania usługi w konfiguracji
W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi podstawowe Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest skonfigurowana w pliku Web.config, w którym jest określone, że usługa używa <xref:System.ServiceModel.BasicHttpBinding> . Opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji, zobacz [porady: Określanie powiązania usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Jest zwykle najlepszym rozwiązaniem, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie imperatively w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane. Ogólnie rzecz biorąc pamiętając powiązania i adresowanie poza kod umożliwia im to zmienić bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.  
  
 Wszystkie z następujących kroków konfiguracji można podjąć przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Aby określić BasicHttpBinding służący do konfigurowania usługi  
  
1.  Definiowanie kontraktu usługi dla typu usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Implementowanie kontraktu usługi w klasie usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Nie określono informacji o adresie lub powiązania wewnątrz implementacji usługi. Ponadto kodu nie ma do zapisania można pobrać informacji z pliku konfiguracji.  
  
3.  Utwórz plik Web.config do konfigurowania punktu końcowego dla `CalculatorService` używającą <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Utwórz plik Service.svc, który zawiera następujący wiersz i umieść go w katalogu wirtualnym programu Internet Information Services (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Aby zmodyfikować wartości domyślne we właściwościach powiązania  
  
1.  Modyfikowania domyślnych wartości właściwości z <xref:System.ServiceModel.WSHttpBinding>, Utwórz nową nazwę konfiguracji powiązania - `<binding name="Binding1">` — poziomu [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element i ustaw nowe wartości dla atrybutów powiązanie, w tym elemencie powiązania. Na przykład aby zmienić domyślne Otwórz i zamknij wartości limitu czasu wynoszącym 1 minutę do 2 minuty, Dodaj do pliku konfiguracji.  
  
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
