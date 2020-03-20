---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 0ec8c3286037e7adbe6f5efb73e846a30b9d48d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185664"
---
# <a name="configuration-and-metadata-support"></a>Konfiguracja i obsługa metadanych
W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązań i elementów wiązania.  
  
## <a name="overview-of-configuration-and-metadata"></a>Omówienie konfiguracji i metadanych  
 W tym temacie omówiono następujące zadania, które są opcjonalnymi elementami 1, 2 i 4 na liście zadań [Kanały programowe.](developing-channels.md)  
  
- Włączanie obsługi pliku konfiguracji dla elementu wiązania.  
  
- Włączanie obsługi plików konfiguracji dla powiązania.  
  
- Eksportowanie WSDL i potwierdzeń zasad dla elementu wiązania.  
  
- Identyfikowanie WSDL i potwierdzeń zasad, aby wstawić i skonfigurować element wiązania lub powiązania.  
  
 Aby uzyskać informacje dotyczące tworzenia powiązań zdefiniowanych przez użytkownika i elementów wiązania, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md) i tworzenie [bindingelement](creating-a-bindingelement.md), odpowiednio.  
  
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby włączyć obsługę plików konfiguracji dla kanału, należy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>zaimplementować dwie sekcje <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> konfiguracji, który umożliwia obsługę konfiguracji dla elementów wiązania i i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, które umożliwiają obsługę konfiguracji dla powiązań.  
  
 Łatwiejszym sposobem jest użycie przykładowego narzędzia [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) do generowania kodu konfiguracji dla powiązań i elementów wiązania.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozszerzanie bindingElementExtensionElement  
 Poniższy przykładowy kod jest pobierany z transport: przykład [UDP.](../samples/transport-udp.md) Jest `UdpTransportElement` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> to, który `UdpTransportBindingElement` udostępnia do systemu konfiguracji. Z kilku podstawowych zastąpienia, przykład definiuje nazwę sekcji konfiguracji, typ elementu wiązania i jak utworzyć element wiązania. Użytkownicy mogą następnie zarejestrować sekcję rozszerzenia w pliku konfiguracyjnym w następujący sposób.  
  
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
  
 Rozszerzenie można odwoływać się od niestandardowych powiązań do korzystania z protokołu UDP jako transportu.  
  
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
 Sekcja `SampleProfileUdpBindingCollectionElement` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> jest, która `SampleProfileUdpBinding` udostępnia do systemu konfiguracji. Większość implementacji jest delegowana `SampleProfileUdpBindingConfigurationElement`do , który <xref:System.ServiceModel.Configuration.StandardBindingElement>pochodzi z . Ma `SampleProfileUdpBindingConfigurationElement` właściwości, które odpowiadają właściwości `SampleProfileUdpBinding`na , i funkcje do mapowania z `ConfigurationElement` powiązania. Na koniec `OnApplyConfiguration` metoda jest zastępowana `SampleProfileUdpBinding`w , jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Aby zarejestrować ten program obsługi w systemie konfiguracji, dodaj następującą sekcję do odpowiedniego pliku konfiguracyjnego.  
  
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
  
 Następnie można się do niego odwoływać z [ \<sekcji system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) konfiguracji.  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Dodawanie obsługi metadanych dla elementu wiązania  
 Aby zintegrować kanał z systemem metadanych, musi obsługiwać zarówno importowanie, jak i eksport zasad. Dzięki temu narzędzia, takie jak [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klientów elementu wiązania.  
  
### <a name="adding-wsdl-support"></a>Dodawanie obsługi WSDL  
 Element wiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji adresowych w metadanych. Podczas korzystania z powiązania SOAP element wiązania transportu należy również wyeksportować poprawny identyfikator URI transportu w metadanych. Poniższy przykładowy kod jest pobierany z transport: przykład [UDP.](../samples/transport-udp.md)  
  
#### <a name="wsdl-export"></a>Eksport WSDL  
 Aby wyeksportować `UdpTransportBindingElement` informacje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> adresowe, implementuje interfejs. Metoda <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> dodaje poprawne informacje adresowe do portu WSDL.  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Implementacja `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody eksportuje również transportowy identyfikator URI, gdy punkt końcowy używa powiązania SOAP:  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Aby rozszerzyć system importowania WSDL na obsługę importowania adresów, dodaj następującą konfigurację do pliku konfiguracyjnego programu Svcutil.exe, jak pokazano w pliku Svcutil.exe.config:  
  
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
  
 Podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje ładowania rozszerzenia importu WSDL przez program Svcutil.exe:  
  
1. Punkt Svcutil.exe do pliku konfiguracyjnego przy użyciu\<pliku /SvcutilConfig:>.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.  
  
 Typ `UdpBindingElementImporter` implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejs. Metoda `ImportEndpoint` importuje adres z portu WSDL:  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Element wiązania niestandardowego można eksportować potwierdzeń zasad w powiązanie WSDL dla punktu końcowego usługi do wyrażania możliwości tego elementu wiązania. Poniższy przykładowy kod jest pobierany z transport: przykład [UDP.](../samples/transport-udp.md)  
  
#### <a name="policy-export"></a>Eksport zasad  
 Typ `UdpTransportBindingElement` implementuje, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> aby dodać obsługę zasad eksportowania. W rezultacie <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` w generowaniu zasad dla dowolnego powiązania, które go zawiera.  
  
 W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, dodaj asercja dla UDP i innego potwierdzenia, jeśli kanał jest w trybie multiemisji. Jest tak, ponieważ tryb multiemisji wpływa na sposób konstruowania stosu komunikacji, a zatem musi być skoordynowane między obiema stronami.  
  
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
  
 Ponieważ niestandardowe elementy wiązania transportu są <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> odpowiedzialne za `UdpTransportBindingElement` obsługę adresowania, implementacja na musi również obsługiwać eksportowanie odpowiednich potwierdzeń zasad adresowania WS, aby wskazać wersję używanego adresowania WS.  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zasad  
 Aby rozszerzyć system importu zasad, dodaj następującą konfigurację do pliku konfiguracyjnego programu Svcutil.exe, jak pokazano w pliku Svcutil.exe.config:  
  
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
  
 Następnie wdrażamy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naszej`UdpBindingElementImporter`zarejestrowanej klasy ( ). W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zbadać potwierdzenia w odpowiednim obszarze nazw i przetwarzać te do generowania transportu i sprawdzanie, czy jest multiemisji. Ponadto należy usunąć twierdzenia, które importer obsługuje z listy potwierdzeń wiązania. Ponownie, podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje integracji:  
  
1. Punkt Svcutil.exe do naszego pliku konfiguracyjnego za\<pomocą pliku /SvcutilConfig:>.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego importera wiązania standardowego  
 Program Svcutil.exe <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> i typ domyślnie rozpoznają i zaimportują powiązania dostarczone przez system. W przeciwnym razie powiązanie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> zostanie zaimportowane jako wystąpienie. Aby włączyć Svcutil.exe <xref:System.ServiceModel.Description.WsdlImporter> i `SampleProfileUdpBinding` importować `UdpBindingElementImporter` również działa jako importer wiązania standard niestandardowy.  
  
 Importer wiązania niestandardowego standard `ImportEndpoint` implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> metodę w <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> interfejsie, aby sprawdzić wystąpienie importowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.  
  
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
  
 Ogólnie rzecz biorąc implementowanie importera wiązania niestandardowego standard polega na sprawdzeniu właściwości importowanych elementów wiązania, aby sprawdzić, czy tylko właściwości, które mogły zostać ustawione przez standardowe powiązanie zostały zmienione i wszystkie inne właściwości są ich wartościami domyślnymi. Podstawową strategią wdrażania standardowego importera wiązania jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów wiązania do standardowego wystąpienia wiązania, które obsługuje standardowe powiązanie, oraz porównywanie powiązania elementy ze standardowego powiązania z importowanymi elementami wiązania.
