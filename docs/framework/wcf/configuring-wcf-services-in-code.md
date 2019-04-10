---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 8a1eeff76b02315143fb7b50ccc41aa18bb9eb0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225706"
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie
Windows Communication Foundation (WCF) umożliwia deweloperom konfigurowanie usług za pomocą plików konfiguracji lub kodu.  Pliki konfiguracyjne są przydatne, gdy usługa musi zostać skonfigurowane po wdrożeniu. Korzystając z plików konfiguracji, specjalistów IT wystarczy zaktualizować plik konfiguracji, nie ponownej kompilacji jest wymagana. Pliki konfiguracyjne, może jednak być złożone i trudne w utrzymaniu. Brak obsługi debugowania plików konfiguracji i elementy konfiguracji odwołują się nazwy, co sprawia, że pliki konfiguracji tworzenia podatne na błędy i trudne. WCF umożliwia również skonfigurowanie usługi w kodzie. We wcześniejszych wersjach, konfigurowanie usług WCF (4.0 i starszych) w kodzie jest łatwe w scenariuszach Self-Hosted <xref:System.ServiceModel.ServiceHost> klasa dozwolona można skonfigurować punkty końcowe i zachowania przed wywołaniem ServiceHost.Open. W scenariuszach hostowanych w sieci web, ale nie masz bezpośredni dostęp do <xref:System.ServiceModel.ServiceHost> klasy. Aby skonfigurować sieci web hostowanych usług, które są wymagane do utworzenia `System.ServiceModel.ServiceHostFactory` utworzonego <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać wszelkie wymagane konfiguracji. Począwszy od .NET 4.5 programu WCF zapewnia łatwiejszy sposób skonfigurować zarówno może być samodzielnie hostowane i sieci web hostowanej usługi w kodzie.  
  
## <a name="the-configure-method"></a>Metoda Konfiguruj  
 Wystarczy zdefiniować publicznej statycznej metody o nazwie `Configure` z następującą sygnaturą w klasie implementacji usługi:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Metoda Konfiguruj przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia dla deweloperów dodać punkty końcowe i zachowania. Ta metoda jest wywoływana przez architekturę WCF, przed otwarciem hosta usługi. Po zdefiniowaniu wszystkie ustawienia konfiguracji usługi w pliku app.config lub web.config zostaną zignorowane.  
  
 Poniższy fragment kodu ilustruje sposób definiowania `Configure` metody i Dodaj punkt końcowy usługi, zachowanie punktu końcowego i zachowania usługi:  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punkt końcowy, który korzysta z protokołu lub można automatycznie dodać punkty końcowe, wywołując ServiceConfiguration.EnableProtocol(Binding), który dodaje punkt końcowy dla każdego adresu podstawowego zgodny z protokołem i każdej umowy serwisowej zdefiniowane. Poniższy kod ilustruje sposób użycia metody ServiceConfiguration.EnableProtocol:  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 Ustawienia w <`protocolMappings`> sekcji są używane tylko w przypadku punktów końcowych aplikacji są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Możesz opcjonalnie załadować konfiguracji usługi z domyślny plik konfiguracji aplikacji, wywołując <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> , a następnie zmień ustawienia. <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Klasy umożliwia także załadować konfiguracji ze scentralizowanego konfiguracji. Poniższy kod ilustruje sposób implementacji:  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
>  Należy pamiętać, że <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Ustawienia w <`service`> tag <`system.serviceModel`>. Model <`host`> dotyczy konfiguracji hosta, nie konfiguracji usługi i pobiera załadowane przed wykonaniem metody konfiguracji.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Konfigurowanie zachowań klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)
- [Konfiguracja](../../../docs/framework/wcf/samples/configuration-sample.md)
- [Aktywacja oparta na konfiguracji w usługach IIS i WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [Konfiguracja i obsługa metadanych](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [Konfiguracja](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [Instrukcje: Określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Instrukcje: Określanie powiązań klienta w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
