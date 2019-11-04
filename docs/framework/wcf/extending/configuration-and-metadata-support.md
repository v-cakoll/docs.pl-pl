---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 3f6d506d719cbb1b2ecc8bae223dfe73e7e2d1a9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425129"
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
 Aby włączyć obsługę plików konfiguracyjnych dla kanału, należy zaimplementować dwie sekcje konfiguracji <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, co umożliwia obsługę konfiguracji dla elementów powiązania oraz <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, które umożliwiają obsługę konfiguracji powiązań.  
  
 Łatwiejszym sposobem jest użycie narzędzia przykładowej [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) do wygenerowania kodu konfiguracji powiązań i elementów powiązania.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozszerzanie BindingElementExtensionElement  
 Następujący przykładowy kod jest pobierany z [transportu: przykład protokołu UDP](../samples/transport-udp.md) . `UdpTransportElement` jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>, który uwidacznia `UdpTransportBindingElement` do systemu konfiguracji. Za pomocą kilku podstawowych zastąpień, przykład definiuje nazwę sekcji konfiguracji, typ elementu powiązania i sposób tworzenia elementu powiązania. Następnie użytkownicy mogą zarejestrować sekcję rozszerzenia w pliku konfiguracji w następujący sposób.  
  
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
 Sekcja `SampleProfileUdpBindingCollectionElement` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>, który uwidacznia `SampleProfileUdpBinding` do systemu konfiguracji. Zbiorcza implementacja jest delegowana do `SampleProfileUdpBindingConfigurationElement`, który pochodzi z <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` ma właściwości, które odpowiadają właściwościom `SampleProfileUdpBinding`i funkcje do mapowania na podstawie powiązania `ConfigurationElement`. Na koniec Metoda `OnApplyConfiguration` zostanie zastąpiona w `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
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
  
 Można się do niego odwoływać z sekcji konfiguracji [> System. serviceModel\<](../../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
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
 Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji dotyczących adresowania w metadanych. W przypadku korzystania z powiązania SOAP element powiązania transportu powinien również eksportować prawidłowy identyfikator URI transportu w metadanych. Następujący przykładowy kod jest pobierany z [transportu: przykład protokołu UDP](../samples/transport-udp.md) .  
  
#### <a name="wsdl-export"></a>Eksport WSDL  
 Aby wyeksportować informacje dotyczące adresowania, `UdpTransportBindingElement` implementuje interfejs <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>. Metoda <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> dodaje do portu WSDL prawidłowe informacje dotyczące adresowania.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` implementacja metody <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> również eksportuje identyfikator URI transportu, gdy punkt końcowy używa powiązania SOAP:  
  
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
  
1. Wskaż plik konfiguracyjny Svcutil. exe, używając > pliku/SvcutilConfig:\<.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.  
  
 Typ `UdpBindingElementImporter` implementuje interfejs <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>. Metoda `ImportEndpoint` importuje adres z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Niestandardowy element powiązania może eksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi, aby przedstawić możliwości tego elementu powiązania. Następujący przykładowy kod jest pobierany z [transportu: przykład protokołu UDP](../samples/transport-udp.md) .  
  
#### <a name="policy-export"></a>Eksport zasad  
 Typ `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>, aby dodać obsługę eksportowania zasad. W związku z tym <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> zawiera `UdpTransportBindingElement` w generacji zasad dla dowolnego powiązania, które zawiera.  
  
 W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>Dodaj potwierdzenie protokołu UDP i inne potwierdzenie, jeśli kanał jest w trybie multiemisji. Jest to spowodowane tym, że tryb multiemisji wpływa na sposób konstruowania stosu komunikacji i w związku z tym musi być koordynowany między stronami.  
  
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
  
 Ponieważ niestandardowe elementy powiązania transportu są odpowiedzialne za obsługę adresowania, implementacja <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> na `UdpTransportBindingElement` musi również obsługiwać eksportowanie odpowiednich zatwierdzeń zasad WS-Addressing w celu wskazania używanej wersji WS-Addressing.  
  
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
  
 Następnie implementujemy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naszej zarejestrowanej klasy (`UdpBindingElementImporter`). W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>Sprawdź potwierdzenia w odpowiedniej przestrzeni nazw i Przetwarzaj je w celu wygenerowania transportu i sprawdzenia, czy jest to multiemisja. Ponadto Usuń potwierdzenia obsługiwane przez importera z listy potwierdzeń powiązań. Po uruchomieniu programu Svcutil. exe dostępne są dwie opcje integracji:  
  
1. Wskaż plik konfiguracyjny Svcutil. exe przy użyciu > pliku/SvcutilConfig:\<.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego importera powiązań standardowych  
 Svcutil. exe i typ <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>, domyślnie rozpoznawanie i importowanie powiązań dostarczonych przez system. W przeciwnym razie powiązanie zostanie zaimportowane jako wystąpienie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>. Aby umożliwić programowi Svcutil. exe i <xref:System.ServiceModel.Description.WsdlImporter> Importowanie `SampleProfileUdpBinding` `UdpBindingElementImporter` również działa jako niestandardowy importer powiązań standardowych.  
  
 Niestandardowy importer powiązań standardowych implementuje metodę `ImportEndpoint` w interfejsie <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>, aby sprawdzić wystąpienie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> zaimportowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.  
  
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
