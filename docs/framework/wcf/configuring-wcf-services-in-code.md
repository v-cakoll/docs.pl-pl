---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 714236bcdb562840323698622cdf3d0c6c89b6ca
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie
Windows Communication Foundation (WCF) umożliwia deweloperom konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.  Pliki konfiguracji są przydatne, gdy usługa musi być skonfigurowana po wdrożeniu. Podczas korzystania z plików konfiguracyjnych, specjalistów IT wystarczy tylko zaktualizować pliku konfiguracji, kompilacji nie jest wymagana. Pliki konfiguracji, jednak można złożone i trudne w utrzymaniu. Nie jest obsługiwane dla debugowania plików konfiguracji i elementy konfiguracji odwołują się nazwy, dzięki czemu tworzenia plików konfiguracyjnych podatne na błędy i trudne. Usługi WCF umożliwia również konfigurowanie usługi w kodzie. W starszych wersjach, konfigurowanie usług WCF (4.0 i starszych) w kodzie było łatwe w scenariuszach siebie <xref:System.ServiceModel.ServiceHost> klasa dozwolona konfigurowania punktów końcowych i zachowania przed wywołaniem ServiceHost.Open. W scenariuszach hostowana w sieci web, możesz nie mają jednak bezpośredni dostęp do <xref:System.ServiceModel.ServiceHost> klasy. Aby skonfigurować sieci web hostowanej usługi są wymagane do utworzenia `System.ServiceModel.ServiceHostFactory` utworzony <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać wszelkie wymagane konfiguracji. Począwszy od platformy .NET 4.5, usługi WCF zapewnia łatwiejszy sposób skonfigurowania obu hosta samodzielnego i sieci web hostowanej usługi w kodzie.  
  
## <a name="the-configure-method"></a>Konfiguruj — metoda  
 Wystarczy zdefiniować publicznej metody statycznej o nazwie `Configure` z następującą sygnaturą w klasie implementacji usługi:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Metoda Konfiguruj przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia deweloperowi dodać punkty końcowe i zachowania. Ta metoda jest wywoływana przez usługi WCF, przed otwarciem hosta usługi. Po zdefiniowaniu wszystkich ustawień konfiguracji usługi określone w pliku app.config lub web.config zostaną zignorowane.  
  
 Poniższy fragment kodu przedstawia sposób definiowania `Configure` — metoda i Dodaj punkt końcowy usługi, zachowanie punktu końcowego i zachowania usługi:  
  
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
            return string.Format("You entered: {0}", value);  
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
  
 Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punktu końcowego, który korzysta z protokołu lub może automatycznie dodać punkty końcowe, wywołując ServiceConfiguration.EnableProtocol(Binding), który dodaje punkt końcowy dla każdego adresu podstawowego zgodny z protokołem i każdej umowy serwisowej zdefiniowane. Poniższy kod przedstawia sposób użycia metody ServiceConfiguration.EnableProtocol:  
  
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
  
 Ustawienia w <`protocolMappings`> sekcji są używane tylko w przypadku punktów końcowych aplikacji są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Można opcjonalnie załadować konfiguracji usługi z domyślny plik konfiguracji aplikacji, wywołując <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> , a następnie zmień ustawienia. <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Klasa umożliwia także załadować konfiguracji z scentralizowane konfiguracji. Poniższy kod ilustruje sposób implementowania to:  
  
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
>  Należy pamiętać, że <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Ustawienia w <`service`> tag <`system.serviceModel`>. Koncepcyjnie <`host`> jest o konfiguracji hosta, nie konfigurację usługi i pobiera załadowane przed wykonaniem metody konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Konfigurowanie zachowań klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 [Aktywacja oparta na konfiguracji](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [Konfiguracja](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [Aktywacja oparta na konfiguracji w usługach IIS i WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [Konfiguracja i obsługa metadanych](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [Konfiguracja](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [Instrukcje: określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Instrukcje: określanie powiązań klienta w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
