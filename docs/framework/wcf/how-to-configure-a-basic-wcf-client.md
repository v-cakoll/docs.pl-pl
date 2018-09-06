---
title: 'Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 2866cbd5862bf55286fc771823488cf913863de2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855858"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)
Jest to piąty sześciu zadań podrzędnych, wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 W tym temacie omówiono pliku konfiguracji klienta, który został wygenerowany za pomocą funkcji Dodaj odwołanie do usługi [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] lub [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Konfigurowanie klienta składa się z określania punktu końcowego, który klient używa w celu uzyskania dostępu do usługi. Punkt końcowy ma adres, powiązanie i kontrakt, a każdy z nich musi być określona w procesie konfigurowania klienta.  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Aby skonfigurować klienta programu Windows Communication Foundation  
  
1.  Otwórz plik wygenerowanego konfiguracji (App.config) z projektu GettingStartedClient. Poniższy przykład jest widok pliku wygenerowaną konfigurację. W obszarze [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, Znajdź [ \<punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     Ten przykład umożliwia skonfigurowanie punktu końcowego, który klient używa w celu uzyskania dostępu do usługi, która znajduje się pod następującym adresem: http://localhost:8000/ServiceModelSamples/Service/CalculatorService  
  
     Element końcowy określa, że `ServiceReference1.ICalculator` kontraktu usługi jest używany do komunikacji między klientem usługi WCF a usługą. Kanał WCF jest skonfigurowany przy użyciu dostarczane przez system <xref:System.ServiceModel.WSHttpBinding>. Ten kontrakt został wygenerowany za pomocą Dodaj odwołanie do usługi w programie Visual Studio. Jest zasadniczo kopię umowy, która została zdefiniowana w projekcie GettingStartedLib. <xref:System.ServiceModel.WSHttpBinding> Powiązanie określa HTTP jako transportu, interoperacyjne zabezpieczeń i inne szczegóły konfiguracji.  
  
2.  Aby uzyskać więcej informacji o sposobie używania wygenerowanego klienta przy użyciu tej konfiguracji, zobacz [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
