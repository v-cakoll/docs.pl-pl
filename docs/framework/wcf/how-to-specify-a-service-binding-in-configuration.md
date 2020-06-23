---
title: 'Instrukcje: Określanie wiązania usługi w konfiguracji'
description: Dowiedz się, jak skonfigurować punkt końcowy dla usługi WCF w pliku konfiguracji. Kontrakt jest zdefiniowany dla usługi i zaimplementowany w klasie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 92d0834091a1f243df6be214f606fbf0093dca54
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244559"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Instrukcje: Określanie wiązania usługi w konfiguracji
W tym przykładzie `ICalculator` jest definiowana umowa dla podstawowej usługi kalkulatora, usługa jest zaimplementowana w `CalculatorService` klasie, a następnie jej punkt końcowy jest skonfigurowany w pliku Web.config, w którym zostanie określony, że usługa używa usługi <xref:System.ServiceModel.BasicHttpBinding> . Opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji można znaleźć [w temacie How to: Określanie powiązania usługi w kodzie](how-to-specify-a-service-binding-in-code.md).  
  
 Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi. Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.  
  
 Wszystkie poniższe kroki konfiguracji można wykonać przy użyciu [Narzędzia Edytora konfiguracji (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Aby uzyskać kopię źródła tego przykładu, zobacz temat [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Aby określić BasicHttpBinding do użycia w celu skonfigurowania usługi  
  
1. Zdefiniuj kontrakt usługi dla typu usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Zaimplementuj kontrakt usługi w klasie usługi.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Nie określono informacji o adresie lub powiązaniu w implementacji usługi. Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.  
  
3. Utwórz plik Web.config, aby skonfigurować punkt końcowy dla programu `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding> .  
  
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
  
4. Utwórz plik Service. svc zawierający poniższy wiersz i umieść go w katalogu wirtualnym Internet Information Services (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Aby zmodyfikować wartości domyślne właściwości powiązania  
  
1. Aby zmodyfikować jedną z domyślnych wartości właściwości <xref:System.ServiceModel.WSHttpBinding> , Utwórz nową nazwę konfiguracji powiązania — `<binding name="Binding1">` w obrębie [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) elementu i Ustaw nowe wartości atrybutów powiązania w tym elemencie powiązania. Na przykład aby zmienić domyślne wartości limitu czasu otwierania i zamykania z 1 minuty na 2 minuty, Dodaj następujący kod do pliku konfiguracji.  
  
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
