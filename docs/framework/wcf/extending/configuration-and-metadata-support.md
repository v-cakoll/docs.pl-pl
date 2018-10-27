---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 65c826c909496a9efeb99801142eb49e4f92d3bc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183493"
---
# <a name="configuration-and-metadata-support"></a>Konfiguracja i obsługa metadanych
W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązania i elementy powiązań.  
  
## <a name="overview-of-configuration-and-metadata"></a>Omówienie konfiguracji i metadanych  
 W tym temacie omówiono czynności, które są elementy opcjonalne, 1, 2 i 4 w [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md) listy zadań.  
  
-   Włączanie obsługę element powiązania w pliku konfiguracji.  
  
-   Włączanie obsługi plików konfiguracji dla powiązania.  
  
-   Eksportowanie WSDL i zasady potwierdzenia dla elementu powiązania.  
  
-   Identyfikowanie potwierdzenia WSDL i zasady, aby wstawić i skonfiguruj powiązania lub element powiązania.  
  
 Aby uzyskać informacji na temat tworzenia powiązań zdefiniowanych przez użytkownika i elementy powiązań, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) i [Tworzenie elementu BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)odpowiednio.  
  
## <a name="adding-configuration-support"></a>Dodanie obsługi konfiguracji  
 Aby włączyć obsługę pliku konfiguracji dla kanału, musi implementować dwie sekcje konfiguracji <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, umożliwiająca obsługę konfiguracji dla elementów, wiązania i <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, umożliwiają one obsługę konfiguracji powiązania.  
  
 Łatwiejszy sposób, w tym celu jest użycie [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) przykładowe narzędzie do generowania kodu konfiguracji dla powiązania i elementy powiązań.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozszerzanie BindingElementExtensionElement  
 Poniższy przykład kodu jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki. `UdpTransportElement` Jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> który uwidacznia `UdpTransportBindingElement` systemu konfiguracji. Za pomocą kilku podstawowych zastąpień przykład definiuje nazwa sekcji konfiguracji, typem elementu powiązania i jak można utworzyć elementu powiązania. Użytkownicy mogą następnie rejestrować w sekcji rozszerzeń w pliku konfiguracji w następujący sposób.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Rozszerzenia mogą być przywoływane z powiązań niestandardowych, aby używać protokołu UDP transportu.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a>Dodawanie konfiguracji dla powiązania  
 Sekcja `SampleProfileUdpBindingCollectionElement` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> który uwidacznia `SampleProfileUdpBinding` systemu konfiguracji. Duża część wykonania jest delegowane do `SampleProfileUdpBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odnoszą się do właściwości `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania. Na koniec `OnApplyConfiguration` metoda zostanie przesłonięta w `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, dodaj następującą sekcję do pliku konfiguracyjnego istotne.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Następnie mogą być przywoływane z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji konfiguracji.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Dodanie obsługi metadanych elementu powiązania  
 Aby zintegrować kanał w systemie metadanych, musi obsługiwać importu i eksportu zasad. Dzięki temu narzędzi takich jak [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klientów elementu powiązania.  
  
### <a name="adding-wsdl-support"></a>Dodawanie pomocy technicznej WSDL  
 Element powiązania transportu powiązanie jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych. Korzystając z powiązania protokołu SOAP, element powiązania transportu powinien również wyeksportować poprawne transportu identyfikatora URI w metadanych. Poniższy przykład kodu jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
#### <a name="wsdl-export"></a>Eksportu WSDL  
 Aby wyeksportować informacje dotyczące adresowania, `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interfejsu. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda dodaje poprawnych informacji adresowania do portu WSDL.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementacji <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda również eksportuje transportu identyfikatora URI, gdy punkt końcowy korzysta z powiązania protokołu SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importu WSDL  
 Aby rozszerzyć system importu WSDL do obsługi importowanie adresów, dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Podczas uruchamiania Svcutil.exe, istnieją dwie opcje w celu uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:  
  
1.  Punkt Svcutil.exe do pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.  
  
2.  Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.  
  
 `UdpBindingElementImporter` Typ implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu. `ImportEndpoint` Metoda importuje adres z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodanie obsługi zasad  
 Element niestandardowego powiązania, można wyeksportować asercji zasad Powiązanie WSDL dla punktu końcowego usługi do wyrażenia możliwości tego elementu powiązania. Poniższy przykład kodu jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
#### <a name="policy-export"></a>Eksportowanie zasad  
 `UdpTransportBindingElement` Typ implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> się Dodaj pomoc techniczna dotycząca eksportowania zasad. W rezultacie <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` podczas generowania zasady dla powiązania zawierający go.  
  
 W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, Dodaj potwierdzenie dla protokołów UDP i innym potwierdzenie, jeśli kanał jest w trybie multiemisji. Jest to spowodowane ma wpływ tryb multiemisji jak stos komunikacji jest tworzony i dlatego musi być koordynowane między obie strony.  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Ponieważ elementy powiązania transportu niestandardowego jest odpowiedzialny za obsługę adresowania, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementacji na `UdpTransportBindingElement` muszą również obsługiwać eksportowania odpowiednie WS-Addressing asercji zasad do wskazania wersji WS-Addressing jest używane.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importuj zasady  
 Aby rozszerzyć system importu zasad, dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Następnie wdrożymy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naszych zarejestrowanych klasy (`UdpBindingElementImporter`). W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, sprawdź potwierdzenia w odpowiedniej przestrzeni nazw i przetworzyć te generowania transportu i sprawdzanie, czy jest multiemisji. Ponadto należy usunąć potwierdzenia, które obsługuje importera z listy powiązania potwierdzenia. Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje integracji:  
  
1.  Punkt Svcutil.exe do naszego pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.  
  
2.  Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowych standardowego powiązanie importera  
 Svcutil.exe i <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typu, domyślnie, rozpoznaje i importować powiązania dostarczane przez system. W przeciwnym razie powiązanie pobiera importowane jako <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienia. Aby włączyć Svcutil.exe i <xref:System.ServiceModel.Description.WsdlImporter> do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importera niestandardowego powiązania standardowych.  
  
 Implementuje importera niestandardowego powiązania standardowa `ImportEndpoint` metody <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu do sprawdzenia <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienia zaimportowane z metadanych, aby zobaczyć, jeśli może ona zostać wygenerowane przez określone powiązanie standardowe.  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Ogólnie rzecz biorąc Implementowanie importera niestandardowego powiązania standardowa polega na sprawdzeniu właściwości elementów wiązania zaimportowanych, aby sprawdzić, czy tylko właściwości, które można ustawić przez powiązanie standardowe zostały zmienione, a wszystkie pozostałe właściwości są ich wartości domyślne. Podstawowe strategii wykonywania importera Powiązanie standardowe jest utworzenie wystąpienia standard powiązania Propagacja powiązania właściwości z elementy powiązania wystąpienie Powiązanie standardowe, które obsługuje standardowe powiązania w celu porównania elementy wiązania standardowa elementami importowanych powiązania.
