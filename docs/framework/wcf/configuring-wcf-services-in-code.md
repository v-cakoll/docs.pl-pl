---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174813"
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie
Windows Communication Foundation (WCF) umożliwia deweloperom konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.  Pliki konfiguracyjne są przydatne, gdy usługa musi być skonfigurowana po wdrożeniu. Podczas korzystania z plików konfiguracyjnych specjalista IT musi tylko zaktualizować plik konfiguracyjny, nie jest wymagana ponowna kompilacja. Pliki konfiguracyjne mogą być jednak złożone i trudne do utrzymania. Nie ma obsługi debugowania plików konfiguracyjnych i elementy konfiguracji są odwoływane przez nazwy, które sprawia, że tworzenie plików konfiguracyjnych podatne na błędy i trudne. WCF umożliwia również konfigurowanie usług w kodzie. We wcześniejszych wersjach WCF (4.0 i wcześniejszych) konfigurowanie usług w kodzie <xref:System.ServiceModel.ServiceHost> było łatwe w scenariuszach hostowanych samodzielnie, klasa umożliwia skonfigurowanie punktów końcowych i zachowań przed wywołaniem ServiceHost.Open. W scenariuszach hostowanych w sieci Web nie masz <xref:System.ServiceModel.ServiceHost> jednak bezpośredniego dostępu do klasy. Aby skonfigurować usługę hosta sieci Web, `System.ServiceModel.ServiceHostFactory` konieczne było <xref:System.ServiceModel.Activation.ServiceHostFactory> utworzenie utworzonej i wykonanej dowolnej potrzebnej konfiguracji. Począwszy od platformy .NET 4.5, WCF zapewnia łatwiejszy sposób konfigurowania zarówno hostowanych samodzielnie, jak i hostowanych usług internetowych w kodzie.  
  
## <a name="the-configure-method"></a>Metoda Konfiguruj  
 Wystarczy zdefiniować publiczną `Configure` metodę statyczną wywołaną z następującym podpisem w klasie implementacji usługi:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure Metoda przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia deweloperowi dodawać punkty końcowe i zachowania. Ta metoda jest wywoływana przez WCF przed otwarciem hosta usługi. Po zdefiniowaniu wszystkie ustawienia konfiguracji usługi określone w pliku app.config lub web.config zostaną zignorowane.  
  
 Poniższy fragment kodu ilustruje sposób `Configure` definiowania metody i dodawania punktu końcowego usługi, zachowania punktu końcowego i zachowań usługi:  
  
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
  
 Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punkt końcowy, który używa protokołu, lub automatycznie dodać punkty końcowe, wywołując ServiceConfiguration.EnableProtocol(Binding), który dodaje punkt końcowy dla każdego adresu podstawowego zgodne z protokołem i każdą zdefiniowaną umową serwisową. Poniższy kod ilustruje sposób korzystania z ServiceConfiguration.EnableProtocol metody:  
  
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
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 Ustawienia w sekcji <`protocolMappings`> są używane tylko wtedy, gdy żadne punkty końcowe aplikacji nie są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Opcjonalnie można załadować konfigurację usługi z domyślnego pliku konfiguracji aplikacji, wywołując, <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a następnie zmienić ustawienia. Klasa <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> umożliwia również ładowanie konfiguracji ze scentralizowanej konfiguracji. Poniższy kod ilustruje sposób zaimplementowania tego:  
  
```csharp
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
> Pamiętaj, <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> że w <`host`>> tagu `system.serviceModel` <`service`> ignor <uje ustawienia>. Koncepcyjnie <`host`> dotyczy konfiguracji hosta, a nie konfiguracji usługi i jest ładowana przed wykonaniem metody Configure.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)
- [Konfigurowanie zachowań klienta](configuring-client-behaviors.md)
- [Uproszczona konfiguracja](simplified-configuration.md)
- [Konfiguracja](./samples/configuration-sample.md)
- [Aktywacja oparta na konfiguracji w usługach IIS i WAS](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [Konfiguracja i obsługa metadanych](./extending/configuration-and-metadata-support.md)
- [Konfiguracja](./diagnostics/exceptions-reference/configuration.md)
- [Instrukcje: określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md)
- [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Instrukcje: określanie powiązań klienta w konfiguracji](how-to-specify-a-client-binding-in-configuration.md)
