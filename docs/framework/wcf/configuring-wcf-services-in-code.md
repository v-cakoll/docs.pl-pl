---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: c6bcf08511470d28e1087108d95e477683b0338b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320642"
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie
Windows Communication Foundation (WCF) umożliwia deweloperom Konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.  Pliki konfiguracji są przydatne, gdy usługa musi zostać skonfigurowana po wdrożeniu. W przypadku korzystania z plików konfiguracji Specjalista IT musi tylko zaktualizować plik konfiguracji, nie jest wymagana ponowna kompilacja. Pliki konfiguracji mogą jednak być skomplikowane i trudne do utrzymania. Nie ma obsługi debugowania plików konfiguracji i elementów konfiguracji, do których odwołują się nazwy, co sprawia, że pliki konfiguracji tworzenia są podatne na błędy i trudne. Funkcja WCF umożliwia również Konfigurowanie usług w kodzie. We wcześniejszych wersjach programu WCF (4,0 i starszych) Konfigurowanie usług w kodzie było łatwe w scenariuszach samoobsługowych, ale Klasa <xref:System.ServiceModel.ServiceHost> umożliwia konfigurowanie punktów końcowych i zachowań przed wywołaniem ServiceHost. Open. Jednak w scenariuszach hostowanych w sieci Web nie masz bezpośredniego dostępu do klasy <xref:System.ServiceModel.ServiceHost>. Aby skonfigurować usługę hostowaną w sieci Web, należy utworzyć `System.ServiceModel.ServiceHostFactory`, która utworzyła <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać dowolną wymaganą konfigurację. Począwszy od platformy .NET 4,5, WCF oferuje łatwiejszy sposób konfigurowania usług samodzielnych i hostowanych w sieci Web w kodzie.  
  
## <a name="the-configure-method"></a>Metoda Configure  
 Po prostu Zdefiniuj publiczną metodę statyczną o nazwie `Configure` z następującą sygnaturą w klasie implementacji usługi:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Metoda Configure przyjmuje wystąpienie <xref:System.ServiceModel.ServiceConfiguration>, które umożliwia deweloperom Dodawanie punktów końcowych i zachowań. Ta metoda jest wywoływana przez funkcję WCF przed otwarciem hosta usługi. Po zdefiniowaniu wszystkie ustawienia konfiguracji usługi określone w pliku App. config lub Web. config zostaną zignorowane.  
  
 Poniższy fragment kodu ilustruje sposób definiowania metody `Configure` i dodawania punktu końcowego usługi, zachowania punktu końcowego i zachowań usługi:  
  
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
  
 Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punkt końcowy, który używa protokołu lub można automatycznie dodać punkty końcowe, wywołując metodę ServiceConfiguration. EnableProtocol (Binding), która dodaje punkt końcowy dla każdego adresu podstawowego zgodne z protokołem i każdym zdefiniowanym kontraktem usługi. Poniższy kod ilustruje sposób używania metody ServiceConfiguration. EnableProtocol:  
  
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
  
 Ustawienia w sekcji < `protocolMappings` > są używane tylko wtedy, gdy żadne punkty końcowe aplikacji nie są dodawane do programu programistycznego <xref:System.ServiceModel.ServiceConfiguration>. Opcjonalnie można załadować konfigurację usługi z domyślnego pliku konfiguracyjnego aplikacji, wywołując <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>, a następnie zmieniając ustawienia. Klasa <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> umożliwia również ładowanie konfiguracji z poziomu scentralizowanej konfiguracji. Poniższy kod ilustruje sposób implementacji:  
  
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
> Należy zauważyć, że <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje < `host` > Ustawienia w < `service` > <. Koncepcyjnie < `host` > jest informacje o konfiguracji hosta, a nie konfiguracji usługi i jest ładowany przed wykonaniem metody Configure.  
  
## <a name="see-also"></a>Zobacz także

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
