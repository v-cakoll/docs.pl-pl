---
title: 'Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bde13abeac782da1c553afa290943eeff925fa4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)
To jest piątym sześciu zadania wymagane do tworzenia prostej [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji. Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 Ten temat disuccess pliku konfiguracji klienta, który został wygenerowany za pomocą funkcji Dodaj odwołanie do usługi [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] lub [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Konfigurowanie klienta obejmuje określenie punktu końcowego, który klient używa do uzyskania dostępu do usługi. Punkt końcowy ma adres, powiązania i kontrakt i każdego z nich musi być określona podczas konfigurowania klienta.  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Aby skonfigurować klienta Windows Communication Foundation  
  
1.  Otwórz plik konfiguracji wygenerowanego (App.config) z projektu GettingStartedClient. Poniższy przykład jest to widok pliku konfiguracyjnego wygenerowany. W obszarze [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, Znajdź [ \<punktu końcowego >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
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
  
     Ten przykład konfiguruje punktu końcowego, który klient używa do uzyskania dostępu do usługi, która znajduje się pod następującym adresem: http://localhost:8000/ServiceModelSamples/Service/CalculatorService  
  
     Określa element punktu końcowego, że `ServiceReference1.ICalculator` kontraktu usługi jest używany do komunikacji między klienta WCF i usługi. Skonfigurowano kanał WCF dostarczane przez system <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>. Ten kontrakt wygenerowanych przy użyciu Dodaj odwołanie do usługi w programie Visual Studio. Jest zasadniczo kopią kontraktu, który został zdefiniowany w projekcie GettingStartedLib. <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Powiązanie określa HTTP jako transportu, interoperacyjne zabezpieczeń i inne szczegóły konfiguracji.  
  
2.  Aby uzyskać więcej informacji o sposobie używania wygenerowanego klienta w tej konfiguracji, zobacz [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
