---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 16c386f8479778c7d2f17fbdfdb95dee558baf52
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795839"
---
# <a name="configuration-and-metadata-support"></a>Konfiguracja i obsługa metadanych
W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązań i elementów powiązania.  
  
## <a name="overview-of-configuration-and-metadata"></a>Przegląd konfiguracji i metadanych  
 W tym temacie omówiono następujące zadania, które są elementami opcjonalnymi 1, 2 i 4 na liście zadań [Tworzenie kanałów](developing-channels.md) .  
  
- Włączanie obsługi pliku konfiguracji dla elementu powiązania.  
  
- Włączanie obsługi plików konfiguracyjnych dla powiązania.  
  
- Eksportowanie potwierdzeń WSDL i zasad dla elementu powiązania.  
  
- Identyfikowanie potwierdzeń WSDL i zasad w celu wstawienia i skonfigurowania elementu powiązania lub powiązania.  
  
 Aby uzyskać informacje na temat tworzenia powiązań zdefiniowanych przez użytkownika i elementów powiązania, zobacz temat [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md) i [Tworzenie BindingElement](creating-a-bindingelement.md)odpowiednio.  
  
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby włączyć obsługę plików konfiguracyjnych dla kanału, należy zaimplementować dwie sekcje <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>konfiguracji, umożliwiające obsługę konfiguracji elementów powiązania <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> oraz i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, które umożliwiają obsługę konfiguracji dla powiązań.  
  
 Łatwiejszym sposobem jest użycie narzędzia przykładowej [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) do wygenerowania kodu konfiguracji powiązań i elementów powiązania.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozszerzanie BindingElementExtensionElement  
 Następujący przykładowy kod jest pobierany z [transportu: Przykład](../samples/transport-udp.md) protokołu UDP. Jest to, który uwidacznia `UdpTransportBindingElement` system konfiguracji. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `UdpTransportElement` Za pomocą kilku podstawowych zastąpień, przykład definiuje nazwę sekcji konfiguracji, typ elementu powiązania i sposób tworzenia elementu powiązania. Następnie użytkownicy mogą zarejestrować sekcję rozszerzenia w pliku konfiguracji w następujący sposób.  
  
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
  
 Do rozszerzenia można odwoływać się z niestandardowych powiązań, aby użyć protokołu UDP jako transportu.  
  
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
 Sekcja `SampleProfileUdpBindingCollectionElement` jest<xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> udostępniana`SampleProfileUdpBinding` systemowi konfiguracyjnemu. Zbiorcza implementacja jest delegowana do `SampleProfileUdpBindingConfigurationElement`elementu, który pochodzi od. <xref:System.ServiceModel.Configuration.StandardBindingElement> Zawiera właściwości, które odpowiadają właściwościom w `SampleProfileUdpBinding`, i `ConfigurationElement` funkcji, które mają być mapowane na podstawie powiązania. `SampleProfileUdpBindingConfigurationElement` Na `OnApplyConfiguration` koniec Metoda zostanie zastąpiona `SampleProfileUdpBinding`w, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, należy dodać następującą sekcję do odpowiedniego pliku konfiguracji.  
  
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
  
 Można go następnie przywoływać z [ \<sekcji konfiguracji > System. ServiceModel](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Dodawanie obsługi metadanych dla elementu powiązania  
 Aby zintegrować kanał z systemem metadanych, musi on obsługiwać Importowanie i eksportowanie zasad. Umożliwia to narzędziom, takim jak [Narzędzie do metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , generowanie klientów elementu powiązania.  
  
### <a name="adding-wsdl-support"></a>Dodawanie obsługi WSDL  
 Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji dotyczących adresowania w metadanych. W przypadku korzystania z powiązania SOAP element powiązania transportu powinien również eksportować prawidłowy identyfikator URI transportu w metadanych. Następujący przykładowy kod jest pobierany z [transportu: Przykład](../samples/transport-udp.md) protokołu UDP.  
  
#### <a name="wsdl-export"></a>Eksport WSDL  
 Aby wyeksportować informacje dotyczące adresowania `UdpTransportBindingElement` , <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> implementuje interfejs. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda dodaje do portu WSDL prawidłowe informacje dotyczące adresowania.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementacja<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody także eksportuje identyfikator URI transportu, gdy punkt końcowy używa powiązania SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Import WSDL  
 Aby zwiększyć system importowania WSDL do obsługi importowania adresów, Dodaj następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config:  
  
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
  
 Podczas uruchamiania programu Svcutil. exe dostępne są dwie opcje pobrania pliku Svcutil. exe w celu załadowania rozszerzeń WSDL:  
  
1. Wskaż plik konfiguracyjny Svcutil. exe przy użyciu pliku/svcutilConfig:\<>.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.  
  
 `UdpBindingElementImporter` Typ<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implementuje interfejs. `ImportEndpoint` Metoda importuje adres z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Niestandardowy element powiązania może eksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi, aby przedstawić możliwości tego elementu powiązania. Następujący przykładowy kod jest pobierany z [transportu: Przykład](../samples/transport-udp.md) protokołu UDP.  
  
#### <a name="policy-export"></a>Eksport zasad  
 Typ `UdpTransportBindingElement` implementuje<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> , aby dodać obsługę eksportowania zasad. W efekcie <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` generowanie zasad dla dowolnego powiązania, które zawiera.  
  
 W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>programie Dodaj potwierdzenie protokołu UDP i inne potwierdzenie, jeśli kanał jest w trybie multiemisji. Jest to spowodowane tym, że tryb multiemisji wpływa na sposób konstruowania stosu komunikacji i w związku z tym musi być koordynowany między stronami.  
  
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
  
 Ponieważ niestandardowe elementy powiązania transportu są odpowiedzialne za obsługę adresowania <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> , implementacja `UdpTransportBindingElement` na serwerze musi również obsługiwać eksportowanie odpowiednich potwierdzeń zasad WS-Addressing w celu wskazania wersji WS-Addressing jest używany.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importowanie zasad  
 Aby zwiększyć system importowania zasad, należy dodać następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config:  
  
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
  
 Następnie implementujemy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> nasze zarejestrowanej klasy`UdpBindingElementImporter`(). <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>Sprawdź potwierdzenia w odpowiedniej przestrzeni nazw i przetwórz je w celu wygenerowania transportu i sprawdzenia, czy jest to multiemisja. Ponadto Usuń potwierdzenia obsługiwane przez importera z listy potwierdzeń powiązań. Po uruchomieniu programu Svcutil. exe dostępne są dwie opcje integracji:  
  
1. Wskaż plik konfiguracyjny Svcutil. exe przy użyciu pliku/svcutilConfig:\<>.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego importera powiązań standardowych  
 Svcutil. exe i <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, domyślnie, rozpoznawanie i importowanie powiązań dostarczonych przez system. W przeciwnym razie powiązanie zostanie zaimportowane jako <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienie. Aby umożliwić programowi Svcutil. exe <xref:System.ServiceModel.Description.WsdlImporter> i `SampleProfileUdpBinding` zaimportować `UdpBindingElementImporter` go również jako niestandardowego importera powiązań standardowych.  
  
 Niestandardowy importer powiązań standardowych implementuje `ImportEndpoint` metodę <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> w interfejsie, aby sprawdzić <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienie zaimportowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.  
  
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
  
 Ogólnie rzecz biorąc, implementacja niestandardowego importera powiązań standardowych polega na sprawdzeniu właściwości zaimportowanych elementów powiązania, aby sprawdzić, czy zmieniono tylko właściwości, które mogły zostać ustawione przez powiązanie standardowe, a wszystkie inne właściwości są ich domyślnymi. Podstawową strategią wdrażania importera powiązań standardowych jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów powiązania do standardowego wystąpienia powiązania, które obsługuje powiązanie standardowe, oraz porównanie powiązania elementy ze standardowego powiązania z zaimportowanymi elementami powiązania.
